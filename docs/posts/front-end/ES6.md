---
date: 2024-04-14
category:
  - 前端
tag:
  - ES6
sticky: 10
archive: false
---

# ES6

ECMAScript是语言标准

## const
一旦声明,立即初始化,允许在不重新赋值的情况下修改它的值（如object）

## let,const,var区别

### 重复声明
- var允许重复声明,let、const不允许

### 变量提升
- var会提升变量的声明到当前作用于的顶部
- let与const不存在变量提升

### 暂时性死区
只要作用域内存在let,const,他们所声明的变量或者常量就自动绑定这个区域，不再受外部作用域的影响

```js
let a = 2
let b = 3

function fn(){
  console.log(b); => 3
  console.log(a); // error
  let a
}
```

- let 与const存在暂时性死区,而var不存在

### window对象的属性和方法

- 全局作用域内,var声明的变量和函数会自动挂载到window对象上,let与const不会

### 块级作用域

- var 没有块级作用域，let与const有

## 模版字符串

模版字符串中，所有的空格、换行或缩进都会保留在输出之中

```js
`字符'串${变量名}\n\\\`字符串${getAge(person)},${2+2}`
```

## 箭头函数

```js
const add = (x,y) =>{
  return x+y
}
add(1,1)

const pow = x =>{
  return x*x
}

const mul = x => x*2

const add1 = (x,y)=>({
  value: x+y
})


const sum = (x,y) => [x,y]
```

### 不适合使用箭头函数的地方

- 作为构造函数
- 需要this指向调用对象的时候
- 需要使用arguments的时候

## this指向

```js
console.log(this); => window

function add(){
  console.log(this); => //不确定,只和谁调用有关
}
add() => window => // 非严格模式下

'use strict'
add() => undefined // 严格模式下
```

::: warning
箭头函数没有自己的this
函数中的this只和谁调用它有关,与谁赋值,谁定义均无关
匿名函数的this,undefined -> window
箭头函数嵌套时,this一层一层往上找
:::

```js
const calc = {
  add: ()=>{
    console.log(this);
  }
}

calc.add() => // 箭头函数没有作用域,{}也没有作用域,所以找到了window
```

## 解构赋值

### 数组的解构赋值

数组能够解构的条件
- 模式或结构能匹配上(条件1)
- 索引值相同的完成赋值(条件2)
- 默认值为undefined
- 默认值只有在一个数组的成员严格等于(===)undefined时,对应的默认值才会有效

```js
const arr = [1,2,3]
console.log(...arr); // 1,2,3

const [a,b,c] = [1,2,3]
console.log(a,b,c); // 1,2,3

const [a,[,,b],c] = [1,[2,4,5],3]

console.log(a,b,c); // 1,5,3

const [a= 1,b = 2] = []
console.log(a,b); // 1,2
```

### 对象的解构赋值

- 模式或结构能匹配上
- 属性名相同的完成赋值
- 可以取到继承的属性,顺着原型链来找

## 对象字面量的增强

- 属性和方法的简洁表示法
- 方括号语法

```js
const age = 18
const person = {
  age,
  speak: function(){
    console.log('speak');
  },
  sleep(){
    console.log('sleep');
  }
}

const prop = 'age'
const func = ()=>'age2'
const p = {
  [func()]: 28
}
p[prop] = 18
console.log(p); // {age: 18,age2: 28}
```

## 剩余参数

```js
const add = (x,y,...args)=>{
  console.log(x,y);
  console.log(args);
}

add() // undefined undefined []
add(1)
add(1,2)
add(1,2,3,4) // 1,2 [3,4]
```

## 数组展开运算符的基本用法

```js
const args = [2,1,3,4]
Math.min(2,1,3,4)
Math.min(...args)
```

### 复制数组

```js
const a = [1,2]
const c = [...a] // 展开后,与a的数值不再有任何关系
```

### 合并数组

```js
const a = [1,2]
const b = [1,2]
const c = [...a,66,77,88,...b] // 展开后,与a,b的数值不再有任何关系
```

### 字符串转数组
```js
const str = ...'alex'

