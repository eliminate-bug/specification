# 1 注释规范

- 单行注释

**[强制]** 必须独占一行。`//` 后跟一个空格，缩进与下一行被注释说明的代码一致。



- 多行注释

[建议] 避免使用 `/*...*/` 这样的多行注释。有多行注释内容时，使用多个单行注释。



- 封装函数/方法工具注释

**[强制]** 封装的函数/方法工具注释必须包含函数说明，有参数和返回值时必须使用注释标识。

*注*：当 `return` 关键字仅作退出函数/方法使用时，无须对返回值作注释标识。

示例：

```js
/**
 * 函数描述
 *
 * @param {string} p1 参数1的说明
 * @param {string} p2 参数2的说明，比较长
 *     那就换行了.
 * @param {number=} p3 参数3的说明（可选）
 * @return {Object} 返回值描述
 */
function foo(p1, p2, p3) {
    var p3 = p3 || 10;
    return {
        p1: p1,
        p2: p2,
        p3: p3
    };
}
```



- 细节注释

[建议] 对于内部实现、不容易理解的逻辑说明、摘要信息等，我们可能需要编写细节注释。

示例：

```js
function foo(p1, p2, opt_p3) {
    // 这里对具体内部逻辑进行说明
    // 说明太长需要换行
    for (...) {
        ....
    }
}
```

**[强制]** 有时我们会使用一些特殊标记进行说明。特殊标记必须使用单行注释的形式。下面列举了一些常用标记：

解释：

1. TODO: 有功能待实现。此时需要对将要实现的功能进行简单说明。
2. FIXME: 该处代码运行没问题，但可能由于时间赶或者其他原因，需要修正。此时需要对如何修正进行简单说明。
3. HACK: 为修正某些问题而写的不太好或者使用了某些诡异手段的代码。此时需要对思路或诡异手段进行描述。

# 2 结构

## 2.1 缩进

- **[强制]** 使用 `4` 个空格做为一个缩进层级，不允许使用 `2` 个空格 或 `tab`字符。
- **[强制]** `switch` 下的 `case` 和 `default` 必须增加一个缩进层级。

示例：

```js
// good
switch (variable) {

    case '1':
        // do...
        break;

    case '2':
        // do...
        break;

    default:
        // do...

}

// bad
switch (variable) {

case '1':
    // do...
    break;

case '2':
    // do...
    break;

default:
    // do...

}
```

## 2.2 空格

- **[强制]** 二元运算符两侧必须有一个空格，一元运算符与操作对象之间不允许有空格。

示例：

```js
var a = !arr.length;
a++;
a = b + c;
```

- **[强制]** 用作代码块起始的左花括号 `{` 前必须有一个空格。

示例：

```js
// good
if (condition) {
}

while (condition) {
}

function funcName() {
}

// bad
if (condition){
}

while (condition){
}

function funcName(){
}
```

- **[强制]** `if / else / for / while / function / switch / do / try / catch / finally` 关键字后，必须有一个空格。

示例：

```js
// good
if (condition) {
}

while (condition) {
}

(function () {
})();

// bad
if(condition) {
}

while(condition) {
}

(function() {
})();
```

- **[强制]** 在对象创建时，属性中的 `:` 之后必须有空格，`:` 之前不允许有空格。

示例：

```js
// good
var obj = {
    a: 1,
    b: 2,
    c: 3
};

// bad
var obj = {
    a : 1,
    b:2,
    c :3
};
```

- **[强制]** 函数声明、具名函数表达式、函数调用中，函数名和 `(` 之间不允许有空格。

示例：

```js
// good
function funcName() {
}

var funcName = function funcName() {
};

funcName();

// bad
function funcName () {
}

var funcName = function funcName () {
};

funcName ();
```

- **[强制]** `,` 和 `;` 前不允许有空格。如果不位于行尾，`,` 和 `;` 后必须跟一个空格

示例：

```js
// good
callFunc(a, b);

// bad
callFunc(a , b) ;
```

- **[强制]** 在函数调用、函数声明、括号表达式、属性访问、`if / for / while / switch / catch` 等语句中，`()` 和 `[]` 内紧贴括号部分不允许有空格。

示例：

