# webpack2.2.1
webpack基础使用 2019-8-6
```
1、在项目中第一次使用vue，显示‘hello vue’用到的包（自己手工打包）
包：
开发环境的包：vue-loader vue-template-compiler css-loader
生产环境的包：vue

安装方式：
npm install vue-loader vue-template-compiler css-loader --save-dev  
npm install vue --save


2.在使用‘html-webpack-plugin’插件+‘webpack-dev-server’包 来实现页面（文件）更新之后，自动打包并刷新页面
包：
开发环境包：webpack webpack-dev-server html-webpack-plugin 
安装方式：npm install webpack@2.2.1 webpack-dev-server@2.4.2 html-webpack-plugin@2.28.0  --save-dev

3.在实现app.vue顶部显示栏的时候
包：
生产环境的包：mint-ui
安装方式：npm i mint-ui --save

4.再点击app-vue 底部tabbar实现路由跳转功能的时候
包：
生产环境的包：vue-router
安装方式：npm i vue-router --save

5.使用MUI实现底部tabber四个选项卡按钮时候不是使用npm安装，是直接放在项目的statics目录下                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            
6.打包css
npm install style-loader css-loader --save-dev

7.打包字体.ttf(mui中)
npm install file-loader url-loader --save-dev

```

# 内容回顾

# webpack
	概念:
		webpack就是一个资源打包工具,它可以将css,js,image,.vue等等文件当做一个模块来进行打包处理,最终将这些资源输出到一个统一的.js文件中,将来在系统中只需要请求这个打包好的.js文件即可完成所有的功能！
		
	为什么要选择webpack
		1.vuejs官方脚手架工具中就使用了webpack模版
		2.对所有的资源会做压缩等优化
		3.它在开发过程中提供了一整套完整的功能,能够使我们开发过程变得高效

--------------------

# webpack的使用

	使用途径:
	
		官方文档
		
		1.x版本,项目中使用的是1.13.3这个版本
			http://webpack.github.io/docs/
			
		2.x版本
			https://webpack.js.org/
			
		https://github.com/webpack/webpack
		
	学习文章:
		http://www.w2bc.com/Article/50764
		http://www.jianshu.com/p/42e11515c10f
		
		
		
	使用步骤:
		1.安装webpack这个全局包 npm install webpack -g
		2.在cmd控制面板中调用webpack的指令给定两个参数 要打包的文件 要输出的文件路径 例如:webpack main.js build.js

--------------------

# webpack的基本概念

	什么是webpack?
		Webpack 是当下最热门的前端资源模块化管理和打包工具。它可以将许多松散的模块按照依赖和规则打包成符合生产环境部署的前端资源。还可以将按需加载的模块进行代码分隔，等到实际需要的时候再异步加载。通过 loader 的转换，任何形式的资源都可以视作模块，比如 CommonJs 模块、 AMD 模块、 ES6 模块、CSS、图片、 JSON、Coffeescript、 LESS 等。
		
	Github地址:
		https://github.com/webpack/webpack
		
	官网:
		https://webpack.js.org/
		
	能做什么?
		打包及优化我们的代码,还能做到按需加载
		
	相比于其它构建工具/打包工具,比如gulp好在哪里? 
		http://webpackdoc.com/what-is-webpack.html
		
		1.代码拆分
		2.Loader
		3.智能解析
		4.插件系统
		5.快速运行

--------------------

# webpack的安装
	
	npm install webpack -g

--------------------

# webpack中的Loader

	作用:
		Webpack 本身只能处理 JavaScript 模块，如果要处理其他类型的文件，就需要使用 loader 进行转换。

--------------------

# webpack中的插件
	作用:
		插件可以完成更多 loader 不能完成的功能。

--------------------

# webpack中webpack-dev-server
	作用:
		可以简化我们的webpack打包的操作,当我们的源代码更改后
		会自动打包,并且刷新页面,有点类似于nodemon

--------------------

# npm? & cmd控制面板 &cmd的指令

	npm:
		1.npmjs.com存储了很多nodejs第三方的功能包
		2.利用npm这个工具,可以将nodejs第三方包通过相关指令进行安装,例如 npm install webpack -g
		3.只要安装好了node.exe这个软件,就自动安装好了npm这个包
		
	如何查看npm
		在终端中输入 npm -v

--------------------

