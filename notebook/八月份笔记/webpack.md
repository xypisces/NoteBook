<h3>webpack示例</h3>
```javascript
	//webpack.config.js
	var path = require('path')
	var webpack = require('webpack')

	module.exports = {
		entry: ['./src/index'], //入口文件
		output: {
			path: path.join(__dirname,'dist'), //输出路径
			filename: 'bundle.js' //输出文件名
		},
		plugins: [
			new webpack.optimize.UglifyJsPlugin({
				compressor:{
					warnings: false,
				},
			}), //内置插件
			new webpack.optimize.OccurenceOrderPlugin() //外置插件
		],
		module: {
			loaders: [{
				test: /\.css$/,
				loaders: ['style','css']
				}]
		}
	}
```