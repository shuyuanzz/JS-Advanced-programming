# learn-js

读书笔记
----

## 目录


*************
### <a href="#js 简介">一.简介</a>
### <a href="#HTML">二.在HTML中使用js</a>
### <a href="#基本概念">三.基本概念</a>
### <a name="js 简介">一.简介</a>

#### js是一种专门为与网页交互而设计的一种语言，由以下三个不同部分组成：
1. ECMAScript，由 ECMA-262定义，提供核心语言功能。
2. DOM，提供访问和操作网页的基本接口。
3. BOM，提供与浏览器交互的方法和接口。    

### <a name="#HTML">二.在HTML中使用js</a>

#### 2.1 <script> 元素

##### 属性:
1. async:可选。表示立即下载脚本，但补妨碍页面中的其他操作。
2. defer:可选。表示脚本可以延迟到文档解析再执行。**只对外部文件有效**。
3. src: 可选。包含要执行代码的外部文件。
4. type:可选 表示编写代码使用的脚本语言的内容类型。默认text/javascript。  

  **&emsp;无论如何包含代码，只要不存在defer和async属性，浏览器都会按照该元素再页面中的出现的先后顺序对他们依次进行解析。**  

  **&emsp;在现实当中，延迟脚本（标签里面的defer='defer'）不一定会按照顺序执行，也不一定会在DOMContenLoaded 事件触发之前执行，因此最好只包含一个延迟脚本。**  

  **&emsp;同样与defer类似，async属性只适用于外部脚本文件，并告诉浏览器立即下载文件，但与defer不同的是，有该标记的脚本并不保证按照他们指定的先后顺序执行。（目的是不让浏览器等待该脚本下载和执行，从而异步加载页面，和其它内容）**
#### 2.2 js引入外部文件的优点:
1. 可维护性。
2. 可缓存。
3. 适应未来。

### <a name="基本概念">三.基本概念</a>
##### 3.1 语法：
**&emsp;在函数中用（let,var,const）声明一个变量，当函数被调用时，就会创建该变量并且为其赋值，在此之后，这个变量又会立即被销毁。在非严格模式下可以直接省略操作符，在函数体内被调用时声明一个全局变量（严格模式下报错）**  

**&emsp;可以用一条语句定义多个变量，只要把每个变量用逗号分开即可（如下）**
```
var message = 'hi',
    shu = 'yuan',
    yuan = 123;
```
##### 3.2 数据类型
&emsp;EMCAScript有五种基本数据类型，分别为，undifined,null,string,boolean,number(ES6新增了一种类字符串类型Symbol),还有一种复杂的数据类型——object。

###### 3.2.1 typeof操作符
&emsp;其用来检测给定变量的数据类型，返回值为字符串：
1. 'undifined'————如果这个值未定义。
2. 'boolean'————如果这个值是布尔值。
3. 'string'————如果这个值是字符串。
4. 'number'————如果这个值是数值。
5. 'object'————如果这个值是对象或者是null。
6. 'function'————如果这个值是函数。  
**&emsp;typeof操作符虽然是一个操作符，其也可以类似函数一样的使用括号，但是不是必须的**  
**&emsp;`typeof null = 'object';`是因为特殊值null被认为是一个空对象的引用，因为函数相对于对象来说自身有一些特殊的属性，因此通过typeof操作符来区分函数和其它对象是有必要的。**  
###### 3.4.2 undifined
**&emsp;对未初始化的变量执行typeof会返回undifined，对未声明的变量执行该操作符也同样会返回undifined值（只有在这种情况和delete使用未声明，的变量才不会报错）**
###### 3.4.3 null
**&emsp;值唯一的两个数据类型：undifined、null。只要意在保存对象的变量还没有真正的保存对象，就应该明确的让该变量保存null值。这样不仅可以体现null作为空对象指针的惯例，也有助于进一步区分null和undifined。**
###### 3.4.4 boolean
数据类型|转换为true的值|转换为false的值
--|:--:|--:
Boolean|true|false
String|任意非空字符串|''
Number|任意非零数值|0和NAN
Object|任何对象|null
undifinde|不适用|undifined  
###### 3.4.5 Number  
**&emsp; 任何涉及NaN的操作都会返回NaN,NaN与任何值都不相等，包括其本身。**
###### 3.4.6 String
**&emsp; 转义字符，可以出现在字符串中的任何位置，而且将被作为一个字符来解析。**  
###### 3.4.7 Object
**&emsp; 在EMCAScript中Object类型是所有它的实例的基础，也就是说所有更具体的对象中，都会有Object类型所具有的任何属性和方法(如下)**  
1. constructor:保存着创建当前对象的函数(构造函数)，比如说:
```
var  o = new Object();
```  
构造函数就是 Object()。  

2. hasOwnProoerty(propertyName：string): 用于检查给定的属性是否在对象的实例中，接收一个类型为string的参数。
3. isPrototypeOf(object):用于检测传入对象是不是当前对象的原型。
4. propertyIsEnumberable(propertyName:string):用于检查给定的属性是否可以使用for-in来枚举。
5. toLocaleString():返回对象的字符串形式，与对象所执行环境的地区相对应。
6. toString():返回对象的字符串表示。
7. valueOf():返回对象的字符串，数值，或者布尔值表示，通常与toString()方法的返回值相同。
##### 3.3 操作符
###### 3.3.1 一元操作符（只能操作一个值）
**&emsp; 前置递增递减和后置递增递减的区别————前置是在语句被求值之前改变，而后置是在语句被求值之后改变。如下：**
```
var a = 1,b = 2;
var c = ++a + b;//4
var d = a + b ;//4
```
```
var a = 1,b = 2;
var c = a++ + b;//3
var d = a + b ;//4
```






