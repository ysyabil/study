## 一、响应式布局

### 1、响应式布局是什么

![01](.\img\01.jpg)

​	伊桑·马科特（Ethan Marcotte）在2010年首先提出了响应式网页设计（RWD,Responsive Web Design）这个术语。在他的一篇文章《Responsive Web Design · An A List Apart Article》中他将已有的三种发开技巧（弹性图片，弹性网格布局，媒体与媒体查询） 进行了整合，命名为响应式网页设计。

所谓响应式页面，是指一套页面，能够适配多种终端，比如宽屏pc电脑，平板，手机，听起来极为的棒，但是，响应式布局极容易出现各式各样的兼容问题，目前社会主流布局方案依然是单独制作移动端页面，所以对响应式，只要抱着能看懂，能做出简单的网页布局即可。

### 2、viewport视口

#### 2.1、什么是viewport

+ viewport 是用户网页的可视区域。
+ viewport 翻译为中文可以叫做"视区"。
+ 手机浏览器是把页面放在一个虚拟的"窗口"（viewport）中，通常这个虚拟的"窗口"（viewport）比屏幕宽，这样就不用把每个网页挤到很小的窗口中（这样会破坏没有针对手机浏览器优化的网页的布局），用户可以通过平移和缩放来看网页的不同部分。

#### 2.2、设置viewport

> 前提：
>
> 由于历史原因，移动端的浏览器为了让没有做移动适配的网页显示更友好，默认会把浏览器视口宽度缩放为 `980px`, 不论屏幕宽度是多少。
>
> 移动端浏览器的默认缩放行为，会让网页缩小； 如果想要做针对移动端适配的网页就必须不要移动端默认缩放。

设置视口宽度与设备宽度保持一致：

```html
<meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1">
```

+ width：控制 viewport 的大小，可以指定的一个值，如果 600，或者特殊的值，如 device-width 为设备的宽度（单位为缩放为 100% 时的 CSS 的像素）。
+ height：和 width 相对应，指定高度。
+ initial-scale：初始缩放比例，也即是当页面第一次 load 的时候缩放比例。
+ maximum-scale：允许用户缩放到的最大比例。
+ minimum-scale：允许用户缩放到的最小比例。
+ user-scalable：用户是否可以手动缩放。

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>视口</title>
    <!-- 完美视口 -->
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
   <style>
        .box {
            margin: 0 auto;
            background-color: pink;
            width: 300px;
            height: 300px;
        };
    </style>
</head>
<body>
    <div class="box">
    </div>
</body>
</html>
```

### 3、媒体类型

| 值          | 描述                                  |
| ---------- | ----------------------------------- |
| all        | 用于所有设备                              |
| screen     | 用于电脑屏幕，平板电脑，智能手机等。                  |
| print      | 用于打印机和打印预览                          |
| speech     | 应用于屏幕阅读器等发声设备                       |
| aural      | 已废弃。用于语音和声音合成器                      |
| braille    | 已废弃。 应用于盲文触摸式反馈设备                   |
| embossed   | 已废弃。 用于打印的盲人印刷设备                    |
| handheld   | 已废弃。 用于掌上设备或更小的装置，如PDA和小型电话         |
| projection | 已废弃。 用于投影设备                         |
| tty        | 已废弃。 用于固定的字符网格，如电报、终端设备和对字符有限制的便携设备 |
| tv         | 已废弃。 用于电视和网络电视                      |

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        body {
            background-color: #333;
        }
        h1 {
            text-align: center;
            color: #fff;
            font-size: 200px;
        }

        /* 单独设置打印机的样式 */
        @media print {
            body {
                background-color: red;
            }
            h1 {
                font-size: 50px;
            }
        }
    </style>
</head>
<body>
    <h1>媒体类型</h1>
</body>
</html>
```

### 4、媒体特性

