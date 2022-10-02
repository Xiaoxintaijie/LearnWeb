### 数据类型

#### 1.基本数据类型
String Number Boolean Symbol Null Undefined

##### String Number Boolean 相互转化/类型转化规则
- == / !=
   > 判断类型->类型转换->判断大小
   > 判断两者类型是否为 `string` 和 `number`，是的话就会将字符串转换为 `number`
   > 判断其中一方是否为 `boolean`，是的话就会把 `boolean` 转为 `number` 再进行判断
- === / !== / Object.is
   > 无类型转化
   > 使用 Object.is 来进行相等判断时，一般情况下和三等号的判断相同，它处理了一些特殊的情况，
   > 比如 -0 和 +0 不再相等，两个 NaN 是相等的。
- 其他类型转化成String
- 其他类型转化成Number
   > 字符串 --> 数字 
   > 如果是纯数字的字符串，则直接将其转换为数字
   > 如果字符串中有非数字的内容，则转换为NaN
   > 如果字符串是一个空串或者是一个全是空格的字符串，则转换为0
- 其他类型转化成Boolean
  > 字符串 --> 布尔值
  > '' -->  false
- 隐式类型转化
   `+`操作符的两边有至少一个`string`类型变量时，两边的变量都会被隐式转换为字符串；其他情况下两边的变量都会被转换为数字
- 显式类型转化
  Number()
  parseInt()
  String()
  Boolean()

##### Null Undefined 区分

先有null,后有undefined

null:
- 新建一个对象但是还没想好存放什么
- 属于Object
- null + number = number

undefined: 
- 定义变量，但是未赋值
- 使用未定义的变量，会报错
- 函数默认参数值
- 函数默认返回值
- 属于undefined
- undefined + number = NaN

判断：
 null == undefined //true
 null === undefined  //false

 null === null  //true
 undefined === undefined  //true

#### 2.引用数据类型
Object

##### 种类
1. 内置对象
   > Array、Math、Data
2. 自定义对象
3. 宿主对象
   > BOM、DOM

##### 创建对象
new 
构造函数
工厂方法

##### 对象属性访问方式
- obj.name 
  静态的;
  不能访问数字的属性;

- obj['name']
  可以接收动态值;
  可以访问数字的属性;
  导致语法错误的字符,可以使用[]

##### 数组 对象 相互转化
- 数组转化成对象
1. ... 扩展运算符
```
const arr = ['one','two','three'];
const obj = {...arr};       
console.log(obj);    // { 0: 'one', 1: 'two', 2: 'three' }
```
2. Object.assign 
```
const arr = ['one','two','three'];
const obj = Object.assign({}, arr);
console.log(obj);       // { 0: 'one', 1: 'tow', 2: 'three' }
```
3. Object.fromEntries() 将一个**键值对数组**转为对象
```
const arr = [["name",'hello'],["age",18],["gender",false]];
const obj = Object.fromEntries(arr);
console.log(obj); //{name: 'hello', age: 18, gender: false}
```
4. forEach

- 对象转化成数组
1. Object.entries() 
   返回一个对象自身的（不含继承的）所有可遍历属性的**键值对的数组**
```
const obj = { foo: 'bar', baz: 42 };
const arr = Object.entries(obj)
console.log(arr); 
// (2) [Array(2), Array(2)]
// 0: (2) ['foo', 'bar']
// 1: (2) ['baz', 42]
```
2. Object.keys()
   返回自身的（不含继承的）所有可遍历属性的**键名的数组**
```
const obj = { foo: 'bar', baz: 42 };
const arr = Object.keys(obj)
console.log(arr); 
// ['foo','baz']
```

3. Object.values()
   返回自身的（不含继承的）所有可遍历属性的**键对应值的数组**
```
const obj = { foo: 'bar', baz: 42 };
const arr = Object.values(obj)
console.log(arr); 
// ['bar',42]
```
4. Array.from()
   将两类对象转为真正的数组：
   类似数组的对象和可遍历的对象(包括 ES6 新增的数据结构 Set 和 Map)
```
let arrayLike = {
    '0': 'a',
     1 : 12,
     length: 3
};
let arr2 = Array.from(arrayLike);
console.log(arr2);
// ['a', 12 ,undefined]
```

