<h3>jQuery</h3>
***

<code>
<ul class="lang">
    <li class="js dy">JavaScript</li>
    <li class="dy">Python</li>
    <li id="swift">Swift</li>
    <li class="dy">Scheme</li>
    <li name="haskell">Haskell</li>
</ul>
</code>

### 查找与替换
- 向下查找用find(),	ul.find('.dy');
- 向上查找用parent(), swf.parent();

###过滤---filter(),map();
- var langs = $('ul.lang li'); var a = lang.filter('.dy') //除去python;
- map()把一个jq对象转化为其他对象

<code>
	var langs = $('ul.lang li');
	var arr = langs.map(function(){
		return this.innerHTML;
	}).get(); //['javascript','python'.....]
</code>

###隐藏与显示 
- hide()
- show()

###获取DOM信息
- attr() 设置属性
- removeAttr() 删除属性
- prop() HTML5
- is(:selected),is(:checked) 判断是否存在

###操作表单 ---val();
###修改DOM结构
- append()从后面插入, prepend()从前插入

<code>
	<div id="test">
		<ul>
			<li><span>Javascript</span></li>
		</ul>
	</div>

	//功能:插入并排序
	var ul = $('#test>ul');
	var lang = ['css','html','jq'];
	//获取原来的内容
	var n = ul.find('span').map(function(){
			return $(this).text(); //$(this)转成jq对象
		}).get();
	//原来内容结合并排序
	lan = lan.concat(n).sort();
	//加入html标签,转成字符串
	var	strlan = lan.map(function(e){
		return '<li><span>'+e+'</span></li>';
		}).join('');
	//更改ul结构
	ul.html(strlan);	
</code>