| 值                       | 描述                                       |
| ----------------------- | ---------------------------------------- |
| aspect-ratio            | 定义输出设备中的页面可见区域宽度与高度的比率                   |
| color                   | 定义输出设备每一组彩色原件的个数。如果不是彩色设备，则值等于0          |
| color-index             | 定义在输出设备的彩色查询表中的条目数。如果没有使用彩色查询表，则值等于0     |
| device-aspect-ratio     | 定义输出设备的屏幕可见宽度与高度的比率。                     |
| device-height           | 定义输出设备的屏幕可见高度。                           |
| **device-width**        | 定义输出设备的屏幕可见宽度。                           |
| grid                    | 用来查询输出设备是否使用栅格或点阵。                       |
| height                  | 定义输出设备中的页面可见区域高度。                        |
| max-aspect-ratio        | 定义输出设备的屏幕可见宽度与高度的最大比率。                   |
| max-color               | 定义输出设备每一组彩色原件的最大个数。                      |
| max-color-index         | 定义在输出设备的彩色查询表中的最大条目数。                    |
| max-device-aspect-ratio | 定义输出设备的屏幕可见宽度与高度的最大比率。                   |
| max-device-height       | 定义输出设备的屏幕可见的最大高度。                        |
| **max-device-width**    | 定义输出设备的屏幕最大可见宽度。                         |
| max-height              | 定义输出设备中的页面最大可见区域高度。                      |
| max-monochrome          | 定义在一个单色框架缓冲区中每像素包含的最大单色原件个数。             |
| max-resolution          | 定义设备的最大分辨率。                              |
| **max-width**           | 定义输出设备中的页面最大可见区域宽度。                      |
| min-aspect-ratio        | 定义输出设备中的页面可见区域宽度与高度的最小比率。                |
| min-color               | 定义输出设备每一组彩色原件的最小个数。                      |
| min-color-index         | 定义在输出设备的彩色查询表中的最小条目数。                    |
| min-device-aspect-ratio | 定义输出设备的屏幕可见宽度与高度的最小比率。                   |
| **min-device-width**    | 定义输出设备的屏幕最小可见宽度。                         |
| min-device-height       | 定义输出设备的屏幕的最小可见高度。                        |
| min-height              | 定义输出设备中的页面最小可见区域高度。                      |
| min-monochrome          | 定义在一个单色框架缓冲区中每像素包含的最小单色原件个数              |
| min-resolution          | 定义设备的最小分辨率。                              |
| **min-width**           | 定义输出设备中的页面最小可见区域宽度。                      |
| monochrome              | 定义在一个单色框架缓冲区中每像素包含的单色原件个数。如果不是单色设备，则值等于0 |
| orientation             | 定义输出设备中的页面可见区域高度是否大于或等于宽度。               |
| resolution              | 定义设备的分辨率。如：96dpi, 300dpi, 118dpcm        |
| scan                    | 定义电视类设备的扫描工序。                            |
| **width**               | 定义输出设备中的页面可见区域宽度。                        |

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        body {
            background-color: #333;
        }
        h1 {
            text-align: center;
            color: #fff;
        }

        /* 视口宽度 当视口宽度是 800px 的时候*/
        @media (width: 800px) {
            body {
                background-color: red;
            }
        }

        /* 最大视口宽度  生效条件：视口宽度 <= 600px */
        @media (max-width: 600px) {
            body {
                background-color: green;
            }
            h1 {
                color: orange;
            }
        }

        /* 最小视口宽度  视口宽度 >= 1000px */
        @media (min-width: 1000px) {
            body {
                background-color: pink;
            }
            h1 {
                color: cyan;
            }
        }

        @media (min-width: 1100px) {
            body {
                background-color: purple;
            }
        }

        @media (device-width: 375px) {
            h1 {
                font-size: 200px;
            }
        }
    </style>
</head>
<body>
    <h1>媒体特性 视口宽度</h1>
