[[Web前端基础]]
**JAvaScript**是一种高级的、解释型的编程语言，使得网页可以交互（如拥有复杂的动画，可点击的按钮，通俗的菜单、表单验证、页面特效、操作页面元素等），常用来为网页添加各种各样的动态功能，为用户提供更流畅更美观的浏览效果
JavaScript支持面向对象编程，命令式编程，以及函数式编程。提供语法来操控文本、数组、日期以及正则表达式等。它已经通过ECMAScript实现语言的标准化
> JavaScript和Java
> JavaScript和Java是两门不同的编程语言，之所以命名为JavaScript是因为带有“Java”字样有助于这门新语言的传播。虽然这两门语言不管在名字上还是在语法上都有很多相似性（和C语言很相似），但这两门语言在设计之处就有不同。JavaScript的语言设计主要受到了Self（一种基于原型的编程语言）和Scheme（一种函数式编程语言）的影响。
> JavaScript是运行在浏览器中的一种动态、弱类型脚本语言，Java是一种可以撰写跨平台应用软件的面向对象的静态、强类型程序设计语言

## 走入JavaScript的世界
### 认识JavaScript
**JavaScript**主要由三部分组成：
1. 核心（ECMAScript）
2. 文档对象模型（DOM）
3. 浏览器对象模型（BOM）
我们可以将这三部分当作三个部门，每个部门都有自己的职责，首先是核心（ECMAScript）
#### 核心（ECMAScript）
`ECMAScript`规定了**这门语言的基本组成部分**，主要由一下几个组成：
* 语法
* 类型
* 语句
* 关键字
* 保留字
* 操作符
* 对象
现在我们只要先知道它们是`JavaScript`**这门语言的基本组成**即可
有了这些基本组成部分，`JavaScript`就可以完成基本的**逻辑以及数据处理**
#### 文档对象模型（DOM）
`DOM`的功能简单来说就是获取到我们写所有的`html`标签，并给标签添加或者删除样式，并可以给标签添加事件（例如点击、拖动等）。这些功能的实现是基于下面几种接口：
* **DOM遍历和范围**：可以找到页面中所有的标签；
* **DOM事件**：例如给某个图片添加拖动事件，使图片可以随意拖动；
* **DOM样式**：可以更改页面中所有元素的样式，例如更改某一段文字的颜色

#### 浏览器对象模型（BOM）
`BOM`只会处理和浏览器相关的东西，比如：
* 弹出新窗口功能
* 移动、缩放、关闭浏览器窗口的功能
* 给用户提供显示器分辨率的功能
* 提供浏览器信息
在初学JavaScript的时候，我们可能只会跟前两种打交道

### 在HTML中使用JavaScript
#### `JavaScript`的书写位置
`JavaScript`与`CSS`的书写位置非常相似，分为`HTML`内部和外部
##### `JavaScript`写在`HTML`内部
###### 1.使用`script`标签嵌入`JavaScript`
`<script></script>`标签可以将`JavaScript`代码嵌入到`HTML`内部，具体嵌入方式如下：
```js
// script标签嵌入JavaScript代码
<script>
    // JavaScript代码
    let name = "Bob";
    function(){
        console.log("我的名字叫："+name);
    }
</script>
```

> 上述代码中，`script`标签中间的代码大家不用去理解，后面或许会看到`<script type="text/javascript" charset="utf-8"></script>`这种类型的`script`标签，其实它跟`<script></script>`标签是一样的，其中`type="text/javascript"`代表> 文档类型是`javascript`类型，字符编解码方式是`utf-8`.这两个暂时都不用去理解

###### 2.注意`script`标签在`HTML`文件中的位置
这里强行规定一个位置就是一种规范。在`body`标签的内部，并保证是在末尾，如下面的代码所示：
```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <title>Document</title>
  </head>
  <body>
    <!-- 正常的html标签一定要写在script标签的前面 -->
    <div></div>
    <!-- 在body标签的内部并在末尾 -->
    <script></script>
  </body>
</html>
```
> `script`标签在`HTML`文件中的位置很随意，但是如果在学习`JavaScript`的`DOM`的时候，如果不注意`script`标签的位置，就会出现意想不到的报错

##### `JavaScript`写在`HTML`外部
和`CSS`一样，在`JavaScript`中也推崇代码分离，即`JavaScript`代码写在`xxx.js`文件中，然后由引入标签去引入即可
这里的引入标签即`script`标签，不一样的是，标签上多了一个`src`参数，引入方式如下：
```js
<script src='index.js'></script>
```
书写位置与内部的书写位置一致，都是在`body`标签内的末尾处。

#### JavaScript入门
##### JavaScript注释
JavaScript注释包括单行注释和块级注释。
###### 单行注释
单行注释以两个斜杠开头，如下：
```js
// 单行注释
```
###### 块级注释
块级注释以一个斜杠和星号开头，以一个星号和斜杠结尾。如下：
```js
/*
 * 注释
 * 注释
 */
```

##### 字符串
字符串就是**用引号引起来的内容**，这里的引号可以是单引号也可以是双引号
**切记**：输入引号的时候，一定要切换为英文输入法

###### console访问控制台
JavaScript与我们之前学习的`HTML/CSS`不一样的是，它的输出结果不是在浏览器的页面中显示，而是在控制台中显示。
`console`表示访问控制台，`log()`表示在控制台输出信息，中间用点`.`连接，完整的写法是：
```js
console.log("要输出的内容");
```
>不用纠结`console.log();`是什么，因为这是浏览器内置对象，也就是浏览器自带的，主要记住这句话可以在控制台输出信息即可

将输出语句写在`script`标签内，完整的写法如下
```js
<script>console.log("Hello World");</script>
```
在`index.js`文件中写`JavaScript`代码的时候，是不需要加`script`标签的，只有在`HTML`代码中才需要加`script`标签。
###### 模版字符串
在一般的字符串中，如果我们要将字符串和变量拼接起来，要用加号`+`区拼接，例如：
```js
let firstName = "胡";
let lastName = "雪岩";

let say = "大家好，我姓" + firstName + "，名" + lastName;

console.log(say);
```
这样的写法非常繁琐，使用模版字符串就可以简化书写，模版字符串的核心就是反引号（\`\`）和占位符`$(expression)`，反引号的作用是将字符串和变量包起来，占位符的作用就是在字符串中插入变量
>记住占位符的语法`$(变量名)`

上面的代码可以使用模版字符串来进行改造
```js
let firstName = "胡";
let lastName = "雪岩";

let say = `大家好，我姓${firstName}，名${lastName}`;

console.log(say);
```
###### 转义符（\\)
转义符在模版字符串和一般字符串中都很常见，比如要写下面这段代码：
```js
let str = "华为正式发布操作系统---"鸿蒙OS"";
console.log(str);
```
但这样的写法是错误的，如果就想在双引号里面写双引号怎么办？要用到转义符(\\)，前后双引号前面添加一个转义符(\\)，代码如下：
```js
let str = "华为正式发布操作系统---\"鸿蒙OS\"";
console.log(str);
```
同样的，如果想在模版字符串中使用反引号（\`\`），也可以在模版字符串中的\`前面添加一个转义符（\\），如：
```js
let firstName = "胡";
let lastName = "雪岩";

let say = `大家好，我姓${firstName}，名${lastName}，喜欢\`看书\``;

console.log(say);
```

###### 多行字符串拼接

再比如我们要输出一首古诗，使用一般的字符串我们就要用到\n 来换行，代码如下：

```js
let str = "春眠不觉晓\n" + "处处闻啼鸟\n" + "夜来风雨声\n" + "花落知多少\n";
console.log(str);
```

但是使用模版字符串，只需要回车就好，代码如下：

```js
let str = `春眠不觉晓
处处闻啼鸟
夜来风雨声
花落知多少`;

console.log(str);
```

###### 在字符串中使用表达式

在以前我们要在一个字符串中使用表达式，我们要去拼接这个表达式，具体做法如下：

```js
let number1 = 20;
let number2 = 10;
console.log(
  "两个数的和是：" +
    (number1 + number2) +
    "\n两个数的差是：" +
    (number1 - number2) +
    "。"
);
```

同样，这种做法就很繁琐，首先加号和引号太多了，输入成本太高，这时候我们就可以充分利用占位符（${expression}）来做点文章，改写如下：

```js
let number1 = 20;
let number2 = 10;
console.log(`两个数的和是：${number1 + number2} 
两个数的差是：${number1 - number2} 。`);
```

###### 模版字符串中使用三元表达式

这里我们就不去管字符串拼接的表达式了，直接使用模版字符串来写三元表达式，先写一个最简单的:
```js
let str = `这里是${false ? "浙江" : "江苏"}`;

console.log(str); // 江苏
```
很容易看出，输出结果是江苏，做更深一步的书写：
```js
let str = `这里是${true ? "江苏" : "浙江"}-${true ? "南京" : "常州"}`;

console.log(str); // 这里是江苏-南京
```
###### 使用场景
```js
// 定义屏幕的宽度，当然这个宽度是根据window的api去获取的
let screen = 760;

// 判断屏幕是大屏还是小屏，这里我们认为大于760px的就是大屏
function isLargeScreen() {
  return screen > 800;
}

// 定义元素的排列方式，大屏row排列，小屏column排列
// 具体什么排列方式，是根据屏幕大小决定的
let item = {
  isCollapsed: screen > 800
};

// 这里我们就要根据上面的信息来动态的获取类名（多个）
const classes = `header ${
  isLargeScreen() ? "" : `icon-${item.isCollapsed ? "column" : "row"}`
}`;

console.log(classes);
```
或者在js代码中组装HTML代码，然后再显示在屏幕中
```js
let htmlCode = `
    <img src='' />
    ${
      true
        ? `<img src='https://ss0.bdstatic.com/70cFuHSh_Q1YnxGkpoWK1HF6hhy/it/u=1906469856,4113625838&fm=26&gp=0.jpg' />`
        : `<img src='' />`
    }
`;
console.log(htmlCode);
// <img src='' />
//    <img src='https://ss0.bdstatic.com/70cFuHSh_Q1YnxGkpoWK1HF6hhy/it/u=1906469856,4113625838&fm=26&gp=0.jpg' />
```
这里的html代码作为条件成功后要输出的内容，要用反引号括起来

## 基础数据类型
### 变量
**变量就是保存值的占位符**，它的作用与二元一次方程的未知数一样，用来临时保存值的。
在`JavaScript`中定义变量的关键字（编程语言中特定的单词）有两个。即`let`、`const`
#### 使用let定义变量
定义变量的格式如下所示
![[Pasted image 20240127125553.png]]
* 关键字：编程语言中特定的单词
* 变量名：用于保存值的占位符；
* 赋值符号：将值赋给变量的符号；
下面来定义一个变量并在控制台输出，核心代码如下：
```js
let name = "Will Smith";
console.log(name);
```
上面的代码包含了两步：
1. 定义变量
2. 给变量赋值

##### 1.定义变量
```js
// 定义一个变量名为name的变量
let name;
```
**注意**：`let`声明变量的时候，不能重复声明同名变量
>如果在不同的作用域声明相同变量是可以的

##### 2.给变量赋值
```js
// 定义变量
let name;

// 给变量赋值
name = "Will Smith";
```
**注意：**
1. 在使用`console.log()`输出变量的时候，并没有加引号`""`。
2. 使用变量一定要在定义变量之后。
>存在其它的定义变量关键字`var`，这是一种过时的定义变量关键字，会导致很多未知的错误，现在已经不常用了，可以忽略

#### 使用const定义变量
const定义变量的方法和let一样，如图所示：
![[Pasted image 20240127131928.png]]
const的用法也和let一样，主要是区分在定义变量的时候，有什么不同
#### `let`和`const`异同点一：
* `let`定义的变量可以被多次重新赋值
```js
let name = "Bob";
console.log(name); // Bob

name = "Tom";
console.log(name); // Tom
```
* `const`定义的变量只能赋值一次
```js
const name = "Bob";
console.log(name); // Bob

