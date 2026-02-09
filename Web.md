# Web网站入门

## html

html：超文本标记语言



### 标签语法

双标签：

标签成对出现，中间包裹内容

`<>`里放英文字母（标签名）

结束标签，在标签名前加`/`

单标签：

只有开始标签，没有结束标签，列如：`<br>`和`<hr>`



#### 注释标签

用法：`<!--注释内容-->`



#### 标题标签

`<h1>~<h6>`(双标签)

1~6,标签由大到小



#### 段落标签

`<p>`(双标签)

文本用p标签包裹



#### 换行与水平线标签

`<br>`换行标签，（单标签），enter不能实现换行

`<hr>`水平线标签，（单标签）



#### 文本格式化标签



| 标签名（两种二选一） |     效果      |
| :------------------: | :-----------: |
|       strong/b       |     加粗      |
|         em/i         |  <i>倾斜</i>  |
|        ins/u         | <u>下划线</u> |
|        del/s         | <s>删除线</s> |



#### 图像标签

用法：`<img src="图片的url" alt="若图片不显示，显示提示">`



属性

|  属性  |   作用   |             说明             |
| :----: | :------: | :--------------------------: |
|  alt   | 替换文本 |    图片无法显示时显示文字    |
| title  | 提示文本 | 鼠标悬停在图片上时显示的文字 |
| width  | 图片宽度 |      值为数字，没有单位      |
| height | 图片高度 |      值为数字，没有单位      |



#### 布局标签

作用：网页布局

`div`：独占一行（双标签）

`span`：不换行（双标签）



### 字符实体

作用：在页面显示预留字符

| 实体名称 | 描述     | 显示结果 |
| -------- | -------- | -------- |
| `&nbsp;` | 空格     |          |
| `&lt;`   | 小于符号 | <        |
| `&gt;`   | 大于符号 | >        |





#### 路径

##### 相对路径

`/文件夹`进入文件夹

`./`当前文件

`../`上一级文件

##### 绝对路径

从系统盘符开始找直到找到文件



#### 超链接标签

用法：`<a href="地址或链接或文件">提示内容</a>`

点击提示内容跳转

`href=“#”`   表示空链接

在新窗口打开  `target="_blank"`  



#### 锚点

href=“#属性值”

```html
<div id="top">跳转到这里</div>
<a href="#top">点击跳转</a>
```







#### 音频标签

|      属性       |       作用       |        特殊说明         |
| :-------------: | :--------------: | :---------------------: |
| src（必要属性） |     音频url      | 支持格式：MP3、Ogg、Wav |
|    controls     | 显示音频控制面板 |                         |
|      loop       |     循环播放     |                         |
|    autoplay     |     自动播放     |        一般禁用         |



#### 视频标签

`<video src="视频的url"></video>`

|      属性       |       作用       |        特殊说明         |
| :-------------: | :--------------: | :---------------------: |
| src（必要属性） |     音频url      | 支持格式：MP3、Ogg、Wav |
|    controls     | 显示音频控制面板 |                         |
|      loop       |     循环播放     |                         |
|    autoplay     |     自动播放     |    一般静音自动播放     |
|      muted      |     静音播放     |                         |



### 列表

作用：布局内容整齐排列的区域



#### 无序列表

作用：布局排列整齐的不需要规定顺序的区域

标签：`ul`嵌套`li`，`ul`是无序列表，`li`是列表条目

`<ul>`标签里面只能包裹`<li>`标签

`<li>`可以包裹任何内容



实例：

```html
<ul>
    <li>第一项</li>
    <li>第二项</li>
    <li>第三项</li>
</ul>
```



#### 有序列表

作用：布局排列整齐的需要规定顺序的区域

标签：`ol`嵌套`li`，`ol`是有序列表，`li`是列表条目

`<ol>`标签里面只能包裹`<li>`标签

`<li>`可以包裹任何内容



实例：

```html
<ol>
    <li>第一项</li>
    <li>第二项</li>
    <li>第三项</li>
</ol>
```



#### 定义列表

标签：`dl`嵌套`dt`和`dd`，`dl`是定义列表，`dt`是定义列表的标题，`dd`是定义列表的描述/详情

`<dl>`标签里面只能包裹`<dd>,<dt>`标签

``<dd>,<dt>``可以包裹任何内容



#### 表格

标签：`table`嵌套`tr`，`tr`嵌套`td/th`

属性：`border="像素值"`设置边框和大小

| 标签名 |    说明    |
| :----: | :--------: |
| table  |    表格    |
|   tr   |     行     |
|   th   | 表头单元格 |
|   td   | 内容单元格 |



##### 表格结构标签

| 标签名 |   含义   |   特殊说明   |
| :----: | :------: | :----------: |
| thead  | 表格头部 | 表格头部内容 |
| tbody  | 表格主体 | 主要内容区域 |
| tfoot  | 表格底部 | 汇总信息区域 |



##### 合并单元格

跨行合并：保留`最上`单元格，属性`rowspan="属性值"`属性值为合并表格数量

跨列合并：保留`最左`单元格，属性`colspan="属性值"`属性值为合并表格数量



