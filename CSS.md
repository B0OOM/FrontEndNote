[[Web前端基础]]
# 什么是CSS
css，即层叠样式表（Cascading Style Sheets），又称串样式列表、级联样式表、串接样式表、阶层式样式表），是一种用来为结构化文档（如HTML文档或XML应用）添加样式（字体、间距和颜色等）的计算机语言，**它的主要职能就是确定布局和元素的表现**。
**CSS不能单独使用**，必须与HTMl或XML一起协同工作，为HTML或XML起装饰作用，其中HTML负责确定网页中有哪些内容，CSS确定以何种外观（大小、粗细、颜色、对其和位置）展现这些元素。CSS可以用于设定页面布局、设定页面元素样式、设定适用于所有网页的全局样式
CSS的作用——**改变HTML元素的样式**。HTML包括结构和内容的信息，CSS文件只包含样式的信息，这样既可以简化HTML文件，又使CSS更易维护


## CSS-美化文档
### HTML内部添加样式的方式
#### 标签中添加声明
	声明的关键字是`style`，如
```html
<input type="text" placeholder="手机号码" style="">
```
* 声明位置不分先后
* 与其它关键字之间用空格隔开
#### 在引号之间添加样式

### 字体大小/字体粗细
在CSS中，样式是由属性和值组成，中间用冒号(`:`)隔开，用(`;`)收尾。就是这样一对组合来描述文字的粗细、大小、颜色等等。
#### 字体大小
设置格式为：`font-size:36px;`
> 当属性为最后一组时可能会把结尾的分号`;`省略，这是允许的，但==不规范==

#### 字体加粗
设置格式为：`font-weight:100;`
>设置文字粗细的时候可以是如：100,200,300等这样的数字，也可以是英文：normal(正常粗细)、lighter(细)、bold(粗)、bolder(更粗)



### 字体颜色/文字对齐方式
#### 颜色
颜色的值的设置方式分为四种：
1. **英文字母形式**：`color:black;` `color:blue;` 
2. **十六进制颜色**：由#开头，后面跟三个数字，每个数字的范围为00~FF，每个数字代表一种颜色，最终颜色由这三种颜色调和而成 `color:#DAE8FC;`
3. **rgb形式**：和十六进制的原理相同，每种颜色的范围为0~225 `color:rgb(253,217,106);`
4. **rgba形式**：比rgb形式多了一个a，这里的a代表的是Alpha（透明度），a的值在0~1之间，也可以直接省略0写成`.4` `color:rgba(253,217,106,.3);`
>多数情况下建议使用十六进制表达方式
>调试的时候可以用英文字母形式，初期的调试就是随便设置一个颜色，查看区块是否存在，区块大小等，在盒模型中会遇到
>如果要设置文字透明度或者背景透明度需要用到rgba形式，后面会遇到

#### 文字居中/居左/居右
格式分别如下
* `text-align:center;`文字居中对齐
* `text-align:left;`文字左对齐
* `text-align:right;`文字右对齐
### 文字行高/字间距/字体
#### 行高
行高是去除了文字大小的尺寸后将剩下的分为两部分分别填充在文字上下
设置格式：`line-height:30px;`
行高的作用主要有两个：
第一个作用：改变段落中行与行之间的距离
第二个作用：使文字上下居中
>将文字外面的图形高度和文字行高设置相同就可以让文字在图形中上下居中

#### 字间距
文字之间的间距，但是中文和英文的字间距不一样
* 英文的字间距是每个字母之间的距离，单词和单词之间的距离不属于字间距
* 中文是每个汉字之间的距离
设置格式：`letter-spacing:30px;`

#### 字体
设置字体的方式很简单，关键字+值即可
设置格式：`font-family:sans-serif;`
设置的字体能否被应用在页面上取决于使用者的电脑有没有安装这个字体，如果想多设置几个字体可以这样写：
```css
font-family: 'Goudy Bookletter 1911', sans-serif, 'Gill Sans Extrabold';
```
页面加载后会先去找代码中设置的字体，先看”Goudy Bookletter 1911“字体有没有在电脑上安装，如果没有安装就去看第二个字体，如果还没有就去看第三个。如果都没有只能使用默认的微软字体
字体写法的注意事项：
>多个字体之间用英文逗号(`,`)隔开
>字体名称中间有空格时要加引号，单引号双引号都行
>中文字体名称要用引号，单引号双引号都行


## CSS-引入方式
### CSS的三种引入方式
#### 行内样式
![[Pasted image 20231208163303.png]]
行内样式需要内嵌在每一个`HTML`标签中，这种书写方式非常繁琐，所以需要把每一个标签中的`CSS`样式抽取出来，成一整段放在`HTML`文件中的某个位置，这就是第二种引入方式——**内部样式**
#### 内部样式
![[Pasted image 20231208163603.png]]
抽离步骤：
1. 首先把每一个标签里的`CSS`样式抽取出来
2. 然后在`head`标签里声明一个`<style></style>`标签
3. 然后把样式都放在`style`标签里
   ![[Pasted image 20231208163729.png]]
4. 讲相同标签样式鞋子相同的大括号，大括号前面加上标签名，如
   ```css
p {
  font-size: 16px;
  color: #ffffff;
}
```
书写规则：
* 不要忘记写声明标签`<style></style>`
* 样式要用花括号括起来
* 每个样式后面要用分号结尾
此时就完成了`CSS`样式从每一个标签到头部(`head`)的搬迁工作

#### 外部样式
代码量增多后，整个`HTML`文件会呈现出头重脚轻的现象，即`CSS`代码要比`HTML`代码多的多，这样不利于阅读和复查代码，更重要的是为了实现代码的分离，让`HTML`负责结构，`CSS`负责样式，所以要对代码进行进一步的分离
![[Pasted image 20231208164242.png]]
步骤如下：
1. 新建一个`index.css`文件
2. 将html代码头部中的`style`标签的样式全部拷贝过来
3. 将复制的`CSS`样式粘贴进index.css文件中；
4. 建立`HTML`和`CSS`文件的联系，即用`link`标签引入`CSS`文件
   >注意这里的link标签引入的位置一定要在head标签内
   
##### link
link标签里有一些属性：
1. `rel`属性规定了当前文档与被链接文档之间的关系，但是`rel`属性的`stylesheet`值（意思是文档的外部样式表）被所有浏览器支持，只需要记住一个值即可
2. `type`属性规定了被链接文档的MIME（多用途互联网邮箱扩展类型）类型，`type`属性对应的最常见的值就是`text/css`，该类型描述样式表
3. `href`属性后跟的是要引入的链接地址

#### 相对路径/绝对路径
##### 绝对路径
绝对路径指的是文件在硬盘上真正存在的路径。这种路径看起来很好理解，但是在使用起来会有很多问题，在更换设备以后往往计算机不能根据给的路径找到要引入的文件，所以要尽量避免使用绝对路径

##### 相对路径
为了避免绝对路径造成页面资源丢失的现象，在引入外部资源的时候，都会选择使用相对路径
**所谓相对路径就是相对于文件自身位置，去寻找要引入的资源文件**
`./`：指当前文件夹目录，如果要引入同一文件夹的内容就要用到`./`
`../`:回到上一级文件夹目录。
用相对路径引入需要记住以下三点：
1. 找到引用资源的文件所在位置，以引用资源的文件为基准，寻找资源
2. `../`返回一层，如果有多层，就用多个`../`比如返回两层就用`../../`
3. 文件夹名代表进入该文件夹，如css/，表示进入css文件夹，从test文件夹里出来进入css文件夹找到index.css文件，可以这样写`../css/index.css`


### 常用选择器
#### 标签选择器
使用标签的名字将标签选中，然后给标签中的文字设置字体样式
![[Pasted image 20231208171540.png]]
可以通过选中所有叫`p`的标签，然后统一给所有的`p`标签设置样式
以后还能接触到很多其他的选择器，选择器的作用就是选中，只有选中以后，才能去对应的做出修改，选择器的一个好处——**减少代码量**

#### 类选择性
前面的标签选择器中我们将很多重复的模块批量化的设置了它们的样式，但是在实际应用中，仅仅一个标签选择器还不足以满足我们日常的开发需求
定义：
```html
<p class="article">
  class是定义类的关键字，article是类名，类名可以任意，但是要符合规范
</p>
```
使用：
```css
.article {
  color: red;
  font-size: 14px;
}
```
如果是内部样式，上面的代码要写在`<style></style>`标签之间，如果是外部样式，直接写在`.css`文件中即可
类选择器的作用就是在普通中寻找特别
一个标签上可以添加多个类名，类名之间要用空格隔开
标签内类名的顺序不会影响最终结果，但是`<style></style>`标签中的类名先后顺序会影响最终结果

