---
created: 2023-11-15T20:53
updated: 2023-11-15T20:53
---
# flex

## [官网地址](https://www.w3.org/TR/css-flexbox-1/)

## flex布局Flexible布局，弹性布局

### flex:flex container 以block-level形式存在
inline-flex:flex-container以inline-level形式存在

## flex container上的属性

### flex items 默认都是沿着main axis主轴从main start 开始往 main end方向排布

- main axis
- main start
- main end

### 模型

### flex-direction

- 决定了items在主轴的排列顺序，从哪个方向开始排

	- 从哪个方向，什么顺序排列

- row(默认)

	- main-start在左，mian-end在右

- row-reverse

	- main-start在右，mian-end在左
	- reverse是reverse了主轴的方向

- column
- column-reverse
- 图示

### justify-content

- 决定了items在主轴上的对齐方式

	- 空隙如何放置

- flex-start（默认）
- flex-end
- space-between
- space-around
- space-evenly
- 图示

### align-items：单行，交叉轴

- cross axis 永远跟main axis 垂直，要么向下，要么向右
- 决定了items在交叉轴cross axis上的对齐方式
- stretch（默认）

	- 当flex items 在cross axis方向的size为auto时，自动拉伸至填充flex container

- flex-start
- flex-end
- center
- baseline
- 图示，size要么是高，要么是宽

	- 例子，交叉轴方向的size是高度

		- 现象

	- 例子,交叉轴方向的size是宽度

		- 现象

### flex-wrap

- flex-wrap决定了flex container是单行还是多行
- nowrap

	- 例子中，flex container总长度是500px
每个flex item长度设置为100px，
现在把flex item的个数从原来的4个变成现在的7个，flex-wrap:nowrap保持不变，看效果

		- 现象：自动收缩，平分宽度

			- 不想这个效果，该如何办？存疑！！！

- wrap

	- 现象

		- 朝着交叉轴的方向换行的，从上往下换行

- wrap-reverse

	- 现象
	- 跟交叉轴方向，相反

- 图示

### flex-flow

- 是flex-direction和flex-wrap的简写
- 图示

### align-content：多行，交叉轴
跟flex-wrap:wrap配合使用

- 决定了多行flex items在cross axis上的对齐方式
- stretch（默认）

	- 拉伸，验证交叉的size拉伸

		- 例子：交叉轴是从上到下，高度

			- 现象

- flex-start

	- 例子

		- 现象：沿着cross start对齐，尽量挨着cross start

- flex-end

	- 现象

- center

	- 现象

- space-between两端对齐

	- 现象

- space-evenly

	- 现象

- space-around

	- 现象

- 图示

	- 图示2

### 总结：看到align是针对cross轴

## flex item上的属性

### order

- 决定了flex items的排布顺序

	- 例子：2是1，其他都是0

		- 现象

	- 例子：2是1，4是-1，其他是0

		- 现象

- 图示

### align-self

- 例子：flex container 设置align-items:center,子元素3 flex item设置align-self:flex-end

	- 现象

- 例子

	- 现象

- 图示

### flex-grow

- 决定了flex items 如何扩展

	- 自己变大
	- 瓜分剩余空间的比例

- 当flex container在main axis方向上有剩余size时，flex-grow属性才会有效

	- size是宽度或者高度
	- 图例：在主轴上的宽度是有剩余的时候，flex-grow有效。

- 例子：1,2,3设置flex-grow:1
扩展比例是1:1:1，大家都是1/3

	- 现象

- 例子，比例：1:2:2，剩余200，1扩展40，2扩展80，3扩展80

	- 现象

- 例子：三个宽度各不一样，100，150，200，剩余50，比例还是1:2:2

	- 现象

- 例子：三个宽度都一样，flex-grow都是0.2

	- 现象

- 例子：0.2:0.2:0.8

	- 现象

- 图示：flex-grow扩展的宽度不能超过max-width或者max-height
- 总结：flex-grow加起来的值，超过1，按照比例分配，如果小于，直接按照剩余乘以比例

### flex-shrink

- 决定了flex items 如何收缩
- 当flex items 在main axis方向上超过了 flex container的size，flex-shrink属性才会有效
- 前端应该是flex-wrap:no-wrap
- 例子：7个100，容器500

	- 现象

- 例子：6个100，flex-shrink:1,600-500超出100，1:1:1:1:1:1，100/6

	- 现象

- 例子：

	- 现象：超出了

- 例子110:1,120:2,130:3...

	- 现象

- 总结：110+120+130+140+150+160=810
810-500=310，超出了310
收缩比例：flex-shrink * item的size(宽度或者高度)，收缩比例分别为：110*1，120*2。。。。
310*（110*1）/ (总比例相加)

	- 例子

- 图示：

### flex-basis

- 图示：flex-basic到底是高度还是宽度取决于主轴
- auto

	- 现象

- content

	- 现象

- 固定值

	- 优先级

- 百度翻译
- 例子

	- 现象：平分

### flex

## 三个默认值会影响默认行为

### align-content默认值stretch

- stretch和size（width，height值为auto时）会产生效果，写死宽度和高度是，拉伸不动了

### flex-grow默认值是0，不扩展

### flex-frink默认值是1，默认按照原始尺寸收缩