```js
// good

callFunc(param1, param2, param3);

save(this.list[this.indexes[i]]);

needIncream && (variable += increament);

if (num > list.length) {
}

while (len--) {
}


// bad

callFunc( param1, param2, param3 );

save( this.list[ this.indexes[ i ] ] );

needIncreament && ( variable += increament );

if ( num > list.length ) {
}

while ( len-- ) {
}
```

- **[强制]** 单行声明的数组与对象，如果包含元素，`{}` 和 `[]` 内紧贴括号部分不允许包含空格。

示例：

```js
// good
var arr1 = [];
var arr2 = [1, 2, 3];
var obj1 = {};
var obj2 = {name: 'obj'};
var obj3 = {
    name: 'obj',
    age: 20,
    sex: 1
};

// bad
var arr1 = [ ];
var arr2 = [ 1, 2, 3 ];
var obj1 = { };
var obj2 = { name: 'obj' };
var obj3 = {name: 'obj', age: 20, sex: 1};
```

- [强制] 行尾不得有多余的空格。

## 2.3 换行

- **[强制]** 每个独立语句结束后必须换行。
- **[强制]** 每行不得超过 `120` 个字符，超长的不可分割的代码允许例外，比如复杂的正则表达式。
- **[强制]** 运算符处换行时，运算符必须在新行的行首。

示例：

```js
// good
if (user.isAuthenticated()
    && user.isInRole('admin')
    && user.hasAuthority('add-admin')
    || user.hasAuthority('delete-admin')
) {
    // Code
}

var result = number1 + number2 + number3
    + number4 + number5;


// bad
if (user.isAuthenticated() &&
    user.isInRole('admin') &&
    user.hasAuthority('add-admin') ||
    user.hasAuthority('delete-admin')) {
    // Code
}

var result = number1 + number2 + number3 +
    number4 + number5;
```

- **[强制]** 在函数声明、函数表达式、函数调用、对象创建、数组创建、`for`语句等场景中，不允许在 `,` 或 `;` 前换行。

示例：

```js
// good
var obj = {
    a: 1,
    b: 2,
    c: 3
};

foo(
    aVeryVeryLongArgument,
    anotherVeryLongArgument,
    callback
);


// bad
var obj = {
    a: 1
    , b: 2
    , c: 3
};

foo(
    aVeryVeryLongArgument
    , anotherVeryLongArgument
    , callback
);
```

- [建议] 在语句的行长度超过 `120` 时，根据逻辑条件合理缩进。

示例：

```js
// 较复杂的逻辑条件组合，将每个条件独立一行，逻辑运算符放置在行首进行分隔，或将部分逻辑按逻辑组合进行分隔。
// 建议最终将右括号 ) 与左大括号 { 放在独立一行，保证与 `if` 内语句块能容易视觉辨识。
if (user.isAuthenticated()
    && user.isInRole('admin')
    && user.hasAuthority('add-admin')
    || user.hasAuthority('delete-admin')
) {
    // Code
}

// 按一定长度截断字符串，并使用 + 运算符进行连接。
// 分隔字符串尽量按语义进行，如不要在一个完整的名词中间断开。
// 特别的，对于 HTML 片段的拼接，通过缩进，保持和 HTML 相同的结构。
var html = '' // 此处用一个空字符串，以便整个 HTML 片段都在新行严格对齐
    + '<article>'
    +     '<h1>Title here</h1>'
    +     '<p>This is a paragraph</p>'
    +     '<footer>Complete</footer>'
    + '</article>';

// 也可使用数组来进行拼接，相对 `+` 更容易调整缩进。
var html = [
    '<article>',
        '<h1>Title here</h1>',
        '<p>This is a paragraph</p>',
        '<footer>Complete</footer>',
    '</article>'
];
html = html.join('');

// 当参数过多时，将每个参数独立写在一行上，并将结束的右括号 ) 独立一行。
// 所有参数必须增加一个缩进。
foo(
    aVeryVeryLongArgument,
    anotherVeryLongArgument,
    callback
);

// 也可以按逻辑对参数进行组合。
// 最经典的是 baidu.format 函数，调用时将参数分为“模板”和“数据”两块
baidu.format(
    dateFormatTemplate,
    year, month, date, hour, minute, second
);

// 当函数调用时，如果有一个或以上参数跨越多行，应当每一个参数独立一行。
// 这通常出现在匿名函数或者对象初始化等作为参数时，如 `setTimeout` 函数等。
setTimeout(
    function () {
        alert('hello');
    },
    200
);

order.data.read(
    'id=' + me.model.id,
    function (data) {
        me.attchToModel(data.result);
        callback();
    },
    300
);

// 链式调用较长时采用缩进进行调整。
$('#items')
    .find('.selected')
    .highlight()
    .end();

// 三元运算符由3部分组成，因此其换行应当根据每个部分的长度不同，形成不同的情况。
var result = thisIsAVeryVeryLongCondition
    ? resultA : resultB;

var result = condition
    ? thisIsAVeryVeryLongResult
    : resultB;

// 数组和对象初始化的混用，严格按照每个对象的 `{` 和结束 `}` 在独立一行的风格书写。
var array = [
    {
        // ...
    },
    {
        // ...
    }
];
```



