#Admaster javascript编码基本规范

> 程序是写给人读的，只是偶尔让计算机执行一下。
> -- Donald Knuth

任何语言都需要强调编码风格的一致性。只要是团队开发，每个人都以相同的方式编写代码至关重要，这样大家才能方便的看懂和维护对方的代码。

本文档大致上是 [Felix's Node.js Style Guide](http://nodeguide.com/style.html)的一个分支。本着与时俱进的精神，这个文档将来还会不断完善，欢迎提交 [issue](https://github.com/AdMaster/js-code-style/issues) 进行讨论。

另外推荐阅读《[编写可维护的JavaScript](http://www.amazon.cn/%E7%BC%96%E5%86%99%E5%8F%AF%E7%BB%B4%E6%8A%A4%E7%9A%84JavaScript-%E6%89%8E%E5%8D%A1%E6%96%AF/dp/B00BQ7RMW0/)》，它所讲述的技巧和技术，可以使JavaScript团队编程从侠义的个人偏好的阴霾走出来，走向真正的高可维护性、高效能和高水准。

我们采用jshint作为javascript代码检测工具，文档如下:

* [通用配置文件](https://raw.github.com/AdMaster/js-code-style/master/.jshintrc)

* [jshint使用参考](https://github.com/AdMaster/js-code-style/wiki/jshint%E4%BD%BF%E7%94%A8%E5%8F%82%E8%80%83)

## 缩进

采用 **2空格** ，node核心就是使用的2空格缩进，我认为这能让代码看上去更紧凑些。

## 分号

**不要省略分号**，我觉得这没有什么好说的。 `ASI` 这种东西在 js 里面被骂了很多年了。

## 编辑器

虽然 [BDFL](http://en.wikipedia.org/wiki/BDFL) 一般会对使用 [vim](http://www.vim.org) 开发程序有所青睐，但我们并不限制你使用编辑器的自由，不过我们建议你的的编辑器应该具有以下的功能：

* 语法高亮
* 行宽限制
* 行尾空白提示
* 分屏显示
* 语法检查器支持

## 行尾空白

**避免行尾空白**，就像你每次用完餐都需要刷牙一样，你应该在每次代码提交之前都把行尾的空白清除干净，否则你的粗心大意会让维护人员觉得代码简直糟糕透顶、无法直视。

## 行宽

**限制 80 字符**，尽管这几年你的显示器变得越来越大了，但是你的脑瓜并没有，你可以留下更多的空间用于代码的分屏显示，不是吗？

## 引用

使用`单引号`，除非你写的是JSON。

正确用法:

``` js
var foo = 'bar';
```

错误用法

``` js
var foo = "bar";
```

## 括号

你的左括号应该同声明位于同一行。

正确用法:

``` js
if (true) {
  console.log('winning');
}
```

错误用法

``` js
if (true)
{
  console.log('losing');
}
```

## 间隔

* 花括号前后应该留有空格

  ``` js
  // 错误写法
  if(condition) doSomething();

  // 正确写法
  if (condition) {
    doSomething();
  }
  ```
* 等号前后应该留有空格

  ``` js
  //错误写法
  var links=$('#nav li');

  //正确写法
  var links = $('#nav li');
  ```

## 注释风格

* 非行为注释缩进需与被注释代码一致

* 单行注释之前总有一个空行

  ``` js
  // 这是一个单行注释
  ```

* 行尾注释之前至少有一个缩进，且行的总长度不超过限制。

* 多行注释之前总有一个空行，且星号后面需要留有一个空格

  ``` js
  /*
   * 一段注释
   * 包含两行文本
   */
  ```

## 变量声明

一次声明一个变量，真能让你的行更容易重排，请忽略[Crockford](http://javascript.crockford.com/code.html)的建议，并将
声明语句放置在合理的位置。

正确用法:

``` js
var keys = ['foo', 'bar'];
var values = [23, 42];

var object = {};
while (items.length) {
  var key = keys.pop();
  object[key] = values.pop();
}
```

错误用法:

``` js
var keys = ['foo', 'bar'],
    values = [23, 42],
    object = {},
    key;

while (items.length) {
  key = keys.pop();
  object[key] = values.pop();
}
```
## 变量命名

变量和属性应该总是使用**小写驼峰命名法**。它们应该显得很直管，单字符变量和不常用的名称缩写应该避免。

正确用法:

``` js
var adminUser = db.query('SELECT * FROM users ...');
```

错误用法

``` js
var admin_user = d.query('SELECT * FROM users ...');
```

## 类名

类名应该使用**大写驼峰命名法**[Variations_and_synonyms](http://en.wikipedia.org/wiki/CamelCase#Variations_and_synonyms)。

正确用法:

``` js
function BankAccount() {
}
```

错误用法

``` js
function bank_Account() {
}
```

## 常量

常量应被声明为一般变量或者静态类变量，全部**使用大写字母**。函数不应该被声明为常量，因为不被编译器支持，而且也不属于标准。

正确用法:

``` js
var SECOND = 1 * 1000;

function File() {
}
File.FULL_PERMISSIONS = 0777;
```

错误用法

``` js
const SECOND = 1 * 1000;

function File() {
}
File.fullPermissions = 0777;
```

## 对象和数组创建

使用**尾部逗号**并且将短声明放置到一行，仅当解释器不通过时使用引用的键名。

正确用法:

``` js
var a = ['hello', 'world'];
var b = {
  good: 'code',
  'is generally': 'pretty'
};
```

错误用法

``` js
var a = [
  'hello', 'world'
];
var b = {"good": 'code'
      , is generally: 'pretty'
      };
```

## 等号

编程要做的可不是记忆[蠢规则](https://developer.mozilla.org/en/JavaScript/Reference/Operators/Comparison_Operators)。
必须使用恒等（三等号）操作符，因为它总是恰如预料的工作。


正确用法:

``` js
var a = 0;
if (a === '') {
  console.log('winning');
}
```

错误用法

``` js
var a = 0;
if (a == '') {
  console.log('losing');
}
```

## 原型扩展

永远__不要__扩展任何对象的原型，尤其是原声对象。无尽的深渊召唤着你，如果你不愿意遵守的话。

正确用法:

``` js
var a = [];
if (!a.length) {
  console.log('winning');
}
```

错误用法

``` js
Array.prototype.empty = function() {
  return !this.length;
}

var a = [];
if (a.empty()) {
  console.log('losing');
}
```

## 条件语句

任何非显示的条件语句都应该被赋与一个描述变量:

正确用法:

``` js
var isAuthorized = (user.isAdmin() || user.isModerator());
if (isAuthorized) {
  console.log('winning');
}
```

错误用法

``` js
if (user.isAdmin() || user.isModerator()) {
  console.log('losing');
}
```

## 函数长度

让你的函数短点儿。好的函数应该可以放到一张幻灯片里，并且大屋子的最后一排观众都能看的清清楚楚。所以别
指望他们有超级视力，你应当把你的的函数长度限制到10行以内。

## 返回声明

一个 `function` 中应只有一个 `return`

正确用法:

``` js
function isPercentage(val) {
  var ret;
  if (val < 0) {
    ret = false;
  }

  if (val > 100) {
    ret = true;
  }

  return ret;
}
```

错误用法

``` js
function isPercentage(val) {
  if (val >= 0) {
    if (val < 100) {
      return true;
    } else {
      return false;
    }
  } else {
    return false;
  }
}
```

这与这个特定的例子，它还可以表现的更短一些：

``` js
function isPercentage(val) {
  var isInRange = (val >= 0 && val <= 100);
  return isInRange;
}
```
## 嵌套闭包

可以使用闭包，但是不要嵌套，不然你的代码会变成一坨...

正确用法:

``` js
setTimeout(function() {
  client.connect(afterConnect);
}, 1000);

function afterConnect() {
  console.log('winning');
}
```

错误用法

``` js
setTimeout(function() {
  client.connect(function() {
    console.log('losing');
  });
}, 1000);
```

## 回调函数(仅node)

由于node使用了非阻塞IO技术，所以函数的通常会使用回调函数来返回它们的结果。node核心库的惯例是将回调函数的第一个参数设为可选的Error对象来判断返回的状态。

## 避免使用的函数

`with`, `eval`, `Object.freeze`, `Object.preventExtension`，尽管一些类库或许会使用这些函数来实现特定的功能，你还是应当最大限度的避免它们。

## [set](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/set) 和 [get](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/get)

不要使用setters，因为它们导致的问题往往比解决的问题多，你可以随意使用getters，因为它们不会产生什么边际效应，例如为一个集合类提供长度属性。

## 事件发送

Node.js自带了一个简单的`EventEmitter`类，你可以从`events`模块来导入它：

``` js
var EventEmitter = require('events').EventEmitter;
```
当你需要创建一个复杂类的时候，通常的做法是让它继承`EventEmitter`然后就可以发送事件了。`EventEmitter`不过是一个
[观察者模式](http://en.wikipedia.org/wiki/Observer_pattern)的简单实现。

然而，我们不应该让对象去监听自己的事件，对象的自我监视是不自然的，它会经常导致不必要的内部实现暴露，并且让你的代码难以追踪。


