# 使用c-for时要设置key的原因

## v-for的基本使用方法

1. v-for="item in items"
2. v-for="(item, index) in items"

*可以用 of 代替 in ，因为它是最接近JavaScript迭代器的语法*
## Template v-for
1. v-for="item in items"
## 对象迭代
1. v-for="value in object"
2. v-for="(value, key) in object"
3. v-for="(value, key, index) in object"
## 整数迭代
1. v-for="n in 10"
## 组件和v-for
在自定义组件里，你可以像任何普通元素一样用 v-for
2.2.0+的版本里，当在组件中使用 v-for 时， key 现在是必须的。

    <my-component v-for="item in items" :key="item.id"></my-component>

由于 JavaScript 的限制， Vue 不能检测以下变动的数组：
当你利用索引直接设置一个项时，例如： vm.items[indexOfItem] = newValue
当你修改数组的长度时，例如： vm.items.length = newLength

解决方式
Vue.set(example1.items, indexOfItem, newValue)
// Array.prototype.splice`
example1.items.splice(indexOfItem, 1, newValue)
