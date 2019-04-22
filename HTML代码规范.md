# HTML编码规范

## 1、代码风格

### 1.1 缩进与换行

**[强制]使用4个空格作为一个缩进层级，不能使用两个空格或tab。**

*[建议]每行不超过120个字符。*

### 1.2 命名

**[强制]`class`的单词全部小写，单词间以 `-` 分隔。**

**[强制]class必须代表相应模块或部件的内容或功能，不得以样式信息进行命名**

```html
<!-- good -->
<div class="sidebar"></div>

<!-- bad -->
<div class="left"></div>
```

**[强制]元素id必须保证页面唯一**

*[建议] `id` 建议单词全字母小写，单词间以 `-` 分隔。同项目必须保持风格一致。*

*[建议] `id`、`class` 命名，在避免冲突并描述清楚的前提下尽可能短。*

**[强制] 同一页面，应避免使用相同的 `name` 与 `id`。**

```js
<input name="foo">
<div id="foo"></div>
<script>
// IE6 将显示 INPUT
alert(document.getElementById('foo').tagName);
```

###  1.3 标签

**[强制] 标签名必须使用小写字母。**

**[强制] 对于无需自闭合的标签，不允许自闭合。**

常见无需自闭合标签有 `input`、`br`、`img`、`hr` 等。

```HTML
<!-- good -->
<input type="text" name="title">

<!-- bad -->
<input type="text" name="title" />
```

**[强制] 对 `HTML5` 中规定允许省略的闭合标签，不允许省略闭合标签。**

**[强制] 标签使用必须符合标签嵌套规则。**

### 1.4 属性

**[强制] 属性名必须使用小写字母。**

```HTML
<!-- good -->
<table cellspacing="0">...</table>

<!-- bad -->
<table cellSpacing="0">...</table>
```

**[强制] 属性值必须用双引号包围。**

不允许使用单引号，不允许不使用引号。

```js
<!-- good -->
<script src="esl.js"></script>

<!-- bad -->
<script src='esl.js'></script>
<script src=esl.js></script>
```

*[建议] 布尔类型的属性，建议不添加属性值。*

```HTML
<input type="text" disabled>
<input type="checkbox" value="1" checked>
```

*[建议] 自定义属性建议以 `xxx-` 为前缀，推荐使用 `data-`。*

```html
<ol data-ui-type="Select"></ol>
```

## 2、通用

### 2.1 DOCTYPE

**[强制] 使用 `HTML5` 的 `doctype` 来启用标准模式，建议使用大写的 `DOCTYPE`。**

### 2.2 编码

**[强制] 页面必须使用精简形式，明确指定字符编码。指定字符编码的 `meta` 必须是 `head` 的第一个直接子元素。**

*[建议] `HTML` 文件使用无 `BOM` 的 `UTF-8` 编码。*

### 2.3 CSS 和 JavaScript 引入

**[强制] 引入 `CSS` 时必须指明 `rel="stylesheet"`。**

*[建议] 引入 `CSS` 和 `JavaScript` 时无须指明 `type` 属性。*

*[建议] 展现定义放置于外部 `CSS` 中，行为定义放置于外部 `JavaScript` 中。*

*[建议] 在 `head` 中引入页面需要的所有 `CSS` 资源。*

*[建议] `JavaScript` 应当放在页面末尾，或采用异步加载。*

## 3、head

### 3.1 title

**[强制] 页面必须包含 `title` 标签声明标题。**

**[强制] `title` 必须作为 `head` 的直接子元素，并紧随 `charset` 声明之后。**

`title` 中如果包含 ASCII 之外的字符，浏览器需要知道字符编码类型才能进行解码，否则可能导致乱码。

## 4、图片

**[强制] 禁止 `img` 的 `src` 取值为空。延迟加载的图片也要增加默认的 `src`。**

*[建议] 避免为 `img` 添加不必要的 `title` 属性。*

*[建议] 为重要图片添加 `alt` 属性。*

*[建议] 添加 `width` 和 `height` 属性，以避免页面抖动。*

*[建议] 有下载需求的图片采用 `img` 标签实现，无下载需求的图片采用 CSS 背景图实现。*

## 5、表单

### 5.1 控件标题

**[强制] 有文本标题的控件必须使用 `label` 标签将其与其标题相关联。**

有两种方式：

1. 将控件置于 `label` 内。

2. `label` 的 `for` 属性指向控件的 `id`。

3. 推荐使用第一种，减少不必要的 `id`。如果 DOM 结构不允许直接嵌套，则应使用第二种。

   ```html
   <label><input type="checkbox" name="confirm" value="on"> 我已确认上述条款</label>
   
   <label for="username">用户名：</label> <input type="textbox" name="username" id="username">
   ```

### 5.2 按钮

**[强制] 使用 `button` 元素时必须指明 `type` 属性值。**

`button` 元素的默认 `type` 为 `submit`，如果被置于 `form` 元素中，点击后将导致表单提交。为显示区分其作用方便理解，必须给出 `type` 属性。

## 6、模板中的 HTML

*[建议] 模板代码的缩进优先保证 HTML 代码的缩进规则。*

```html
<!-- good -->
{if $display == true}
<div>
    <ul>
    {foreach $item_list as $item}
        <li>{$item.name}<li>
    {/foreach}
    </ul>
</div>
{/if}

<!-- bad -->
{if $display == true}
    <div>
        <ul>
    {foreach $item_list as $item}
        <li>{$item.name}<li>
    {/foreach}
        </ul>
    </div>
{/if}
```

*[建议] 模板代码应以保证 HTML 单个标签语法的正确性为基本原则。*

```html
<!-- good -->
<li class="{if $item.type_id == $current_type}focus{/if}">{ $item.type_name }</li>

<!-- bad -->
<li {if $item.type_id == $current_type} class="focus"{/if}>{ $item.type_name }</li>
```

*[建议] 在循环处理模板数据构造表格时，若要求每行输出固定的个数，建议先将数据分组，之后再循环输出。*

```html
<!-- good -->
<table>
    {foreach $item_list as $item_group}
    <tr>
        {foreach $item_group as $item}
        <td>{ $item.name }</td>
        {/foreach}
    <tr>
    {/foreach}
</table>

<!-- bad -->
<table>
<tr>
    {foreach $item_list as $item}
    <td>{ $item.name }</td>
        {if $item@iteration is div by 5}
    </tr>
    <tr>
        {/if}
    {/foreach}
</tr>
</table>
```