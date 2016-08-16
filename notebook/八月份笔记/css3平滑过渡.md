<h3>CSS3过渡</h3>

font-smoothing:antialiased //抗锯齿,用于英文字体

<h4>隐藏元素</h4>
<ul>
	<li>display:none</li>
	<li>position:absolute left:-9999</li>
	//上面两种是隐藏,下面是隐藏,但是占位,可点击
	<li>visibility:hidden</li>
	<li>opacity:0</li>
</ul>

<h4>滚动(有兼容性问题)(-webkit,-moz,-o,-ms)</h4>
<ul>
	<li>translate3d(0,0,0) 开启硬件加速</li>
	<li>backface-visibility:hidden 背面不可见</li>
</ul>
<span>transform:translateY(0%)</span>
<span>平滑过渡:transition:all 0.6s ease-in-out(由慢到快到慢)</span>
<p>旋转:transform:rotate(45deg)</p>

<h4>@font-face</h4>
<ul>
	<li>font-family</li>
	<li>src:url() format()</li>
	<li>font-wight:normal</li>
	<li>font-style:normal</li>
</ul>

<h4>animation动画</h4>
<p>用于创建动画,不需要事件触发,而transition需要触发</p>
<ul>
	<li>animation-name:绑定的选择器名称</li>
	<li>animation-duration:持续多久</li>
	<li>animation-timing-function:速度曲线</li>
	<li>animation-delay:延迟时间</li>
	<li>animation-direction:是否轮流反向播放</li>
	<li>animation-iteration-count:播放次数</li>
</ul>
<span>animation:move 0.6s ease-in-out 0.2s backwards(播放前处于开始状态);</span>
<code>
@-webkit-keyframes move{
	0%{
	-webkit-transform:translateY(-40px);
	opacity:0;
	}
	100%{
	-webkit-transform:translateY(0px);
	opacity:1;
	}
}
</code>