#### id选择器
id选择器与类选择器非常相似
在标签中定义id：
```html
<p id="p-item">这是一段文字</p>
```
使用id选择器
```css
#p-item {
  font-size: 24px;
  font-weight: 400;
}
```
除了定义和使用的规范不同之外，基本没有什么变化，不同的地方是：
1. id选择器在文档中只会出现一次，像下面这种使用方式是不对的
   ```html
<a href="#" id="link">点击进入详情</a>
<!-- link这个id名已经被使用，就不可以再次定义 -->
<a href="#" id="link">点击进入主页</a>
```
id就像身份证号码一样，全国只能一个，同样，id选择器也是如此，link重复了
2. 不能像类选择器一样，一个标签上定义多个id名，像下面这种写法是错误的
   ```html
<a href="#" id="link linkto">点击进入详情页</a>
```
id选择器在写页面的时候用的不是很广泛

##### 选择器的层叠性
在写`CSS`样式的时候，有时候因为粗心会把之前写过的标签又重新写一次，然后给{}里面添加样式，这样可能会有两种结果：
1. 添加新的效果（如果添加的是一个新属性）
2. 改变之前已经存在的效果（如果该属性之前就存在）
>选择器的层叠性，在后面的类选择器和id选择器同样适用


### 高级选择器
常用的高级选择器有四种：
* 后代选择器
* 交集选择器
* 子选择器
* 并集选择器
#### 后代选择器（空格）
`P a`----选择所有p标签内的所有a标签
后代选择器的书写规则：用空格隔开，例如
```css
/* 选择id名为password的标签内部所有类名为box的元素内部的所有p标签 */
#password .box p{}
/* 选择所有p标签内部的所有span标签 */
p span{}
/* 选择所有p标签内部的所有类名为spanItem的标签 */
p .spanItem{}
```
>这里体现了一种编程思想，就是抽离，将`li`标签公有的属性抽离在`ul li`选择器内，因为这个选择器选中的是所有的`li`，然后再分别用`.first-ul li`和`.second-ul li`选择器来设置不同的属性

##### 重点理解后代
在`HTML`中，随着页面复杂程度的增加，会出现很多标签嵌套的现象，比如：
```html
<ul>父
    <li>子
        <p>孙
            <span>曾孙
                <a href="">曾曾孙</a>
            </span>
        </p>
    </li>
</ul>
```
这段代码中，标签和标签当中就形成了子代关系，a、span、p、li就是ul标签的后代，以上述代码为例，要想选中a标签，可以有很多办法：
```css
/* 方法一： */
a{}
/* 方法二 */
ul a{}
/* 方法三 */
ul li p a{}
/* 方法四 */
ul li p span a{}
```
方法的选择还需要根据关系的不同进行选择
```html
<ul>父
    <li>子
        <p class="p-one">孙
            <span>曾孙
                <a href="">曾曾孙1</a>
            </span>
        </p>
        <p class="p-two">孙
            <span>曾孙
                <a href="">曾曾孙2</a>
            </span>
        </p>
    </li>
</ul>
```
```css
/* 方法一 */
ul li .p-one span a{}
/* 方法二 */
.p-one span a{}
```


#### 交集选择器
书写规则是：
```css
a.special{}
```
```html
<a href="#" class="special">超链接</a>
<a href="#">超链接</a>
<a href="#">超链接</a>
<a href="#">超链接</a>
```
它的意思是在所有a标签内，类名为`special`的标签
#### 子选择器
子选择器与后代选择器类似，不同的是后代选择器突出的是“后代”，子选择器突出的是“子”。比如同样的`HTML`代码，用不同的选择器，得到的结果就是不同的
使用`>`来选中下一级元素

#### 并集选择器
要给不同的标签或者不同的类名添加相同的样式，就要用到并集选择器
书写规则是在标签名或者类名后面用逗号(`,`)隔开
并集选择器的作用是“和”，为一系列类或标签添加相同的属性

### 选择器的优先级
#### 单个选择器的优先级
**id选择器>类选择器>标签选择器**
在优先级相同的情况下，上下位置的不同才会导致属性被层叠
#### 文字属性的继承性
除了`h`标签，其他标签写了文字后默认会有相同的颜色、大小，这就是文字属性的继承性导致的，都继承了`body`标签的字体大小、颜色、字间距等
#### 高级选择器的优先级
##### 权重的计算方法
单个选择器的优先级可以通过**id选择器>类选择器>标签选择器**的顺序判断，多个选择器的优先级需要用到选择器权重的叠加性，优先级越高权重越大
##### 权重的作用
权重的作用就是决定当两个不同的选择器给同一个标签设置了相同的属性时，选择哪一个选择器

### CSS注释
在CSS代码中注释方式跟HTML中不同，格式为`/* CSS注释内容 */`


## CSS-盒模型
### 盒模型-content
在网页布局中，页面就是由一个个大小不一的小块构成，比如淘宝的商品缩略图
先了解一个新的标签——`div`标签
`div`就是一个干净透彻的矩形
由四部分组成：
* 内容区`content`
* 内边距`padding`
* 边框`border`
* 外边距`margin`
>注意顺序，由内到外
>>如果由外到内讲，就是外边距、边框、内边框、内容区>

`div`是一个矩形，实际上 内边距、边框、外边框又由**上、下、左、右**四条边组成，把`div`拆分的这么细，就意味着四条边既可以统一设置样式，也可以分开设置样式。
>内容区是最中心的完整区域，没有四边的概念，也就是说内容区的四条边的样式由内边距、边框、外边距的样式决定

div矩形的四个组成部分，就是所谓的“盒模型”
#### 内容区：content
`div`标签写出来的时候是没有高度的，但是有宽度，宽度默认和父标签的宽度是一样的
>这里所说的宽度不是肉眼看到的宽度，而是width属性设置的宽度

##### width/height
要画一个矩形，首先要设置矩形的宽高，矩形的宽高对应两个CSS属性`width`,`height`，他们的值是数字，单位是`px`
核心代码如下
```html
<div class="box"></div>
```
```css
.box {
  width: 200px;
  height: 100px;
}
```

但仅仅这样写，我们在页面上是看不到这个矩形的，因为我们还没有给它着色，而 div 默认是不填充颜色的。

要给矩形添加背景颜色，需要学习一个新的 CSS 属性，`background-color`——背景颜色，这个属性的值和设置字体颜色一样，有十六进制，`rgb`，`rgba`，英文单词形式的颜色

##### 百分百尺寸
设置块元素的宽高除了`px`形式，还有`%`形式。比如说：
```html
<div class="father">
  <div class="son"></div>
</div>
```
```css
.father {
  width: 200px;
  height: 80px;
  background-color: #5b6dcd;
}
.son {
  width: 60%;
  height: 20%;
  background-color: #fec03e;
}
```
>这里的`%`是相对于父元素的，也就是说子元素的宽度是父元素的`60%`……

#### 内边距：padding
就是这个绿色的框
![[Pasted image 20231209103338.png]]
>`padding`区域是包含在背景颜色区域内的，也就是说背景颜色包含了`padding`和`content`

##### padding分开写
padding默认是给矩形四周添加相同的内边距，但是在实际应用中会有四周内边距不同的情况，所以要分别给矩形设置内边距，没有设置的内边距默认为0
代码如下：
```css
.box {
    padding: 20px;
}
```
这个代码等价于
```css
.box {
    padding-top: 20px; /*上内边距*/
    padding-right: 20px; /*右内边距*/
    padding-bottom: 20px; /*下内边距*/
    padding-left: 20px; /*左内边距*/
}
```
##### padding简写
`padding`分别`top`、`right`、`bottom`、`left`这四个方向区设置
上述代码最初形式是这样
```css
div{
    padding:20px 20px 20px 20px;
}
```
###### 上下一样，左右一样
上下一样写一个即可，左右一样写一个即可（顺序不可变）最后变成：
```css
div{
    padding: 20px 30px;
}
```
>第一个是上，第二个值是右，第三个值如果没有就和第一个值保持一致，第四个值如果没有就和第二个值保持一致

###### 上下一样，左右不一样
使用简写要这样写
```css
div{
    padding: 20px 30px 20px 10px;
}
```

