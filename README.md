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