name = "Tom"; // 报错
console.log(name); // 不执行
```

#### `let`和`const`异同点二：
* `let`定义变量的时候，可以不赋初始值
```js
let age;
console.log(age); // undefined
```
* `const`定义变量的时候，要赋初始值，否则会报错
```js
const age; // 报错
console.log(age);  // 不执行
```

### 数值类型
常用的数值类型主要包括**整数，浮点数（你可以理解为小数）和NaN（Not a Number 非数值）**，当然还有其他类型的一些数值。
#### 整数
`JavaScript`中的整数和数学中的整数是一样的，是正整数、零、负整数的集合，一般来说，我们所接触的整数都是十进制的，例如：
```js
let number = 8;
console.log(number); // 8
```
除了十进制还有八进制，十六进制，所谓十进制就是逢10进1，八进制就是逢8进1，十六进制就是逢16进1，我们用几张图来简单理解一下进制问题，红色方块表示进位：
##### 八进制
![[Pasted image 20240127171941.png]]
```js
let number1 = 010; // 八进制的8
let number2 = 011; // 八进制的9
let number3 = 012; // 八进制的10
```
##### 十进制
![[Pasted image 20240127172003.png]]
```js
let number1 = 7; // 十进制的7
let number2 = 20; // 十进制的20
```
##### 十六进制
![[Pasted image 20240127172020.png]]
```js
let number1 = 0x010; // 十六进制的16
let number2 = 0x11; // 十六进制的17
let number3 = 0x12; // 十六进制的18
```
#### 浮点数
浮点数必须包含一个小数点，并且小数点后面至少有一位数字、小数点前面可以没有数字，但是不推荐这种写法，
下面是几种常见的浮点数值：
```js
let floatNumber1 = 2.0;
let floatNumber2 = 0.4;
let floatNumber3 = .2; // 正确，但是不推荐
```
除此之外还有一些极大或者极小的数值，可以用科学计数法`e`来表示，例如：
```js
let bigNumber = 9.43e7; // 等于94300000
```
上面的数值表示9.34乘以10的7次方
```js
let smallNumber = 3e-7; // 等于0.0000003
```
上面的数值表示3乘以10的-7次方。
##### 浮点数的精度丢失现象
浮点数值的最高精度是17位小数，但是在算数运算当中其精度远不如整数。
例如，0.1加0.2的结果不是0.3：
```js
let number1 = 0.1;
let number2 = 0.2;
console.log(number1 + number2); // 0.30000000000000004
```
因此在后面我们学习到条件判断的时候，不要使用这种判断：
```js
if (a + b == 0.3) {
  console.log('输出成功');
}
```
这种判断条件会因为精度丢失让本来应该成立的判断条件却不成立了。
#### NaN
NaN（Not a Number）即非数值。
简单来说，就是两个变量执行了一个运算，例如`+`、`-`、`*`、`/`当中的一种，返回的结果仍然是数字类型，但是执行的数学运算没有成功。
有以下几种情况会出现`NaN`：
1. 0/0
2. 字符串乘以数字
3. `NaN`和任何数进行运算

### 类型转换/字符串拼接
类型转换主要包括两种，**隐式转换和强制类型转换**
#### 隐式转换
* 数字字符串加数字，数字隐式转换为字符串
```js
console.log(20 + "20"); // 2020
// 调换位置亦可
console.log("20" + 20); // 2020
```
输出的结果不是40，而是2020。
* 数字字符串与数字做非加法运算，字符串隐式转换为数字
```js
console.log("20" - 10); // 10
console.log(10 * "10"); // 100
console.log(10 / "2"); // 5
```
* 数字字符串与数字字符串做非加法运算，隐式转换为数字
```js
console.log("20" - "10"); // 10
console.log("20" / "10"); // 2
console.log("20" * "10"); // 200
```
#### 强制类型转换
强制类型转换要学习两个，parseInt（将小数字符串、整数字符串或者小数转换为整数）、parseFloat（将小数字符串转换为小数）
##### parseInt
* 整数字符串转换为整数
```js
let number = "20";
//  将number转换为整数类型
let converNumber = parseInt(number);
console.log(converNumber); // 20
// 判断转换后的数据类型
console.log(typeof converNumber); // number
```
* 小数字符串转换为整数
```js
let number = "20.5";
let converNumber = parseInt(number);
console.log(converNumber); // 20  不足21一律按照20算
console.log(typeof converNumber); // number
```
* 小数转换为整数
```js
let number = 20.5;
let converNumber = parseInt(number);
console.log(converNumber); // 20
```

##### parseFloat
将小数字符串转换为小数
```js
let number = "20.9";
let converNumber = parseFloat(number);
console.log(converNumber); // 20.9
console.log(typeof converNumber); // number
```

#### 字符串拼接
字符串拼接主要是为了有格式的在控制台输出一些信息
需要字符串拼接技术来实现：
* 字符串拼接使用的符号是`+`（加号）
* 字符串用引号引起来，单双引不做要求，但是要对应，不能是前半部分单引号，后半部分双引号。
* 变量名不能用引号，如果变量名在字符串中间，可以用加号和引号区分开。


### 运算符
#### 相等/全等
在编译语言里会经常去做值的判断，比较判断两个值是否相同，这时候就要用到相等（\=\=）和（\=\=\=）全等运算符，这两个运算符的区别是前者只判断值是否相同，后者在此基础上还要判断类型是否相同
由于相等存在类型转换问题，为了保持代码中数据类型的完整性，**推荐使用全等**
#### 自增/自减
自增（++）/自减（--）符号
自增一般在循环中用的比较多



## 布尔类型/条件判断
### 布尔类型
布尔类型简单来说就是`true`（真）和`false`（假）。这在后面学习流程控制语句和条件判断的时候使用非常频繁。
布尔类型的数据是区分大小写的，也就是说`true`、`false`是布尔类型数据，`TRUE`、`FALSE`都不是布尔类型数据
可以吧`true`、`false`理解为一个值，和字符串数值一样，都是作为一个值来赋给变量的。
### 布尔运算
在实际应用当中，布尔类型的数据大多情况下是通过计算得到的，这种计算叫做**布尔运算**
#### 基本布尔运算
如相等`==`、全等`===`、大于`>`、大于等于`>=`、小于`<`、小于等于`<=`、不等`!=`、非`!`
##### 两种布尔运算的简便写法

| 数据类型 | 转换为true的值 | 转换为false的值 |
| ---- | ---- | ---- |
| 字符串 | 如何非空字符串 | “”（空字符串） |
| 数字 | 如何非零数字 | 0 |
通过代码理解这个表：
```js
let str = 'Bob';

if (str) {
  console.log('代码被执行了'); // 会被执行
}
// 上面代码等同于
if (str !== '') {
  console.log('代码被执行了'); // 会被执行
}
```
解释一下代码
```js
if (条件) {
  // 待执行代码
}
```
这段代码中，括号`()`里面的是“条件”，大括号`{}`里面的是要执行的代码，整个代码的意思就是，如果`()`里面的条件为`true`，那么就执行代码，如果条件里面是一个空字符串，那么就会被当做`false`


#### 逻辑或（||）/逻辑与（&&）
##### 逻辑或
一真即真，都假即为假
##### 逻辑与
都真为真

### 条件判断
#### if
条件判断语句的格式如下：
```js
if(){
...
}
```
**注意**：当if条件下面只有一条语句，那么花括号（`{}`）可以不加。
#### if-else
`if`条件判断规定了符合条件的执行内容，`if-else`不仅规定了符合条件的执行内容，还规定了不符合条件的执行内容
#### if--else-if
格式如下：
```js
if(){
...
}else if(){
...
}else{
...
}
```
#### switch
`switch`语句可以说是`if else if`的变形
```js
let weather = 'rain';