###### 上下不一样，左右一样
使用简写要这样写
```css
div{
    padding: 30px 10px 20px;
}
```
总结就是按照上、右、下、左的顺序去写，如果没有值就和对立面的值一样
##### box-sizing
`box-sizing`规定了如果计算一个元素的总宽度和高度，它有两个值`content-box`,`border-box`，默认是`content-box`
`content-box`尺寸计算公式：
```txt
width = 内容的宽度
height = 内容的高度
```
`border-box`尺寸计算公式
```txt
width = border + padding + 内容的宽度
height = border + padding + 内容的高度
```
>也就是说，`box-sizing`规定了两种计算部分，每个值代表一种计算部分，工程师**不能**任意写计算公式

`border-box`的`width`包含了`content`、`padding`、`border`，所以设置以后不会溢出父元素的`content`
#### 边框：border
边框就是包裹在`padding`外面的一层线
##### 给矩形设置边框线
设置边框线的语法是： 
```css
.box {
  /* 设置矩形大小 */
  width: 200px;
  height: 30px;
  /* 设置边框线 */
  border-width: 2px;
  border-color: grey;
  border-style: solid;
}
```
* `border-width`：边框的粗细，单位是px
* `border-color`：边框的颜色，和之前的方法一样
* `border-style`：边框的线型：`solid`是实线，`dashed`是虚线（最常用的就是这两种）
##### 边框的简写
可以只用一行代码就实现三行代码的效果
```css
.box {
  border: 2px solid blue;
}
```
> `border`后面跟的三个值之间要用空格隔开，值的顺序可以忽略

##### 分别设置边框
可以分别给`border`上下左右设置不同的值
首先是一种繁琐的不推荐的方法
```css
.box {
  /*设置顶部border*/
  border-top-color: blue;
  border-top-style: solid;
  border-top-width: 2px;
  /*那么接下来，left，right，bottom是类似的，这里忽略不写*/
}
```
推荐的书写方式如下
```css
.box {
  /* 添加顶部border */
  border-top: 1px solid black;
  /*添加右侧border*/
  border-right: 3px solid orange;
  /*添加底部border*/
  border-bottom: 5px dashed pink;
  /*添加左侧border*/
  border-left: 10px dashed purple;
}
```
##### 利用层叠性设置边框
如果边框的左右上的边框样式相同，只有下边框的样式是不一样的，就需要用属性的层叠性来实现
```css
.box {
  /*设置矩形的宽*/
  width: 300px;
  /*设置矩形的高*/
  height: 300px;
  /*设置矩形的背景颜色*/
  background-color: white;
  /*设置矩形的边框*/
  /*统一设置矩形的所有边框样式*/
  border: 2px solid black;
  /*重新设置一个下边框的样式来层叠掉统一设置的边框的样式*/
  border-bottom: 5px solid orange;
}
```
这样可以减少代码的书写量

##### 无边框
如果想要某个边框不显示，可以这么写
```css
.box {
  border-bottom: none;
}
```

##### 圆角
很多情况下，矩形都不是四四方方的，需要一点圆角来点缀，圆角属性是归类于边框的，即`border-radius`
###### 圆角的统一设置
```css
.box {
  border-radius: 12px;
}
```
如果此时不设置矩形的宽、高、背景色或者边框颜色，圆角是看不出来的，但是**看不到并不代表不存在**

###### 圆角分开设置
圆角属性也是可以拆开来设置的，他没有上下左右，而是左上角，右上角，右下角，左下角
```css
.box {
  width: 200px;
  height: 200px;
  background-color: violet;
  border-top-left-radius: 5px;
  border-top-right-radius: 10px;
  border-bottom-left-radius: 20px;
  border-bottom-right-radius: 15px;
}
```
##### 阴影
```html
<div class="box"></div>
```
```css
.box {
  width: 200px;
  height: 200px;
  border: 1px solid #c4c4c4;
  /* x偏移量 | y偏移量 | 阴影模糊半径 | 阴影扩散半径 | 阴影颜色 */
  box-shadow: 2px 2px 2px 1px rgba(0, 0, 0, 0.2);
  border-radius: 15px;
}
```
阴影的实现原理可以看作是在矩形下面有一个重叠的，同样大小的矩形，如果在x轴，y轴上移动，就会有阴影效果
* x偏移量：在x轴上移动，向右为正
* y偏移量：在y轴上移动，向下为正
* 阴影模糊半径：边线的清晰度
* 阴影扩散半径：向外伸展
* 阴影颜色：矩形下面那个矩形的背景色



#### 外边距：margin
外边距就是矩形和矩形之间的距离
```css
.box{
    /*总写*/
    margin: 20px;
    /*分开写*/
    margin-top: 20px;
    margin-right: 20px;
    margin-bottom: 20px;
    margin-left: 20px;
}
```
其实`margin`的设置方式和`padding`是一样的
##### 两个盒子之间的margin的计算
###### 水平距离
![[Pasted image 20231209115954.png]]
第一个盒子的右margin为30px第二个盒子的左margin为20px，最后两个盒子之间的水平距离就是50px，如果第二个盒子没有设置margin-lift，那么就会默认为第二个盒子的margin-left为0px
###### 垂直距离
垂直距离会取两个盒子margin的最大值，所以垂直距离的设置一般会选择其中的一个区设置

###### 盒子左右居中
margin还有一个作用就是使盒子左右居中，但是有一个前提，就是必须有宽度
```html
<div class="father"> 
    <div class="son"></div>
</div>
```
```css
.father{
    width:400px;
    height:200px;
    border: 1px solid #ccc;
}

.son{
    width:200px;
    height:100px;
    margin:0 auto;
    border: 1px solid #ccc;
}
```
#### display：block/none
##### display：block
###### 块元素性质一 独占一行
在学`HTML`的标签时，应该对块、行内这种词汇有所了解
块元素的性质就是独占一行，其它的标签元素不能跟它在同一行显示
如图![[Pasted image 20231209121902.png]]
###### 块元素性质二 可以设置宽高
给块元素设置宽高会有效果，而给行内元素设置就不行

###### 行内元素和块元素之间的转换
标签是行内元素还是块元素，根本原因是标签自带的默认`display`属性
* 块元素默认的`display`属性的值是`block`
* 行内元素默认的`display`属性的值是`inline`

只要设置行内元素和块元素的`display`属性的值就可以实现行内元素和块元素之间的转换
##### display：none
`none`就是无的意思，如果给标签设置了这个属性值，标签就会消失，在网页布局中最常用的就是用`none`、`block`来控制元素的显示和隐藏

#### display：inline/inline-block
##### inline
1. 行内元素不能设置宽、高
2. 行内元素可以设置`padding`
   >虽然这样做可以给人块元素的感觉，但是还是有区别的，尽量不要用这种方式区设置一个规定大小的块
3. 行内元素可以设置左右`margin`，但是不能设置上下`margin`

##### inline-block
`inline-block`既有`block`的性质，还具有`inline`的性质，可以理解为`inline-block`就是一个可以在同一行显示的块元素
`inline-block`要比`block`在应用中更为广泛
###### 空白折叠现象
按照常理将`div`的`display`属性从`block`切换成`inline-block`之后我们希望得到
![[Pasted image 20231209124314.png]]
但得到的结果是这样的
![[Pasted image 20231209124334.png]]
我们并没有设置`margin`，盒子中间还是多了一点空白，这就是传说中的空白折叠现象。原因是因为两个div之间多了一行回车，在`html`中，回车被当作是一个文字，所以这里的空白就是文字的空白，相当于在两个`div`之间加了一个字母
解决这个空白的三种办法：
1. 去除回车（将div标签写在一行）
2. 给父元素添加`word-spacing`属性
   `word-spacing`就是单词和单词之间的距离，这里将这个距离写成负值就可以了，这个值要尽量小，一般写小于-20px的值，具体如下
   ```html
<div class="father">
  <div class="box1"></div>
  <div class="box2"></div>
</div>
```
```css
.father {
  word-spacing: -50px;
}

.box1 {
  width: 200px;
  height: 50px;
  display: inline-block;
  background-color: #fff2cc;
}

.box2 {
  width: 200px;
  height: 50px;
  display: inline-block;
  background-color: #b0e3e6;
}
```
3. 给父元素设置 font-size:0px;
   将文字大小设置为0空隙自然就会消失，具体如下
   ```html
<div class="father">
  <div class="box1"></div>
  <div class="box2"></div>
</div>
```
```css
.father {
  font-size: 0px;
}

.box1 {
  width: 200px;
  height: 50px;
  display: inline-block;
  background-color: #fff2cc;
}

.box2 {
  width: 200px;
  height: 50px;
  display: inline-block;
  background-color: #b0e3e6;
}
```