##### 数组 对象 合并方式
- 数组
  扩展运算符 ...
  concat 合并两个数组，返回新数组
  slice 创建一个包含原有数组中一个或多个元素的新数组，不会影响原始数组

- 对象
  扩展运算符 ...
  > ```
  > let bar1 = { a: 1, b: 2 };
  > let bar2 = { c: 1, b: 5 };
  > let bar3 = {...bar1,...bar2};
  > console.log(bar3); // {a: 1, b: 5, c: 1}
  > ```
  assign
  _.deepClone

##### 确认数组的方法
检测类型的两种方法
Array.isArray(obj) 返回布尔值

##### 数组常用方法区分
some
every
fliter
find
findIndex
Map
forEach
reduce
splice
slice

#### 3.存放方式 
基本数据类型存放在**栈**
> 简单数据段，占据空间小、大小固定，属于被频繁使用数据
> 先进后出
> 栈区内存由编译器自动分配释放

引用数据类型值存放在**堆**，地址存放在**栈**
> 占据空间大、大小不固定
> 优先队列，是按优先级来进行排序的，优先级可以按照大小来规定。
> 堆区内存一般由开发着分配释放，若开发者不释放，程序结束时可能由**垃圾回收机制**回收。

#### 4.检测类型方法
- typeof 
  使用方式：console.log(typeof null); // 'object' 
  返回变量基本类型的字符串
  只能识别基本数据类型，除了function不能识别其他引用数据类型
  可以用于判断变量是否存在

- instanceof
  使用方式：object instanceof constructor 
  返回布尔值
  可以准确地判断复杂引用数据类型，但是不能正确判断基础数据类型

- Object.prototype.toString(.call)
  使用方式：Object.prototype.toString.call(1)    // "[object Number]"
  返回统一格式字符串：“[object Xxx]” 
  所有数据类型均可以判断

### ES6
- let const 
- 箭头函数
- 扩展运算符
  > 复制/合并数组，类数组转数组，数组转化成对象，
  > 复制/合并对象
- rest参数
  > arguments
- 解构赋值
  > 对象：严格以属性名作为定位依据
  > 数组：以元素的位置为匹配条件
  > 扩展运算符可以与解构赋值结合起来，用于生成数组，要放在最后
- promise
- 模板字符串
- Symbol
- 模块化
- Class类 --- prototype
- async await

#### 1.ES6新增数组方法
**Array.from()**
Array.of()

copyWithin()
find()、findIndex() 查找
fill() 使用给定值，填充一个数组
entries()，keys()，values() 遍历
includes() 判断数组是否包含给定的值,返回布尔值
flat()，flatMap() 将数组扁平化处理，返回一个新数组，对原数据没有影响


#### 2.ES6新增对象方法
**Object.is** 比较两个值是否严格相等
**Object.assign** 对象的合并
Object.getOwnPropertyDescriptors()
Object.setPrototypeOf()，Object.getPrototypeOf()
**Object.keys()，Object.values()，Object.entries()** 对象转化成数组
**Object.fromEntries()** 数组转化成对象

#### 3.深浅拷贝
- 深拷贝
  lodash.deepClone

- 浅拷贝
  1. assign(target,source)
   > 克隆
   > 复制（可以多个复制给一个）
   > 追加值，值覆盖
   > 合并（对象）
  2. ...
   > 克隆和合并数组 类数组转数组
   > 克隆和合并对象
  3. concat() 直接调用
  4. slice(begin,end) 参数是数字，end表示不包括，默认一直到末尾

#### 4.let var const 区别
允许值的修改
指针指向

设置初始值

重复声明

变量提升 不声明能使用
 > 变量提升的优点: 1. 提高性能  2. 容错性更好
暂时性死区 不声明不能使用
块级作用域
- 无var声明的变量均为全局变，可以随意修改


#### 5.箭头函数

普通函数this指向发生者（哪里发生的）
箭头函数this指向创建者（哪里创建的）

#### 6.rest参数和arguments的区别
- rest接收函数多余参数/没有给出名称的参数
  arguments是指所有的参数
- rest形成的是一个数组，属于数组实例，可以用sort、pop等数组方法
  arguments是**类数组**，属于对象，不具备数组的原型方法，有其他作用
- rest要放在形参的最后，不能再有其他参数
- 函数的length属性，不包括rest参数
- rest可以把函数的多个入参收敛进一个数组里



