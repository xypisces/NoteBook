<h3>CSS布局</h3>
<strong>核心:浮动float,负边距,相对定位</strong>

<h3>Flex布局</h3>
<strong>容器的属性</strong>
```html
<ul>
	//决定项目的排列方向:row(水平),row-reverse(方向水平),column(垂直)
	<li>flex-direction:row/row-reverse/column/column-reverse</li>
	//如何换行--//不换行/从上至下/从下至下
	<li>flex-wrap:nowrap/wrap/wrap-reverse</li>
	//flex-direction与flex-wrap合体属性.默认值为row nowrap;
	<li>flex-flow</li>
	//项目对齐方式:左/右/居中/两端对齐,项目之间间隔相等/项目两侧间隔相等,因此项目间隔会比边距的大一倍
	<li>justify-content:flex-start/flex-end/center/space-between/space-around</li>
	//垂直方向(1行)如何对齐:左/右/居中/项目第一行文字对齐/占满整个容器
	<li>align-items:flex-start/flex-end/center/baseline/stretch</li>
	//同上(只是有多行时用这个)
	<li>align-content:flex-start/flex-end/center/space-between/space-around/stretch</li>
</ul>
```
<strong>项目的属性</strong>
```html
<ul>
	<li>order:定义项目的排列顺序。数值越小，排列越靠前，默认为0。</li>
	<li>flex-grow:定义项目的放大比例，默认为0，即如果存在剩余空间，也不放大</li>
	<li>flex-shrink:属性定义了项目的缩小比例，默认为1，即如果空间不足，该项目将缩小</li>
	<li>flex-basis:在分配多余空间之前，项目占据的主轴空间</li>
	<li>flex:flex-grow, flex-shrink 和 flex-basis的简写，默认值为0 1 auto////auto(1 1 auto),none( 0 0 auto)</li>
	//建议优先使用这个属性
	<li>align-self:允许单个项目有与其他项目不一样的对齐方式,属性可能取6个值，除了auto，其他都与align-items属性完全一致</li>
</ul>