## CSS-定位
### Position-static（默认定位）
CSS中一个非常关键的属性`position`，这个属性在CSS用于定位DOM元素，修改DOM元素的布局
浏览器会自动给所有的DOM元素添加`position:static`
>static遵循默认的文档流布局，top、left、right、bottom属性都无效

**position**除了static属性值以外，还有四个常用值，分别是：
* relative（相对定位）
* absolute（绝对定位）
* fixed（固定定位）
* sticky（粘性定位)

### Position-relative(相对定位)
如果想在当前位置进行偏移，同时不影响整体页面布局，可以使用`relative`，CSS如下
```css
.first {
  position: relative;
  left: 50px;
  top: 50px;
}
```
>left：50px；表示距离自己原来的位置左侧50px
>top：50px；表示距离自己原来的位置顶部50px

>这里的left、right、top、bottom的调账都是相对于当前元素的调整，所以称为**相对定位**


### Position-absolute（绝对定位）
绝对定位不为元素预留空间，通过指定元素**相对于最近的非static定位祖先元素的偏移**，来确定元素位置
这里有三个关键词**最近**、**非static定位**和**祖先元素**。
分析一下浏览器是怎么布局absolute元素的
1. 首先获取到第一张图片元素，发现它是**absolute**布局
2. 寻找它的父亲节点，发现此元素并未配置**position**属性，遵循默认布局**position=static**，并不符合**非static**要求
3. 继续寻找父亲节点的父亲节点
4. 发现他已经没有父亲节点了，所以按照他的位置为标准进行偏移
>absolute（绝对定位）和relative（相对定位）的区别：
>relative是相对自己进行top、left、right、bottom进行偏移
>absolute是寻找最近的非static的祖先节点进行偏移


### Position-fixed（固定定位）
文章的标题会一直停留在浏览器的顶部，不会随着页面的滚动而消失，这就是`fixed`的功能——**固定**
>固定定位和绝对定位类似，但元素的包含块为屏幕视口(viewport)
>固定定位不为元素预留空间，而是通过指定元素相对于屏幕视口的位置来指定元素位置，元素的位置在屏幕滚动时不会改变

#### z-index
HTML页面是由多个图层构成的，浏览器怎么决定不同图层的优先级呢？这就是`z-index`决定的
1. 默认非static元素的z-index都为0
2. z-index越大则越在最上面，离观察者越近
3. 同样的z-index，在HTML中的元素越靠后，则越在最上面，离观察者越近

### Position-sticky(粘性布局)
会在滚动到顶部时黏在顶部，向下滚动时又恢复其在文档中的位置
### Float（浮动）
**Float**是CSS中最常用的布局属性，使用他可以让元素靠左或者靠右排版，它的使用非常简单，但是使用后引起的行为是千变万化，可能会引起祖先，兄弟，后代元素布局的变化，可能会产生奇奇怪怪问题。
这里有两个新标签`nav``main`，这两个标签都是`HTML5`标签，相比较div，它们是有含义的，可以更明确的传达区块的含义
>nav：一般用于表示此区块是导航区域
>main：一般用户表示此区块是网页的主体区域

float的两个最基本的属性：
* left
* right
即向左浮动和向右浮动
### 实战
#### 模态框
特点：
1. 模态框总是在浏览器的中心，浏览器随意的放大缩小，模态框还是在浏览器中心
2. 模态框总有一个半透明的背景
##### 完成半透明背景
```html
<div class="mask"></div>
```
```css
.mask {
  position: fixed; /*1*/
  left: 0;
  right: 0;
  top: 0;
  bottom: 0;
  background-color: rgba(0, 0, 0, 0.7); /*2*/
}
```
1. 通过fixed上下左右都为0，设置mask是撑满整个屏幕的
2. background-color使用rgba颜色设置方法，最后一位设置颜色透明度
这里就完成了模态框半透明效果
##### 完成模态框内部
```html
 <div class="modal">
    <img src="链接" />
  </div>
```
```css
.modal {
  background-color: #fff;

  /* 设置长宽 */
  width: 300px;
  height: 150px;

  /* 设置圆角20px */
  border-radius: 20px;
}

.modal > img {
  display: block;
  width: 200px;
  margin: 39px auto; /*1*/
}
```
上面标注1处的代码是为了让优课达Logo上下左右居中

**元素水平居中**
1. 如果内部是行内元素，可以在父容器上使用`text-align:center`
2. 如果内部是块状元素，可以在子容器上使用`margin:0 auto`（如果不是块状元素，需要设置`display:block;`）

**元素垂直居中**
后面会使用`flex`实现元素的垂直居中，这里先用`margin`完成垂直居中效果
> margin-top=(modal 高度-img 高度)/2

##### 完成模态框布局
要把整个中间区域显示在浏览器的中间，要设置`position:fixed`
```css
.modal {
  position: fixed; /*1*/
  left: 50%; /*2*/
  top: 50%; /*3*/
  background-color: #fff;

  /* 设置长宽 */
  width: 300px;
  height: 150px;

  /* 设置圆角20px */
  border-radius: 20px;
}

.modal > img {
  display: block;
  width: 200px;
  margin: 39px auto;
}
```
如果这样设计会往右下角偏移部分，所以需要用`margin`进行修正
```css
.modal {
  position: fixed;
  left: 50%;
  top: 50%;

  margin-left: -150px; /*1*/
  margin-top: -75px; /*2*/

  background-color: #fff;

  /*设置长宽*/
  width: 300px;
  height: 150px;

  /*设置圆角20px*/
  border-radius: 20px;
}
```
#### 搜索框
两个部分：
* 搜索框
* 搜索结果列表
* 
### 背景
#### 背景颜色
##### 渐变色
之前的设置的颜色都是纯色，我们学习点高级的技巧，怎么利用`background`这个属性设置渐变色
需要学习`background`的一个新的值——**linear-gradient**
![[Pasted image 20231209233818.png]]
需要设置好**渐变类型、渐变方向、开始颜色、结束颜色**即可实现简单的渐变效果
###### 渐变方向
具体有如下值
* to right / to left  向右/向左渐变
* to top / to bottom  向上/向下渐变
* to right bottom / to right top  向右下/向右上渐变
* to left bottom / to left top  向左下/向左上渐变
* xxxdeg    xxx范围（0到360）更精确的渐变方向

