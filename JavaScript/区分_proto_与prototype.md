# JavaScript原型介绍

## 一 什么是原型

原型是JavaScript中最常听到的一个概念，要了解什么是原型，我们只需要了解一下几点：

第一，	每个对象都有原型，原型也是一个对象
第二，	每个函数在创建时都会有一个与之对应的原型对象，并包含一个指针指向它的原型对象。原型对象也可能拥有原型。
第三，	与普通对象不同的是，在原型上定义的属性和方法是所有实例共享的，这个特性是 JavaScript中实现继承的原理。

## 二 prototype和__proto__

上面说到，每个对象都有原型，我们会在很多书中见到一些与原型有关的示例，会发现有的地方指向原型对象的指针是prototype，有些地方是__proto__，经常会使人产生一些疑惑，这两个指针是同一个么？后者是前者的缩写么？如果不是，那这两个指针有什么区别呢，分别在什么情境下应用呢？我们带着下面的问题继续向下看。
每个对象中都有指向原型对象的指针，这个指针是[[prototype]]，但是这个指针是对象的内部属性，也就是说我们无法使用.[[prototype]]的方式使用。__proto__是Firefox和chrome中对[[prototype]]的实现。所以现在我们知道_proto_指针指向的是对象的原型。那一个普通对象（非函数）的原型是什么，这里涉及到了继承的原理，本文的下面会讨论，现在只需要知道默认情况下，每个对象的原型指针都是指向它构造函数的原型。我们看下面的例子。

    function Person(name, age){
        this.name = name;
        this.age = age;
     }
    var person1 = new Person("lily",18)
    
在这个例子中，person1的构造函数是Person，那么person的原型是什么，就是接下来要介绍的prototype指针。

在JavaScript中，函数也是对象，但是不同的是，函数除了__proto__指针之外，还有另外一个原型指针，即prototype，这个指针指向的是函数自己的原型，也就是说，函数作为对象，有一个__proto__指针指向创建它的构造函数的原型，而函数作为其他对象的构造函数，有着属于自己的原型。接下来考虑Person的构造函数。虽然Person在这里是作为构造函数使用，但是它仍然是一个函数，在JavaScript中，函数是继承自Function，那么可知，Person.__proto__指向的Function的原型，即Person.__proto__=== Function.prototype。

另外，原型对象会默认包含两个指针，一个__proto__指针，是原型对象作为一个对象拥有的指向其构造函数的原型的指针，还有一个constructor指针，指向的是创建了该原型的函数的引用。即person1.__proto__.constructor === Person。对象由于共享原型中的属性与方法，故对象也会从原型上继承constructor属性。整个这个例子的指针关系如下图所示。

 ![关系图](https://github.com/shly/notes/blob/master/JavaScript/shiyitu1.jpg)
 
之前有说到，原型也是一个对象，任何对象都有__proto__指针，那原型对象作为一个对象，它的__proto__也应该指向自己构造函数的原型。之前说到每个函数创建过程中都会有一个与之对应的原型对象，这个原型对象都是继承自Object，因此除了Object的原型外，所有的原型对象的__proto__指向的都是Object的原型，Object的原型的__proto__是null。
接下来，通过几个特殊的对象及实例对prototype及__proto__属性进行区分。
1.	对象字面量
var a = {}
这里a是一个最简单的对象字面量，按照上面的分析，它不是一个函数，因此没有prototype属性，它的__proto__应该指向它构造函数的原型，即Object的原型，下面我们在chrome的命令行中进行测试。运行结果如下。
  
     a.__proto__ === Object.prototype  => true
 
2.	引用类型
引用类型是一种能够数据结构，用于将数据和功能组织到一起，类似于Java中类的概念，引用类型的值是引用类型的示例，相当于Java中类的实例。JavaScript中的引用类型主要有以下几类：Object，Array，Date，RegExp，Function以及特殊的引用类型Boolean、Number和String。对于引用类型，我们需要知道的是在JavaScript中，引用类型是以函数的形式存在的，因此它们也有prototype属性，指向它们各自的原型，它们的属性与方法都是定义在原型上的，因此可以被所有的实例共享。除了Function和Object外，其他的引用类型的原型链基本相同。下图以Array类型为例说明引用类型的原型指针指向。

  ![关系图](https://github.com/shly/notes/blob/master/JavaScript/shiyitu2.jpg)
   
从图中可以看出，除了Object，其他的引用类型都继承自function，即其他引用类型的__proto__指向都是Function.prototype。另外Object的原型的__proto__指向为null。最后，对于prototype和__proto__，总结如下：

1.	__proto__不是规范，是chrome和Firefox等浏览器对[[prototype]]属性的实现

2.	任何对象都有[[prototype]]属性指针，指向构造函数的原型。包括原型对象和函数。

3.	函数作为特殊的对象，除了拥有[[prototype]]属性之外，还有prototype属性，指向自己的原型对象。

4.	原型对象的[[prototype]]属性指向Object的原型对象, Object的原型的[[prototype]]属性指向的是null。

5.	Function的prototype与__proto__的指向相同。

## 三 原型链

JavaScript中的对象将原型作为模板，从原型中继承方法和属性，原型对象本身又拥有原型，从它的原型中继承属性和方法，一层一层推进，构成了原型链，根据前面的介绍，Object的原型的__proto__属性是null，故原型链的终点是null。

 ![关系图](https://github.com/shly/notes/blob/master/JavaScript/shiyitu3.jpg)
    
上图展示的就是一个作用域链，在实例上找一个属性或方法，如果找不到会通过__proto__指针向上查找，找实例构造函数的原型上有没有该属性或方法。
四 继承
前面有提到JavaScript中的继承是利用原型实现的。原理是所有实例共享构造函数的原型。下面JavaScript中一个简单继承的实现方式：

     function Animal (name, age){
    this.name = name;
    this.age = age;
    }
    Animal.prototype.getName = function(){
        return this.name;
    }
    function Person(name, age, gender){
        Animal.call(this, name, age);
    this.gender = gender;
    }
    Person.prototype = new Animal ();
    var lily = new Person("lily","18","girl");
    lily.getName()  => lily
    
在这个实例中父类构造函数，子类构造函数和原型的关系如下图所示。

![关系图](https://github.com/shly/notes/blob/master/JavaScript/shiyitu4.jpg)
  
如图所示，在这个例子中方法是通过原型继承的，实例调用getName方法时是沿着原型链向上查找，最终在Aninmal的类的原型中找到的该方法从而调用的。而在构造函数中定义的属性则是通过call方法实现的继承，最后顺便介绍使用new操作符创建一个对象时都经历了哪些步骤：

1.	创建一个新对象

2.	这个新对象会被执行[[prototype]]连接

3.	这个新对象会绑定到函数调用的this

4.	如果函数没有返回其他对象，则new表达式中的函数调用会自动返回这个新对象。

例如：当代码 new Fun() 执行时，会执行以下步骤：

1.	创建一个继承自Fun.prototype的新的对象。

2.	构造函数 Fun被执行，执行的时候，相应的传参会被传入。当Fun ()没有参数时，Fun后面的()可以被省略（所以在很多书中创建对象使用的是 new Fun，没有后面的“()”）。

3.	this被绑定到这个新对象。

4.	如果构造函数返回了一个“对象”，那么这个对象会取代整个new出来的结果。如果构造函数没有返回对象，那么new出来的结果为步骤1创建的对象。