#### 表单

作用：收集用户信息

使用场景：登录、注册页面，搜索区域



##### input标签

用法：`<input type="属性值">`

提示属性`placeholder="提示内容"`

border:none;          /*删除默认边框*/

outline:none;          /*删除选择边框*/



> radio常跟属性

实例：

```html
<input type="radio" name="gender" checked>男  <!--默认选择男-->
<input type="radio" name="gender" >女
```



> file常跟属性

multiple：能选择多个文件



实例：

```html
<input type="file" multiple>
```





| type属性值 |           说明           |
| :--------: | :----------------------: |
|    text    | 文本框，用于输入单行文本 |
|  password  |          密码框          |
|   radio    |          单选框          |
|  checkbox  |          多选框          |
|    file    |         上传文件         |



| 属性名  |   作用   |                特殊说明                |
| :-----: | :------: | :------------------------------------: |
|  name   | 控件名称 | 控件分组，同时只能选中一个（单选功能） |
| checked | 默认选中 |   属性名和属性值相同，简写为一个单词   |



##### 下拉菜单

标签：`select`嵌套`option`，`select`是下拉菜单整体，`option`是下拉菜单的每一项

`selected`默认选择



实例：

```html
<select>
    <option selected>重庆</option>
    <option>北京</option>
    <option>上海</option>
</select>
```



##### 文本域

标签：`textarea`双标签，默认有拖拽功能，以后需要用css样式设置尺寸，不然将影响其他区域

用法：`<textarea>默认提示文字</textarea>`



##### label标签

> 增大点击范围

写法一：

- label标签只包裹表单控件
- 设置label标签的for属性值和表单控件的id属性相同



实例：

```html
<input type="radio" name="gender" id="1">  <label for="1">男</label>

<input type="radio" name="gender" id="2" ><label for="2">女</label>
```



写法二：

- 直接用label标签包裹文字和表单控件



实例：

```html
<label><input type="radio" name="gender" >男</label>
<label><input type="radio" name="gender" >女</label>
```



##### button按钮

用法：`<button type="属性值">按钮</button>`



| type属性值 | 说明                                           |
| ---------- | ---------------------------------------------- |
| submit     | 提交按钮，点击后可提交数据到后台（默认功能）   |
| reset      | 重置按钮，点击后将表单控件恢复默认值           |
| button     | 普通按钮，默认没有功能，一般配合JavaScript使用 |



##### form标签

form标签包裹的内容标签，能够用button提交到后台



实例：

```html
<form>
    账号<input type="text" placeholder="请输入账号">
    密码<input type="password" placeholder="请输入密码">
    <button type="reset">重置</button>
</form>
<button type="reset">重置</button>     <!--写在form外面的重置按钮不生效-->
```





## css

### css注释

用法：`/*注释内容*/`

### css选择器

#### id选择器

html中id元素`唯一`

id选择器可以为标有特定id的html元素指定特定的样式，一般配合JavaScript使用

css中id选择器以`#`定义



实例：

```css
#para1
{
	text-align:center;
	color:red;
}
```



#### class选择器

css中class选择器以`.`定义

在`.`前面加标签名，则定义该标签的class选择器，其他有同样class属性的将不受影响

class选择器能够包含多个属性值，用空格隔开



实例：

```css
.center{text-align:center;}  /*定义所有class=“center”*/

p.center{text-align:center;}  /*只定义p属性的class样式*/
```



#### 通配符选择器

作用：查找页面所有标签，设置相同样式

用`*`表示，不需要调用，浏览器自动查找所有标签，设置相同的样式



#### 后代选择器

作用：修改当前标签下的子标签的样式

如果只修改当前标签下的一个子标签用`>`



实例：

```html
<html>
    <head>
        <style>
            div p{           /*只修改div下的p标签的字体颜色*/
                color:red;
            }
        </style>
    </head>
    <body>
        <p>hello!</p>
        <div>
            
            <p>
                hello!     
            </p>
        </div>
    </body>
</html>
```



#### 并集选择器

选择多组标签设置相同样式

用法：选择器1，选择器2，.... {css样式}                         <!--选择器之间用逗号隔开-->





#### 伪类选择器

表示元素状态，选中的某一个状态设置样式

鼠标悬停状态：选择器`标签名:hover`{css属性}



实例：

```
<html>
    <head>
        <style>
             p:hover{           
                color:red;
            }
        </style>
    </head>
    <body>
        <p>hello!</p>
        <div>
            
            <p>
                hello!     
            </p>
        </div>
    </body>
</html>
```



##### 伪类超链接

| 选择器   | 作用           |
| -------- | -------------- |
| :link    | 访问前         |
| :visited | 访问后         |
| :hover   | 鼠标悬停       |
| :active  | 点击时（激活） |

> [!IMPORTANT]
>
> 如果要设置这四种状态要按照`lvha`顺序写



#### 结构为类选择器

作用：根据元素的结构关系查找元素

使用时将E替换成标签名

|     选择器     |              说明              |
| :------------: | :----------------------------: |
| E:first-child  |        查找第一个E元素         |
|  E:last-child  |       查找最后一个E元素        |
| E:nth:child(N) | 查找第N个E元素（第一个N值为1） |

