<h3>web自适应</h3>
<span>移动端头部必须加上这句</span>
<code>
	<meta name="viewport" content="width=device-width,initial-scale=1.0,maximum-scale=1.0,user-scalable=0">
</code>

<h4>1:Flex布局</h4>

<h4>2:rem</h4>
```css
//此时1rem=10px;rem的值是继承父类元素
html{
	font-size:10px;
}
div{
	font-size:1rem;
	height:2rem;
	width:3rem;
	border:0.1rem solid #000;
}
```
由此可以得知其他设备下根元素的字体大小
```javascript
//计算公式 640/100=device-width/x 设置其他设备字体的大小
//当前假设设备为iphone5(640屏幕),根元素字体为100px;

	var deviceWidth = window.documentElement.clientWidth;
	document.documentElement.style.fontSize = (deviceWidth/6.4)+'px';

	//节流阀函数,判断后执行
	window.onresize = _.debounce(function(){
		var deviceWidth = document.documentElement.clientWidth>1300?1300:document.documentElement.clientWidth;
		document.documentElement.style.fontSize=(deviceWidth/6.4)+'px';
	},50);
```
<h4>完整代码</h4>
```html
<!DOCTYPE html>
<html>
<head>
  <title>测试</title>
  <meta name="viewport" content="width=device-width,user-scalable=no,maximum-scale=1" />
  <script type="text/javascript">
(function() {
  // deicePixelRatio ：设备像素
  var scale = 1 / devicePixelRatio;
  //设置meta 压缩界面 模拟设备的高分辨率
  document.querySelector('meta[name="viewport"]').setAttribute('content', 'initial-scale=' + scale + ', maximum-scale=' + scale + ', minimum-scale=' + scale + ', user-scalable=no');
  //debounce 为节流函数，自己实现。或者引入underscoure即可。
  var reSize = _.debounce(function() {
      var deviceWidth = document.documentElement.clientWidth > 1300 ? 1300 : document.documentElement.clientWidth;
      //按照640像素下字体为100px的标准来，得到一个字体缩放比例值 6.4
      document.documentElement.style.fontSize = (deviceWidth / 6.4) + 'px';
  }, 50);
 
  window.onresize = reSize;
})();
  </script>
  <style type="text/css">
    html {
      height: 100%;
      width: 100%;
      overflow: hidden;
      font-size: 16px;
    }
 
    div {
      height: 0.5rem;
      widows: 0.5rem;
      border: 0.01rem solid #19a39e;
    }
 
    ........
  </style>
  <body>
    <div>
    </div>
  </body>
</html>
```
<h4>media query</h4>
<span>优点:可以根据不同设备显示不同的布局!</span>
```css
@media screen and(min-width:320px)and(max-width:650px){
	//手机
	.class{
	float:left;
}
}
@media screen and(min-width:650px)and(max-width:980px){
//pad
	.class{
	float:right;
}
}
@media screen and(min-width:980px)and(max-width:1240px){
	//pc
	.class{
	float:right;
}
}
```