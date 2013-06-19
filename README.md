#Javascript编码基本规范

首先要知道没有人可以强制你怎样去写代码，因为那是你的自由，但是鉴于我们的项目都是多人合作的产物，而且没人喜欢阅
读杂乱的代码，所以有个统一的编程风格就是一件非常有价值的一件事，尽管起初你需要配置好编辑器 并且在编程时显得小心
一些，但总的来说还是值得的。

本文档大致上是[Felix's Node.js Style Guide](http://nodeguide.com/style.html)的一个分支。本着与时俱进的精神，这个
文档将来还会不断完善，欢迎提交 [issue](https://github.com/AdMaster/js-code-style/issues) 进行讨论。

## 缩进

采用`2空格`，node核心就是使用的2空格缩进，我认为这能让代码看上去更紧凑些。

## 分号

`不要省略分号`，这是一场无休止的战争([semicolon slavery](http://blog.izs.me/post/3393190720/how-this-works),
[玉柏的分号观](https://github.com/lifesinger/lifesinger.github.com/issues/98))，鉴于大多数程序员还是习惯使用分号，
出于代价最小化的考虑，我们还是使用分号吧。

## 编辑器

虽然 [BDFL](http://en.wikipedia.org/wiki/BDFL) 一般会对使用 [vim](http://www.vim.org) 开发程序有所青睐，但我们并
不限制你使用编辑器的自由，不过我们建议你的的编辑器应该具有以下的功能：

* 语法高亮
* 行宽限制
* 行尾空白提示
* 分屏显示
* 语法检查器支持

## 行尾空白

`避免行尾空白`，就像你每次用完餐都需要刷牙一样，你应该在每次代码提交之前都把行尾的空白清除干净，否则你的粗心大意会
让维护人员觉得代码简直糟糕透顶、无法直视。

## 行宽

`限制80字符`，尽管这几年你的显示器变得越来越大了，但是你的脑瓜并没有，你可以留下更多的空间用于代码的分屏显示，不是吗？

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

变量和属性应该总是使用`小写驼峰命名法`。它们应该显得很直管，单字符变量和不常用的名称缩写应该避免。

正确用法:

``` js
var adminUser = db.query('SELECT * FROM users ...');
```

错误用法

``` js
var admin_user = d.query('SELECT * FROM users ...');
```

## 类名

类名应该使用`大写驼峰命名法`[Variations_and_synonyms](http://en.wikipedia.org/wiki/CamelCase#Variations_and_synonyms)。

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

常量应被声明为一般变量或者静态类变量，全部`使用大写字母`。函数不应该被声明为常量，因为不被编译器支持，而且也不属于标准。

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

使用`尾部逗号`并且将短声明放置到一行，仅当解释器不通过时使用引用的键名。

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
使用恒等（三等号）操作符，因为它总是恰如预料的工作。


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

永远_不要_扩展任何对象的原型，尤其是原声对象。无尽的深渊召唤着你，如果你不愿意遵守的话。

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

尽量避免使用嵌套if，尽可能早的返回值。


正确用法:

``` js
function isPercentage(val) {
  if (val < 0) {
    return false;
  }

  if (val > 100) {
    return false;
  }

  return true;
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

由于node使用了非阻塞IO技术，所以函数的通常会使用回调函数来返回它们的结果。node核心库的惯例是将回调函数的第一个参数设为可
选的Error对象来判断返回的状态。

## 避免使用的函数

`with` `eval` `Object.freeze` `Object.preventExtension`，尽管一些类库或许会使用这些函数来实现特定的功能，你还是应当最大限
度的避免它们。

## [set](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/set) 和 [get](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/get)

不要使用setters，因为它们导致的问题往往比解决的问题多，你可以随意使用getters，因为它们不会产生什么边际效应，例如为一个集合类
提供长度属性。

## 事件发送

Node.js自带了一个简单的`EventEmitter`类，你可以从`events`模块来导入它：

``` js
var EventEmitter = require('events').EventEmitter;
```
当你需要创建一个复杂类的时候，通常的做法是让它继承`EventEmitter`然后就可以发送事件了。`EventEmitter`不过是一个
[观察者模式](http://en.wikipedia.org/wiki/Observer_pattern)的简单实现。

然而，我们不应该让对象去监听自己的事件，对象的自我监视是不自然的，它会经常导致不必要的内部实现暴露，并且让你的代码难以追踪。