# webpack案例
	
	意义:
		明白模块化开发的思想(需要谁就导入谁)
	
	写法:
		var 模块 = require('xxx/xxx.js');
		路径可以是相对路径也可以是绝对路径
		
	
	注意:
		我们通过require导入的模块,其实就是对应js文件中通过module.exports导出的东西
		
	步骤:
		1.先写好js代码
		2.利用webpack打包成浏览器可以解析的js代码,主要对main.js进行打包,这样main.js依赖的模块也会一并打包
		3.在网页中导入上一步中打包并且生成好的build.js,在浏览器中运行
	
	webpack打包指令:
		webpack 要打包的文件 输出的文件

--------------------

# 项目说明
	
	整个项目是一个单页应用,所以整个项目只需要一个Vue对象
	
------------------

# 项目搭建(文件夹搭建、文件搭建)
	
Vue项目的根目录
├─node_modules         //存放项目中要用到的nodejs第三方包        
└─src                  //项目开发阶段源码存放区  
    ├─main.js          //Vue对象所在文件,打包总入口文件  
    ├─App.vue          //App的入口文件 
    ├─components       //子组件文件夹
    ├─kits             //工具类文件夹
|dist           	   //项目发布阶段代码存放区
|statics               //项目静态资源文件存放区       
    │  ├─css           //整个项目的样式文件
    │  ├─images        //整个项目的图片资源
    │  ├─MUI           //一个移动Web的UI框架
│ package.json 		   // npm 包管理配置文件和项目启动配置文件
| webpack.config.js    //webpack总的配置文件

------------------
		