## 2.4 语句

- **[强制]** 不得省略语句结束的分号
- **[强制]** 在 `if / else / for / do / while` 语句中，即使只有一行，也不得省略块 `{...}`。

示例：

```js
// good
if (condition) {
    callFunc();
}

// bad
if (condition) callFunc();
if (condition)
    callFunc();
```

- **[强制]** 函数定义结束不允许添加分号。

示例：

```js
// good
function funcName() {
}

// bad
function funcName() {
};

// 如果是函数表达式，分号是不允许省略的。
var funcName = function () {
};
```

# 3 命名

- **[强制]** `变量` 使用 `Camel命名法`。

示例：

```js
var loadingModules = {};
```

- **[强制]** `常量` 使用 `全部字母大写，单词间下划线分隔` 的命名方式。

示例：

```js
var HTML_ENTITY = {};
```

- **[强制]** `函数` 使用 `Camel命名法`。

示例：

```js
function stringFormat(source) {
}
```

- **[强制]** 函数的 `参数` 使用 `Camel命名法`。

示例：

```js
function hear(theBells) {
}
```

- **[强制]** `类名` 使用 `名词`。

示例：

```js
function Engine(options) {
}
```

- [建议] `函数名` 使用 `动宾短语`。

示例：

```js
function getStyle(element) {
}
```

- [建议] `boolean` 类型的变量使用 `is` 或 `has` 开头。

示例：

```js
var isReady = false;
var hasMoreCommands = false;
```

- [建议] `Promise对象` 用 `动宾短语的进行时` 表达。

示例：

```js
var loadingData = ajax.get('url');
loadingData.then(callback);
```

# 4 变量

- **[强制]** 变量、函数在使用前必须先定义，不通过var定义变量将导致变量污染全局环境。

示例：

```js
// good
var name = 'MyName';

// bad
name = 'MyName';
```

- **[强制]** 每个 `var` 只能声明一个变量。

示例：

```js
// good
var hangModules = [];
var missModules = [];
var visited = {};

// bad
var hangModules = [],
    missModules = [],
    visited = {};
```

- **[强制]** 变量必须 `即用即声明`，不得在函数或其它形式的代码块起始位置统一声明所有变量。

示例：

```js
// good
function kv2List(source) {
    var list = [];

    for (var key in source) {
        if (source.hasOwnProperty(key)) {
            var item = {
                k: key,
                v: source[key]
            };

            list.push(item);
        }
    }

    return list;
}

// bad
function kv2List(source) {
    var list = [];
    var key;
    var item;

    for (key in source) {
        if (source.hasOwnProperty(key)) {
            item = {
                k: key,
                v: source[key]
            };

            list.push(item);
        }
    }

    return list;
}
```

# 5 条件

- **[强制]** 在 Equality Expression 中使用类型严格的 `===`，可以避免等于判断中隐式的类型转换。仅当判断 `null` 或 `undefined` 时，允许使用 `== null`。

示例：

```js
// good
if (age === 30) {
    // ......
}

// bad
if (age == 30) {
    // ......
}
```

- [建议] 对于相同变量或表达式的多值条件，用 `switch` 代替 `if`。

示例：

```js
// good
switch (typeof variable) {
    case 'object':
        // ......
        break;
    case 'number':
    case 'boolean':
    case 'string':
        // ......
        break;
}

// bad
var type = typeof variable;
if (type === 'object') {
    // ......
}
else if (type === 'number' || type === 'boolean' || type === 'string') {
    // ......
}
```

# 6 循环

- [建议] 不要在循环体中包含函数表达式，事先将函数提取到循环体外。

