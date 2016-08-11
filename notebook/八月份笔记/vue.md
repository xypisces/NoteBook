<h3>Vue的组件</h3>

<p>特点:可拔插,独立作用域,观察者模式,完整的生命周期</p>

```javascript
	Vue.component('child',{
		props:['msg'],
		template:'<span>{{ msg }}</span>',
		data: function(){
			return {
			title : 'TalkingCoder'
		}
	},
	methods: {

	},
	ready: function() {
		//组件准备好回调,获取数据
	},
	beforeDestroy:function() {
		//销毁,解绑,取消定时器
	},
	events :{
		//...
	}
})
```