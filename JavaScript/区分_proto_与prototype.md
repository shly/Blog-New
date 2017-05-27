# 区分_proto_与prototype
1. 对象都具有_proto_属性，指向创建它的构造函数的原型
2. 方法是一个特殊的对象，除了拥有_proto_属性外，还有prototype属性，指向自己的原型对象。方法都是继承自Function，故方法（包括构造函数）的_proto_应该都
指向Function.prototype
3. Object.prototype._proto_为null,故原型链的终点为null