const str1 = 'alex'.split('')
```

### 获取数组索引
```js
arr = [1,2,3]
arr.keys() // [0,1,2]
arr.values() // [1,2,3]
arr.entries() // 同时获取key与value [] [0,1] [1,2],[2,3]
for(const [index,value] of arr.entries()){
  console.log(index,value);
}
```

## 对象操作

### 展开对象/复制对象

```js
const apple = {
  color: 'red',
  taste: '甜'
}

const apple1 = {...apple}
```

### 合并对象

```js
const apple = {
  color: 'red',
  taste: '甜'
}

const pen {
  color: '黑',
  use: '写字'
}

const mixed = {...apple, ...pen} // 后面属性值会覆盖前面的，对象中的对象属性不会合并
```

## Set 

集合

- 数组是一些列的数据集合
- Set 是一组无序,没有重复的数据集合
- Set不能用下标访问,因为其无序
- 只能有一个NaN
- ...set => 数组

```js
const s = new Set()
s.add(1)
s.add(2)
s.add(3)
console.log(s);
```

### 方法

- add 添加成员
- has 判断是否有某个成员
- delete 删除某个成员
- clear 全部删除
- forEach
- size 成员个数
  
```js
s.forEach(function(value,key,set){
  // value = key
  console.log(value,key,set === s); // x,x true
  console.log(this); //document
},document)
```

### Set构造函数的参数

```js
const s = new Set([1,2,1])
console.log(s); // Set(2){1,2}

const s1 = new Set('hello')
console.log(s1); // 类数组
```

### 数组去重

- 把数组传给Set
- 再展开Set

### 字符串去重

```js
[...new Set('abacdfesafad')].join('')
```

### 存放DOM

## Map

键值对集合
与对象的区别,对象一般用字符串当键
Map可以把基本数据类型,引用数据类型,都可以作为Map的键
```js
const m = new Map()
m.set('name','rubyc')
console.log(m);
```

### Map的实例方法和属性

- set 添加成员
- get 获取成员值
- has 判断有没有某成员
- delete 删除成员
- clear 全部删除
- forEach

```js
m.forEach(function(value,key,map){
  console.log(value,key,map === m)
  console.log(this); // document
},document)
```

### Map的构造函数的参数

```js
console.log(new Map([
  ['name': 'alex'],
  ['age': 18]
]));
```

## Iterator-迭代器

```js
const it = [1,2][Symbol.iterator]()
console.log(it.next());
console.log(it.next());
```

## for...of(用来代替迭代器)

```js
for(const item of arr){
  console.log(item);
}
```

## 字符串相关

### includes

```js
'abc'.includes('a',0) => true
'abc'.includes('a',1) => false
'abc'.includes('ab') => true
```

### padStart和padEnd()

```js
'x'.padStart(5,'ab') // ababx
'x'.padEnd(5,'ab') // xabab
'1'.padStart(2,0) // 01
'10'.padStart(2,0) // 10
```

### trimStart()和trimEnd()

```js
'   abc'.trimStart() // abc
'   abc'.trimLeft() // abc
'abc  '.trimEnd() // abc
'abc  '.trimRight() // abc
'    abc  '.trim() // abc
```

### Array.from()

```js
Array.from('hello') // ['h','e','l','l','o']
```

### find()和findIndex()

```js
[1,5,10,15].find((value,index,arr)=>{
  return value > 9
}) // 10

[1,5,10,15].findIndex((value,index,arr)=>{
  return value > 9
}) // 2
```

## 对象相关

### Object.assign()

```js
Object.assign(object1,object2)
Object.assign({},object1,object2) // 返回新对象，object1就不会变化
{...object1,...object2}
```

### Object.keys()

### Object.values()

### Object.entries()

```js
const person = {
  name: 'Alex',
  age: 18
}

console.log(Object.keys(person));
console.log(Object.values(person));
console.log(Object.entries(person));
```

与数组三个方法的区别

- 数组三个方法返回的都是实例方法，返回的都是Iterator
- 对象三个方法返回的都是构造函数方法，返回的都是数组