###### 渐变位置
渐变不一定是从开始到结束，可以设置各种中间状态，比如不需要从一开始就进行渐变，而是在30%~70%之间进行渐变
![[Pasted image 20231209234254.png]]
可以在色值后面跟一个值**百分百，PX**，来约定变色起止位置
除了这些还有其他更多的方式，详情请见[相关文档](https://developer.mozilla.org/zh-CN/docs/Web/Guide/CSS/Using_CSS_gradients)

#### 背景图片
CSS除了设置背景颜色，还可以设置背景图片
![[Pasted image 20231210002213.png]]
想实现这样的效果需要以下代码：
```html
<!DOCTYPE html>
<head>
  <meta charset="utf-8" />
  <link rel="stylesheet" type="text/css" href="./index.css" />
  <title>优课达</title>
</head>
<body>
  <div class="box">HELLO WORLD</div>
</body>
```
```css
.box {
  width: 100%;
  height: 250px;
  border: 1px solid #e8e8e8;
  font-size: 30px;
  font-weight: bold;
  color: yellowgreen;
}
```
要给一个元素设置背景图片，需要用到`background-image`标签，加一个`url`包裹的远程或者本地图片地址
1. 当背景图片长宽任意一项小于容器的长宽，背景图片会出现重复。使用`background-repeat:no-repeat;` 禁止图片的重复
   * repeat——这是默认值，将在垂直和水平方向进行重复
   * repeat-x——背景图片只在水平方向重复
   * repeat-y——背景图片只在垂直方向重复
   * no-repeat——背景图片只显示一次，不重复
2. 背景图片不居中，可以使用`background-position:center;`解决

|值|描述|
|---|---|
|- top left<br>- top center<br>- top right<br>- center left<br>- center center<br>- center right<br>- bottom left<br>- bottom center<br>- bottom right|左侧两个元素为一组一起出现，分别代表**垂直**和**水平**布局  <br>  <br>比如：  <br>**background-position: top left**; 效果等于  <br>**background-position-x: left;**  <br>**background-position-y: top;**  <br>如果只写一个关键词，那么另一个关键词默认是**center**|
|x% y%|第一个值是**水平位置**，第二个值是**垂直位置**。  <br>左上角是 0% 0%。右下角是 100% 100%。如果只写一个值，另一个值将是 50%。|
|xpx ypx|第一个值是**水平位置**，第二个值是**垂直位置**。  <br>左上角是 0 0，单位是像素 (0px 0px) 或任何其他的 CSS 单位。如果只写一个值，另一个值将是50%|
3. 将背景图片撑满整个容器，需要认识一个新的属性`background-size`，这个属性可以设置背景图片大小

|值|描述|
|--|-----|
|cover|把背景图片扩展至足够大，以使背景图片完全覆盖背景区域，背景图像的某些部分也许无法显示在背景定位区域中|
|contain|把图像扩展至最大尺寸，以使其宽度和高度完全适应内容区域|
|xpx ypx|手动设置宽度和高度|
|x% y%|手动设置宽度和高度相对于容器的百分比|
>cover就是满足图片长宽中较小的一方撑满屏幕
>contain就是满足图片长宽中较大的一方撑满屏幕

可以写出以下代码
```css
.box {
  width: 350px;
  height: 250px;
  border: 1px solid #e8e8e8;
  font-size: 30px;
  font-weight: bold;
  color: yellowgreen;

  background-image: url(https://style.youkeda.com/img/ykd-components/logo.png);
  background-repeat: no-repeat;
  background-size: contain;
  background-position: center;
}
```
##### background合并写法
在background后连续跟多个背景属性值，如果没有此属性则置空，合并上述属性后的结果是
![[Pasted image 20231210003515.png]]
```css
.box {
  width: 350px;
  height: 250px;
  border: 1px solid #e8e8e8;
  font-size: 30px;
  font-weight: bold;
  color: yellowgreen;

  background: url(https://style.youkeda.com/img/ykd-components/logo.png)
    no-repeat center / contain;
}
```
其它属性：
[position-attachment](https://developer.mozilla.org/zh-CN/docs/Web/CSS/background-attachment)
[position-clip](https://developer.mozilla.org/zh-CN/docs/Web/CSS/background-clip)

## CSS伪类
### CSS伪元素-::after/::before
伪元素就是利用`css`代码在标签内部的前面，或者后面添加一个行内元素，这个行内元素可以理解为`span`
伪元素的写法：
```css
/* before */
选择器::before{
  /* 使用空白符号占位 */
  content: '';
}

/* after */
选择器::after{
  /* 使用空白符号占位 */
  content: '';
}
```
在选择器前面添加一个元素用`before`,在选择器后面添加一个元素用`after`
### CSS伪类--清除浮动
### 浮动的问题
父元素的兄弟元素会浮动在父元素的子元素中
希望的页面效果![[Pasted image 20240116234913.png]]
实际的页面效果![[Pasted image 20240116234932.png]]

现在我们需要一种技术可以让父元素包住浮动的子元素，即——**清除浮动**
### 清除浮动
```css
.clearfix::after{
  content: '';
  display: block;
  clear: both;
}
```
只要在父盒子上添加`clearfix`类名即可
```html
<!-- 添加清除浮动类名 -->
<div class="father-one clearfix">
    <div class="son-one">son-one</div>
    <div class="son-two">son-two</div>
    <div class="son-three">son-three</div>
</div>
```
记住：**哪个盒子的子元素有浮动，就在哪个盒子上添加清除浮动**
### CSS伪类——事件伪类
伪类通俗来说就是鼠标移动上去，字体颜色、背景颜色或者边框中的一种或多种样式发生了改变。
#### `hover`——鼠标移动上去
在鼠标移动上去后，背景颜色和文字发生了改变，这两种状态的转换过程叫做伪类
具体代码如下：
```css
li:hover{
    background-color: #47A0FC;
    color: white;
}
```
#### `active`——鼠标点击时（这里指的是点住鼠标不松开）
> 首先需要用选择器选中要添加伪类的标签`ul>li`
> 然后在选择器后面添加对应的伪类
> 最后在花括号内添加要改变的样式
```css
ul>li:active{
    /* 要改变的效果 */
    color: black;
}
```
==注意==`hover`一定要在`active`之前，否则不会生效
#### `focus`——获取焦点后
一般用于具有焦点的元素，如`input`，可以让`input`获取到焦点以后，改变`input`的边框颜色。
#### CSS伪类——列表伪类
##### 1. 匹配其父元素中的第一个子元素——`:first-child`
具体做法只要在基础代码上添加如下代码即可：
```css
ul>li:first-child{
    background-color: #3687FC;
    color: #FFFFFF;
}
```
==注意==：这里的选择器`ul>li`选到的是子元素`li`而不是父元素`ul`
##### 2.匹配到父元素中最后一个子元素——`:last-child`
与匹配第一个子元素类似
##### 3.匹配父元素中的第n个子元素——`:nth-child()`
`child`后面的括号可以添加任意数字，==从1开始==，1代表`first-child`。括号内除了可以写数字还可以写特定单词`odd`（奇数），`even`（偶数）。

##### 注意
列表伪类不止可以用于列表标签，只要是并列的相同元素都可以用列表伪类

### CSS装饰
#### CSS装饰——cursor
##### cursor
改变鼠标箭头的变化
详细可查[MDN文档](https://developer.mozilla.org/zh-CN/docs/Web/CSS/cursor)
#### CSS装饰——box-shadow/text-shadow
##### box-shadow——盒子阴影
其基本原理是盒子下面的另一个盒子改变样式或者位置
可以用[点击阴影效果在线调试工具](https://www.w3cschool.cn/tools/index?name=css3_boxshadow)调节相关的属性值来查看效果
> 一个盒子可以添加多个阴影

在实际应用中，前端工程师很难调出好看的阴影，主要是复制设计稿上的阴影值，所以阴影是一个常用但不重要的属性，只要知道如何找到并设置就好
```css
div{
    box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.11);
}
```

##### text-shadow——文字阴影
文字阴影和盒子阴影一样，就是文字下面还有一层相同文字
```css
span{
    text-shadow: 0px 0px 10px rgba(0, 0, 0, 0.11);
}
```

### CSS Flex布局
#### CSS Flex布局
Flex布局可以简便、完整、响应式地实现各种页面布局，并且已经得到所有浏览器的支持，所以可以放心安全的使用这项功能。flex布局有强大的空间分布和对齐能力，可以很容易解决传统布局比较难解决的布局问题
##### 什么是flex
Flex是Flexible Box的缩写，意为“弹性布局”，用来为盒装模型提供最大的灵活性。任何一个容器都可以指定为Flex布局
**它最显著的效果就是把原本从上到下排列的块状元素变成水平排列：**
![[Pasted image 20240119214950.png]]
HTML如下：
```html
<div class="container">
  <div class="item">项目1</div>
  <div class="item">项目2</div>
  <div class="item">项目3</div>
</div>
```
CSS如下
```css
.container {
  display: flex;
  background: #D5E8D4;
  border: 1px solid #5D9E5A;
}

.item {
  width: 50px;
  height: 50px;
  background: #FFF2CC;
  border: 1px solid #B7A570;
  margin: 10px;
}
```
fkex设置在父元素上，采用了flex布局的元素称为Flex容器，简称容器（container），它的所有子元素称为Flex项目，简称项目（item）
![[Pasted image 20240119215304.png]]

#### justify-content和ailgn-items
如果想让各项均匀分布，就需要用到flex布局中**控制水平方向分布**的属性justify-content使各项均匀分布
##### 1.调整水平方向的分布justify-content
**justify-content属性定义了项目在水平方向上的对齐方式**
> justify-content是容器的属性，设置在容器上

justify-content有六个有效值：
```
justify-content: flex-start | flex-end | center | space-between | space-around | space-evenly;
```

六个值的表现形式如下：

![](https://document.youkeda.com/P3-2-HTML-CSS/1.4/9.jpg?x-oss-process=image/resize,w_800/watermark,image_d2F0ZXJtYXNrLnBuZz94LW9zcy1wcm9jZXNzPWltYWdlL3Jlc2l6ZSx3XzEwMA==,t_60,g_se,x_10,y_10)

> 在六个值中，我们最常用到的就是 “space-between” 了。

##### 2.调整垂直方向上的分布align-items
**align-items属性定义项目在垂直方向上如何对齐**
> 特别注意，align-items是容器的属性，设置在容器上

align-items有五个有效值：
```
align-items: flex-start | flex-end | center | baseline | stretch;
```
五个值的表现形式如下：
![[Pasted image 20240119235044.jpg]]
> 五个值中最常用到的是center，另外align-items的默认值是stretch，即默认项目和容器等高

#### flex-wrap
默认情况下项目都排在水平方向上，并且都是单行排列，不会换行。即使所有项目的宽度超过了容器宽度也不会换行，并且会在宽度上进行压缩
如果想让项目换行，可以用flex-wrap属性，定义项目是否换行，以及如何换行
flex-wrap可能取三个值。flex-wrap：nowrap|wrap|wrap-reverse；
![[Pasted image 20240120094408.jpg]]

#### flex:none和flex：1
当一行排不下又需要项目能够排在一行里，宽度有不被压缩，需要用到**项目属性**，flex，它可以控制项目的放大和缩小
##### 不允许项目压缩、放大 flex：none
如果希望项目排在一行里，但是项目的宽度又不被压缩，就要给项目设置flex：none，使项目不能被压缩或放大。
>之前我们接触到的属性，justify-content、align-items、flex-wrap，都是设置在flex容器上的。但这个控制项目是否被压缩或放大的属性是设置在flex项目上的

##### 项目自动充满剩余空间 flex：1
如果一行有剩余的情况下，希望项目能够均匀放大，撑满水平方向，我们应该给**所有项目**设置flex：1。
> 注意，因为所有项目设置的flex的值都为1，所以所有项目的宽度都相同，我们可以用这一点来平分一行空间

##### 两栏自适应布局
指的是一栏固定宽度，另一栏随浏览器宽度的变化自动调节自己的宽度

##### 指定项目放大
如果一行有剩余的情况下，可以任意指定某个项目放大撑满剩余空间，只要给指定项目设置flex：1即可。

#### flex-direction
和之前三栏自适应相似，如果有的时候需要垂直方向上的三栏自适应布局，上下两栏固定，中间栏高度充满剩余空间，这样在不同高度的手机上都能适应。
flex布局提供了一个属性flex-direction，当设置flex-direction：column时，上面的横向三拦自适应布局会变成纵向的：
##### 主轴和交叉轴
flex布局中的两根轴——主轴和交叉轴：
![[Pasted image 20240120164345.jpg]]
默认情况下两根轴的方向：**主轴**：水平，从左到右；**交叉轴**：垂直，从上到下；
容器中的项目默认按照**主轴**方向排列。
> 主轴和交叉轴是**相互垂直**的关系，交叉轴的方向会随着主轴方向的改变而改变，两轴线始终保持垂直关系

##### 改变容器中主轴和交叉轴的方向 flex-direction
flex-direction是容器的属性，设置在容器上。
flex-direction有四个有效值
1. row：即默认值，主轴为水平方向，起点在左端
2. row-reverse：主轴为水平方向，起点在右端
3. column：主轴为垂直方向，起点在上沿
4. column-reverse：主轴为垂直方向，起点在下沿
四种有效值情况下项目的排练方向：
![[Pasted image 20240120164943.jpg]]

### CSS高级美化
#### 单行文本超出省略
在网页中常常遇到文本内容溢出，用省略号代替剩余内容的情况
在正常情况下，文本内容超出了所给的宽度范围，文字会自动换行，但我们并不希望它换行，这时候就需要进行单行文本溢出省略的操作了，这里就涉及三个知识：强制不换行、元素内容溢出处理和文本溢出省略
##### 强制不换行
 推荐使用`white-space:nowrap;`实现不换行

##### 元素内容溢出overflow
overflow属性决定超出盒子的内容怎么显示，它有5个有效值：`overflow: visible | hidden | inherit | scroll | auto;`

|值|描述|
|---|---|
|visible|**默认值**。内容不会被修剪，会呈现在元素框之外。|
|hidden|内容会被修剪，并且超出的内容不可见|
|inherit|规定应该从父元素继承 overflow 属性的值。|
|scroll|内容会被修剪，浏览器会显示滚动条以便查看超出的内容|
|auto|由浏览器定夺，如果内容被修剪，就会显示滚动条|

##### 文本溢出省略text-overflow
它有两个值：`text-overflow:clip|ellipsis;`
* clip：默认值，表示在内容区域的极限处截断文本
* ellipsis：表示用一个省略号("...")来表示被截断的文本 

#### 多行文本超出省略
WebKit内核的浏览器实现多行文本溢出省略比较简单
```css
/* 隐藏超出部分 */
overflow : hidden;
/* 文本超出就用省略号 */
text-overflow: ellipsis;
/* 把对象作为弹性伸缩盒子模型显示 */
display: -webkit-box;
/* WebKit内核的浏览器的私有属性，设置文本超出2行就用省略号 */
-webkit-line-clamp: 2;
/* WebKit内核的浏览器的私有属性，设置或检索伸缩盒对象的子元素的排列方式 */
-webkit-box-orient: vertical;
```

### CSS预处理器
#### SCSS介绍
##### 什么是SASS
**SASS**是一款CSS预编译器，它定义了一种新的编程语言，为CSS增加了一些编程的特性。开发者使用这种语言进行编码后，代码需要被编译成CSS才能被浏览器理解
SASS比CSS更像一门编程语言，它可以有变量、函数、控制语句、导入、嵌套等高级功能，类似的CSS预编译器还有**less**、**Stylus**等
有了这些高级功能，SASS可以：
1. 提供变量，实现一键替换主题色之类的功能；
2. 用嵌套写法减少选择器的重复书写；
3. 用混用功能解决代码复用问题；
4. 用函数进行复杂的运算
5. 把样式代码模块化，减少不同模块的代码间不必要的相互影响，提高代码的安全性
> Sass是对CSS的拓展，让CSS语言更强大、优雅。它允许使用变量嵌套规则、mixins、导入等众多功能，并且完全兼容CSS语法，Sass有助于保持大型样式结构良好，同时也能够快速开始小型项目，特别是在搭配Compass样式库一同使用，主要体现在以下方面：
> 完全兼容CSS3
> 在CSS基础上增加变量、嵌套、混合等功能
> 通过[函数](http://sass-lang.com/docs/yardoc/Sass/Script/Functions.html)进行颜色值与属性值的运算
> 提供[控制指令 (control directives)](https://www.sass.hk/docs/#t8)等高级功能
> 自定义输出格式

###### 安装
对scss文件，需要手动执行命令进行编译转换。打开终端，进入作业目录后输入命令：
```shell
sass --watch index.scss:index.css
```
这条命令的意思是把index.scss编译转换成index.css文件

##### Sass和Scss
Scss其实是Sass3为了兼容CSS引入的新语法
CSS的语法是选择器+声明块。声明块是由花括号和声明组成的
但最早的Sass语法格式，是**缩进格式**，是一种简化格式，使用“缩进”代替“花括号”表示属性属于某个选择器，用“换行”代替“分号”分隔属性。
Scss语法完全兼容CSS3，并且继承了Sass的强大功能，也就是说任何标准的CSS3样式表都是具有相同语义的有效的Scss文件。
**Sass和Scss的大部分扩展，例如变量、parent references和指令都是一致的；唯一不同的是，SCSS需要使用分号和花括号而不是换行和缩进**

#### 变量
在CSS属性的基础上Sass提供了一些名为SassScript的新功能。SassScript可作用于任何属性，允许属性使用变量、算数运算等额外功能
SassScript最普遍的用法就是变量，变量以美元符合“$"开头，赋值方法与CSS属性的写法一样：
```scss
$width: 10px;
```
使用变量：
```scss
#main {
  width: $width;
}
```
编译成css：
```css
#main {
  width: 10px;
}
```
如果变量类型为字符串，一般不需要加引号，但有些特殊情况，如字符串中有双斜杠"//"，就需要用英文输入法状态下的单引号或者双引号包裹字符串，用引号的写法：
```scss
// 变量需要定义在使用之前
$position: "absolute";
$mainTxtColor: '#333';

// 应用
#main {
  position: $position;
  color: $mainTxtColor;
}
```
>因为在Sass中双斜杠表示单行注释

除了简单的赋值，Sass中变量还可以定义类似的数组的变量
```scss
$animals: puppy kitty chick;
```
这样的变量一般会配合Sass中的循环语句使用

##### 简单计算
```scss
$width: 10px;

#main {
  width: $width / 2;
}
```
编译成css：
```css
#main {
  width: 5px;
}
```
Sass中支持在使用变量的时候进行简单的加减乘除的计算，这样我们就可以很方便的低于固定宽高比的元素。比如：
```scss
$width: 10px;

#main {
  width: $width / 2;
  height: $width * 2;
}
```
编译成css
```css
#main {
  width: 5px;
  height: 20px;
}
```
上面元素的宽高比：width：height=1/4，不管怎么改变$width这个值，宽高比都不会变
##### 插值法
`#{}`插值几乎可以在Sass样式表的任何地方使用
```scss
$name: "mail";
$top-or-bottom: "top";
$left-or-right: "left";

.icon-#{$name} {
  background-image: url("/icons/#{$name}.svg");
  position: absolute;
  #{$top-or-bottom}: 0;
  #{$left-or-right}: 0;
}
```
编译后变成：
```css
.icon-mail {
  background-image: url("/icons/mail.svg");
  position: absolute;
  top: 0;
  left: 0;
}
```
>插值法可以插入任何类型的变量，不仅仅是字符串

#### 嵌套
```css
main .double .item .links {
  text-align: center;
}

main .double .item .links a {
  margin-right: 20px;
}
```
这种长长的css选择器写法可读性可维护性差，在Sass提供了一个很实用的功能：嵌套。比如可以提出共同的选择器：
```scss
main .double .item .links {
  text-align: center;
  a {
    margin-right: 20px;
  }
}
```
##### 嵌套规则
Sass允许将一套CSS样式嵌套进另一套样式中，内层样式将它的外层选择器作为父选择器
![[Pasted image 20240123235829.jpg]]
可以避免重复输入父选择器，而令复杂的CSS结构更易于管理
##### 父选择器 &
在嵌套CSS规则，有时也需要直接使用嵌套外层的父选择器，如，当某个元素设定hover样式时，可以用&代表嵌套规则外层的父选择器
![[Pasted image 20240124000150.jpg]]
这样可以使代码结构更清晰，大大降低写错的概率，安全性、可读性、可维护性都有很大的提升

#### 复用：mixin/include
很多编程语言中都有解决代码复用的方案，我们可以用混合（mixin/include）来定义可重复使用的样式。mixin/include除了可以用来解决代码复用问题，还能解决无语义的类名问题
##### 无参数混合
以前在css可以通过复用类名来实现代码的复用
现在可以用Sass的mixin/include来解决复用问题：
```scss
@mixin square {
  width: 100px;
  height: 100px;
}

// 应用：
.user-avatar {
  @include square;
}
.admin-avatar {
  @include square;
}
```
在上面的代码中，定义了一个可复用的代码块，并取名为square，然后通过使用关键词@include，在后面应用这个样式
混合的使用方法：**“@mixin”：定义可复用的样式“@include”：应用可复用的样式**

##### 有参数混合
###### 参数无默认值
给定义的复用代码块传入参数，增加可用性。
```scss
@mixin square($size) {
  width: $size;
  height: $size;
}

// 应用
.avatar {
  @include square(100px);
}
```
这里使用square的时候传入一个值$size，然后根据传入的值来处理元素
###### 参数有默认值
传参数的这种情况，我们还可以给参数设定默认值，比如：
```scss
@mixin square($size: 100px) {
  width: $size;
  height: $size;
}

// 不传参数就会使用默认的值 100px
.avatar {
  @include square;
}

// 传入参数就会使用传入的值 200px
.avatar-200 {
  @include square($size: 200px);
}
```

### CSS响应式
#### 响应式布局
响应式布局就是一个网站能够兼容多个终端，而不是为每个终端做一个特定的版本
响应式布局主要是通过规定**特定的宽度范围使用特定的布局**来实现在不同的设备上应用不同的布局，在同一设备上通过调整浏览器的宽度也可以改变页面布局
要使页面在不同的宽度范围内使用特定的布局，就需要制定对应的规则，这里就需要用到CSS3中的媒体查询@media了
#### 媒体查询
媒体查询是CSS3中引入的一种CSS技术，仅满足特定条件时，才使用对应的CSS属性块。
媒体查询的基础语法：
![[Pasted image 20240124132502.jpg]]
> "screen"：告知设备在打印页面时使用衬线字体，在屏幕上显示用无衬线字体。如果网页不需要考虑用户去打印时，可以直接把上图代码中的"screen and"去掉。

##### QQ注册页的响应式布局
根据浏览器宽度不同，有三种布局
![[Pasted image 20240124133402.jpg]]
###### 条件：最大宽度（max-width）
当宽度小于等于900px，也就是最大宽度是900px，所以宽度条件是("max-width:900px")
![[Pasted image 20240124133711.jpg]]
###### 条件：最小宽度（min-width）
当宽度大于1080px，即浏览器的最小宽度为1080px（min-width:1080px):
![[Pasted image 20240124134135.jpg]]
###### 逻辑操作符 and
当浏览器宽度大于900px，小于1080px，即浏览器的最小宽度900px（min-width：900px），最大宽度是1080px（max-width:1080px）并用逻辑操作符and把两个条件结合起来：
![[Pasted image 20240124134538.jpg]]
#### 断点
##### 断点
以QQ注册页为例，我们用两个点（900px和1080px）把浏览器宽度分成三段，在这三段中，页面左侧大图有不同的表现：
![[Pasted image 20240124141337.jpg]]
这两个点（900px和1080px）就是我们所说的断点
断点的值的设置和设备的尺寸有很大关系
以下是典型的断点
![[Pasted image 20240124141514.png]]
##### 冲突的媒体查询条件
在QQ注册页中，除了上一章的写法，还可以这样写
```css
/* 小于等于 900px时应用此布局 */
@media screen and (max-width: 900px) {
  .container .side {
    /* 提示：把原来的 display:none; 改成了 width:0; */
    width: 0;
  }
}

/* 小于等于 1080px时应用此布局 */
/* 提示：把原来的条件 “(min-width: 900px) and (max-width: 1080px)” 改成了 “(max-width: 1080px)” */
@media screen and (max-width: 1080px) {
  .container .side {
    width: 240px;
  }
}

/* 大于1080px时应用此布局 */
@media screen and (min-width: 1080px) {
  .container .side {
    width: 480px;
  }
}
```
把上面的规则表示在数轴上：
![[Pasted image 20240124142112.jpg]]
当浏览器宽度小于900px，会同时满足两个条件，根据css中越靠后优先级越高的原则，所以应用width：240px，不符合预期。所以冲突的媒体查询条件的顺序要排好。
![[Pasted image 20240124142256.jpg]]
实际上应该把第一个条件和第二个条件的顺序交换一下。

总结：
* 媒体查询用max-width表示条件时，大的断点要放上面
* 反过来用min-width表示条件时，小的断点要放上面
![[Pasted image 20240124142438.jpg]]

#### Sass文件的导入
这个模块化就是HTML中的不同结构对应一个样式文件，比如微博banner对应一个banner的样式文件，左侧栏对应的左侧栏样式文件，最后把它们导入到一个文件中，再把这个文件编译后的css文件引入html文件即可。
![[Pasted image 20240124143553.jpg]]

### 移动端web开发
#### 认识meta
如果要做手机端上用的页面（H5），除了用媒体查询进行小屏幕设备的适配，还需要设置一些特别的内容，比如页面是否允许用户缩放等。这里我们需要用到`<head>`元素中的`<meta>`元素。
##### meta元素
`<meta>`是一个自闭合元素，只有开始标签，没有结束标签。对meta元素进行设置指的是通过标签属性进行设置。
`<meta>`元素表示那些不能由其它HTML元相关元素表示的任何元数据信息（meta-information），比如页面是否允许用户缩放、比如针对搜索引擎和更新频度的描述和关键词等。
>元数据：用来描述数据的数据，不理解没关系，只要知道meta在移动端开发中的作业就可以了。

下面是**youku首页的Meta设置**
```html
<!-- 声明文档使用的字符编码 -->
<meta charset="utf-8">
<!-- http-equiv相当于http的文件头作用，它可以向浏览器传回一些有用的信息，以帮助浏览器正确地显示网页内容 -->
<!-- 与http-equiv对应的属性值为content，这里IE=edge告诉IE使用最新的引擎渲染网页 -->
<meta http-equiv="X-UA-Compatible" content="IE=Edge">
<!-- name属性主要用于描述网页，与之对应的属性值为content，content中的内容主要是便于搜索引擎机器人查找信息和分类信息用的 -->
<meta name="title" content="优酷-中国领先视频网站,提供视频播放,视频发布,视频搜索 - 优酷视频" />
<meta name="keywords" content="视频,视频分享,视频搜索,视频播放,优酷视频" />
<meta name="description" content="视频服务平台,提供视频播放,视频发布,视频搜索,视频分享" />
```
charset的属性：
* utf-8：HTML5的默认字符集为UTF-8，UTF-8（Unicode）涵盖了世界上几乎所有的字符和符号
> 设置utf-8之后。就能识别中文了。

###### 移动web前端meta的基础设置
在开发移动端页面时，需要设置meta标签如下：
```html
<!-- 设置移动端视图 -->
<meta name="viewport" content="width=device-width,initial-scale=1.0,minimum-scale=1.0,maximum-scale=1.0,user-scalable=no" />
```
viewport的属性：
* width:viewport的宽度
* height:viewport的高度（很少用）
* initial-scale:初始的缩放比例
* minimum-scale:允许用户缩放到的最小比例
* maximum-scale:允许用户缩放到的最大比例
* user-scalable:用户是否可以手动缩放
所以上面的设置表示：H5页面窗口自动调整到设备宽度，并且禁止用户缩放页面

#### 认识新的单位 rem/em
开发响应式页面时，同一个元素在不同的浏览器宽度下常常会设置不同的尺寸。
比如下面这个页面，在两种宽度下标题字体大小（font-size）和右上角logo大小是不同的
![[Pasted image 20240124220435.jpg]]
我们可以这样做
```scss
// .title选中大标题“11 powerful examples of responsive web design”
// .logo选中右上角logo
@media screen and (max-width: 768px) {
  .title {
    font-size: 40px;
  }
  .logo {
    width: 160px;
    height: 160px;
  }
}
@media screen and (min-width: 768px) {
  .title {
    font-size: 50px;
  }
  .logo {
    width: 200px;
    height: 200px;
  }
}
```
之后如果需要新增一个断点，就需要新增一个媒体查询（@media），并且需要把所有要调整的样式都写一遍，如果需要调整的样式有很多，那么工作量就会很大。
我们可以使用css3中的单位rem来简化这个工作。
rem是一个相对长度单位，我们熟悉的px可以认为是一个绝对单位。在不同环境中，1rem可以转化为不同的px值。
###### 单位rem和px之间的转换
使用rem作为单位时，rem和px之间的转换比取决于页根元素（`<html></html>`)的字体大小，简单来说：1rem=根元素的字体大小。
拿上面的例子来说，如果现在浏览器的默认字体大小为16px，当浏览器宽度width<=678px时，标题的大小为40px，如果用rem表示应该是2.5rem（2.5*16px=40px）
>一般浏览器中根元素的字体默认大小为16px，有些情况下可能为其他大小，最小显示字体一般为10px，即设置10px以下的数值等是没有用的，显示的时候都会按照10px的大小进行显示，除非用到了css中的transform（这个另当别论）。

###### 单位rem的使用
用rem写大小，然后通过媒体查询设置不同宽度下根元素（`<html></html>`)的字体大小，间接对应的大小，这样媒体查询里就只需要设置根元素的字体大小就可以了

###### 单位：em
rem是相对于根元素的字体大小转换的。em则是根据父元素的字体大小转换的。
如：
```html
<div class="parent">
  父元素中的文字
  <div class="child">
    子元素中的文字
  </div>
</div>
```

```scss
.parent {
  // 父元素的字体大小为 20px
  font-size: 20px;

  > .child {
    // 子元素的字体大小为 0.7 * 20px = 14px
    font-size: 0.7em; 
    // 特别注意：子元素的宽度为 10 * 14px = 140px
    width: 10em;
  }
}
```
子元素的em转换分两种：
1. 子元素字体大小：0.7em 
	这里的1em和父元素的字体大小相同，为20px，所以子元素的字体大小为0.7*20px=14px
2. 子元素的宽度：10em
	这里的1em和子元素的字体大小相同，为14px，所以子元素的宽度10*14px=140px
**注意这两种计算中的子元素宽度计算过程**
> 既然上面两种情况下1em对应的px值不同，那么如何理解呢？其实子元素中除了font-size属性外，其它属性计算的时候是根据子元素本身的字体大小计算的，但由于子元素本身的字体大小是根据父元素的字体大小计算的，所以可以认为em是根据父元素的字体大小转换的。

因为em是相对父元素字体大小进行计算的，所以这里就暴露了一个问题，如果在多层嵌套中使用em，那么计算的时候就会饭勺级联反应，一旦嵌套过多，很容易计算出错

#### 认识新的单位vw/vh
##### 单位vw和单位vh
vw和vh也是相对长度单位
* 1vw=1/100视口宽度；
* 1vh=1/100视口高度；
视口（viewport）就是指文档的可见部分
![[Pasted image 20240124223213.jpg]]
在**模态框**可以用到这两个单位
##### 模态框
模态框（modal dialog）：通常指页面中弹出的窗口。像首次登录时弹出的用户协议、用户信息完善弹框，都属于模态框。
![[Pasted image 20240124223358.jpg]]
模态框的半透明覆盖层的特征即大小覆盖整个视口，我们现在用vj和vw做上图的模态框的半透明覆盖层
###### 1.设置模态框蒙层的大小为视口大小
```scss
// 将蒙层的宽高设置为视口的宽度和高度
width: 100vw;
height: 100vh;
```
###### 2.将模态框蒙层用position：fixed定位到浏览器左上角：
```scss
// 用定位把蒙层定位到浏览器的左上角
position: fixed;
top: 0;
left: 0;
```

## 实战开发
### 设计稿尺寸处理
在实际的前端开发工作中，会根据设计稿来进行开发，一般移动端设计稿是基于iPhone6的尺寸制作的，所以设计稿宽度往往是750px。
现在高清屏像素比一般是2，比如iPhone6实际可视区域宽度是375px，但能够显示750px。基于这个原因，我们在写样式代码的时候需要把设计稿上的尺寸除以2才能使用。
但是如果每个值都要计算才能使用会非常麻烦。好在Sass允许我们自定义函数
#### Sass自定义函数
自定义函数基础语法如下：
![[Pasted image 20240124233041.jpg]]
我们可以用上面这个自定义函数统一处理设计稿上的尺寸，比如：
```scss
@function psd2px($px) {
  @return #{$px / 2}px;
}

.header {
  // 假设设计稿上高度是100px，那么函数参数就写100，计算后返回的值就是 50px
  height: psd2px(100);
}
```
##### 移动端的响应式布局尺寸处理
这样的返回值仍是以px为单位的值，出于响应式布局的考虑，需要把传入的px值转换成一个rem单位的值。
###### 1.设置根元素的字体大小
由于1rem对应的px值是根据根元素的字体大小进行计算的，所以这里要先确定根元素的字体大小：
```scss
html {
  font-size: 20px;
}
```
###### 2.重写自定义函数
```scss
html {
  font-size: 20px;
}

@function psd2px($px) {
  @return #{$px / 40}rem;
}
```
为什么返回语句传入的参数要除以40？
以设计稿宽度750px，设备像素比为2的情况推断。设计稿上的100px->我们要显示的是50px，所以100px/2。其次由于1rem=20px，所以50px=2.5rem，所以40=100/2.5。
###### 3.用媒体查询写响应式布局
根据iPhone机型尺寸设置断点![[Pasted image 20240125104245.jpg]]
```scss
@function psd2px($px) {
  @return #{$px / 40}rem;
}

@media screen and (max-width: 768px) {
  html {
    font-size: 20px;
  }
}

// <= 320px 的情况下，根元素的字体大小等比例缩小
@media screen and (max-width: 320px) {
  html {
    font-size: 20px / 375 * 320;
  }
}
```

### 固定头部
![[Pasted image 20240125104415.jpg]]
HTML如下：
```html
<header class="header">
  <!-- 主导航 -->
  <nav class="nav"></nav>

  <!-- 副导航 -->
  <div class="subnav"></div>
</header>
```
#### 1.垂直方向
主导航的分布，“关注”、“热门”、红包按钮和圆形加号按钮距离下边8px，相机按钮距离下边10px。
这种情况可以用flex布局align-items：flex-end使其底部对齐，然后给相机按钮单独设置2px下外边距实现对齐。
#### 2.水平方向
主导航部分水平方向的分布较难处理，直接使用flex布局的justify-content属性，比较难调整
通过一定方法使左右两侧的按钮宽度相同，然后通过flex的justify-content：space-between实现中间部分的居中。
### 横向滚动
副导航由可横向滚动的导航和右侧的按钮组成。
横向滚动可以使用overflow：scroll属性，但是这个属性在ios移动端会很卡，不够顺滑，所以还需要加上一个属性 -webkit-overflow-scrolling：touch，这个属性可以解决ios上滚动卡顿的问题。
#### 副导航右侧按钮的实现
使用绝对定位固定它的位置，使用背景图+渐变色实现半透明效果
```scss
.btn-addclass {
  background: url(./images/add.png) no-repeat center / px2rem(16) px2rem(16), linear-gradient(to right, rgba(#fff, 0.8), rgba(#fff, 0.8) 50%, #fff 50%);
}
```
最后用position：fixed将导航固定到头部