# 使用 webpack+vue 来展示一个 `Hello Vue`

	依赖的包:
		生产环境 : vue 
		开发环境 : vue-loader vue-template-compiler css-loader
		
	使用步骤:
		准备工作:
			1.安装 vue vue-loader vue-template-compiler css-loader 的包
			2.写好App.vue文件,格式参考下面的
			3.在main.js中写好代码,代码主要有三部分
				4.1 导入vue : import Vue from 'vue'
				4.2 导入需要的模块 : import App from './App.vue'
				4.3 创建Vue对象(写法参考代码）
				
		开始打包
			4.在webpack.config.js中配置好相关参数,主要有
				4.1 配置好要打包的总文件(入口文件路劲)
				4.2 配置好打包完成之后输出文件的路径
				4.3 设置好打包vue的loader(因为webpack默认只支持js打包)
			
		使用并且显示 `Hello Vue`
			5.在dist目录中创建一个网页 index.html,并且在body中配置好
			一个id=app 的div
			6.在index.html的最后导入 刚刚打包好的bundle.js
			7.在浏览器中运行index.html即可看到效果

	注意点:
		1.在 4.3 步骤中,要写上`render : c=>c(App)` 表示将vue渲染好的内容交给webpack去打包
		
		2.在index.html页面中导入bundle.js时一定要注意,一定要在最后导入
		否则可能出现找不到 #app 的错误
		
------------------

# App.vue的结构

	<template>
		写html代码
		
		注意:这里必须有一个根元素,否则在vue2.x里面会报错,比如
		<div>
			
		</div>
	</template>
	
	<script>
		写导出的代码:代码是固定的
		```
		export default{
			data(){
				return {
					属性:值
				}
			}
		}
		```
	</script>
	
	<style>
    	css样式
	</style>

------------------

# webpack.config.js
	作用:
		提高效率,简化开发
		
	概念:
		1.这个文件就是webpack的默认配置文件,默认名称为:webpack.config.js
		2.将来只需要在cmd面板上执行 webpack 就会自动去查找webpack.config.js中的内容进行相关的打包操作

	配置文件的写法:
		http://webpack.github.io/docs/configuration.html
	
	在配置文件的module.exports中,通常需要做哪些事?
		1.写好入口文件配置
		2.写好输出配置
		3.写好Loader相关的配置
		4.写好plugins(插件)相关的配置
	
	配置文件中的js代码:
		```
			module.exports = {
			    entry: "./main.js",//输入文件
			    output: {
			        filename:'./build.js'//输出文件
			    }
			}
		```
		
	各参数详解:
		http://blog.csdn.net/zaichuanguanshui/article/details/53610694
		
--------------------

# 使用 `html-webpack-plugin`插件 + `webpack-dev-server`包 来实现页面(文件)更新之后,自动在内存中打包并且刷新页面

	好处:
		当某个文件(页面、css、js等)更新之后webpack能自动检测到,并且打包,打包完成之后再刷新页面,这一条龙服务
	
	需要的包:
		webpack webpack-dev-server html-webpack-plugin
	
	使用步骤:
		1.安装 webpack webpack-dev-server html-webpack-plugin 这三个包
		
		2.在webpack.config.js文件中配置相关代码
			主要配置两个地方
			
			```
			var htmlWebpackPlugin = require('html-webpack-plugin');
				
				
		    plugins:[
		        new htmlWebpackPlugin({
		            title:'index',
		            filename:'index.html', //在内存中生成的网页的名称
		            template:'index222.html' //生成网页名称的依据
		        })
		    ]
		 	```
		 	
		 3.package.json的 scripts 标签中配置一段代码
		 	```
		 		"scripts": {
			    	"test": "echo \"Error: no test specified\" && exit 1",
			    	"dev" : "webpack-dev-server --inline --hot --open --port 3008"
			  	},
		 	
		 	```
		 	
		 4.在终端中运行 npm run dev 即可
		 
	 
	 package.json的 scripts 中dev对应值的参数说明:
	 
	 		-- inline :自动刷新
			-- hot :热加载
			-- port 指定监听端口
			-- open : 自动在默认浏览器中打开
			-- host： 可以指定服务器的ip，不指定默认为127.0.0.1(localhost)

		   
	 注意点:
	 	它是在内存中生成了一个网页,凡是对可以编译的文件修改之后都会自动打包并且刷新浏览器
		
--------------------

# webpack-dev-server 使用过程中可能遇到的问题
	
	1.webstorm修改文件，webpack-dev-server不会自动编译刷新 : 
		http://www.cnblogs.com/wshiqtb/p/5924172.html
	
	2.启动webpack-dev-server成功后在地址栏中永远只出现 http://localhost:3008/webpack-dev-server/
		原因:在package.json中的script配置错了
		"dev": "webpack-dev-server --inline --hot --open --port 3008"
		
		写成了下面的错误形式
		"dev": "webpack-dev-server --line --hot --open --port 3008"

--------------------

# webpack 打包其它扩展名的文件

# webpack 打包css

	需要的包:
		style-loader css-loader
		
	拓展:
		package.json
		
		1.利用npm init 来创建一个package.json
		2.在安装包的时候在后面加上 npm i 包 --save-dev
		3.以后提交到svn、git或是发给别人时不要把node_modules提交上去或是发给别人,只需要把package.json提交上去,别人拿到package.json之后只需要在终端执行一下 npm install 就可以安装全部依赖的包了

	使用步骤:
		1.使用 npm init 生成package.json文件
		2.安装style-loader css-loader这两个包 npm i style-loader css-loader --save-dev
		3.在webpack.config.js中配置好相关的js代码
			```
				module.exports = {
				    entry: "./main.js",
				    output: {
				        filename:'./build.js'
				    },
				    module : {
				        loaders : [
				            {
				                test:/\.css$/,
				                loader:'style-loader!css-loader'
				            }
				        ]
				    }
				}
			```
	
	注意点:
		1.在loader中的写法必须是 loader:'style-loader!css-loader',中间用!分割
		2.加载顺序是从右到左
		3.配置文件中不要写错了,写错了可能报的错就到别的地方去了,比如在配置文件中少写了loaders中的s,到时候报错就不知道报错到哪里去了,建议拷贝
		
--------------------

# autoprefixer-loader
	作用:
		自动前缀的包,自动在打包的过程中将css写法加上不同浏览器内核的前缀,达到不同浏览器的兼容
		
	依赖的包:
		style-loader css-loader autoprefixer-loader
	
	使用步骤:
		1.安装好 autoprefixer-loader 这个包
			npm install autoprefixer-loader --save-dev
		
		2.在webpack.config.js中配置好相关的js代码
		
			```
				module : {
				        loaders : [
				            {
				                test:/\.css$/,
				                loader:'style-loader!css-loader!autoprefixer-loader'
				            }
				        ]
				    }
			```
		
	注意点:
		1.在loader中的写法必须是 loader:'style-loader!css-loader!autoprefixer-loader',中间用!分割
		2.加载顺序是从右到左
		3.配置文件中不要写错了,写错了可能报的错就到别的地方去了,比如在配置文件中少写了loaders中的s,到时候报错就不知道报错到哪里去了,建议拷贝
		

--------------------

# webpack 打包less

	需要的包:
		style-loader css-loader autoprefixer-loader less-loader less

	使用步骤:
		1.安装 less less-loader 包
		2.在webpack.config.js中进行配置
			```
				{
	                test:/\.less$/,
	                loader:'style-loader!css-loader!autoprefixer-loader!less-loader' //注意新开一个
	            }
			```
		
	注意点:
		1.把原先css后缀的文件名,改为less,并且在里面使用@作为占位符
		2.不要在原先css配置的loader基础上面改,最好重新再写一个{}
		3.less-loader 依赖less包

--------------------

# webpack 打包 sass

	需要的包:
		style-loader css-loader sass-loader node-sass
	
	使用步骤:
		1.安装 sass-loader node-sass 包
		2.在webpack.config.js中进行配置
			```
				{
	                test:/\.sass$/,
	                loader:'style-loader!css-loader!autoprefixer-loader!sass-loader'
	            }
			```
	
	注意点:
		1.把原先css后缀的文件名,改为sass,并且在里面使用$作为占位符
		2.不要在原先css配置的loader基础上面改,最好重新再写一个{}
		3.sass-loader依赖 node-sass
	
--------------------	

# webpack 实现图片及字体图标打包

	需要的包:
		url-loader file-loader
	
	使用步骤:
		1.安装 url-loader 及 file-loader包
		2.在webpack.config.js中进行配置
			```
				{
	                test:/\.(png|jpg)$/, //正则表达式
	                loader:'url?limit=50000' //url是url-loader的简写,后面的图片大小表示当图片小于40kb的时候,那么则将这张图片编译成base64的字符串给浏览器使用,否则将图片打包到编译文件夹中
	            }
			```
	
	文字图标:
		https://github.com/dcloudio/mui/tree/master/examples/hello-mui
		
		http://www.dcloud.io/hellomui/examples/icons-extra.html
	
	注意事项:
		1.url-loade 依赖 file-loader
		2.url?limit=xxx 的含义
		3.文字图标在原先loader的后面加上 ttf
			```
				{
	                test:/\.(png|jpg|ttf)$/, //正则表达式
	                loader:'url?limit=50000' //url是url-loader的简写,后面的图片大小表示当图片小于40kb的时候,那么则将这张图片编译成base64的字符串给浏览器使用,否则将图片打包到编译文件夹中
	            }
			```
	
	
--------------------

# webpack es6转es5的语法

	为什么要改?
		因为浏览器只识别es5的语法
		
	依赖的包:
		babel-core babel-loader babel-preset-es2015 babel-plugin-transform-runtime
		
	使用步骤:
		1.安装 babel-core babel-loader babel-preset-es2015 babel-plugin-transform-runtime 包
		2.在packweb.config.js中进行配置
			配置有两种方式:
			
			第一种:在loaders中配置一个
				```
					{
		                test:/\.js$/, //正则表达式
		                loader:'babel-loader?presets[]=es2015',
		                exclude:/node_modules/
		            }
				```
			第二种【推荐】:在loaders中配置,然后还要再配置一个babels
				```
					{
		                test:/\.js$/, //正则表达式
		                loader:'babel-loader',
		                exclude:/node_modules/
		            }
		            
		            babel:{
				        presets:['es2015'],
				        plugins:['transform-runtime']
				    }
				```
		

--------------------

# es6语法总结

	导入的写法
		
		1.没有变量接收
			import 'xxx.xxx';
			
		2.有变量接收
			import calcObj from './calc.js';
			
			//按需导入
			import {substrict} from './calc.js';
			
			import {PI} from './calc.js';
	
	导出的写法
	
		第一种:
		module.exports = {
			add,substrict
		}
		
		第二种:
		export function substrict(){
		}
		
		第三种:
		export const PI = 3.14
		
		第四种:
		export default{
			add,substrict
		}
		
	方法的写法
		箭头函数
		
		(形参1,形参2,形参N)=>{
			代码xxxx
		}
		
	注意点:
	 	如果是使用 import {xxxx} from './xxx.js'
	 	
	 	在导出时必须使用这种
	 	export const xxx = xxx;
	 	或者
	 	export function xxx = {
	 		xxxxxx
	 	}

--------------------

# Vue项目中使用到的Vue的技术点

	1.webpack
	2.利用vue-resource来请求API
	3.利用vue-router来实现路由
	4.利用vue的组件化思想来实现每个页面
	5.这个项目属于单页

--------------------

# vue项目中使用到的UI框架
	
	mint-ui:
		饿了么前端团队推出的 Mint UI 是一个基于 Vue.js 的移动端组件库
		
		http://mint-ui.github.io/#!/zh-cn
		
	mint-ui使用步骤:
		
		
	mui:
		mui不是vue的组件,只是一套css和js组成的移动端UI框架,类似于Bootstrap
		
		http://www.dcloud.io/hellomui/
		
	mui使用步骤:

------------------