查找多个标签

:nth-child(公式)



实例：

```html
<!doctype html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport"
        content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>Document</title>
  <style>
    li:nth-child(-2n+4){             /*找4之前的2n项*/
      background-color: darkmagenta;
    }
  </style>
</head>
<body>
<ul>
  <li>li1</li>
  <li>li2</li>
  <li>li3</li>
  <li>li4</li>
</ul>
</body>
</html>

```





实例：

```html
<!doctype html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport"
        content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>Document</title>
  <style>
    li:first-child{
      background-color: gray;							/*第一个li元素 */
    }
    li:nth-child(3){
      background-color: darkmagenta;
    }												/*第3个li元素 */
    li:last-child{
      background-color: blue;						/*最后一个li元素 */
    }
  </style>
</head>
<body>
<ul>
  <li>li1</li>
  <li>li2</li>
  <li>li3</li>						
  <li>li4</li>
</ul>
</body>
</html>

```



#### 伪元素选择器

作用：创建虚拟元素（伪元素），用来摆放装饰性内容

|  选择器   |            说明             |
| :-------: | :-------------------------: |
| E::before | 在E元素里面最前面添加伪元素 |
| E::after  |  在E元素里面最后添加伪元素  |



> [!WARNING]
>
> 必须设置content：“”属性，用来设置伪元素的内容，如果没有内容，则引号留空
>
> 伪元素默认是行内显示模式
>
> 权重和标签选择器相同















### css创建

#### 插入样式表

##### 外部样式表

用`link`标签链接样式表，写在头部标签内

用法：

<link rel="表样式"  type="文件类型"  href="链接资源地址">



##### 内部样式表

在头部标签内写，用`<style>css样式</style>`标签包裹



实例：

```css
<head>
<style>
p{color:red;}
body{background-image:url("images/back40.gif");}
</style>
</head>
```



##### 内联样式

直接在标签内写css样式

用法：

<标签名  style=“css样式”>文本内容</标签>



实例：

```css
<p style="color:red;margin-left:20px">段落内容</p>
```



### css背景

#### 颜色

> #### background-color

实例：

```css
body{background-color:red;}
```



#### 图像

> #### background-image

实例：

```css
body {background-image:url('图片路径');}
```



#### 图像-水平或垂直平铺或不平铺

> #### background-repeat

实例：

```css
body{
    background-image:url('图片路径');
    background-repeat: repeat-y;  /*垂直平铺*/
    background-repeat: repeat-x;  /*水平平铺*/
    background-repeat: no-repeat;  /*不平铺*/
}
```



#### 设置图片大小

> background-size



关键字

cover：等比例缩放背景图片以完全覆盖背景区，可能图片部分看不见

contain：等比例缩放背景图片以完全装入背景区，可能部分区域为空白



百分比：根据盒子尺寸计算图片大小



数字+单位（如：px，rem等）



#### 伴随页面滚动或固定

> #### background-attachment

作用：背景不会随元素的内容滚动

background-attachment:fixed;





#### 改变图像在背景的位置

> #### background-position

background-position：x轴坐标  y轴坐标；



关键字

|  位置  | 描述 |
| :----: | :--: |
| right  | 右边 |
|  left  | 左边 |
| bottom | 底部 |
|  top   | 顶部 |
| center | 居中 |



实例：

```css
background-position:12px 23px;
/*也可以是位置参数*/
background-position:right bottom;   /*右下方*/
```



> [!NOTE]
>
> 关键字取值方法，可以颠倒顺序
>
> 只写一个关键字，另一个方向默认居中，数字只写一个值表示水平方向，垂直方向居中



#### 背景-复合属性（简写）

实例：

```css
body {background:#ffffff url('img_tree.png') no-repeat right top;}
```



### 显示模式

标签（元素）的显示方式

作用：布局网页的时候，根据标签的显示模式选择合适的标签摆放内容



#### 块级元素

独占一行

宽度默认是父级的100%

添加宽高属性不生效

#### 行内元素

一行可以显示多个

设置宽高属性不生效

宽高尺寸由内容撑开

#### 行内块元素

一行可以显示多个

设置宽高属性生效

宽高尺寸也可以由内容撑开



#### 转换显示模式

属性名：display

用法：display:属性值；

| 属性值       | 效果   |
| ------------ | ------ |
| block        | 块级   |
| inline-block | 行内块 |
| inline       | 行内   |



### css文字属性

|      属性       |         描述         |
| :-------------: | :------------------: |
|    font-size    | 字体大小（要有单位） |
|   font-weight   |       字体粗细       |
|   font-style    |       字体倾斜       |
|   line-height   |         行高         |
|   font-family   |        字体族        |
|      font       |     字体复合属性     |
|   text-indent   |       文本缩进       |
|   text-align    |       文本对齐       |
| text-decoration |        修饰线        |
|      color      |         颜色         |



### css三大特性

#### 继承性

子级默认继承父级的文字控制属性，若标签有默认样式将不继承



#### 层叠性

