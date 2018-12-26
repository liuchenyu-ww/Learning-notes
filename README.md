# 前端面试之道

> JS基础知识点及常考面试题

## 原始 (Primitive) 类型

```
涉及面试题: 原始类型有哪几种？null是对象嘛？
```

在js中，存在着6种原始值，分别是:
- boolean
- null
- undefined
- number
- string
- symbol

JS的 `number` 类型是浮点类型的, 在使用中会遇到某些Bug, 比如 `0.1 + 0.2 !== 0.3` , 

`String` 类型是不可变的，无论你再 `string` 类型上调用何种方法，都不会对值有改变。

另外对于 `null` 来说, 很多人会认为他是个对象类型, 其实这是错误的. 虽然 `typeof null` 会输出 `object` , 但是这只是JS存在的一个悠久的Bug. 在JS的最初版本中使用的是32位系统, 为了性能考虑使用低位存储变量的类型信息, ·000· 开头代表的是对象, 然而 `null` 表示为全零, 所以将它错误的判断为 `object` . 虽然现在的内部类型判断代码已经改变了, 但是对于这个Bug却是一直流传了下来.


## 对象 (Object) 类型

```
涉及面试题:对象类型和原始类型的不同之处？ 函数参数是对象会发生什么问题？
```

在JS中, 出了原始类型那么其他的都是对象类型了. 对象类型和原始类型不同的是, 原始类型存储的是值, 对象类型存储的地址. 当你创建了一个对象类型的时候, 计算机会在内存中帮我们开辟一个空间来存放值, 但是我们需要找到这个空间, 这个空间会拥有一个地址.

```
const a = []
```

对于常量 `a` 来说, 假设内存地址为 `#001`, 那么在地址 `#001` 的位置放了值 `[]`, 常量 `a` 存放了地址 `#001` , 再看一下代码

```
const a = []

const b = a

b.push(1)
```

当我们将变量赋值给另一个变量时, 复制的时原本变量的地址, 也就是说当前变量 `b` 存放的地址也是 `#001` , 当我们惊醒数据修改的时候, 就会修改存放在地址 `#001` 上的值, 也就导致了两个变量的值都发生了改变.

接下来我们来看函数参数时对象的情况

```
function test(person) {
  person.age = 26
  person = {
    name: 'yyy',
    age: 30
  }

  return person
}

const p1 = {
  name: 'yck',
  age: 25
}

const p2 = test(p1)

console.log(p1) //  ->?
console.log(p2) //  ->?

答案
{name: "yck", age: 26}  // p1
{name: "yyy", age: 30}  // p2
```

解析:

- 首先, 函数传参是传递对象指针的副本
- 到函数内部修改参数的属性这步, 当前 `p1` 的值已经被修改了
- 但是重新为 `person` 分配了一个对象时就出现了分歧, 下图

![解析](https://user-gold-cdn.xitu.io/2018/11/14/16712ce155afef8c?imageView2/0/w/1280/h/960/format/webp/ignore-error/1)

















<!-- ## 前台应用技术栈

>
[Vue2+](https://cn.vuejs.org/v2/guide/) 

[Element](http://element-cn.eleme.io/#/zh-CN)

[Echarts](http://echarts.baidu.com/)

[Jquery](https://jquery.com/)

[axios](https://www.axios.com/) -->


## 关于笔记

```
JS学习之路，不断进步
```

## 笔记攥写人

```
AiLuoLiuCenYu -刘
```