</body>
</html>
```

### 5、媒体查询运算符

- `and` 并且
- `,` 或者
- `not` 否定 一定要指定媒体类型，因为媒体类型默认all，not后永远返回假
- `only` only + 媒体类型

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        body {
            background-color: #333;
        }
        h1 {
            text-align: center;
            color: #fff;
        }

        /* 视口宽度在 400px 到 500px 之间 */
        @media (min-width: 400px) and (max-width: 500px) {
            body {
                background-color: #f90;
            }
        }
        
        /* 视口宽度小于等于 200px 或 大于等于 1000px */
        @media (max-width: 200px), (min-width: 1000px) {
            body {
                background-color: skyblue;
            }
        }

        /* not  不是屏幕*/
        @media not screen {
            h1 {
                color: red;
            }
        }

        /* only */
        @media only screen {
            h1 {
                color: purple;
            }
        }

        @media only screen and (min-width: 768px) {
            
        }

    </style>
</head>
<body>
    <h1>媒体查询的运算符</h1>
</body>
</html>
```

### 6、媒体查询用法

#### 6.1、用法一

媒体查询由一种媒体类型组成，并可包含一个或多个表达式，这些表达式可以解析为 true 或 false。

```css
@media not|only mediatype and (expressions) {
  CSS-Code;
}
```

如果指定的媒体类型与正在显示文档的设备类型匹配，并且媒体查询中的所有表达式均为 true，则查询结果为 true。当媒体查询为 true 时，将应用相应的样式表或样式规则，并遵循正常的级联规则。

#### 6.2、方法二

可以针对不同的媒体使用不同的样式表

```css
<link rel="stylesheet" media="mediatype and|not|only (expressions)" href="print.css">
```

### 7、阈值设置

#### 7.1、设置一

两个断点： 640px 1024px

- 小屏幕 <=640px
- 中等屏幕 641px ~ 1024px
- 大屏幕 >1024px

#### 7.2、设置二

三个断点： 768px 992px 1200px

- 手机 超小屏幕 <= 768px
- 平板 小屏幕 769px ~ 992px
- 中等屏幕 993px ~ 1200px
- 大屏幕 > 1200px

#### 7.3、设置三

四个断点： 576px 768px 992px 1200px

- 超小屏幕 <=576px
- 小屏幕 577px ~ 768px
- 中等屏幕 769px ~ 992px
- 大屏幕 993px ~ 1200px
- 超大屏幕 >1200px

#### 7.4、案例练习

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>响应式设计</title>
    <style>
        /* 
            超小屏幕  container 宽 100%
            小屏幕： 750px
            中等屏幕： 970px;
            大屏幕： 1170px
         */

        * {
            margin: 0;
            padding: 0;
        }
        .container {
            margin: 0 auto;
            height: 200px;
            background-color: pink;

            /* 默认宽度 */
            width: 100%;
        }

        @media (min-width: 768px) {
            .container {
                width: 750px;
                background-color: red;
            }
        }

        @media (min-width: 992px) {
            .container {
                width: 970px;
                background-color: green;
            }
        }

        @media (min-width: 1200px) {
            .container {
                width: 1170px;
                background-color: yellow;
            }
        }

    </style>
</head>
<body>
    <div class="container"></div>