相同的属性会覆盖：后面的css属性覆盖前面的css属性

不同的属性会叠加：不同的css属性都会生效



#### 优先级

也叫权重，当一个标签使用了多种选择器时，基于不同种类的选择器的匹配原则

规则（标签范围越大优先级越小）：

通配符选择器<标签选择器<类选择器<id选择器<行内样式<!important



##### 优先级-叠加计算规则

叠加计算：如果是复合选择器，则需要权重叠加计算

规则：

（行内样式，id选择器个数，类选择器个数，标签选择器个数）

- 从左向右依次比较选个数，同级个数多的优先级高，相同就向后继续比
- !important权重最高
- 继承权重最低



### Emmet写法

以下都在写完，光标移到该段最后，再用tab键补全，不然会用问题

> 类选择器

标签名.类名



> id选择器

标签名#id名



> 同级标签

标签名+标签名



> 父子级标签

标签名>标签名



> 多个相同标签

标签名*个数



> 有内容的标签

标签{内容}



### Pxcook软件

开发模式智能识别

导入UI能够查看画面尺寸大小，颜色，边距等



### 盒子模型

重要部分：

内容区域-width&height

外边距-padding（出现在内容于盒子边缘之间）

边框线-border

外边距-margin（出现在盒子外面）



#### 边框线

属性名：border

属性值：边框线粗细  线条样式  颜色（不区分顺序）

常用线条样式

| 属性值 | 线条样式 |
| :----: | :------: |
| solid  |   实线   |
| dashed |   虚线   |
| dotted |   点线   |



实例：

```css
<!doctype html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport"
        content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>Document</title>
  <style>
    div{
      width: 3rem;
      height: 3rem;
      background-color: peachpuff;
      border: 1px solid black;        /*实线边框，1像素 黑色*/
    }
  </style>
</head>
<body>
<div>
  你好！
</div>
</body>
</html>
```



#### 单向边框线

border-top   上

border-bottom   下

border-right   右										/*属性值与上方相同*/

border-left    左

 

#### 内边距

padding：大小值+单位

padding-方位词，单独设置某一方向大小



> 多值写法

| 取值个数 | 含义                               |
| -------- | ---------------------------------- |
| 一个值   | 四个方向均为相同值                 |
| 两个值   | 前面为上下的值，后面为左右         |
| 三个值   | 前面为上的值，中间为左右，后面为下 |
| 四个值   | 从左向右，上右下左（顺序取值）     |



#### 外边距

margin：大小值+单位

margin-方位词，单独设置某一方向大小



#### 尺寸计算

默认情况

盒子尺寸=内容尺寸+border尺寸+内边距尺寸

给盒子加border/padding会撑大盒子

解决：

手动减法，减掉border/padding的尺寸

内减模式：box-sizing：border-box



#### 版心居中

margin： 上下    左右：auto；

要求：宽度要有值



#### 清除默认样式

去掉列表的项目符号

list-style：none；



```css
*{
margin:0;
padding:0;					/* *号代表全部*/
box-sizing:border-box;
}
```



#### 元素溢出

作用：控制溢出元素的内容的显示方式

属性名：overflow

| 属性值 | 效果                                       |
| ------ | ------------------------------------------ |
| hidden | 溢出隐藏                                   |
| scroll | 溢出滚动（无论是否溢出，都显示滚动条位置） |
| auto   | 溢出滚动（溢出才显示滚动条位置）           |



#### 外边距-合并现象

场景：垂直排列的兄弟元素，上下margin会合并

现象：取两个margin中的较大值生效



#### 外边距-塌陷问题

场景：父子级标签，子级的添加上外边距会产生塌陷问题

现象：导致父级一起向下移动



解决方法：

- 取消子级margin，父级设置padding
- 父级设置overflow：hidden
- 父级设置border-top



#### 行内元素-内外边距问题

场景：行内元素添加margin和padding，无法改变元素垂直位置

解决方法：给行内元素加line-height可以改变垂直位置



#### 圆角效果

作用：设置元素的外边框为圆角

属性名：border-radius

属性值：数字+单位/百分比

四值：从`左上角`开始，顺时针赋值

三值：左上  右上+左下   右下

两值：左上+右下   右上+左下



#### 阴影效果

作用：元素设置阴影效果

属性名：box-shadow

属性值：x轴偏移量  y轴偏移量  模糊半径  扩散半径  颜色  内外阴影



### 浮动

作用：让块元素水平排列

属性名：`float`

属性值

`left`：左对齐

`right`：右对齐



#### 清除浮动

场景：浮动元素会脱标，如果父级没有高度，子级无法撑开父级高度（可能导致页面布局错乱）

解决方法：清除浮动（清除浮动带来的影响）

方法一：额外标签法

在父级内容的最后添加一个块级元素，设置长沙市、属性clear：both

方法二：单伪元素法

```css
.clearfix::after{
	content="";
	display:block;
	clear:both;
}
```

方法三：双伪元素法（`推荐`）

```css
.clearfix::before,
.clearfix::after{
    content:"";
    display:table;
}
.clearfix::after{
    clear:both;
}
```

方法四：

