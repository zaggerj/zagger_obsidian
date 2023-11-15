---
created: 2023-11-15T20:50
updated: 2023-11-15T20:50
---
# html html5

## html

## 语义化

## dom

## 2D 3D

## 本地存储

## svg

### stroke

- stroke-dasharray

	- 1. stroke意思是：画短线于，在...上划线
	- 2. stroke-dasharray:用于创建虚线，之所以后面跟的是array的，是因为值其实是数组。请看下面解释
	- stroke-dasharray = '10'
	- stroke-dasharray = '10, 5'
	- stroke-dasharray = '20, 10, 5'
	- 
	- stroke-dasharray为一个参数时： 其实是表示虚线长度和每段虚线之间的间距
	- 　　如：stroke-dasharray = '10' 表示：虚线长10，间距10，然后重复 虚线长10，间距10
	- 两个参数或者多个参数时：一个表示长度，一个表示间距
	- 　　如：stroke-dasharray = '10, 5' 表示：虚线长10，间距5，然后重复 虚线长10，间距5
	- 　　如：stroke-dasharray = '20, 10, 5' 表示：虚线长20，间距10，虚线长5，接着是间距20，虚线10，间距5，之后开始如此循环

- 3. stroke-dashoffset： offset：偏移的意思。

	- 这个属性是相对于起始点的偏移，正数偏移x值的时候，相当于往左移动了x个长度单位，负数偏移x的时候，相当于往右移动了x个长度单位。
	- 需要注意的是，不管偏移的方向是哪边，要记得dasharray 是循环的，也就是 虚线-间隔-虚线-间隔。
	- 这个属性要搭配stroke-dashoffset才能看得出来效果，非虚线的话，是无法看出偏移的。
	- 概念有点抽象，来看一个MDN的例子，图中红线段是偏移的距离
	- 