</body>
</html>
```

## 二、BFC

### 1、什么是BFC

**Block Formatting Context** 简称 **BFC**，中文翻译为 **块级格式上下文**。

#### 1.1、W3C 中对 BFC 的定义

Floats, absolutely positioned elements, block containers (such as inline-blocks, table-cells, and table-captions) that are not block boxes, and block boxes with 'overflow' other than 'visible' (except when that value has been propagated to the viewport) establish new block formatting contexts for their contents.

> **译文：**
>
> 浮动、绝对定位元素、不是块盒子的块容器(如inline-blocks、table-cells和table-captions)，以及`overflow`属性的值除`visible`以外的块盒(除非该值已传播到视口)，将为其内容建立新的块格式化上下文。

https://www.w3.org/TR/CSS22/visuren.html#block-formatting

#### 1.2、MDN 上对 BFC 的定义

A **block formatting context** is a part of a visual CSS rendering of a web page. It's the region in which the layout of block boxes occurs and in which floats interact with other elements.

> **译文：**
>
> **块格式化上下文（Block Formatting Context，BFC）** 是Web页面的可视CSS渲染的一部分，是块盒子的布局过程发生的区域，也是浮动元素与其他元素交互的区域。

https://developer.mozilla.org/en-US/docs/Web/Guide/CSS/Block_formatting_context

https://developer.mozilla.org/zh-CN/docs/Web/Guide/CSS/Block_formatting_context

#### 1.3、到底什么是 BFC

首先，BFC 的意思是 **Block Formatting Context** ，即**块级格式上下文**。 然后，当元素满足了某些条件，我们认为该元素创建了 **BFC**。 创建了 BFC 的元素我们可以把他看做是一个独立的容器，容器内的元素不论如何布局都不会影响到外面。

### 2、创建 BFC 的方式

+ 浮动元素：元素的float不是none的元素。
+ 绝对定位的元素：position的值为absolute或fixed。
+ 行内块：`display:inline-block`
+ 具有`overflow`并且值不是`visible`的块元素。
+ 伸缩项目
+ 多列容器
+ 根元素
+ `column-span` 为 `all` 的元素始终会创建一个新的BFC，即使该元素没有包裹在一个多列容器中。
+ 表格单元格（th、td）、表格行（tr）、表格标题（caption）、table、thead、tbody、tfoot。

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        body {
            /* display: flex;
            flex-direction: column; */
        }
        .wrapper {
            border: 2px dashed red;
            padding: 10px;

            /* 开启BFC */
            /* overflow: auto; */
            /* display: inline-block; */
            /* column-count: 1; */
            /* column-span: all; */
            /* position: absolute; */
        }
        .box {
            width: 100px;
            height: 100px;
            border: 2px solid green;

            float: left;
        }
    </style>
</head>
<body>
    <div class="wrapper">
        <div class="box box01">1</div>
        <div class="box box02">1</div>
        <div class="box box03">1</div>
        <div class="box box04">1</div>
    </div>

    <p style="width: 600px;">Lorem ipsum dolor sit amet consectetur adipisicing elit. Eligendi vel quae corrupti. Molestias, necessitatibus et consequuntur nam velit impedit expedita vel perferendis autem animi eligendi itaque quis, aperiam error dignissimos!</p>
</body>
</html>
```

### 3、创建 BFC 可以解决的问题

#### 3.1、清除子元素浮动的影响

```html
<!DOCTYPE html>
<html>
    <head>
        <style>
            #wrapper{
                width:200px;
                border:5px solid green;
                /* overflow:hidden; */
                display:flow-root;
            }
            #box{
                float:left;
                width:100px;
                height:100px;
                border:1px solid blue;
            }
        </style>
    </head>
    <body>
        <div id="wrapper">
            <div id="box"></div>
        </div>
    </body>
</html>
```

#### 3.2、解决外边距塌陷

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        .wrapper {
            
            background-color: #ccc;

            /* 创建 BFC */
            /* float: left; */
            /* position: absolute; */
            /* overflow: hidden; */
            /* column-count: 1; */
            overflow: auto;
        }
        .box {
            width: 100px;
            height: 100px;
            border: 2px solid green;
            margin: 30px;
        }
    </style>
</head>
<body>
    <div class="wrapper">
        <div class="box box01">1</div>
        <div class="box box02">1</div>
        <div class="box box03">1</div>
        <div class="box box04">1</div>
    </div>
</body>
</html>
```

## 三、蓝湖工具

**蓝湖官网：**https://lanhuapp.com/

### 1、安装

![l1](.\img\l1.png)

![l2](.\img\l2.png)

![l3](.\img\l3.png)