父元素添加css属性overflow:hidden



### flex布局

设置方式：给父元素设置display:flex，子元素可以自动挤压或拉伸

组成部分：

弹性容器

弹性盒子

主轴：默认在水平方向

侧轴/交叉轴：默认在垂直方向



#### 主轴对其方式

属性名：justify-content（水平）

| 属性值        | 效果                               |
| ------------- | ---------------------------------- |
| flex-start    | 默认值，弹性盒子从起点开始依次排列 |
| flex-end      | 弹性盒子从终点开始依次排列         |
| center        | 弹性盒子沿主轴居中排列             |
| space-between | 弹性盒子沿主轴均匀排列，           |
| space-around  |                                    |
| space-evenly  |                                    |



align-items（垂直）









### css动画

#### 3D转换

##### rotateX（）方法

围绕其中一个给定度数x轴旋转的元素



##### rotateX（）方法

围绕其中一个给定度数y轴旋转的元素



##### 转换属性

| 属性                | 描述                             |
| ------------------- | -------------------------------- |
| transform           | 向元素应用2D或3D转换             |
| transform-origin    | 允许你改变被转换元素的位置       |
| transform-style     | 规定被嵌套元素如何在3D空间中显示 |
| perspective         | 规定3D元素的透视效果             |
| perspective-origin  | 规定3D元素的底部位置             |
| backface-visibility | 定义元素在不面对屏幕时是否可见   |



3D转换方法

| 函数                                                         | 描述                                      |
| :----------------------------------------------------------- | :---------------------------------------- |
| matrix3d(*n*,*n*,*n*,*n*,*n*,*n*, *n*,*n*,*n*,*n*,*n*,*n*,*n*,*n*,*n*,*n*) | 定义 3D 转换，使用 16 个值的 4x4 矩阵。   |
| translate3d(*x*,*y*,*z*)                                     | 定义 3D 转化。                            |
| translateX(*x*)                                              | 定义 3D 转化，仅使用用于 X 轴的值。       |
| translateY(*y*)                                              | 定义 3D 转化，仅使用用于 Y 轴的值。       |
| translateZ(*z*)                                              | 定义 3D 转化，仅使用用于 Z 轴的值。       |
| scale3d(*x*,*y*,*z*)                                         | 定义 3D 缩放转换。                        |
| scaleX(*x*)                                                  | 定义 3D 缩放转换，通过给定一个 X 轴的值。 |
| scaleY(*y*)                                                  | 定义 3D 缩放转换，通过给定一个 Y 轴的值。 |
| scaleZ(*z*)                                                  | 定义 3D 缩放转换，通过给定一个 Z 轴的值。 |
| rotate3d(*x*,*y*,*z*,*angle*)                                | 定义 3D 旋转。                            |
| rotateX(*angle*)                                             | 定义沿 X 轴的 3D 旋转。                   |
| rotateY(*angle*)                                             | 定义沿 Y 轴的 3D 旋转。                   |
| rotateZ(*angle*)                                             | 定义沿 Z 轴的 3D 旋转。                   |
| perspective(*n*)                                             | 定义 3D 转换元素的透视视图。              |



#### 转换过渡

过渡属性