- [地址](https://www.cnblogs.com/daisygogogo/p/11044353.html)

### 分组 - <g>

- 定义

	- SVG 中的分组你可以理解为 PS 中的图层，一块图层里面通常只会放一下高内聚的图形，这样既方便移动又方便做动画。SVG 中的分组标签就是 g，使用 g 标签包裹的所有子元素都认同为一组。

- 例子

	- 

- 需要注意的是，使用 g 进行分组，并不会改变原有元素的在屏幕上展示的效果。
- 不过，g 标签除了分组，还有另外一个很重要的功能–动画
- 分组动画

	- 在分组重定义动画是直接写在 transform 属性当中的。实际上，每个子标签都可以使用 transform 的相关属性。
	- <g transform="translate(...) scale(...) rotate(...) translate(...) rotate(...)"> ... </g>
	- 每种变换动画之间是通过 空格或逗号 连接的。它的执行顺序是从右到左。为啥呢？实际上可以理解为，这就是几个嵌套的 g 叠在一起。
	- 
	- [具体可以使用的动画形式和 CSS 动画一模一样，详情可以参考: SVG 动画。](https://developer.mozilla.org/en-US/docs/Web/SVG/Attribute/transform)

### svg形状

- 矩形 <rect>

	- <rect> 标签
<rect> 标签可用来创建矩形，以及矩形的变种。
	- 参数

		- x 属性定义矩形的左侧位置（例如，x="0" 定义矩形到浏览器窗口左侧的距离是 0px）
		- y 属性定义矩形的顶端位置（例如，y="0" 定义矩形到浏览器窗口顶端的距离是 0px）
		- rect 元素的 width 和 height 属性可定义矩形的高度和宽度
		- rx 和 ry 属性可使矩形产生圆角。
		- style 属性用来定义 CSS 属性
		- CSS 的 fill 属性定义矩形的填充颜色（rgb 值、颜色名或者十六进制值）
		- CSS 的 stroke-width 属性定义矩形边框的宽度
		- CSS 的 stroke 属性定义矩形边框的颜色
		- CSS 的 opacity 属性定义整个元素的透明值（合法的范围是：0 - 1）

	- 例子

		- 例子1：

			- <?xml version="1.0" standalone="no"?>
<!DOCTYPE svg PUBLIC "-//W3C//DTD SVG 1.1//EN" 
"http://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd">

<svg width="100%" height="100%" version="1.1"
xmlns="http://www.w3.org/2000/svg">

<rect width="300" height="100"
style="fill:rgb(0,0,255);stroke-width:1;
stroke:rgb(0,0,0)"/>

</svg>

		- 例子2：

			- <?xml version="1.0" standalone="no"?>
<!DOCTYPE svg PUBLIC "-//W3C//DTD SVG 1.1//EN" 
"http://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd">

<svg width="100%" height="100%" version="1.1"
xmlns="http://www.w3.org/2000/svg">

<rect x="20" y="20" width="250" height="250"
style="fill:blue;stroke:pink;stroke-width:5;
fill-opacity:0.1;stroke-opacity:0.9"/>

</svg>

		- 例子3：

			- <?xml version="1.0" standalone="no"?>
<!DOCTYPE svg PUBLIC "-//W3C//DTD SVG 1.1//EN" 
"http://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd">

<svg width="100%" height="100%" version="1.1"
xmlns="http://www.w3.org/2000/svg">

<rect x="20" y="20" width="250" height="250"
style="fill:blue;stroke:pink;stroke-width:5;
opacity:0.9"/>

</svg>

		- 例子4：

			- <?xml version="1.0" standalone="no"?>
<!DOCTYPE svg PUBLIC "-//W3C//DTD SVG 1.1//EN" 
"http://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd">

<svg width="100%" height="100%" version="1.1"
xmlns="http://www.w3.org/2000/svg">

<rect x="20" y="20" rx="20" ry="20" width="250"
height="100" style="fill:red;stroke:black;
stroke-width:5;opacity:0.5"/>

</svg>

- 圆形 <circle>

	- circle> 标签

		- <circle> 标签可用来创建一个圆。

	- 【参数】

		- cx 和 cy 属性定义圆点的 x 和 y 坐标。如果省略 cx 和 cy，圆的中心会被设置为 (0, 0)

r 属性定义圆的半径。

	- 【例子】

		- <?xml version="1.0" standalone="no"?>
<!DOCTYPE svg PUBLIC "-//W3C//DTD SVG 1.1//EN" 
"http://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd">

<svg width="100%" height="100%" version="1.1"
xmlns="http://www.w3.org/2000/svg">

<circle cx="100" cy="50" r="40" stroke="black"
stroke-width="2" fill="red"/>

</svg>

- 椭圆 <ellipse>

	- <ellipse> 标签

		- <ellipse> 标签可用来创建椭圆。椭圆与圆很相似。不同之处在于椭圆有不同的 x 和 y 半径，而圆的 x 和 y 半径是相同的。

	- 【参数】

		- cx 属性定义圆点的 x 坐标
		- cy 属性定义圆点的 y 坐标
		- rx 属性定义水平半径
		- ry 属性定义垂直半径
		- style="fill:yellow"

	- 【例子】

		- 例子1

			- <?xml version="1.0" standalone="no"?>
<!DOCTYPE svg PUBLIC "-//W3C//DTD SVG 1.1//EN" 
"http://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd">

<svg width="100%" height="100%" version="1.1"
xmlns="http://www.w3.org/2000/svg">

<ellipse cx="300" cy="150" rx="200" ry="80"
style="fill:rgb(200,100,50);
stroke:rgb(0,0,100);stroke-width:2"/>

</svg>

- 线 <line>

	- <line> 标签

		- <line> 标签用来创建线条。

	- 【参数】

		- x1 属性在 x 轴定义线条的开始
		- y1 属性在 y 轴定义线条的开始
		- x2 属性在 x 轴定义线条的结束
		- y2 属性在 y 轴定义线条的结束

	- 【例子】

		- <?xml version="1.0" standalone="no"?>
<!DOCTYPE svg PUBLIC "-//W3C//DTD SVG 1.1//EN" 
"http://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd">

<svg width="100%" height="100%" version="1.1"
xmlns="http://www.w3.org/2000/svg">

<line x1="0" y1="0" x2="300" y2="300"
style="stroke:rgb(99,99,99);stroke-width:2"/>

</svg>

- 折线 <polyline>

	- <polyline> 标签

		- <polyline> 标签用来创建仅包含直线的形状。

	- 【例子】

		- <?xml version="1.0" standalone="no"?>
<!DOCTYPE svg PUBLIC "-//W3C//DTD SVG 1.1//EN" 
"http://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd">

<svg width="100%" height="100%" version="1.1"
xmlns="http://www.w3.org/2000/svg">

<polyline points="0,0 0,20 20,20 20,40 40,40 40,60"
style="fill:white;stroke:red;stroke-width:2"/>

</svg>

- 多边形 <polygon>

	- <polygon> 标签

		- <polygon> 标签用来创建含有不少于三个边的图形

	- 【参数】

		- points 属性定义多边形每个角的 x 和 y 坐标

	- 【例子】

		- <?xml version="1.0" standalone="no"?>
<!DOCTYPE svg PUBLIC "-//W3C//DTD SVG 1.1//EN" 
"http://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd">

<svg width="100%" height="100%" version="1.1"
xmlns="http://www.w3.org/2000/svg">

<polygon points="220,100 300,210 170,250"
style="fill:#cccccc;
stroke:#000000;stroke-width:1"/>

</svg>

- 路径 - <path>

	- Path

		- path 在 SVG 中的地位应该是比较高的，实际上，利用 path 这个一个标签可以画出任意的图形。path 中 d(data) 属性是用来定义相关线条数据，通常是以 M/m 为起始，代表的就是 move to 的意思。在 path 中，一共可以定义 10 种不同的图形。例如 M/m，L/l。 大家可以注意，每种标识符有两种书写方式，即，大小写。
		- 大写: 参照的是绝对坐标，即，SVG 的右上角
		- 小写: 参照的相对坐标，即，前一个点的坐标。
		- 而在 10 种不同表示符中，又可以分为直线和曲线两种不同的标识符。这里，我们分类来讲解一下。

	- 线型

		- M = moveto

			- M/m
			- 该使用定义起始点的，没啥特殊的作用。
			- <path d="M10 10"/>
			- 表示，以 (10,10) 为起始点。

		- L = lineto

			- L/l
			- 原意是 Line to，用来画线段的。格式和 M/m 差不多：
			- L x y (or l dx dy)

		- H = horizontal lineto

			- H/h
			- 用来画水平线，即，Horizontal。既然方向已经定了，剩下的就是距离，格式很简单：
			- H x (or h dx)

		- V = vertical lineto

			- V/v
			- 用来画竖直线，即，vertical。同上，方向也定了，格式为：
			- V y (or v dy)
			- 看个例子吧：
			- <path d="M10 10 H 90 V 90 H 10 L 10 10"/>
			- 该 path 实际上就是画了一个正方形，宽 = 高 = 90。

				- 

	- 曲线

		- 曲线就是 Web 画图中常见的 Bezier Curves（贝塞尔），Arcs，several Bezier curves（很多贝塞尔 - .-）等。
		- C = curveto

			- C/c
			- 这是正统的贝塞尔曲线，需要 4 个参考点，下图应该说比较确切表示了二次贝塞尔所需要的点。所以，C/c 需要定义三个点。

				- 

			- 参数

				- 两个控制点一个终点

			- 基本格式为：
			- C x1 y1, x2 y2, x y (or c dx1 dy1, dx2 dy2, dx dy)
			- 例如：
			- <path d="M10 10 C 20 20, 40 20, 50 10" stroke="black" fill="transparent"/>

		- S = smooth curveto

			- S/s
			- 该标识符实际上使用来表示一个反射贝塞尔，即，在原有贝塞尔上再加一段贝塞尔曲线，所以，S/s 一般和 C/c 一起使用。
			- 基本格式为：
			- S x2 y2, x y (or s dx2 dy2, dx dy)
			- 实际样式图为：

				- 

			- 相当于原有的贝塞尔曲线的最后一段进行反向延长并对称。然后加上新定义的一段限制曲线。
			- 具体实例为：
			- <path d="M10 80 C 40 10, 65 10, 95 80 S 150 150, 180 80" stroke="black" fill="transparent"/>

		- Q = quadratic Bézier curve

			- Q/q
			- 该标识符是用来定义二次(Quadratic)贝塞尔曲线，该曲线相当于上面传统的贝塞尔来说，更加简单，它只需要定义三个点，即可完整一个贝塞尔曲线，具体作图过程如下：
			- 
			- 参数

				- 一个控制点，一个终点

			- 基本格式为：
			- Q x1 y1, x y (or q dx1 dy1, dx dy)
			- 即为图上点， P1(x1,y1)，P2(x,y)。
			- 起始点为 M 定义的点，例如：
			- <path d="M10 80 Q 95 10 180 80" stroke="black" fill="transparent"/>

		- T = smooth quadratic Bézier curveto

			- T/t
			- 该标识符和 S 差不多，也是一个贝塞尔曲线的延长。相当于原曲线的控制点 P1 相当于 end point P2 做对称，然后，只需要定义一个终点即可，即，T/t 只需要定义贝塞尔曲线里面的终点即可：
			- T x y (or t dx dy)
			- 
			- 简单来说，C/S，Q/T 是两两搭配一起使用的。在使用的时候，千万不要搞混即可。

		- A = elliptical Arc

			- 弧线
			- A/a
			- 该曲线是用来画弧线(Arcs)，而，弧线通常是圆/椭圆的一部分。当，椭圆的两个轴径长相等则为圆，所以，A/a 是按照椭圆作为基准格式

				- A rx ry x-axis-rotation large-arc-flag sweep-flag x y 
				- a rx ry x-axis-rotation large-arc-flag sweep-flag dx dy

			- 参数

				- rx,ry: 代表的就是长轴短轴，没得说。
				- x,y: 代表的是弧长的结束点。开始点就是上一个命令的终点。
				- x-axis-rotation: x 轴的旋转角度。顺时针为正
				- large-arc-flag[0,1]: 表示取大弧还是小弧。因为两点之间的弧长有两部分。
				- sweep-flag[0,1]: 取顺时针的弧，还是逆时针的弧长。参考点是以起始点开始的。

			- 图示

				- 

	- Z = closepath

		- Z/z
		- 该标识符用来表示 path 的结束，并且将最后一点和 M/m 标识开头的一点连接起来。所以，它不存在什么表示点之类的，格式为：
		- Z (or z)
		- 而上面也可以进行相关的优化，最终的结果为：
		- <path d="M10 10 H 90 V 90 H 10 L 10 10"/>
		- // 使用 Z
		- <path d="M10 10 H 90 V 90 H 10 Z" fill="transparent" stroke="black"/>

### svg滤镜

- SVG 滤镜用来向形状和文本添加特殊的效果。
- 在 SVG 中，可用的滤镜有：

	- feBlend
	- feColorMatrix
	- feComponentTransfer
	- feComposite
	- feConvolveMatrix
	- feDiffuseLighting
	- feDisplacementMap
	- feFlood
	- feGaussianBlur
	- feImage
	- feMerge
	- feMorphology
	- feOffset
	- feSpecularLighting
	- feTile
	- feTurbulence
	- feDistantLight
	- fePointLight
	- feSpotLight

- 注释：您可以在每个 SVG 元素上使用多个滤镜！
- SVG 高斯模糊

	- 特点

		- 必须在 <defs> 标签中定义 SVG 滤镜。
		- 高斯模糊（Gaussian Blur）
		- <filter> 标签用来定义 SVG 滤镜。
		- <filter> 标签使用必需的 id 属性来定义向图形应用哪个滤镜？
		- <filter> 标签必须嵌套在 <defs> 标签内。
		- <defs> 标签是 definitions 的缩写，它允许对诸如滤镜等特殊元素进行定义。

	- 【例子】

		- <?xml version="1.0" standalone="no"?>
<!DOCTYPE svg PUBLIC "-//W3C//DTD SVG 1.1//EN" 
"http://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd">

<svg width="100%" height="100%" version="1.1"
xmlns="http://www.w3.org/2000/svg">

<defs>
<filter id="Gaussian_Blur">
<feGaussianBlur in="SourceGraphic" stdDeviation="3" />
</filter>
</defs>

<ellipse cx="200" cy="150" rx="70" ry="40"
style="fill:#ff0000;stroke:#000000;
stroke-width:2;filter:url(#Gaussian_Blur)"/>

</svg>

	- 例子2

		- <?xml version="1.0" standalone="no"?>
<!DOCTYPE svg PUBLIC "-//W3C//DTD SVG 1.1//EN" 
"http://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd">

<svg width="100%" height="100%" version="1.1"
xmlns="http://www.w3.org/2000/svg">

<defs>
<filter id="Gaussian_Blur">
<feGaussianBlur in="SourceGraphic" stdDeviation="20"/>
</filter>
</defs>

<ellipse cx="200" cy="150" rx="70" ry="40"
style="fill:#ff0000;stroke:#000000;
stroke-width:2;filter:url(#Gaussian_Blur)"/>

</svg>

	- 【例子，解释】

		- <filter> 标签的 id 属性可为滤镜定义一个唯一的名称（同一滤镜可被文档中的多个元素使用）
		- filter:url 属性用来把元素链接到滤镜。当链接滤镜 id 时，必须使用 # 字符
		- 滤镜效果是通过 <feGaussianBlur> 标签进行定义的。fe 后缀可用于所有的滤镜
		- <feGaussianBlur> 标签的 stdDeviation 属性可定义模糊的程度
		- in="SourceGraphic" 这个部分定义了由整个图像创建效果

- SVG渐变

	- SVG 渐变必须在 <defs> 标签中进行定义。
	- SVG 渐变

		- 渐变是一种从一种颜色到另一种颜色的平滑过渡。另外，可以把多个颜色的过渡应用到同一个元素上。

	- 在 SVG 中，有两种主要的渐变类型：

		- 线性渐变
		- 放射性渐变

	- 线性渐变

		- <linearGradient> 可用来定义 SVG 的线性渐变。
		- <linearGradient> 标签必须嵌套在 <defs> 的内部。<defs> 标签是 definitions 的缩写，它可对诸如渐变之类的特殊元素进行定义。
		- 线性渐变可被定义为水平、垂直或角形的渐变：

			- 当 y1 和 y2 相等，而 x1 和 x2 不同时，可创建水平渐变
			- 当 x1 和 x2 相等，而 y1 和 y2 不同时，可创建垂直渐变
			- 当 x1 和 x2 不同，且 y1 和 y2 不同时，可创建角形渐变

		- 【例子】

			- <?xml version="1.0" standalone="no"?>
<!DOCTYPE svg PUBLIC "-//W3C//DTD SVG 1.1//EN" 
"http://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd">

<svg width="100%" height="100%" version="1.1"
xmlns="http://www.w3.org/2000/svg">

<defs>
<linearGradient id="orange_red" x1="0%" y1="0%" x2="100%" y2="0%">
<stop offset="0%" style="stop-color:rgb(255,255,0);
stop-opacity:1"/>
<stop offset="100%" style="stop-color:rgb(255,0,0);
stop-opacity:1"/>
</linearGradient>
</defs>

<ellipse cx="200" cy="190" rx="85" ry="55"
style="fill:url(#orange_red)"/>

</svg>

		- 【代码解释】

			- <linearGradient> 标签的 id 属性可为渐变定义一个唯一的名称
			- fill:url(#orange_red) 属性把 ellipse 元素链接到此渐变
			- <linearGradient> 标签的 x1、x2、y1、y2 属性可定义渐变的开始和结束位置
			- 渐变的颜色范围可由两种或多种颜色组成。每种颜色通过一个 <stop> 标签来规定。offset 属性用来定义渐变的开始和结束位置。

		- 【例子】

			- <?xml version="1.0" standalone="no"?>
<!DOCTYPE svg PUBLIC "-//W3C//DTD SVG 1.1//EN" 
"http://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd">

<svg width="100%" height="100%" version="1.1"
xmlns="http://www.w3.org/2000/svg">

<defs>
<linearGradient id="orange_red" x1="0%" y1="0%" x2="0%" y2="100%">
<stop offset="0%" style="stop-color:rgb(255,255,0);
stop-opacity:1"/>
<stop offset="100%" style="stop-color:rgb(255,0,0);
stop-opacity:1"/>
</linearGradient>
</defs>

<ellipse cx="200" cy="190" rx="85" ry="55"
style="fill:url(#orange_red)"/>

</svg>

	- SVG 放射性渐变

		- <radialGradient> 用来定义放射性渐变。
		- <radialGradient> 标签必须嵌套在 <defs> 中。<defs> 标签是 definitions 的缩写，它允许对诸如渐变等特殊元素进行定义。
		- 【例子】

			- <?xml version="1.0" standalone="no"?>
<!DOCTYPE svg PUBLIC "-//W3C//DTD SVG 1.1//EN" 
"http://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd">

<svg width="100%" height="100%" version="1.1"
xmlns="http://www.w3.org/2000/svg">

<defs>
<radialGradient id="grey_blue" cx="50%" cy="50%" r="50%"
fx="50%" fy="50%">
<stop offset="0%" style="stop-color:rgb(200,200,200);
stop-opacity:0"/>
<stop offset="100%" style="stop-color:rgb(0,0,255);
stop-opacity:1"/>
</radialGradient>
</defs>

<ellipse cx="230" cy="200" rx="110" ry="100"
style="fill:url(#grey_blue)"/>

</svg>

		- 【代码解释】

			- <radialGradient> 标签的 id 属性可为渐变定义一个唯一的名称，fill:url(#grey_blue) 属性把 ellipse 元素链接到此渐变，cx、cy 和 r 属性定义外圈，而 fx 和 fy 定义内圈 渐变的颜色范围可由两种或多种颜色组成。每种颜色通过一个 <stop> 标签来规定。offset 属性用来定义渐变的开始和结束位置。

		- 【例子】

			- <?xml version="1.0" standalone="no"?>
<!DOCTYPE svg PUBLIC "-//W3C//DTD SVG 1.1//EN" 
"http://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd">

<svg width="100%" height="100%" version="1.1"
xmlns="http://www.w3.org/2000/svg">

<defs>
<radialGradient id="grey_blue" cx="20%" cy="40%" r="50%"
fx="50%" fy="50%">
<stop offset="0%" style="stop-color:rgb(200,200,200);
stop-opacity:0"/>
<stop offset="100%" style="stop-color:rgb(0,0,255);
stop-opacity:1"/>
</radialGradient>
</defs>

<ellipse cx="230" cy="200" rx="110" ry="100"
style="fill:url(#grey_blue)"/>

</svg>

	- 各种svg案例

		- [地址](https://www.w3school.com.cn/svg/svg_examples.asp)

- <defs> 标签是 definitions 的缩写，它允许对诸如滤镜等特殊元素进行定义。

### svg mask（蒙版|遮罩）

### svg clipPath（裁剪）

### svg 动画

