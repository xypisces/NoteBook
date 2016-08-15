<h3>ES6</h3>
<ul>
	<li>默认参数</li>
	<li>模板表达式</li>
	<li>多行字符串</li>
	<li>拆包表达式</li>
	<li>改进的对象表达式</li>
	<li>箭头函数 =&></li>
	<li>Promise</li>
	<li>块级作用域let和cont</li>
	<li>类</li>
	<li>模块化</li>
</ul>

<h4>默认参数</h4>
```css
	//before
var link = function(height,color,url){
	var height = height || 50;
	var color = color || 'red';
	var url = url || 'http://azat.co'
}
//now
//ES6中默认值可以直接放在参数中
var link = function(height=50,color='red',url='http://azat.co'){
	
}
```
<h4>模板表达式</h4>
```css
//before
var name = 'Your name is'+first+''+last+'.'
var url = 'http://localhost:3000/api/messages/'+id
//now
使用${name}来表示模板字符;
var name = 'Your name is ${first} ${last}'
```
<h4>多行字符串</h4>
<span>//用''包起来即可</span>

<h4>ES6拆包表达式</h4>
```css
//before
var data = $('body').data();
var house = data.house;
var mouse = data.mouse;

var jsonMiddle = require('body-parser').json
var body=req.body;
	username = body.username;
	password = body.password;
//now
var {house,mouse} = $('body').data()
var {jsonMiddle} = require('body-parse')
var {username,password} = req.body
```

<h4>对象表达式</h4>
```JavaScript
//before
var serviceBase = {port:3000,url:'azat.co'},
	getAccounts = function(){return [1,2,3]}

var accountServiceES5={
	port:serviceBase.port,
	url:serviceBase.url,
	getAccounts:getAccounts,
	toString:function(){
	return JSON.stringify(this.valueOf())
},
	getUrl:function(){return 'http://'+this.url+':'+this.port},
	valueOf_1_2_3:getAccounts()
};
//now
var serviceBase = {port:3000,url:'azat.co'},
	getAccounts = function(){return [1,2,3]}
var accountService ={
	_proto_:serviceBase, //_proto_设置继承
	getAccounts,
	toString(){ //ES6不同function
	return JSON.stringify((super.valueOf()))
},
	getUrl(){return 'http://'+this.url+':'+this.port},
	['valueOf_'+getAccounts().join('_')]:getAccounts()
};

<h4>箭头函数</h4>
<strong>适合闭包之中</strong>
```javascript
//before
 var _this=this
 $('.btn').click(function(event){
 _this.sendData();
 })
 //now
 $('.btn').click((event)=>{
 this.sendData();
 })
```

