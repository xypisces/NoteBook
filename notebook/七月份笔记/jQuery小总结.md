### 选择器

```javascript
	$('li:first') //第一个元素
	$('li:last') //最后一个元素

	$('tr:even') //索引为偶数的元素
	$('tr:odd') //单数

	$('tr:eq(1)') //给定索引值元素
	$('tr:gr(0)') // 大于索引值
	$('tr:lt(2)') // 小于索引值

	$(':focus') //获取焦点元素
	$(':animated') //获取正在执行效果的元素
```

###	内容以及表单选择器

```javascript
	$("div:contained('nick')") //包含nick的文本
	$("td:empty") //不包含元素
	$("div:has(p)") //含有所匹配的元素
	$("td:parent") //含有子元素或者文本的元素
```

### 事件

```javascript
	$(document).ready(function(){
	do something..
	});

	//简写
	$(function($){
		do something..
		});

	//绑定事件
	$("p").bind("click",function(){
		do something...
		});

	$("p").bind({
		"mouseover":function(){
				do something..
			},
		"mouseout":function(){
			do something..
		}	
	});

	$("p").one("click",function(){}); //绑定一次事件
	$("p").unbind("click") //解绑
```
