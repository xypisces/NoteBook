<h3>变量</h3>
```css
	@public-color:#fff;
	#header{
	color:@public-color;
	}
```
<h3>混合</h3>
```css
   //将一个定义好的class A轻松的引入到另一个class B中，从而简单实现class B继承class A中的所有属性。我们还可以带参数地调用，就像使用函数一样
   .public-font(@font:5px){
   		font-size:@font;
   		margin:@font;
   }
   #header {
     .public-font;
   }
   #header {
   		.public-font(10px);
   }
``` 
<h3>嵌套</h3>
```css
	#header{
	font-size:10px;
	p{
	font-size:20px;
		a{
			font-size:30px;
			&:hover{
				font-size:40px;
			}
		}
	}
}
```

<h3>函数运算</h3>
```css
	@the-border:1px;
	@base-color:#111;
	#header{
	color:@base-color *3;//#333;
	border:@the-border + 2px; //3px;
}

<h4>Others</h4>
```
//javascript表达式
	@var : 'hello'.toUpperCase()+'!' ----> @var : 'HELLO!';
//避免编译 :使用 ~
	.class{
	filter:~"ms:alwaysHasItsOwnSyntax"
}
//字符串插值: 使用 @{name}
	@base-url:'http://assets.fnord.com';
	background-image:url("@{base-url}/images/bg.png");
//引入 @import
	@import 'lib.less';
	@import 'lib.css';
//命名空间
	#bundle{
		.button(){
		....
	}
		.tab{..}
		.cilck{...}
}
	#header a{
	color:orange;
	#bundle > .button; //引入bundle下的.button 
}

-------!-------
//引导---使用when对参数进行判断,符合哪个就'引导'其使用哪个样式
.mixin(@a) when (lightness(@a)>=50%){
	background-color:black;
}
.mixin(@a) when (lightness(@a)>50%){
	background-color:white;
}
.mixin(@a){
	color:@a;
}

.class1{ .mixin(#ddd)}
.class2{ .mixin(#555)}
得到
.class1{
	background-color:black;
	color:#ddd;
}
.class2{
	background-color:white;
	color:#555;
}

//模式匹配--与'引导'类似
.mixin(dark,@color){
	color:darken(@color,10%)
}
.mixin(light,@color){
	color:lighten(@color,10%);
}
.mixin(@_,@color){
	display:block;
}

@swith:light; //可与上面参数匹配进行引用.
.class{
	.mixin(@swith,#888);
}
得到
.class{
	color:#a2a2a2;
	display:block;
}

<h4>区别:模式匹配是确定的参数可选,引导则是判断</h4>
```