*注*：循环体中的函数表达式，运行过程中会生成循环次数个函数对象。

示例：

```js
// good
function clicker() {
    // ......
}

for (var i = 0, len = elements.length; i < len; i++) {
    var element = elements[i];
    addListener(element, 'click', clicker);
}


// bad
for (var i = 0, len = elements.length; i < len; i++) {
    var element = elements[i];
    addListener(element, 'click', function () {});
}
```

- [建议] 对循环内多次使用的不变值，在循环外用变量缓存。

示例：

```js
// good
var width = wrap.offsetWidth + 'px';
for (var i = 0, len = elements.length; i < len; i++) {
    var element = elements[i];
    element.style.width = width;
    // ......
}


// bad
for (var i = 0, len = elements.length; i < len; i++) {
    var element = elements[i];
    element.style.width = wrap.offsetWidth + 'px';
    // ......
}
```

- [建议] 对有序集合进行顺序无关的遍历时，使用逆序遍历。

*注*：逆序遍历可以节省变量，代码比较优化。

示例：

```js
var len = elements.length;
while (len--) {
    var element = elements[len];
    // ......
}
```

# 7 数据类型

## 7.1 类型

### 7.1.1 类型检测

- **[建议]** 类型检测优先使用 `typeof`。对象类型检测使用 `instanceof`。`null` 或 `undefined` 的检测使用 `== null`。

  示例：

  ```js
  // string
  typeof variable === 'string'
  
  // number
  typeof variable === 'number'
  
  // boolean
  typeof variable === 'boolean'
  
  // Function
  typeof variable === 'function'
  
  // Object
  typeof variable === 'object'
  
  // RegExp
  variable instanceof RegExp
  
  // Array
  variable instanceof Array
  
  // null
  variable === null
  
  // null or undefined
  variable == null
  
  // undefined
  typeof variable === 'undefined'
  ```

### 7.1.2 类型转换

- [建议] 转换成 `string` 时，使用 `+ ''`。

  示例：

  ```js
  // good
  num + '';
  
  // bad
  new String(num);
  num.toString();
  String(num);
  ```

- [建议] 转换成 `number` 时，通常使用 `+`。

  示例：

  ```js
  // good
  +str;
  
  // bad
  Number(str);
  ```

- [建议] `string` 转换成 `number`，要转换的字符串结尾包含非数字并期望忽略时，使用 `parseInt`。

  示例：

  ```js
  var width = '200px';
  parseInt(width, 10);
  ```

- **[强制]** 使用 `parseInt` 时，必须指定进制。

  示例：

```js
	// good
	parseInt(str, 10);

	// bad
	parseInt(str);
```

- [建议] 转换成 `boolean` 时，使用 `!!`。

示例：

```js
var num = 3.14;
!!num;
```

- [建议] `number` 去除小数点，使用 `Math.floor` / `Math.round` / `Math.ceil`，不使用 `parseInt`。

示例：

```js
// good
var num = 3.14;
Math.ceil(num);

// bad
var num = 3.14;
parseInt(num, 10);
```

## 7.2 字符串

- **[强制]** 字符串开头和结束使用单引号 `'`。

*注*：实际使用中，字符串经常用来拼接HTML。为方便HTML中包含双引号而不需要转义写法。

示例：

```js
var str = '我是一个字符串';
var html = '<div class="cls">拼接HTML可以省去双引号转义</div>';
```

## 7.3 对象

- **[强制]** 使用对象字面量 `{}` 创建新 `Object`。

示例：

```js
// good
var obj = {};

// bad
var obj = new Object();
```

- **[强制]** 不允许修改和扩展任何原生对象和宿主对象的原型。

  示例：

  ```js
  // 以下行为绝对禁止
  String.prototype.trim = function () {
  };
  ```

- [建议] `for in` 遍历对象时, 使用 `hasOwnProperty` 过滤掉原型中的属性。

  示例：

  ```js
  var newInfo = {};
  for (var key in info) {
      if (info.hasOwnProperty(key)) {
          newInfo[key] = info[key];
      }
  }
  ```

## 7.4 数组

- **[强制]** 使用数组字面量 `[]` 创建新数组，除非想要创建的是指定长度的数组。

  示例：

  ```js
  // good
  var arr = [];
  
  // bad
  var arr = new Array();
  ```

- [建议] 清空数组使用 `.length = 0`。