| 属性                                                         | 描述                                         |
| :----------------------------------------------------------- | :------------------------------------------- |
| [transition](https://www.runoob.com/cssref/css3-pr-transition.html) | 简写属性，用于在一个属性中设置四个过渡属性。 |
| [transition-property](https://www.runoob.com/cssref/css3-pr-transition-property.html) | 规定应用过渡的 CSS 属性的名称。              |
| [transition-duration](https://www.runoob.com/cssref/css3-pr-transition-duration.html) | 定义过渡效果花费的时间。默认是 0。           |
| [transition-timing-function](https://www.runoob.com/cssref/css3-pr-transition-timing-function.html) | 规定过渡效果的时间曲线。默认是 "ease"。      |
| [transition-delay](https://www.runoob.com/cssref/css3-pr-transition-delay.html) | 规定过渡效果何时开始。默认是 0。             |



#### 3D动画

| 属性                                                         | 描述                                                         |
| :----------------------------------------------------------- | :----------------------------------------------------------- |
| [@keyframes](https://www.runoob.com/cssref/css3-pr-animation-keyframes.html) | 规定动画。                                                   |
| [animation](https://www.runoob.com/cssref/css3-pr-animation.html) | 所有动画属性的简写属性。                                     |
| [animation-name](https://www.runoob.com/cssref/css3-pr-animation-name.html) | 规定 @keyframes 动画的名称。                                 |
| [animation-duration](https://www.runoob.com/cssref/css3-pr-animation-duration.html) | 规定动画完成一个周期所花费的秒或毫秒。默认是 0。             |
| [animation-timing-function](https://www.runoob.com/cssref/css3-pr-animation-timing-function.html) | 规定动画的速度曲线。默认是 "ease"。                          |
| [animation-fill-mode](https://www.runoob.com/cssref/css3-pr-animation-fill-mode.html) | 规定当动画不播放时（当动画完成时，或当动画有一个延迟未开始播放时），要应用到元素的样式。 |
| [animation-delay](https://www.runoob.com/cssref/css3-pr-animation-delay.html) | 规定动画何时开始。默认是 0。                                 |
| [animation-iteration-count](https://www.runoob.com/cssref/css3-pr-animation-iteration-count.html) | 规定动画被播放的次数。默认是 1。                             |
| [animation-direction](https://www.runoob.com/cssref/css3-pr-animation-direction.html) | 规定动画是否在下一周期逆向地播放。默认是 "normal"。          |
| [animation-play-state](https://www.runoob.com/cssref/css3-pr-animation-play-state.html) | 规定动画是否正在运行或暂停。默认是 "running"。               |



#### 可见元素裁剪

clip-path:inset(上裁剪距离 右裁剪 下裁剪 左裁剪)；

| 取值类型       | 示例                         | 说明                                                         |
| -------------- | ---------------------------- | ------------------------------------------------------------ |
| 长度值（px）   | `inset(10px 20px 10px 20px)` | 从上下各裁 10px，左右各裁 20px（固定像素距离）               |
| 百分比（%）    | `inset(5% 10% 5% 10%)`       | 从上下各裁元素高度的 5%，左右各裁元素宽度的 10%（相对元素尺寸，推荐用） |
| 关键字（auto） | `inset(auto 20px auto 20px)` | `auto` 表示 “不裁剪”（此处上下不裁，左右各裁 20px）          |





#### 实例

```css
<!doctype html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport"
          content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        .line-scan{
            margin: 10px auto;    /*设置显示位置*/
            width: 500px;			/*设置长度和粗细*/
            height: 2px;
            transform-origin: left center;
            animation:scan 3.5s ease forwards;
            animation-delay: 1s;
        }
        @keyframes scan {
            0%{
                transform: scaleX(0);
                background: linear-gradient(90deg,#853c4a,#99505e);
                opacity: 0;
            }
            100%{
                transform: scaleX(1);
                background: linear-gradient(90deg,#853c4a,#99505e);
                opacity: 1;
            }
        }
    </style>
</head>
<body>
<div class="line-scan"></div>
</body>
</html>
```



### svg矢量图

SVG 专用样式属性，替代普通 CSS 的`color`/`background`：

|    SVG 属性    |         作用         |    对应 CSS 写法     |
| :------------: | :------------------: | :------------------: |
|     `fill`     | 填充颜色（图形内部） |    `fill: coral;`    |
|    `stroke`    |   描边颜色（轮廓）   |   `stroke: #333;`    |
| `stroke-width` |       描边粗细       | `stroke-width: 2px;` |
|   `opacity`    |        透明度        |   `opacity: 0.8;`    |



#### 内联式（推荐）

```html
<svg class="icon-svg" width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
  <circle cx="12" cy="12" r="10" stroke="coral" stroke-width="2"/>
</svg>
```



## javascript

关键字

|   break    |  do   |   if    |  switch  | typeof  | case  |   with   |
| :--------: | :---: | :-----: | :------: | :-----: | :---: | :------: |
|    else    |  in   |  this   |   var    |  catch  | false |  delete  |
| instanceof | throw |  void   | continue | finally |  new  | function |
|    true    | while | default |   for    |  null   |  try  |  return  |



### 注解

单行注释：//

多行注释：/**/



### 运算符

#### 算术运算符

> `+`，`-`，`*`，`/`，`%`，`++`，`--`



#### 赋值运算符

> `=`



#### 比较运算符

> `>`，`<`，`>=`，`<=`，`==`，`!=`



#### 逻辑运算符

> `&&`，`||`，`!`





### 输入和输出

#### 输出

`document.write`(“内容”)

作用：向body内输出内容



`alert`（“内容”)

作用：弹出警示框



console.log(‘控制台打印’)

作用：控制台输出



#### 输入

`prompt`(“输入内容”)

作用显示一个对话框，让用户输入



### 字面量

字面量在计算机里描述事/物





### 基础

#### 变量

用`let`声明变量

用法：let 变量名



#### 数组

let 数组名=[数据1，数据2，...]

访问用下标，下标从0开始



> length

获取数组长度

用法：数组名.length



#### 常量

一旦定义无法改变，声明时必须赋值

`const` 常量名=常量



### 数据类型

**基本数据类型**

#### number数字型

数学中的所有数字，整数，小数，正数，负数等



#### string字符串型

用双引号，单引号或反引号引起来的都是字符串



##### 字符串拼接

`+`能将两个字符串连接起来



##### 模板字符串

只能使用`反引号`

内容拼接时用`${}`包裹变量



#### boolean布尔型

只有`true`和`false`两个值

‘’,0,undefined,null,false,NaN转换为布尔值都是false，其余则为true



#### undefined未定义型

未定义是比较特殊的类型，只有一个值undefined

一个变量只声明不赋值，默认值为undefined



#### null空类型

代表无，空

**引用数据类型**

#### object对象



> [!NOTE]
>
> typeof能够检查数据的类型
>
> typeof 数据 或 typeof(数据)



#### 类型转换

表单输入的默认为字符串



##### 显式转换

用法：数据类型（要转换的数据）

只保留整数：parseInt（数据）

可保留小数：parseFloat（数据）



##### 隐式转换



### 语句

#### 分支语句

##### if语句

条件满足执行条件后面的语句

> 单分支if

```javascript
if(条件){代码块}
```



> 多分支if

```javascript
if(条件){
    代码块
}else if(条件){
    代码块
}else{代码块}
```



##### switch语句

有符号条件的执行case后面的代码，没有就执行default

```javascript
switch(数据){
        case 值1：
        代码块;
        break;
        case 值2：
        代码块;
        break;
        
        .....
        
	    default:
        代码块;
        break;
}
```



##### 三元运算符

用法：条件？满足执行的代码：不满足执行的代码



#### 循环语句

需要有结束条件，否则该循环为死循环

##### while循环

```javascript
while(条件){
    代码块
}
```



##### for循环

常用于变量数组等

```javascript
for(变量起始值;终止条件;变量变化量){
    代码块
}
```



##### 退出循环

`continue`退出当前循环，继续进行后续循环

`break`退出整个循环



##### 循环嵌套

```javascript
for(条件){
    for(条件)}{
        代码块
    }
}
```



实例：

```javascript
for(let i=0;i<4;i++){
    for(let j=0;j<4;j++){
        document.write("*");
    }
    document.write('<br>')
}
/*
打印
****
****
****
****
*/
```



### 数组

数组可以存储任意类型数据

声明数组：

let 数组名=[数据1，数据2，...]

遍历数组从0索引开始



#### 数组增删改查

> 增加数据

数组.push（元素1，元素2，...）

将一个或多个元素放在数组末尾



数组.unshift（元素1，元素2，...）

将一个或多个元素放在数组开头



> 删除数据

数组.pop()

删除数组最后面的一个元素



数组.shfit()

删除数组最前面的一个元素



数组.splice(起始位置，删除几个元素)      //起始位为数组下标，若不写删除几个元素，则删除到最后

删除指定元素



> 修改数据

用数组下标修改数据

用法：

数组[下标]=新值



> 查询数据

使用下标访问



### 函数

#### 定义

> 函数声明

```js
function 函数名(){函数体}
```

调用：

```js
函数名()
```



> 函数传参

```js
function 函数名(参数1，参数2，...){函数体}
```

调用：

```js
函数名(参数，参数2，...){函数体}
```



> 默认参数

在调用函数时没有接收参数，就使用默认值，收到就覆盖默认值

```js
function 函数名(参数1=参数值，参数2=参数值，...){函数体}
```



> 函数返回值

```js
function 函数名(参数1，参数2，...){
    函数体
	return 返回值
}
```

调用时接收

```js
let 变量名=函数名(参数1，参数2，...)
```



#### 作用域

> 局部

```js
function 函数名(参数1，参数2，...){
    let num=0;        /*局部变量，在该function外不可用*/
    函数体
	return 返回值
}
```



> 全局

```js
let count=1;      /*全局变量，下面的函数可调用*/
function 函数名(参数1，参数2，...){
    let num=0;        /*局部变量，在该function外不可用*/
    函数体
	return 返回值
}
```



> [!NOTE]
>
> 如果局部和全局中声明了相同的变量，函数内调用就近原则



#### 匿名函数

没有名字，无法直接使用



> 函数表达式

将匿名函数赋值给一个变量，通过变量进行调用

声明：

```js
let 变量名=function (){函数体}
```

调用：

```js
变量名()
```



> 立即执行函数

```js
//方式1
(function (){函数体})();

//方式2
(function (){函数体}());
```



> [!CAUTION]
>
> 立即执行函数必须分号结束，不让两函数会相互影响



#### 逻辑中断

短路：只存在于&&和||中，当满足一定条件会让右边的代码不执行



### 对象

对象（object）：JavaScript中的一种数据类型



声明

```js
let 对象名={属性1：属性值，属性2：属性值，...}
```



#### 对象增删改查

> 查

对象名.属性



> 删



> 改

对象名.属性=新值





### DOM

#### 动态创建HTML元素

document.createElement(参数)

参数为要创建的元素标签

返回值为元素对象，可设置属性，内容或添加到页面中



##### 设置元素属性/内容

> 设置类

元素对象.className=“类名”



> 设置id

元素对象.id=“id属性”



> 设置文本内容

元素对象.textContent=“文本”



> 设置样式

元素对象.style.属性=“属性值”



> 按键监听

元素对象.addEventListener(事件类型，事件触发执行的回调函数)



事件类型：

`click`：鼠标左键点击

`contextmenu`：鼠标右键点击

`mouseover`：鼠标悬停

`keydown`：按键按下

`load`：页面加载完成



> 将创建的元素加入页面

document.body.appendChild(元素对象)



#### 获取窗口参数

##### 获取物理屏幕尺寸（`screen` 对象）

screen.width

screen.height



##### 获取浏览器视口尺寸（可见区域）

window.innerWidth

window.innerHeight



##### 获取网页文档总尺寸（完整页面大小）

获取**整个 HTML 文档的实际宽高**（包含滚动隐藏区域），是页面真实大小：

document.documentElement.scrollWidth

document.documentElement.clientWidth





#### innerHTML

设置元素或获取元素内部的HTML内容

它允许通过字符串形式直接操作元素的内部结构，是动态修改页面内容的常用方法



> 读取元素内部的html内容

const 命名=元素属性.innerHTML



> 覆盖原来的内容

元素属性.innerHTML=‘新的HTML字符串’



实例：

```js
container.innerHTML = '<h1>新标题</h1><p>这是动态添加的内容</p>';
```



> `+=`：追加HTML内容

用法：

元素属性.innerHTML+=‘新的HTML字符串’



#### querySelector

从DOM中查询并返回第一个匹配指定css选择器的方法，属于API



用法：

const 命名=document.querySelector(css选择器)

返回值：匹配到的第一个元素节点（htmlElement对象）；没有匹配项，返回null



#### offsetWidth

尺寸样式发生变化时，会自动更新

用于精确获取元素的布局宽度，是前端布局计算、动态定位等场景的核心属性



> 计算方式

offsetWidth=内容宽度（content）+左右内边距（padding）+左右边框（border）



#### offsetHeight

> 计算方式

offsetHeight=内容宽度（content）+上下内边距（padding）+上下边框（border）



#### setInterval

用于周期性重复执行某个函数或代码片段的**定时器函数**



用法：

const 命名=setInterval（callback，delay[，arg1，arg2，...]）

参数说明：

callback（必要）：每次间隔后要执行的函数或代码片段（不推荐字符串形式）

delay（必要）：每次执行的时间间隔，默认最小延迟约4ms（受浏览器限制）	

arg（可选）：给callback函数传参（IE9及以下不支持）



返回值：一个非零的整数intervalID（定时器标识），用于通过clearInterval取消定时器



#### clearInterval

终止由setInterval创建的周期性定时器的函数，与setInterval配合使用，是管理定时器生命周期的核心方法



用法：

clearInterval（intervalID）

参数说明：

intervalID（必要）：由setInterval返回的定时器标识（一个非零整数），用于指定要取消的定时器









### API

#### canvas图形绘制

用法：

```html
<canvas id="" width="宽度" height="高度	"></canvas>
```



##### context获取上下文

```js
const 命名=getContextId("");  //找到绘画位置
const 命名=canvas.getContext("2d"); //创建canvas对象
```



`getContext('2d')` 返回一个 **CanvasRenderingContext2D** 对象，它提供了所有的绘图方法



##### 位置坐标

对象.fillRect（x轴，y轴，图像宽，图像高）



##### 路径（绘制线条）

闭合开始绘制路径：对象.beginPath()    //不闭合两次绘制会受影响

闭合结束绘制路径：对象.closePath()



开始位置：对象.moveTo（x，y）

结束位置：对象.lineTo（x，y）

路径显示(必要)：对象.stroke()



##### 绘制圆形

绘方向默认为：顺时针

用法：

```js
arc(x,y,r,start,stop)
```

x，y：圆心x，y轴

r：半径

start：圆弧起始角度，以弧度为单位

stop：圆弧结束角度，以弧度为单位

弧度=角度（直接写数字）*Math.PI/180



> [!NOTE]
>
> 圆弧开始/结束路径连接圆心，用moveTo



##### 文本

> font定义字体

对象.font=“”



> 绘制实心文本

fillText(text,x,y)



> 绘制空心文本

strokeText(text,x,y)



##### 渐变

> 线条渐变

createLinearGradient(起x,起y,终x1,终y1)



> 径向/圆渐变

createRadialGradient(起x,起y,起r,终x1,终y1,终r1)



> 添加颜色停止点，设置两次一个起点，一个终点

addColorStop(offset,color)

说明：

offset：一个0~1.0之间的数，表示颜色在渐变线上的位置

color：颜色用16进制表示颜色



##### 图像

绘画的可以是img标签，也可以new Image()一个对象



设置图像源：图片对象.src=‘路径’



等待图像加载完毕再开始绘制：图片对象.onload

drawImage(image,x,y)



在onload回调函数中绘制图像，不然图像未加载完成就开始绘制，将绘制失败



实例：

```js
图片对象.onload=function (){
    2d对象.drawImage(图片对象,x,y)   //x,y为图片左上角在画布中的位置
}
```



> 缩放绘制

```js
2d对象.drawImage(image,x,y,dwidth,dheight)   //dwith，dheight为缩放到画布上的宽度，长度
```



> 切片绘制(Sprite动画常用)

```js
2d对象.drawImage(image,sx,sy,swidth,sheight,dx,dy,dwidth,dheight)
```

sx,sy/dx,dy：截取起始/结束坐标

swidth,sheight：截取的宽高

dwith，dheight：缩放到画布上的宽度，长度



> 图像变形

- 将坐标系原点移动到画布中心

​	2d对象.translate(canvas.width/2,canvas.height/2)

- 旋转45度（需要转换为弧度）

​	2d对象.rotate(Math.PI/4)

- 缩放

​	2d对象.scale(width,height)



2d对象.restore()：恢复到保存之前的状态
