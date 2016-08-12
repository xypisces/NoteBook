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

<h4>函数运算</h4>
```css
	@the-border:1px;
	@base-color:#111;
	#header{
	color:@base-color *3;//#333;
	border:@the-border + 2px; //3px;
}
