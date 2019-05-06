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

  **无论如何包含代码，只要不存在defer和async属性，浏览器都会按照该元素再页面中的出现的先后顺序对他们依次进行解析。**  

  **在现实当中，延迟脚本（标签里面的defer='defer'）不一定会按照顺序执行，也不一定会在DOMContenLoaded 事件触发之前执行，因此最好只包含一个延迟脚本。**  

  **同样与defer类似，async属性只适用于外部脚本文件，并告诉浏览器立即下载文件，但与defer不同的是，有该标记的脚本并不保证按照他们指定的先后顺序执行。（目的是不让浏览器等待该脚本下载和执行，从而异步加载页面，和其它内容）**
#### 2.2 js引入外部文件的优点:
1. 可维护性。
2. 可缓存。
3. 适应未来。

### <a name="基本概念">三.基本概念</a>


