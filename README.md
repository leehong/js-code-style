#Javascript编码基本规范

首先要知道没有人可以强制你怎样去写代码，因为那是你的自由，但是鉴于我们的项目都是多人合作的产物，而且
没人喜欢阅读杂乱的代码，所以有个统一的编程风格就是一件非常有价值的一件事，尽管起初你需要配置好编辑器
并且在编程时显得小心一些，但总的来说还是值得的。

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

## 行尾空白

`避免行尾空白`，就像你每次用完餐都需要刷牙一样，你应该在每次代码提交之前都把行尾的空白清除干净，否则你的粗心大意会
让维护人员觉得代码简直糟糕透顶、无法直视。

## 行宽

`限制80字符`，尽管这几年你的显示器变得越来越大了，但是你的脑瓜并没有，你可以留下更多的空间用于代码的分屏显示，不是吗？

## 引用

使用`但引号`，除非你写的是JSON。

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
  'is generally': 'pretty',
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