switch (weather) {
  case 'snow':
    console.log('堆雪人');
    break;
  case 'windy':
    console.log('呆在家里');
    break;
  case 'rain':
    console.log('雨中漫步');
    break;
  default:
    console.log('工作');
    break;
```


## 数组
### 认识数组
数组一次可以存放多个值
#### 数组的表示方法

在`JavaScript`中，数组的表示方法是一个方括号`[]`
可以吧`[]`理解为一个**空数组**，空数组就是没有存放任何内容的数组。
数组的内容和内容之间要用逗号（`,`）隔开，
```js
[1,2,3,4]
```
数组有很有意思的特性，可以存放不同类型的值。甚至在数组里还能再存放数组。
如果要使用数组，还是需要一个变量来存储它
>这里的存储准确来说是存储了指向数组的地址。

存储数组的变量和存储值的变量是一样的
#### 数组的索引
数组里的每一个内容都对应一个编号，且从0开始索引
* 可以通过索引（下标）来取出数组中对应的值
* 也可以通过索引（下标）来修改对应位置的值
* 还可以通过索引（下标）在新的位置上插入值


### 数组元素操作（增/删/改/查）
#### 数组元素操作--增
##### push方法（从尾加）
`push`方法可以在数组的末尾添加值，使用方法：
```js
变量名.push('要添加的值');
```
>一次可以添加多个值

##### unshift方法（从头加）
和`push`方法类似

#### 数组元素操作--删
##### pop方法（从后往前删除）
`pop`方法对应的是`push`方法，表示从后往前删除。
##### shift方法（从前往后删除）
`shift`表示从开始位置删除一个元素
##### splice方法（删除指定位置的值）
`splice`方法在括号内可以写一个参数，也可以写两个参数
###### 一个参数
删除从指定位置开始到结束位置的所有元素，并返回被删除的元素（如果有变量）
###### 两个参数
删除从指定位置开始，删除第二个参数数的元素，并返回被删除的元素（如果有变量）

#### 数组元素操作--改
##### splice方法（需改指定位置的元素）
`splice`方法括号里需要添加三个值（也叫参数），分别代表三个意思：
1. 第一个值，整数类型，表示起始位置
2. 第二个值，整数类型，表示步长（往后选几个元素，1代表往后选1个元素）
3. 第三个参数，要替换的数组的值
![[Pasted image 20240127214726.png]]
数组的下标不是在正下方，而是在左下角
###### 步长为0
等价于在起始位置后面插入一个新元素
###### 步长为1
等价于将起始位置代替一个新元素
###### 步长为2
等价于将起始位置及后面一个元素用新元素替代

#### 数组元素操作--查
目前只学习一个方法--`indexOf()`
`indexOf()`括号内可以写两个参数，不过常用的是添加一个参数的情况
##### 一个参数
以要查询的目标为参数
**返回值是`-1`表示未找到，非`-1`数字表示找到的元素的下标**
##### 两个参数
第一个参数是要找的值，第二个参数是开始寻找的位置


### 二维数组
二维数组就是在一维数组内继续添加方括号，即在数组内部继续添加数组。
如果要用二维数组来存放信息，需要先定义一个一维数组，然后分开存放。
```js
// 定义一个一维数组
let arr1 = [];
// 给一维数组里面添加数据
arr1[0] = '宇智波佐助';
arr1[1] = '男';
arr1[2] = '下忍';
arr1[3] = 12;
console.log(arr1); // ['宇智波佐助','男','下忍',12]
// 给一维数组里面添加数据
arr2 = [];
arr2[0] = '春野樱';
arr2[1] = '女';
arr2[2] = '下忍';
arr2[3] = 12;
console.log(arr2); // ['春野樱','女','下忍',12]
// 给一维数组里面添加数据
arr3 = [];
arr3[0] = '漩涡鸣人';
arr3[1] = '男';
arr3[2] = '下忍';
arr3[3] = 12;
console.log(arr3); // ['漩涡鸣人','男','下忍',12]
// 将一维数组添加到另一个数组中，形成二维数组
let arr = [];
arr[0] = arr1;
arr[1] = arr2;
arr[2] = arr3;
console.log(arr);
// [
//   ['宇智波佐助', '男', '下忍', 12],
//   ['春野樱', '女', '下忍', 12],
//   ['漩涡鸣人', '男', '下忍', 12],
// ]
```
如果直接使用`arr[0][0]`会报错，一维使用`arr[0]`操作获取到的数据是`undefined`，再去执行`arr[0][0]`就是无效操作了。
还可以使用`push`方法来给数组赋值：
```js
let arr = [];
arr.push([]);
arr[0].push('宇智波佐助');
arr[0].push('男');
arr[0].push('下忍');
arr[0].push(12);

arr.push([]);
arr[1].push('春野樱');
arr[1].push('女');
arr[1].push('下忍');
arr[1].push(12);

arr.push([]);
arr[2].push('漩涡鸣人');
arr[2].push('男');
arr[2].push('下忍');
arr[2].push(12);

console.log(arr);
```

## 循环
### for循环
一个for循环会一直重复执行，直到指定的循环条件为false。和Java、C的for循环相似。
#### for循环的写法
![[Pasted image 20240127220658.jpg]]
#### for...in和for...of的写法
1. for...in循环的语法是这样的：
```js
    let peppaFamily = ["佩奇", "乔治", "猪妈妈", "猪爸爸"];
    
    for (let i in peppaFamily) {
      console.log(peppaFamily[i]);
    }
    // 输出:
    // 佩奇
    // 乔治
    // 猪妈妈
    // 猪爸爸
    ```
for...in循环会访问数组中的每一项，这里的i对应数组中每一项的下标。
2. for..of循环
```js
    let peppaFamily = ["佩奇", "乔治", "猪妈妈", "猪爸爸"];
    
    for (let item of peppaFamily) {
      console.log(item);
    }
    // 输出:
    // 佩奇
    // 乔治
    // 猪妈妈
    // 猪爸爸
 ```
 for...of循环也会访问数组中的每一项，这里的item对应数组中每一项
 **两者的区别：**
 for...in循环遍历的结果是数组元素的下标，而for...of遍历的结果是元素的值

### while循环
#### while循环
while语句的语法如下：
![[Pasted image 20240127223242.jpg]]
**注意：初始条件写在while循环外，更新条件的表达式写在执行内容里。**
#### do...while循环
do...while的语法如下：
![[Pasted image 20240127223509.jpg]]
区别是do...while会先执行一次再判断
### 跳出循环 break/continue
#### 跳出整个循环：break
跳出循环直接执行循环以后的语句
#### 跳过某次迭代：continue
结束当前迭代，进入下次迭代，并不会终止循环
## 函数
### 函数概述
JavaScript和其它编程语言一样，可以使用函数来解决问题，**函数是一段可以反复调用的代码块**，往往能够实现一个特定的功能，可以解决代码重复的问题。在JavaScript中，函数是头等（first-class）对象，有时我们也可称其为方法。
在学习自定义函数前，先看看JavaScript中的一个内置函数Math.random()。
#### 获取随机数Math.random()
Math是一个内置对象，用于执行数学任务。
```js
const num = Math.random();
```
通过这行代码，可以获得一个范围在\[0,1）之间的随机数。包括0但不包括1。
如果要获取一个三位数随机数，即范围在\[100,1000）之间，可以这样做：
1. 再获取\[100,1000）之间的随机数
要获取\[100,1000）的数，Math.random()应该属于\[0.1,1）。
```js
// num1 的范围是 [0.1, 1)
const num1 = Math.random() * 0.9 + 0.1;
// num2 的范围是 [100, 1000)
const num2 = Math.floor(num1 * 1000);

console.log(num2);
```
>Math.floor(x)是js内置方法，返回小于x的最大整数。比如Math.floor(2.3)返回2，Math.floor(4.9)返回4.


### 自定义函数
JavaScript和其它编程语言一样，可以自定义函数。可以用自定义函数来解决代码复用的问题。自定义函数是需要自行声明的，先来看函数的声明。
#### 函数的声明
js中函数声明有三种方法，这里主要讲两种：
##### 1.用function命令声明
格式如下：
![[Pasted image 20240128002719.jpg]]
用function命令声明函数有四个东西缺一不可
1. 关键词“function”
2. 函数名（自己取的）
3. 函数名之后的小括号
4. 包裹函数体用的大括号
>函数名一般和函数功能有关，一般用小驼峰命名法：即第一个单词首字母小写，后面其它单词首字母大写。

###### 函数的调用
通过函数名来调用函数
**注意，在调用函数的时候，要在函数名后加上英文小括号“（）”，即圆括号运算符。

##### 2.用函数表达式声明
除了用function命令声明函数，还可以用变量赋值的写法。
函数表达式声明函数的格式如下：
![[Pasted image 20240128003128.jpg]]
这种写法将一个匿名函数赋值给变量，赋值等号右边为匿名函数，又称函数表达式。
**注意，采用函数表达式声明函数时，function命令后面不带有函数名**

es6中函数表达式声明可以用箭头函数简写为：
```js
let print = () => {
  console.log("JavaScript 真有趣");
};
```
箭头函数的小括号前省略了function，小括号后加了箭头"=>".
##### 函数声明的提升
采用function命令声明函数时，整个函数会被提升到代码头部。但是函数表达式声明函数的时候不存在函数声明提升，要注意顺序。

##### 两种声明方式的区别
1. 结尾的大括号后是否需要加";"
   * function命令声明：结尾的大括号后不需要加";"
   * 函数表达式：结尾的大括号后需要加";"
2. 有无声明提升
   * function命令声明：有提升；
   * 函数表达式：没有提升；

##### 函数重复声明
如果同一个函数被多次声明，后面的声明会覆盖前面的声明。
##### 立即执行函数
当函数只使用一次时，通常使用IIFE（Immediately Invokable Function Expressions）：
```js
(function() {
  console.log("这个函数只执行一次");
})();
```
他会在函数声明后立即调用函数。之后因为是匿名函数的原因从而无从调用。

### 函数参数
在定义函数时，在括号内加入变量用于接受外部传入的参数，如果有多个参数，用","分隔。在调用函数时，**需要按顺序传入数据**
如果传入的数据超过函数的参数，并不会影响结果，因为**JavaScript允许传入任意个参数而不影响调用**，因此传入的参数比定义的参数多也没有问题。这点和Java有区别，在JavaScript中这样是不会报错的。
如果传入的数据比定义的少也不会报错，只是未传入的部分的值为undefined
#### 参数默认值
在函数定义的时候用=给参数赋默认值

### 函数的返回值
和其它编程语言一样，js函数可以分为“无返回值”和“有返回值”两种
使用“return”把生产的结果返回

### 内置函数——计时器1
常在注册、登录时遇到验证手机号的情况，为了防止频繁获取验证码，会在点击获取后开始倒计时60s，在这段时间里用户不能再次获取验证码。
倒计时每一秒会更新一下，这个可以用js提供的定时执行代码函数setTimeout()和setInterval()来完成，这个定时执行代码的功能，叫做定时器(timer)
#### 延时执行 setTimeout()
setTimeout函数用来指定某个函数或某段代码，在多少毫秒之后执行，它返回一个整数，表示定时器的编号，以后可以用来取消这个定时器。
setTimeout函数基础语法如下：
![[Pasted image 20240128010929.jpg]]
setTimeout函数接受两个参数，第一个参数func|code是将要推迟执行的函数名或者一段代码，第二个参数delay是推迟执行的毫秒数。
一下是setTimeout的三种写法，关注第一个参数的写法和运行顺序：
```js
console.log(1);

/**
 * 第一个参数是代码，注意代码需用引号包裹，否则会立即执行代码
 * 第二个参数是 1000，即 1000ms 后执行 console.log(2)
 */
setTimeout('console.log(2)', 1000);

/**
 * 第一个参数是匿名函数
 * 第二个参数是 2000，即 2s 后执行 console.log(3)
 */
setTimeout(function () {
  console.log(3);
}, 2000);

// 第一个参数是函数名，注意函数名后不要加小括号“()”，否则会立即执行 print4
setTimeout(print4, 3000);

console.log(5);

function print4() {
  console.log(4);
}
```
运行结果：
```js
// 立即执行
console.log(1);
// 立即执行
console.log(5);
// 1s 后执行
console.log(2);
// 2s 后执行
console.log(3);
// 3s 后执行
print4(); // 即：console.log(4)
```
使用setTimeout来做验证码的60s倒计时：
```js
// 首先定义计时总秒数，单位 s
let i = 60;

// 定义变量用来储存定时器的编号
let timerId;

// 写一个函数，这个函数即每次要执行的代码，能够完成上述的 1、2、3
function count() {
  console.log(i);
  i--;
  if (i > 0) {
    timerId = setTimeout(count, 1000);
  } else {
    // 清除计时器
    clearTimeout(timerId);
  }
}

// 首次调用该函数，开始第一次计时
count();
```
#### 回调函数
setTimeour的第一个参数即“回调函数”。把函数指正（指向函数的指针变量）作为参数传给setTimeout，当延时时间到了（触发条件达成）之后，就会通过函数指正调用函数，即调用回调函数。

### 内置函数——计时器2
函数setInterval，用法和setTimeout完全一致，区别仅仅在于setInterval指定某个人鱼每隔一段时间就执行一次，也就是无限次的定时执行。
#### 无限调用setInterval
setInterval函数基础语法如下：
![[Pasted image 20240128012222.jpg]]
现在用setInterval来实现隔1s打印数字1：
```js
let timer = setInterval(print, 1000);

function print() {
  console.log(1);
}
```
改进后的代码：
```js
let i = 60;
print();
let timer = setInterval(print, 1000);

function print() {
  console.log(i);
  i--;
  if (i < 1) {
    clearInterval(timer);
  }
}
```
## 对象
### 对象阐述
对象（object）是JavaScript语言的核心概念，也是最重要的数据类型
#### 什么是对象
对象简单来说就是一组“键值对”（key-value）的集合，是一种无序的复合数据集合：
![[Pasted image 20240128133146.jpg]]
* 大括号：定义一个对象；
* person：定义的对象被赋值给`person`，则`person`将指向这个对象；
* `name:'henry'`：键值对（key：value），键值之间用`:`隔开；
* 一个对象中可以包含多个键值对，每个键值对之间用`,`隔开，最后一个键值对后可以加`,`，也可以不加。
**注意：当一个对象被赋值给`person`，在`person`中保存的是对象的内存地址。而不是对象本身，这种赋值被称为引用**
这种定义对象的方法称为“字面量”。
#### 键名
对象的键名基本都是字符串，键名加不加引号是一样的
```js
let person = {
  name: 'henry',
  age: 18
}

// 和上面的写法意思一样
let person = {
  'name': 'henry',
  'age': 18
}
```
#### 方法
对象的每一个键名又称为“属性”（property），它的“键值”可以是任何数据类型，当它是函数的时候，我们把这个属性称为“方法”，可以像函数那样调用：
```js
let person = {
  name: 'henry',
  age: 18,
  run: function() {
    console.log('running');
  }
}

person.run();
```
#### 对象的创建
除了上面的“字面量”方法，还可以通过构造函数创建新对象。使用构造函数创建对象，需要两步走：
1. 创建一个构造函数，构造函数的名称通常用大驼峰命名法命名；
2. 通过new创建对象实例；
其中，构造函数可以声明对象的名称、属性和方法。
>大驼峰命名法：当变量名或函数名是由一个或多个单词连结在一起，而构成的唯一识别字时，所有单词的首字母均需要大写。

使用函数来创建person对象：
```js
// 第一步：创建构造函数
function People(name, age) {
  this.name = name;
  this.age = age;
}

// 第二步：通过 new 创建对象实例
let person = new People('henry', 18);
console.log(person);
```
**注意：** 构造函数People中的`this`是函数运行时，在函数体内部自动生成的一个对象，只能在函数体内部使用。this就是函数运行时所在的环境对象。
用这个构造函数创建一个对象实例，那么构造函数里的`this.name=name`就表示将传入的参数`name`赋值给对象实例中对应的属性`name`。


### 自定义对象的属性操作
`person`对象就是一个自定义对象
对象是由键值对组成的无序的复合数据集合，键值可以是任何数据类型。当它是函数的时候，我们称为“方法”，调用方法和调用函数的写法一样：
```js
let person = {
  name: 'henry',
  age: 18,
  run: function() {
    console.log('running');
  }
}

person.run();
```
#### 属性的读取
JavaScript中有两种方法读取一个对象的属性：点运算符和方括号运算符
```js
let person = {
  name: 'henry',
  age: 18,
  run: function() {
    console.log('running');
  }
}

person.run();
```
两种写法的效果是一样的，都能够读取对应属性的值，但是方括号运算符的方括号中可以是一个变量。
```js
let person = {
  name: 'henry',
  age: 18
}

let variable = 'name';
console.log(person[variable]);

variable = 'age';
console.log(person[variable]);
```
对象中属性的值可以是任何数据类型，如果某个属性的值是对象，如何读取这个键值对象中的属性呢？
还是使用点运算符或者方括号运算符：
```js
let person = {
  name: 'henry',
  age: 18,
  parents: {
    papa: 'jack',
    mama: 'mary'
  }
}

console.log(person.parents.papa);
console.log(person['parents']['mama']);
```
像`person.parents.papa`或`person.['parents']['mama']`这样的写法被称为“链式引用”
#### 属性的赋值
属性的赋值和读取一样，可以通过点运算符和方括号运算符完成：
```js
let person = {
  name: 'henry',
  age: 18
}

person.name = 'tom';
person['age'] = 10

console.log(person.name);
console.log(person.age);
```
#### 属性的查看
查看一个对象本身的所有属性，可以使用Object.keys方法：
```js
let person = {
  name: 'henry',
  age: 18
}

console.log(Object.keys(person));
```
>代码中的Object，是JavaScript提供的基本对象，JavaScript的所有其它对象都继承自Object对象，即那些对象都是Object的实例。keys是Object对象的一个静态方法。

`Object.key(person)`返回的是一个数组，这个数组由`person`对象的所有属性名构成
#### 属性的删除和增加
如果要删除对象中的某个属性，可以使用delete命令。
```js
let person = {
  name: 'henry',
  age: 18
}

delete person.name;

console.log(person);
```
增加一个属性：
```js
let person = {
  name: 'henry',
  age: 18
}

person.gender = 'male';
```
### 遍历对象属性
如果想要在一个对象中查找某个符合条件的属性，我们就需要遍历对象了。
在JavaScript中可以通过`for...in`或借助`Object.keys`来实现
#### 用`for...in`遍历属性
```js
let person = {
  name: 'henry',
  age: 18,
}

for (let key in person) {
  console.log('键名：' + key + '；键值：' + person[key]);
}
```

#### 借助`Object.keys`遍历属性
由于Object.keys方法返回的是一个由对象中所有属性名组成的数组，我们可以借助这一点来遍历对象：
```js
let person = {
  name: 'henry',
  age: 18,
}

let keys = Object.keys(person);

for (let i = 0; i < keys.length; i++) {
  console.log('键名：' + keys[i] + '；键值：' + person[keys[i]]);
}
```

### 对象的继承
Java中是有“继承”这个概念的，在JavaScript也有。
> Object是JavaScript提供的基本对象，JavaScript的所有其它对象都继承自Object对象，即那些对象都是Object的实例。keys是Object对象的一个静态方法

就是说我们之前学习的“自定义对象”就是继承自JavaScript提供的Object对象的
所有我们除了可以用“字面量”和自定义的构造方法创建对象外，还可以使用JavaScript提供的构造函数Object()或者“继承”来创建对象：
```js
// 字面量
let o1 = {
  name: 'alice',
};

// 构造函数
let o2 = new Object();
let o3 = new Object();

// 继承
funtion O4() {
}; 
O4.prototype = o1; 
let o4 = new O4();
```
在这段代码中，最后一种方法创建的o4对象继承自o1，o1就是o4的原型
#### 原型
原型其实也是JavaScript中的一个对象。原型就是为了罩对象继承的上一级对象。
o1继承自Object，Object就是o1的原型
o4继承自o1，o1就是o4的原型
一个对象，它称呼继承的上一级对象为原型，它自己也可以称为原型链下一级对象的原型
#### 属性是否存在：in
可以用in运算符来判断对象是否拥有某个属性：
```js
let person = {
  name: 'henry',
  age: 18,
};

'name' in person;
'gender' in person;
'toString' in person;
```
`toString`是Object对象1属性。person继承自Object，所以也有这个属性。
所以由于继承的存在，一个对象中的属性分成了两类：继承属性和自身属性。
Object.keys方法返回的属性就包括了这两种属性。
如何判断对象自身属性中是否拥有某个属性呢？
#### 自身属性是否存在：hasOwnProperty
```js
let person = {
  name: 'henry',
  age: 18,
};

person.hasOwnProperty('name');
person.hasOwnProperty('gender');
person.hasOwnProperty('toString');
```
#### Object与JSON、Map的区别
JavaScript中有几个写法和对象长得类似的概念，JSON、Map
##### JSON
JSON是一种轻量级的文本数据交换格式，用JavaScript的语法书写，单独立于这种语言，是编程语言间用于传递数据而约定的数据格式。
###### JSON格式和JavaScript对象的转换
1. JSON.parse():JSON格式=>JavaScript对象
```js
// 一个 JSON 字符串
const jsonStr =
  '{"sites":[{"name":"Runoob", "url":"www.runoob.com"},{"name":"Google", "url":"www.google.com"},{"name":"Taobao", "url":"www.taobao.com"}]}';

// 转成 JavaScript 对象
const obj = JSON.parse(jsonStr);
```
2. JSON.stringify():JAvaScript对象=>JSON格式
```js
const jsonStr2 = JSON.stringify(obj)；
```
##### Map
Map和Object很相似，都可以保存键值对，但是仍有区别：
1. 一个Object的键通常是字符串，但一个Map的键可以是任意值，包括函数、对象、基本类型，所以Map会方便很多；
2. Map中的键值是有序的，而添加到对象中的键则不是；
3. Map的键值对个数可以直接获取，Object则要借助Object.keys()等计算得到
4. Map可直接进行迭代，Object则要借助Object.keys()等；
5. Map不存在键名和原型键名冲突问题，可以直接覆盖，Object则不行；
从某种程度上说，Map比Object更灵活方便，但是Map不能直接转为JSON格式进行通讯，所以可以把Map作为Object的补充来使用。

### 内置对象——Math、Storage
#### Math对象
Math也是JavaScript的一个原生对象，它能提供各种数学功能。该对象不是构造函数，不能生成实例，所有的属性和方法都必须在Math对象上调用。
Math提供的一些用途
##### 常量
Math对象的静态属性，提供以下一些数学常数：
```js
Math.E // 常数e。
Math.LN2 // 2 的自然对数。
Math.LN10 // 10 的自然对数。
Math.LOG2E // 以 2 为底的e的对数。
Math.LOG10E // 以 10 为底的e的对数。
Math.PI // 常数π。
Math.SQRT1_2 // 0.5 的平方根。
Math.SQRT2 // 2 的平方根。
```
常用的是常数π，即Math.PI
##### 静态方法
Math对象提供以下一些静态方法：
```js
Math.abs() // 绝对值
Math.ceil() // 向上取整
Math.floor() // 向下取整
Math.round() // 四舍五入取整
Math.max() // 最大值
Math.min() // 最小值
Math.pow() // 指数运算
Math.sqrt() // 平方根
Math.log() // 自然对数
Math.exp() // e的指数
Math.random() // 随机数
```
>注意：以上方法除了Math.random()都需要传入合适的参数，即需要处理的数字。

注意几个取整方法。
```js
Math.ceil(4.6) // 向上取整，取大于等于 x，并且与它最接近的整数。
Math.floor(4.6) // 向下取整，取小于等于 x，并且与它最接近的整数。
Math.round(4.6) // 四舍五入取整，取与 x 最接近的整数。
```
除了Math之外，还有一个常用的内置对象：Storage
#### Storage对象
Storage接口用于脚本在浏览器保存数据。两个对象部署了这个接口：window.sessionStorage和window.localStorage。
sessionSrotage保存的数据用于浏览器的一次会话（session），当会话结束（通常是窗口关闭），数据被清空；localStorage保存的数据长期存在，下一次访问该网站的时候，网页可以直接读取以前保存的数据。
主要看一下window.localStorage的用法。
##### 数据的存入：setItem
写法：
```js
window.localStorage.setItem('myLocalStorage', 'storage Value');
```
window.localStorage.setItem('key','value')方法接受两个参数：
1. key：键名；
2. value：键值
两个参数都是字符串，不是字符串的参数会被转成字符串后再存入浏览器
注意，如果要存入的数据不是字符串类型的数据，最好先转换成字符串类型，比如要存入一个对象可以这么写：
```js
const obj = {
  name: 'henry',
  age: 18
}
const value = JSON.stringify(obj);
window.localStorage.setItem('myLocalStorage', value);
```
>JSON.stringify()方法可以将一个JavaScript值（对象或者数组）转换为一个JSON字符串。

##### 读取数据：getItem
写法：
```js
window.localStorage.getItem('myLocalStorage');
```
window.localStorage.getItem('key');接受一个参数，即键名。

##### 清楚缓存：clear
写法：
```js
window.localStorage.clear();
```


### 内置对象——String
JavaScript原生提供的三个包装对象之一就是`String`（另外两个是Number、Boolean）。它给字符串提供了很多好用的方法，但是只要掌握很少的几个就已经足够了。
>包装对象：原生对象可以把原始类型的值编程（包装成）对象。
>>`let v2 = new String('abc');`
>包装对象的最大目的：1.使得JavaScript的对象涵盖所有的值；2.使得原始类型的值可以方便地调用某些方法（比如下面的这些）

#### 字符串长度：length
```js
let len = 'here is an apple'.length;
```
字符串中的空格也计算在内的。
#### 查找字符：indexOf()
从字符串中查找某个子字符串是否存在：
```js
let str = 'here is an apple';
const index = str.indexOf('an');
console.log(index);
```
当str中存在子字符串an时，返回的值为an中的a所在的下标（下标从0开始计），即8。
当str中不存在子字符串an时，返回值为-1。
#### 去掉两端空格：trim()
我们在输入内容的时候常常会遇到多输入空格的时候，这时候可以用`trim()`把字符串开头和结束位置的空格去掉。
```js
// 'here' 之前有一个空格，'apple' 之后有三个空格
let str = ' here is an apple   ';
const trimedStr = str.trim();
console.log(str.length);
console.log(trimedStr.length);
```
>注意，`trim()`是去掉字符串前后的空格，不论前后有多少空格都会去掉，但不会去掉中间的空格。另外，`trim()`不会改变原字符串`str`，而是复制一份原字符串，修改后返回给`timedStr`。

#### 截取字符串：substring/substr
如果要截取一个字符串中的一部分，可以用`substring`或`substr`
比如要截取一个URL中#之后的内容：https://www.youkeda.com/userhome#collect
可以这样做：
```js
let url = 'https://www.youkeda.com/userhome#collect';

// 首先找到 # 后第一个字母的下标
const index = url.indexOf('#') + 1;

// 有 hash 才能进行截取，没有就直接提示不存在
if (index) {
  // 用 substring 截取字符串
  const hash1 = url.substring(index, url.length);

  // 计算 hash 的长度
  const lenHash = url.length - index;
  // 用 substr 截取字符串
  const hash2 = url.substr(index, lenHash);

  console.log(hash1);
  console.log(hash2);
} else {
  console.log('不存在 hash');
}
```
* substring（start，end）——要截取的字符串的开始下标；end——要截取的字符串的结束下标
* substr（start,len）：start——要截取的字符串的开始下标；len——要截取的字符串长度。
>注意：substring和substr的第二个参数不写的时候，会一直截取到字符串结束为止。

它们和`trim`一样都不会改变原字符串，而是返回处理后的字符串
#### 分隔字符串：split
split方法按照给定规则分割字符串，返回一个有分割出来的子字符串组成的数组：
```js
const splitedStr = 'a|b|c'.split('|');
console.log(splitedStr);
```
`split`也不会改变原字符串，而是返回一个由分割出来的子字符串组成的数组。
#### 小结
| 属性/方法 | 作用 |
| ---- | ---- |
| str.length | 返回字符串长度 |
| str.indexOf(sub) | 返回子字符串sub的开始下标，不存在则返回-1<br>注意：这里的参数sub是个字符串变量 |
| str.trim() | 字符串前后去空格 |
| str.substring(s,e) | 截取下标从s到e的子字符串<br>注意：这里的参数s和e是个数字变量 |
| str.substr(s,len) | 截取下标从s开始，长度len的子字符串<br>注意：这里的参数s和len是个数字变量 |
| str.split(pattern) | 按规格pattern分割字符串<br>注意：这里的参数pattern是个字符串变量 |
### 内置对象——Array
Array是JavaScript的原生对象之一，它为数组提供了很多实用的方法，这里学习其中几个。
#### 连接数组：join()
join()方法以指定参数作为分隔符，将所有数组成员连接为一个字符串返回。如果不提供参数，默认用逗号分隔：
```js
let arr = [1, 2, 3, 4];

arr.join(" "); // '1 2 3 4'
arr.join(" | "); // "1 | 2 | 3 | 4"
arr.join(); // "1,2,3,4"
```
这个方法和字符串里的`split`方法正好是一对作用相反的方法：
```js
let str = "a|b|c";

const splited = str.split("|");
console.log(splited);

const joined = splited.join("|");
console.log(joined);
```
`join()`方法不会改变原数组
#### 倒序排列：reverse()
`reverse`方法用于颠倒排列数组元素，返回改变后的数组。
```js
let str = "a|b|c";

const splited = str.split("|");
console.log(splited);

const joined = splited.join("|");
console.log(joined);
```
==注意：该方法将改变原数组。==
这个方法对原本有序的数组用起来很方便，比如按时间顺序排列之类的
如果数组原本无序，该如何排序呢？
#### 排序：sort()
sort方法对数组成员进行排序，默认是按照**字典顺序**排序。如果想让sort方法按照自定义方式排序，可以传入一个函数作为参数。
将数组按照人物年龄从小到大排列：
```js
let arr = [
  { name: "jenny", age: 18 },
  { name: "tom", age: 10 },
  { name: "mary", age: 40 },
];

arr.sort(function (a, b) {
  return a.age - b.age;
});

console.log(arr);
```
这个函数有两个参数，比较两个数组成员，原数组中a排在b之前。
这个函数有返回值，当返回值大于0时，表示第一个成员一个排在第二个成员之后，否则排在第二个成员之前
==注意，该方法将改变原数组==
#### 遍历：map/forEach
遍历数组我们之前用的是`for`循环，但其实JavaScript提供了两个很方便的遍历方法
##### 有返回值的遍历：map
map方法的使用：接受一个函数，然后将数组的所有成员一次传入这个参数函数，最后把每一次执行结果组成一个新数组返回
```js
let arr = [
  { name: "jenny", age: 18 },
  { name: "tom", age: 10 },
  { name: "mary", age: 40 },
];

// elem: 数组成员
// index: 成员下标
// a: 整个数组
const handledArr = arr.map(function (elem, index, a) {
  elem.age += 1;
  console.log(elem, index, a);
  return elem.name;
});

console.log(arr);
console.log(handledArr);
```
map方法的参数函数可以有三个参数：elem、index、a。
* elem：表示依次传入的数组成员
* index：表示依次传入的数组成员对应的下标
* a：表示蒸柜数组

##### 无返回值的遍历：forEach
用法和map基本一直，不过没有返回值：
```js
const handledArr = arr.forEach(function (elem, index, a) {
  elem.age += 1;
  console.log(elem, index, a);
  return elem.name;
});

console.log(handledArr);
```

#### 小结

关于数组我们需要掌握的几个基础用法：

|属性/方法|作用|
|---|---|
|arr.join(pattern)|按规则 pattern 连接数组，返回字符串|
|arr.reverse()|将原数组倒序排列|
|arr.sort(func)|自定义排序，根据传入的参数函数 func 将数组成员排序|
|arr.map(func)|根据传入的参数函数 func 对数组进行遍历操作，返回操作后的数组  <br>函数有三个参数，依次为：数组成员、对应下标、整个数组|
|arr.forEach(func)|根据传入的参数函数 func 对数组进行遍历操作，无返回值  <br>函数有三个参数，依次为：数组成员、对应下标、整个数组|


### 内置对象——Date
在实际工作中常常会遇到要处理时间的情况，所以需要学习要学JavaScript提供的时间库的一些功能。JavaScript提供一个原生的时间库：`Date`对象。以国际标准时间1970年1月1日00:00:00作为时间的零点，可以表示的范围是前后各1亿天。
#### 获取当前时间：new Date()
在不加参数的情况下返回的就是当前时间
如果传入了一些参数，就能够生成**特定的时间对象**，可以传入数字、字符串、毫秒数：
```js
// 传入表示“年月日时分秒”的数字
let dt1 = new Date(2020, 0, 6, 0, 0, 0);
console.log(dt1);

// 传入日期字符串
let dt2 = new Date("2020-1-6");
console.log(dt2);

// 传入距离国际标准时间的毫秒数
let dt3 = new Date(1578240000000);
console.log(dt3);
```
1. 如果之传入一个数字，会被认为传入的是毫秒数
2. 月份的范围是0-11而不是1-12
#### 日期运算
##### 时间差：毫秒数
两个时间对象是可以直接相减的，返回值为两者的毫秒数差：
```js
let dt1 = new Date(2020, 2, 1);
let dt2 = new Date(2020, 3, 1);

// 求差值
let diff = dt2 - dt1;

// 一天的毫秒数
let ms = 24 * 60 * 60 * 1000;

console.log(diff / ms); // 31
```
##### 早晚比较：大小于符号
如果要比较两个时间的早晚，可以直接使用`>`或者`<`：
```js
let dt1 = new Date(2020, 2, 1);
let dt2 = new Date(2020, 3, 1);

console.log(dt1 > dt2); // false
console.log(dt1 < dt2); // true
```
#### 解析日期字符串：Date.parse()
Date.parse方法用来解析日期字符串，返回该时间距离时间零点的毫秒数
`Date.parse()`方法可以把日期字符串转成距离时间零点的毫秒数

时间对象中有三大类方法 to方法、get方法和set方法，这里学习一部分方法
#### 时间对象转时间字符串：to方法
to方法有很多，这是`toJSON()`方法：
```js
let dt = new Date();
let dtStr = dt.toJSON();

console.log(dtStr); // 2020-01-03T09:44:18.220Z
```
为什么打印的时间和当前时间差8个小时，因为打印的时间是标准时间，而我们的时间是东八区时间，比国际标准时间快8个小时

#### 获取时间对象的年/月/日：get方法
Date对象提供了一些列get方法，用来获取实例对象某个方面的值：
```js
let dt = new Date();
dt.getTime(); // 返回实例距离1970年1月1日00:00:00的毫秒数。
dt.getDate(); // 返回实例对象对应每个月的几号（从1开始）。
dt.getDay(); // 返回星期几，星期日为0，星期一为1，以此类推。
dt.getFullYear(); // 返回四位的年份。
dt.getMonth(); // 返回月份（0表示1月，11表示12月）。
dt.getHours(); // 返回小时（0-23）。
dt.getMilliseconds(); // 返回毫秒（0-999）。
dt.getMinutes(); // 返回分钟（0-59）。
dt.getSeconds(); // 返回秒（0-59）。
```
>注意：这些get方法返回的都是整数，不同的方法返回值的范围不一样：分钟和秒：0到59；小时：0到23；星期：0（星期天）到6（星期六）；日期：1到31；月份：0（一月）到11（十二月）

* 除了“日期”外，其它的时间范围都是从0开始的
#### 设置时间对象的年/月/日：set方法
set方法和get方法正好相反，能够设置事件对象的某个方面的值。
```js
let dt = new Date();
dt.setTime(ms); // 设置实例距离1970年1月1日00:00:00的毫秒数。
dt.setDate(date); // 设置实例对象对应每个月的几号（从1开始）。
dt.setFullYear(year); // 设置四位的年份。
dt.setMonth(month); // 设置月份（0表示1月，11表示12月）。
dt.setHours(hour); // 设置小时（0-23）。
dt.setMilliseconds(ms); // 设置毫秒（0-999）。
dt.setMinutes(min); // 设置分钟（0-59）。
dt.setSeconds(sec); // 设置秒（0-59）。
```
>set方法没有setDat方法，因为星期几是计算得到的。

以上方法了解即可，需要的时候在MDN上查询即可。
#### 小结
![[Pasted image 20240129024800.jpg]]


## BOM
### BOM
之前学习的是`JavaScript`的基本语法，现在我们开始学习如何和`HTML`和`CSS`一起联合使用，学习怎么完成**页面交互过程**
为了能让页面显示出来，首先需要在浏览器中输入网址，敲击回车，浏览器能自动渲染网页内容。和浏览器渲染有关的对象，叫做**浏览器对象模型（Browser Object Model)——BOM**
**BOM**是由一系列相关对象构成，每个对象都提供了很多方法和属性
但是BOM缺乏标准，属于约定俗称，所以在不同浏览器并不完全相同。在前端有一门高级技术叫做**浏览器兼容处理**，用于处理这类问题
现在业界主要以**Chrome**为准，主要学习**BOM**一些共同的对象和API
#### BOM对象
在BOM里最重要的对象有5个，分别如下：
1. window（窗口）：window是整个网页的框架，每个网页的内容都是装载在window里面
2. navigator（浏览器）：navigator里面存储浏览器相关信息
3. histor（历史）：每个网页可以前进后退，history便拿来存储整个网页栈的
4. screen（显示屏幕）：screen包含我们显示屏幕的信息，这个是硬件信息
5. location（地址）：location包含当前访问的地址（网址）信息
![[Pasted image 20240129131238.jpg]]
**特别的：**
* screen是**整个电脑**唯一的
* navigator是**整个浏览器**唯一的，如果有多个浏览器就会有多个navigator
* window是**每个网页**唯一的，每个网页都有一个独立的window
* history，location是**每个网页**的信息，也是唯一的。

### window
#### HTML中嵌入JavaScript
在所有BOM中最重要的是**window对象**
在之前的学习中只是单纯写`JavaScript`，这次吧JavaScript写到**HTML**中，方便执行
```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <title>优课达</title>
  </head>
  <body>
    <h1>优课达-学的比别人好一点</h1>
    <script src="./index.js"></script>
  </body>
</html>
```
在`body`底部加入`<script src="./index.js"></script>`，嵌入执行脚本，然后在`index.js`脚本中加入`JavaScript`代码

#### window
在`JavaScript`中可以用**console.log**打印一下window，看看window到底是什么：
![[Pasted image 20240129131900.png]]
在`window`对象中，有很多**方法**，比如`alert`，`confirm`...还有一些**属性对象**比如：`console`，`screen`，`navigator`，`location`...
如果还不清楚可以查看：[MDN文档](https://developer.mozilla.org/zh-CN/docs/Web/API/Window)
官方解释为：
1. window对象表示一个浏览器窗口或一个frame框架，处于对象层次的**最顶端**，提供了处理浏览器窗口的方法和属性
2. window对象是浏览器对象中的**默认对象**，所以可以隐式的引用window对象的属性和方法。在浏览器环境中，添加到window对象中的方法、属性等，其作用域都是全局的。
>window是默认对象，如果调用window上面的方法，可以省略，也可以称为隐式调用window上面的属性和方法


### Location/History
#### Location
用`Location`对象来保存当前页面位置的信息。
可以查看MDN文档[Location](https://developer.mozilla.org/zh-CN/docs/Web/API/Location)
##### Location属性
通过文档可以看到Location中常用属性如下：

| 属性 | 解释 |
| ---- | ---- |
| href | 整个网页地址 |
| hostname | 网页域名 |
| host | 网页域名+端口信息 |
| Protocol | 代表协议信息 |
| origin | 页面来源的域名的标准形式 |
| pathname | 包含url路径部分 |
| search | 表示URL参数 |
用图表示如下：
![[Pasted image 20240129154405.jpg]]
##### Location方法
只需要重点掌握一个方法——**reload()**
刷新当前页面
为了防止无限快速循环，需要设置一个定时器延迟调用reload。
```js
setTimeout(function () {
  window.location.reload();
}, 3000);
```
其它方法了解即可
###### 跳转到新地址
可以修改Location直接将网页地址赋值给Location即可
```js
window.location = 'https://www.youkeda.com';
```
#### History
**History**允许操作浏览器的曾经在标签页或者框架里访问的会话历史记录，由这个名称可以得知，History会存储该窗口的历史记录
[History](https://developer.mozilla.org/zh-CN/docs/Web/API/History)
如果原始网页为`https://www.youkeda.com`，那History中的存储为
```js
// 会话记录
['https://www.youkeda.com'];
```
如果在网页中点击某个链接，或者用`window.location=xxx`跳转到`https://www.baidu.com`，那history中存储为：
```js
// 会话记录
['https://www.youkeda.com', 'https://www.baidu.com'];
```
这是一个数组（或者说是列表），在实际存储中用到的数据结构和数组特别类似，叫做**栈**
在history中需要掌握两个方法，**back()** 和 **forward()** 分别对应浏览器左上角的返回和前进按钮

### Navigator/Screen
#### Navigator
**Navigator**表示用户代理的状态和标识，也就是浏览器基本信息。这里有一个属性——**userAgent**，代表当前浏览器的用户代理
结果如下：
```html
Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/121.0.0.0 Safari/537.36 Edg/121.0.0.0
```
通过这个信息可以得知
>**Mozila**是一个基金会，表示这是一个主流浏览器  **Windows NT 10.0; Win64; x64**表示电脑信息  **Chrome/121.0.0.0**表示浏览器版本




## DOM和DOM操作
### 初识DOM
#### 初识DOM
本节内容是**整个JavaScript 甚至 整个前端 最最核心的内容**
本节的终点——**文档对象模型**（Document Object Model）简称为**DOM**。
官方解释为：
>文档对象模型（DOM）可以将**web页面**与**脚本或编程语言**连接起来

##### 1. web页面
这里的web页面就是之前用HTML和CSS绘制的页面，也称作为**文档**
##### 2.脚本或编程语言
为什么不直接说JavaScript语言呢？
>因为DOM是一种**规范**，也可以说是**约定**，只要遵循这个规范，无论的`JavaScript`还是`python`，或者`Java`都可以被连接起来

DOM如何实现连接的？
#### DOM映射
HTML和XML这种形式的文档其实是**树状结构**，也对应数据结构中的**树**
举个例子：
```html
<html>
  <head>
    <title>youkeda</title>
  </head>
  <body>
    <div>
      <h1>优课达</h1>
      <p>学的比别人好一点</p>
    </div>
  </body>
</html>
```
![[Pasted image 20240129164153.jpg]]
图示就是一棵倒着的树，最顶端是树根，这就是DOM树。
DOM树特性：
1. 树根是DOCUMENT，也可以称为整个页面文档
2. 每个HTML标签称之为**DOM节点**，英文为**Node**或者**Element**
3. 每个HTML标签包裹的子标签，在树上体现为分支，称为**儿子节点**。
4. 儿子节点类推可以得知后面为**孙子节点**
5. 所有的长辈称为**祖先节点**
6. 亲兄弟称为**兄弟节点**
上面的特性中的**粗体**是专业术语（有趣）

### 访问DOM
#### 获取DOCUMENT
web网页最终会映射为一棵DOM树，DOM树连接网页和JavaScript语言，那么如何获取DOM树的根部元素呢？
DOCUMENT元素会存在全局变量window下面，可以通过下面的代码来访问：
```js
window.document;
```
最终JSConsole效果如下：
![[Pasted image 20240129165816.png]]
从中可以知道`window.document`得到的是一个`HTMLDocument`对象，对象内容有点多，只要知道几个属性就行了：比如document内容key为`documentElement`
还可以了解一下`body`，`head`属性，分别对应HTML中的`body`，`head`内容
#### Chrome调试工具
使用Chrome开发者工具可以很方便的阅读
使用方法：
1. 在**非工程目录区域**点击右键，点击**检查**开启开发者窗口
2. 然后在开发者窗口里切换到**Console**面板
3. 再点击代码演示
4. 可以看到Console里面出现  **\#document** 这个是Chrome单独处理过的，可读性较强
#### 选择器查询
如果想获取某一个特殊节点该怎么办？
这就需要用到**选择器查询方法**——**querySelector()**
这个方法需要传递一个字符串形式的**selectors**作为筛选条件，需要用学过的CSS只是，用`.类名`作为条件，如果相同类名的节点很多，还可以加强筛选条件，用`父类.子类名`筛选。如：
```js
document.querySelector('main .core .subtitle');
```
##### 迭代查询
得到元素后，还可以利用这个元素继续筛选器内部元素，比如想筛选器内部的a标签，可以继续完善代码：
```js
let subtitle = document.querySelector('main .core .subtitle');
console.log(subtitle.querySelector('a'));
```
#### 选择器全量查询
上面只能查询到第一个满足条件的节点，如果想查询所有满足条件的节点只要换个方法就行了，改为**querySelectorAll()**
此时会返回多个节点，并且查询返回的是一个**类数组**，可以直接通过索引访问
>类数组，就是类似数组形式，（可以通过索引访问的对象都可以成为类数组），从JSConsole中我们实际得到的是**NodeList**对象
#### 其它筛选方法
`querySelector`和`querySelectorAll`是最新提出的方法，在这两个方法之前有一套最原生的DOM查询函数：
**getElementByld()**：根据**id**查询某个节点
**getElementsByClassName()**：根据**class**查询多个节点
**getElementsByTagName()**：根据**标签名**查询多个节点
querySelector（All）和getElementXXX有什么具体区别呢？最主要的区别在于——**动态性**
>querySelector查询出来的元素是拷贝的原始数据，不会再随着页面DOM节点的改变而变化
>get系列方法查询出来的元素就是原始数据，所以会跟着页面DOM节点的改变而变化

只要记住以后大多数用`querySelector(All)`即可

### DOM属性
#### DOM种类
本次学习DOM内部细节，学习它的重要属性，先统计一下之前遇到的DOM种类。
```html
<!-- HTMLDocument 根文档 -->
<html>
  ……
</html>

<!-- HTMLDivElement DIV类型 -->
<div class="subtitle">
  ……
</div>

<!-- HTMLAnchorElement 超链接类型 -->
<a class="free-bright">免费靓号</a>

<!-- HTMLInputElement Input类型 -->
<input class="password" type="pasworkd" placeholder="请输入密码" />
```
基本每一种HTML标签都有一种DOM类型对应，还有非常多的类型，可以打开[MDN网站](https://developer.mozilla.org/zh-CN/docs/Web/API)搜索`Element`
了解一下即可。
#### DOM属性
##### DOM类别
上面能看到很多DOM种类，可以归纳为几个类别：
1. 元素节点
2. 特性节点
3. 文本节点
4. 其它的不重要忽略……
这三种节点分别对应什么HTML代码？看案例：
html代码：
```html
<!DOCTYPE html>
<head>
  <meta charset="UTF-8" />
  <title>优课达</title>
</head>
<body>
  <div id="test">优课达</div>
  <script src="./index.js"></script>
</body>
```
JS代码：
```js
let divDom = document.querySelector('div#test');
console.log(divDom.nodeType, divDom.nodeName, divDom.nodeValue);

// 获取DIV节点的第一个儿子节点，代表 '优课达' 这个字符串
let txtDom = divDom.firstChild;
console.log(txtDom.nodeType, txtDom.nodeName, txtDom.nodeValue);

// 获取DIV节点的id属性
let attDom = divDom.attributes.id;
console.log(attDom.nodeType, attDom.nodeName, attDom.nodeValue);
```
结果为：

| 节点 | nodeType | nodeName | nodeValue | 类型 |
| ---- | ---- | ---- | ---- | ---- |
| divDom | 1 | DIV | null | 元素节点 |
| txtDom | 3 | \#text | 优课达 | 文本节点 |
| attDom | 2 | id | test | 特性节点 |
总结特性如下：
1. 整个HTML中，无论是标签，标签属性，还是纯文本字符串都是`Element`，不同的地方在于`nodetype`分别是`1,2,3`
2. HTML标签都是**元素节点**，可以用`nodeName`获取标签名称
3. 纯文本都是**文本节点**，可以用`nodeValue`获取文本内容
4. 标签的每个属性都是**特性节点**，可以用`nodeName`取得属性Key，用`nodeValue`取得属性Value
5. `attributes`可以获取元素节点的所有属性，得到的结果是一个字典，通过属性Key获取对应的特性节点
##### DOM内容
继续修改上面的代码，如下：
```js
let divDom = document.querySelector('div#test');
console.log(divDom.nodeType, divDom.nodeName, divDom.nodeValue);

// 获取DIV节点的第一个儿子节点，代表 '优课达' 这个字符串
let txtDom = divDom.firstChild;
console.log(txtDom.nodeType, txtDom.nodeName, txtDom.nodeValue);

// 获取DIV节点的id属性
let attDom = divDom.attributes.id;
console.log(attDom.nodeType, attDom.nodeName, attDom.nodeValue);
```
```js
let divDom = document.querySelector('div#test');
console.log(divDom.outerHTML, divDom.innerHTML, divDom.innerText);
```
结果如下：

| 属性 | 总计 |
| ---- | ---- |
| outerHTML | **整个DOM的HTML代码** |
| innerHTML | **DOM内部HTML代码** |
| innerText | **DOM内部纯文本内容** |
实际情况下根据需要利用不同的属性获取内容
##### DOM亲属
我们可以利用`firstChild`属性获取到元素的**第一个儿子节点**，还能获取到哪些其它亲属呢？

| 属性 | 总结 |
| ---- | ---- |
| firstChild | 指定节点的第一个子节点 |
| lastChild | 指定节点的最后一个子节点 |
| childNodes | 指定节点的子节点的集合 |
| parentNode | 指定节点在DOM树中的父节点 |
>注意：
>选择一个父节点的子节点时，非IE浏览器 如FireFox、Chrome等，会把换行符也当作一个元素，也就是说不同浏览器的表现是不一样的
>> 具体项目中腰考虑到多浏览器的情况

#### DOM样式
通过DOM可以访问到CSS特性。

| 属性 | 类型 | 总结 |
| ---- | ---- | ---- |
| classList | `DOMTokenList`<br>类数组 | classList数组方式存储所有的class名称 |
| style | `CSSStleDeclaration` | 对象货字典的方法存储CSS Style |

#### DOM数据属性
网页设计的初衷是使**数据**和**特定的HTML标签**相关联，而我们能肉眼看到的数据只是HTML标签内部纯文本（innerText）部分，数据肯定不止肉眼所见那么少，因为有的数据不一定是为了展示，而是有前途用途。
HTML提供一种数据属性的标准，利用`data-`允许在标准内于HTML元素中存储额外的信息。例如：
```html
<!DOCTYPE html>
<head>
  <meta charset="UTF-8" />
  <title>优课达</title>
</head>
<body>
  <article data-parts="3" data-words="1314" data-category="python">
    ...
  </article>
  <script src="./index.js"></script>
</body>
```
`article`是语义化标签中放置文章区域的标签。对文章而言除了文章内容还有其他额外数据，例如：段落字数，分类，等。
这些额外数据不一定直接展示，字数可能是某种特效菜展示，分类数据是动态更新时需要用到。
注意，数据属性**很重要**，在前端中广泛应用，可以去看看其它网站的代码。
如何通过JS来获取呢？
```js
const article = document.querySelector('article');
console.log(article.dataset);
```
可以看出`dataset`是个Map对象，是`data-*`这个`*`的**Key-Value**的集合

### DOM操作（案例一）
#### 引言
通过前面的学习已经对DOM有了很深入的了解，可以使用JavaScript完成任意网页内容提取。
后面通过实例来学习DOM操作怎么使用
#### DOM样式修改
如何通过JavaScript来完成选定的渲染
>是否可以在选定的时候，向`select`插入一个`img`节点，渲染选中的图片，然后再次点击的时候清除`select`内部节点

如果要这样实现，我们需要怎么做？
1. 使用JavaScript创建节点（`img`节点）
2. 设置节点的样式、属性(`img`节点设置`src`属性)
3. 在已存在节点内部添加子节点（`img`节点需要添加到`select`中）
4. 清空节点内部子节点（再次点击时清空`select`的子节点）

```js
// 保存当前是否选中的状态
let isSelected = false;

// 获取整个元素的节点
const box = document.querySelector('.box');

// 获取select框节点
const select = document.querySelector('.select');

// 给整个元素添加点击事件【大家可以先忽略这部分】
box.addEventListener('click', function () {
  // 点击以后触发这个函数

  // 修改当前选中状态，取反即可
  isSelected = !isSelected;

  // 如果当前是选中状态、则添加img到select中
  if (isSelected) {
    // 创建一个img标签节点
    const img = document.createElement('img');

    // 设置img的src属性和样式，让其撑满select框
    img.src = 'https://style.youkeda.com/img/sandwich/check.png';
    img.setAttribute('style', 'width: 100%; height: 100%;');

    // 将这个节点添加到select框中
    select.appendChild(img);
  } else {
    // 如果不是选择状态，则清空内部子元素
    select.innerHTML = '';
  }
});
```

上面的代码都有详细的注释，大家仔细阅读下。
##### 1. 创建标签节点

**document.createElement(tagName)**

> 此方法用于创建一个由标签名称 tagName 指定的 HTML 元素，也就是上节课提到的**元素（标签）节点**。

如果想创建一个`div`标签，我们可以使用：

```js
const div = document.createElement('div');
```

**document.createTextNode(string)**

如果想继续在这个`div`标签内部，添加纯文本内容，可以继续使用创建文本方法**document.createTextNode()**，代码如下：

```js
const div = document.createElement('div');
const txt = document.createTextNode('优课达-学的比别人好一点');
```

我们继续把`txt`添加到`div`中，把`div`添加到`body`中，代码如下：

```js
const div = document.createElement('div');
const txt = document.createTextNode('优课达-学的比别人好一点');
div.appendChild(txt);
document.body.appendChild(div);
```
##### 2. 添加新节点

**appendChild(newNode)**

在上面的案例中，我们多次用到`appendChild()`，此方法可以往该节点中插入儿子节点。
上面案例比较多，我就不举例了，我再给大家介绍一些和此方法类似的 API。

**inserBefore(newNode， referenceNode)**

此方法和`appendChild()`刚好相反，`appendChild`是在**所有儿子节点之后**添加，`inserBefore`是在**某个目标儿子节点之前**添加。

`insertBefore(newNode, referenceNode)`，需要两个参数，`newNode`表示新节点，`referenceNode`表示目标节点，也就是新节点插入到目标节点之前。

我们来看一个案例：

```html
<!DOCTYPE html>
<head>
  <meta charset="utf-8" />
  <title>优课达</title>
</head>
<body>
  <ul class="root">
    <li class="sars">SARS</li>
  </ul>
  <script src="./index.js"></script>
</body>
```

在案例中，我们有一个列表，里面陈列着疾病`SARS`。后来我们发现`H1N1`，因为没有`SARS`严重，我们将其放在`SARS`后。 2020 年发生`新型冠状病毒`，比`SARA`严重，需要插入到其前面，最终的顺序为

```html
<ul class="root">
  <li>新型冠状病毒</li>
  <li>SARS</li>
  <li>H1N1</li>
</ul>
```

那如何用 JS 来完成这个动态逻辑呢？我们来看看代码：

```js
const root = document.querySelector('ul.root');
const sars = document.querySelector('li.sars');

// 创建 H1N1
const H1N1 = document.createElement('li');
const H1N1Txt = document.createTextNode('H1N1');
H1N1.appendChild(H1N1Txt);
root.appendChild(H1N1);

// 创建 新型冠状病毒
const nCoV = document.createElement('li');
const nCoVTxt = document.createTextNode('新型冠状病毒');
nCoV.appendChild(nCoVTxt);
root.insertBefore(nCoV, sars);
```
上面的代码中重复代码太多，所以我们可以通过函数来实现代码的复用：
```js
function createDisease(txt) {
  const dom = document.createElement('li');
  const domTxt = document.createTextNode(txt);
  dom.appendChild(domTxt);
  return dom;
}

const root = document.querySelector('ul.root');
const sars = document.querySelector('li.sars');

// 创建 H1N1
const H1N1 = createDisease('H1N1');
root.appendChild(H1N1);

// 创建 新型冠状病毒
const nCoV = createDisease('新型冠状病毒');
root.insertBefore(nCoV, sars);
```
##### 3.设置样式、属性
可以通过下面代码设置CSS样式，和直接在HTML代码中写`style`。
```js
img.setAttribute('style', 'width: 100%; height: 100%;');
```
`dom.style`是一个Map对象，如果不想全量替换样式，还可以单独设置某些属性，如：
```js
dom.style.color = 'xxxx';
```
**setAttribute()** 不仅仅可以设置`style`之外，所有HTML属性都能用他设置，比如`id`、`src`、`type`、`disabled`等等。
###### classList
如果要给img设置太多的样式写起来会很麻烦。之前我们知道`classList`能获取到DOM上所有的类，所有我们能把样式写成CSS，然后只用添加或删除class
`classList`提供了基础操作的增删改查方法。

##### 4.innerHTML
在示例中，我们使用`innerHTML=''`清空`select`节点的所有后代内容。
我们还可以利用`innerHTML`给元素添加内容。
可以把代码这样改写：
```js
function createDisease(txt) {
  const dom = document.createElement('li');

  // 我们可以直接用innerHTML设置其纯文本
  dom.innerHTML = txt;
  return dom;
}
```

### DOM操作（案例二）
#### 案例介绍
在搜索的时候会存在联想搜索的情况
开发步骤：
1. 首先，不考虑鼠标交互的情况下，完成静态HTML页面
2. 监听搜索框Input（下一章会学）
3. 当输入内容是**肺炎**时，显示模糊搜索结果
4. 当输入内容不是**肺炎**时，显示**登录查看历史**
#### 开发静态HTML页面
这部分比较简单，直接看代码：
```html
<body>
  <div>
    <nav>
      <!-- 头部搜索框区域 -->
    </nav>
    <main>
      <!-- 输入非'肺炎'情况 -->
      <section class="login">
        登录查看历史
      </section>
      <!-- 输入'肺炎'情况 -->
      <ul class="search-result">
        <li>
          <i class="search"></i>
          <p><em>肺炎</em>疫情实时动态</p>
          <i class="edit"></i>
        </li>
        ……
      </ul>
    </main>
  </div>
</body>
```
代码主要分为3块区域，**搜索框**，**登录查看历史**，**肺炎相关列表**，最后两个区域不会共存。
#### 监听Input输入事件，处理区域显示隐藏
监听部分代码暂时内置：
```js
const input = document.querySelector('input');

// 监听键盘事件
input.addEventListener('keyup', function() {
  // this 是DOM节点，this.value可以获取input内输入的值
  console.log(this.value);
});
```
在Input输入框里输入内容，内容会实时在JSConsole打出，说明就已经完成输入事件的监听。
##### 监听输入肺炎时，显示肺炎查询结果
显示和隐藏可以利用CSS中的`display:block/none;`进行控制。
可以先修改CSS将**登录查看历史**设置可见，将**搜索结果**设置不可见
```css
main .search-result {
  padding: 0;
  display: none;
}
```
然后修改JavaScript，动态控制显示和隐藏：
```js
const input = document.querySelector('input');

const login = document.querySelector('.login');
const searchResult = document.querySelector('.search-result');

// 监听键盘事件
input.addEventListener('keyup', function() {
  // this 是DOM节点，this.value可以获取input内输入的值
  if (this.value === '肺炎') {
    login.style.display = 'none';
    searchResult.style.display = 'block';
  } else {
    login.style.display = 'block';
    searchResult.style.display = 'none';
  }
});
```
#### 肺炎搜索结果动态显示
我们知道搜索结果不会是页面写死的，实际情况下这些数据都会实时变换的，这部分是由JavaScript发起网络请求返回的数据，然后利用动态生成节点的方法插入页面。
暂时还未学习网络请求，暂时先模拟在JavaScript代码中：
```js
let data = [
  '<em>肺炎</em>实时疫情动态',
  '<em>肺炎</em>的症状有哪些症状',
  '<em>肺炎</em>武汉',
  '<em>肺炎</em>症状',
  '<em>肺炎</em>最新',
  '<em>肺炎</em>是怎么引起的',
  '<em>肺炎</em>最新消息',
  '<em>肺炎</em>实时',
  '<em>肺炎</em>症状及表现',
  '<em>肺炎</em>最新情况'
];
```
我们需要利用这份数据生成多个`li`标签内容，模版如下：
```html
<li>
  <i class="search"></i>
  <p><em>肺炎</em>疫情实时动态</p>
  <i class="edit"></i>
</li>
```
封装一个函数，用于生成这个`li`DOM节点，代码如下：
```js
function createSearchItem(txt) {
  const item = document.createElement('li');
  item.innerHTML = `<i class="search"></i><p>${txt}</p><i class="edit"></i>`;
  return item;
}
```
这里使用`innerHTML`和`模版字符串`快速创建`li`内容。
最后需要遍历搜索结果数据数组，依次创建`li`，并插入到页面中，代码如下：
```js
let data = [
  '<em>肺炎</em>实时疫情动态',
  '<em>肺炎</em>的症状有哪些症状',
  '<em>肺炎</em>武汉',
  '<em>肺炎</em>症状',
  '<em>肺炎</em>最新',
  '<em>肺炎</em>是怎么引起的',
  '<em>肺炎</em>最新消息',
  '<em>肺炎</em>实时',
  '<em>肺炎</em>症状及表现',
  '<em>肺炎</em>最新情况'
];

function createSearchItem(txt) {
  const item = document.createElement('li');
  item.innerHTML = `<i class="search"></i><p>${txt}</p><i class="edit"></i>`;
  return item;
}

const input = document.querySelector('input');

const login = document.querySelector('.login');
const searchResult = document.querySelector('.search-result');

// 监听键盘事件
input.addEventListener('keyup', function() {
  // this 是DOM节点，this.value可以获取input内输入的值
  if (this.value === '肺炎') {
    // 先把原始内容清空
    searchResult.innerHTML = '';
    for (let i = 0; i < data.length; i++) {
      searchResult.appendChild(createSearchItem(data[i]));
    }

    login.style.display = 'none';
    searchResult.style.display = 'block';
  } else {
    login.style.display = 'block';
    searchResult.style.display = 'none';
  }
});
```


## DOM事件
### DOM事件
#### DOM绑定事件
之前已经接触到事件了，比如：
```js
// 监听Input输入事件
dom.addEventListener("input", function () {});

// 监听鼠标放置，移动事件
dom.addEventListener("mouseover", function () {});

// etc...
```
可以看到DOM通过`addEventListener(eventName,callback)`绑定`eventName`事件，这是现在官方认定的绑定操作
还有不恰当的写法：
##### 一、事件嵌套到HTML代码中
```html
<div onclick="console.log('xxx')"></div>
```
>这种写法会导致JavaScript代码镶嵌在HTML代码中，导致HTML代码非常大，不利于文件分离。

##### 二、事件方法替换
```js
dom.onclick = function () {};
```
这种写法只能在这个DOM上绑定一个点击事件，下一个设置`onclick`会顶替上面的事件方法。相比较而言`addEventListener()`可以添加多个监听事件。所以推荐使用`addEventListener()`

#### DOM事件
打印DOM事件对象后，DOM事件对象会通过回调函数参数传递给我们，如下：
```js
const h1 = document.querySelector("h1");
h1.addEventListener("click", function (e) {
  console.log(e);
});
```
点击后可以看到结果：
![[Pasted image 20240130142923.png]]
通过结果可以看出，这是一个`MouseEvent`，这个对象有几个关键属性

| 属性 | 解释 |
| ---- | ---- |
| target | 点击事件触发的DOM节点 |
| type | 事件名称 |
| pageX/pageY | 鼠标事件触发的页面坐标 |
[官方文档](https://developer.mozilla.org/zh-CN/docs/Web/Events)可以看更多的常用事件
大概介绍一下：
##### 焦点事件
**focus**：表单组件（Input，Textarea等）获取焦点事件
**blur**：表单组件（Input，Textarea等）失去焦点事件
##### 鼠标事件
**click**：点击事件
**dblclick**：双击事件
**mousedown**：在元素上按下任意鼠标按钮
**mouseleave**：指针移出元素范围外（不冒泡）
**mousemove**：指针在元素内移动时持续触发
**mouseover**：指针移到有时间监听的元素或者它的子元素内
**mouseout**：指针移出元素，或者移到它的子元素上
**mouseup**：在元素上释放任意鼠标按键
##### 键盘事件
**keydown**：键盘按下事件
**keyup**：键盘释放事件
##### 视图事件
**scroll**：文档滚动事件
**resize**：窗口放缩事件
##### 资源
**load**：资源加载成功的事件

### 点击事件
#### UCode案例
在DOM事件中，最常用的是**点击事件**，比如页面跳转，点击页面按钮进行操作等。

![[Pasted image 20240130184114.png]]
底部和右侧的按钮都是可以点击的。
##### 一、静态页面
先完成页面样式的设计
##### 二、Like按钮点击事件
如何实现：
1. 点击按钮后，添加`has-like`class，再次点击（取消Like），删除`has-like`class
2. 点击按钮后，将数字+1，再次点击（取消Like），数字-1
首先给按钮添加点击事件，并利用`hasLike`变量标识是否喜欢：
```js
// 默认是未点击喜欢
let hasLike = false;

const likeBtn = document.querySelector(".like-btn");
likeBtn.addEventListener("click", function () {
  // 点击事件
  hasLike = !hasLike;
  console.log(hasLike);
});
```
##### 三、根据`hasLike`修改页面信息
根据`hasLike`的值，修改页面信息：
```js
// 默认是未点击喜欢
let hasLike = false;

const likeBtn = document.querySelector(".like-btn");
const likeBtnRight = likeBtn.querySelector(".right");
likeBtn.addEventListener("click", function () {
  // 点击事件
  hasLike = !hasLike;
  if (hasLike) {
    likeBtn.classList.add("has-like");
    likeBtnRight.innerHTML = parseInt(likeBtnRight.innerText.trim()) + 1;
  } else {
    likeBtn.classList.remove("has-like");
    likeBtnRight.innerHTML = parseInt(likeBtnRight.innerText.trim()) - 1;
  }
});
```
##### 四、点击三个点显示操作列表
监听三个点的按钮，点击控制`options`区域的显示和隐藏，即`dispaly:block/none;`
代码如下：
```js
let showMore = false;
const moreBtn = document.querySelector(".workspace-item-more .select");
const morePanel = document.querySelector(".workspace-item-more .options");
moreBtn.addEventListener("click", function () {
  showMore = !showMore;

  // 控制morePanel的显示和隐藏
  if (showMore) {
    morePanel.style.display = "block";
  } else {
    morePanel.style.display = "none";
  }
});
```
#### 总结
>监听**DOM事件**，使用**DOM操作**，修改**DOM属性**


### 冒泡、捕获、委托
#### 冒泡、捕获、委托
这节的主题不经常遇到，但是很多场景都会用到这个知识
在上一个案例的基础上想添加一个点击事件，跳转到对应页面，代码如下：
```js
// ......
// 省略前面的代码

const workspace = document.querySelector('.workspace');
workspace.addEventListener('click', function() {
  window.location.href = 'https://www.youkeda.com';
});
```
#### 冒泡
在点击事件后会先厨房`Like`click事件，再次触发`workspace`click事件，这就是**事件冒泡**
看图示：
![[Pasted image 20240130202225.png]]
从上到下整个是和`buttom.like-btn`的DOM树
1. 点击事件触发`button.like-btn`监听事件
2. 冒泡找到其父亲节点，触发父亲节点的监听事件
3. 依次冒泡直到html根元素为止

如何修复上面的冒泡导致效果异常呢？
使用**阻止冒泡-e.stopPropagation();**
改进后的代码如下：
```js
// ......省略
likeBtn.addEventListener('click', function(e) {
  // 点击事件
  e.stopPropagation()

// ......省略
```
#### 捕获
捕获和冒泡是完全相反的，冒泡是从当前元素沿着祖先节点往上冒泡，而捕获是从根HTML节点开始依次移动到当前元素
我们使用`addEventListener`是在冒泡阶段监听事件，如果想在捕获阶段监听事件，需要传递第三个参数为`true`，代码如下：
```js
dom.addEventListener('click', function() {}, true);
```
实际场景中捕获使用的非常少，遇到具体情况再具体分析，了解即可
#### 委托
**委托**其实是**冒泡事件**的一种应用，这个概念依赖于这样一个事实：如果想在**大量子元素中单击任何一个都可以运行一段代码**，可以将事件监听器设置在其**父节点**上，并让子节点上发生的事件冒泡到父节点上，而不是每个子节点单独设置事件监听器
上节作业的代码如下：
```js
const box = document.querySelector('.box');
const imgArr = box.children;

for (let i = 0; i < imgArr.length; i++) {
  imgArr[i].addEventListener('click', function() {
    document.body.style.backgroundImage = `url(${imgArr[i].src})`;
  });
}
```
利用委托可以只监听`box`，代码修改如下：
```js
const box = document.querySelector('.box');
const imgArr = box.children;

for (let i = 0; i < imgArr.length; i++) {
  imgArr[i].addEventListener('click', function() {
    document.body.style.backgroundImage = `url(${imgArr[i].src})`;
  });
}
```
如何获取当前点击图片的地址呢？需要把这个地址赋值给`body.style`
虽然事件监听是在`.box`上，但`MouseEvent`的`target`在`<img />`上，也就是
>target表示真实响应事件的DOM节点

完善后的代码如下：
```js
const box = document.querySelector('.box');

box.addEventListener('click', function(e) {
  // 注意box区域比img大，如果点击在空白间隔区域，那么返回的节点将不会是IMG，需要特殊处理一下
  if (e.target.nodeName === 'IMG') {
    document.body.style.backgroundImage = `url(${e.target.src})`;
  }
});
```
最终效果和之前写法一样，利用父元素统一监听所有儿子节点的监听事件
#### 总结
本次内容更多是一种技巧性，应用性知识，多用即可


### 移动事件
#### 鼠标移动事件
之前我们学习到的鼠标移动事件一共有5个如下：
##### **mousemove**：指针在元素内移动时持续触发
>这个是鼠标移动事件，比较简单

##### **mouseenter**：指针移到有事件监听的元素内
##### **mouseleave**：指针移出元素范围外（不冒泡）
>这个是鼠标进入和离开事件，但是仅仅只作用于当前DOM节点，不会作用于其后代节点

##### **mouseover**：指针移到有事件监听的元素或者它的子元素内
##### **mouseout**：指针移出元素，或者移到它的子元素上
>这个也是鼠标进入和离开事件，但和`enter/leave`不同的是：此事件除了作用于当前DOM节点，也会同时作用于其后代节点

大部分都会使用**mouseover/mouseout**

### 表单元素事件
#### 表单元素事件
##### 焦点事件
获取焦点——**focus**和失去焦点——**blur**
##### 内容值变化
对于表单元素，有两种事件可以可以监听元素内容变化——**input**和**change**
区别：

| 事件 | 介绍 |
| ---- | ---- |
| change | 当用户提交对元素值的更改时触发 |
| input | 只要value值修改就会触发 |


### 滚动事件
#### 场景
页面滚动事件，什么时候需要监听滚动
##### 1.无尽滚动
在网站看到过页面滚动到底端，会加载新内容，再次滚动到底端，又会加载新内容
##### 2.动态效果
在页面滚动时切换新的头部

#### 事件描述
滚动事件名称为——**scroll** 
通过以下代码：
```js
window.addEventListener('scroll', function () {
  console.log(window.scrollY);
});
```
打印出来的数字就是`scrollY`（Y轴滚动距离）

#### 无尽滚动
当页面快滚动到底部时添加新的文章内容到`body`中
代码如下：
```js
window.addEventListener('scroll', function () {
  // 可以通过clientHeight获取内容高度
  const height = document.body.clientHeight;

  // 通过screen.height获取浏览器的高度
  const screenHeight = window.screen.height;

  // 当距离底部的距离小于500时，触发页面新增内容
  if (height - window.scrollY - screenHeight < 500) {
    console.log('加载新文章内容');
    // 在底部添加10张图片
    const div = document.createElement('div');
    let str = '';
    for (let i = 0; i < 10; i++) {
      str += `
       <img
        class="first"
        alt=""
        src="https://document.youkeda.com/P3-1-HTML-CSS/1.8/1.jpg?x-oss-process=image/resize,h_300"
      />
      `;
    }
    div.innerHTML = str;
    document.body.appendChild(div);
  }
});
```
上面代码主要用到的技术
1. 内容高度`document.body.clientHeight`
2. 浏览器高度`window.screen.height`
3. 滚动距离`window.scrollY`
4. 滚动距离底部距离`内容高度-浏览器高度-滚动距离`

## 网络请求
### 协议
#### 什么是协议
协议，就是网络协议的简称，网络协议是通信计算机双方必须共同遵从的一组约定。如怎样建立连接，怎样互相识别等。只要遵守这个约定，计算机之间才能相互通信交流。
#### HTTP/HTTPS协议
目前网站主要有两种协议，HTTP和HTTPS
感兴趣可以看[文档](https://ham.youkeda.com/articles/detail/5f3756865e205f30b2c2b0f5)
### URL
URL就是我们常说的网址
其全称是`Uniform Resource Locator`(统一资源定位符)
`URL`的格式规范规定了由哪几部分组成，以及各种符号的作用
![[Pasted image 20240201221636.png]]
说明：
* 协议类型和域名之间以`://`（固定写法）分隔
* 路径（英文常称为`path`）以单斜杠`/`开头，中间每层的分隔符也是单斜杠`/`
  * 路径相当于一层一层的文件夹，但是不要和windows的文件夹分隔符`\`搞混淆了
* 参数：
  * 路径与参数之间用`?`分隔，看到`?`就知道后面的内容就是参数了
  * 多个参数之间用`&`分隔
  * 参数用“参数名=参数值”（`key=value`)的格式表示。
>这些规则很多但不需要刻意背

#### 扩展知识点
##### 端口号
可能会看到这样的URL：
https://www.douban.com:443/gallery/topic/116390/?from=hot_topic_note&sort=new
域名后的`:443`表示网站的端口号。`HTTP`协议默认的端口号是`80`，`HTTPS`协议默认的端口号是`443`，默认的端口号是可以省略的，其它的端口号就必须要写明。

##### 路径的两种情况
###### 1. 相对路径
在开发过程中可能会看到这样的`URL`
[gallery/topic/116390/?from=hot_topic_note&sort=new]
不是以`/`开头的路径表示相对路径，但是具体相对什么就很复杂了，要根据具体情况，所以这种相对路径非常容易出错
###### 2. 默认路径
实际上在没有输入路径时，表示请求网站的默认页面，服务器就会返回一个**默认**页面给浏览器，通常服务器**默认**的页面是首页。

### API+GET请求
#### 什么是API
API全称Application programming Interface，应用程序接口，API一般是指一些预先定义的函数，目的是可以为开发人员快速访问某一程序，而无需了解和访问源码，或理解它内部工作机制的细节
简单的说，**API可以快速调用某个程序**
更多相关知识可以看这个[文档](https://ham.youkeda.com/articles/detail/5f3756bd5e205f30b2c2b125)

#### fetch调用API
所谓`API`，本质上就是一个`URL`，开头也是`http`（或`https`），知识返回的内容有明显的区别，没有大量多余的字符
`API`返回的内容统称为`数据`，使用`javascript`获取这部分数据可以用**fetch**方法。
代码如下：
```js
fetch(
  'https://www.fastmock.site/mock/b73a1b9229212a9a3749e046b1e70285/f4/f4-11-1-1'
)
  .then(function (response) {
    return response.json();
  })
  .then(function (myJson) {
    console.log(myJson);
  });
```
这里有新的语法：`.then`，为了弄清楚这个，我们先知道`fetch()`返回结果是一个`promise`对象
#### Promise
**Promise**是**异步编程**的一种解决方案，之前异步编程是通过回调方法实现的，看看在`fetch`之前是怎么完成网络调用的：
```js
let oReq = new XMLHttpRequest();
oReq.addEventListener('load', function () {
  console.log(this.responseText);
});
oReq.open(
  'GET',
  'https://www.fastmock.site/mock/b73a1b9229212a9a3749e046b1e70285/f4/f4-11-1-1'
);
oReq.send();
```
这是老版的`ajax`调用，以后几乎用不到这种方法
这种方法需要写一大段代码，然后通过`addEventListener`监听`load`事件，然后再触发`function`回调函数，如果在这个函数继续加入`setTimeout`或者`addEventListener`监听代码，那么就会出现多层嵌套，专业叫做**回调地狱**。
而`Promise`对象可以通过`.then`触发回调函数，`then`中文意思**下一步**，也非常符合人的语义化习惯。
在上面`response.json()`返回的也是一个`Promise`对象，所有后续可以继续使用`.then`触发后续回调。
>把**嵌套型**的回调调整为**平铺型**的回调，就完美的解决了回调地狱问题
#### GET请求
像上面这种请求数据的接口，一般称为`GET接口`，而`fetch`在不指定类型时，默认是发起`GET请求`。
在实际情况中，服务端开发同学在给出API接口时，会告诉你这个API是一个`GET`还是`POST`类型
#### GET参数请求
在上面练习了如何在程序中调用`GET类型API`获取结果，很多情况下，`API`调用需要参数
只要把包含参数的完整`URL`直接传入到方法中就可以了。


### POST请求
提交数据至服务器进行增加、修改、删除等操作，都是`POST`擦欧洲哦，在网页上提交表单进行登录的场景就是`POST`操作
#### fetch-POST操作
`fetch`默认是发起`GET`请求，如果要发起`POST`请求，需要加一个参数**method**就行了，代码如下：
```js
fetch(
  'https://www.fastmock.site/mock/b73a1b9229212a9a3749e046b1e70285/f4/f4-11-4-1',
  {
    method: 'POST'
  }
)
  .then(function(response) {
    return response.json();
  })
  .then(function(myJson) {
    console.log(myJson);
  });
```
此时的登录会显示失败，因为没有提供账号密码。我们可以通过`body`属性完成`POST`请求的传参。注意，在利用body传递`json`格式数据时，需要在`headers`里面加入`contentType信息`
完善代码如下：
```js
// 把JSON数据序列化成字符串
const data = JSON.stringify({
  username: 'admin',
  password: '123456'
});

fetch(
  'https://www.fastmock.site/mock/b73a1b9229212a9a3749e046b1e70285/f4/f4-11-4-1',
  {
    method: 'POST',
    body: data,
    headers: {
      'content-type': 'application/json'
    }
  }
)
  .then(function(response) {
    return response.json();
  })
  .then(function(myJson) {
    console.log(myJson);
  });
```

### Chrome Network
#### Chrome Network
这次学习怎么使用Chrome开发者工具来查看网络请求
这次学习的面板是`Network`
#### 查看GET请求
1. 选择**检查**
2. 在Chrome开发者工具中选择**Network**面板
3. 再次刷新页面

从`Headers`可以得到几个信息

| 属性 | 描述 |
| ---- | ---- |
| Request URL | 请求地址 |
| Request Method | 请求类型 |
| Status Code | 请求状态码 |

切换到`Preview`可以看到返回值的情况，通过这样的方式可以完整的观察网络请求情况
#### 查看POST请求
和查看GET请求方法类似

在实际开发中，利用好这些工具是**提高开发效率和排查问题**的最有效的手段
