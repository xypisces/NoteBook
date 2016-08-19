<h3>WEB动画</h3>

<h4>JS动画 ---TweenMax .TweenLite</h4>
<h4>CSS动画</h4>
<code>
.box{
	animation:movingBox 1300ms infinite alternate;
}
@keyframes movingBox{
	0% {
	transform: translate(0,0);
	opacity:0.3;
	}
	25%{
	opcity:0.9;
	}
	50%{
	transform:translate(100px,100px);
	opcity:0.2;
	}
	100%{
	transform:translate(30px,30px);
	opacity:0.8;
	}
}
</code>

<ul>
	<li>transition:transform 500ms linear//线性</li>
	<li>transition:transform 500ms ease-out//渐出</li>
	<li>transition:transform 500ms ease-in</li>
	<li>transition:transform 500ms ease-in-out</li>
</ul>