# webpack #

[webpack](https://webpack.js.org)是一个前端资源打包工具，你可以选择将css，scss，less，img全部打包成js文件。现在前端开发都是使用webpack配合框架来构建项目；初次使用webpack是配合前端框架[vue](https://cn.vuejs.org),使用vue-cli脚手架搭建的项目，先说下使用vue-cli遇到的问题。

## vue-cli ##

使用vue-cli脚手架搭建环境
1. 先使用**npm install -g vue-cli**安装全局vue-cli

2. 使用**vue init webpack 你的项目名**基于webpack构建项目
    >使用该命令，系统会进行安装步骤，可以直接回车不用管。  
    **Use ESLint to lint your code**是官网默认推荐使用ESLint语法检测。  
    **Set up unit tests**是否安装单元测试。  
    **Setup e2e tests with Nightwatch**是否安装e2e测试

3. 使用**npm install**安装模块  

## 目录 ##  

<img src="./img/微信图片_20180123100459.png"/>  

目录|介绍  
-|- 
build|基于webpack项目构建相关代码
config|项目开发环境配置相关代码 
node_modules|项目依赖相关模块 
src|源代码目录 
static|静态资源文件目录  
dist|打包后生成的目录  

## ESlint ##
[ESlint](https://eslint.org/)是一种严格模式开发，在前面安装脚手架时，官网就推荐使用**ESlint**开发，如果不习惯使用**ESlint**，可以在**build**目录下的webpack.base.config文件里注释掉这段代码：
```
    ...(config.dev.useEslint ? [createLintingRule()] : []),
```

## scss ##
在实际开发中，，不管是使用scss，还是less都会碰到需要引用全局样式。如果在入口文件里面引入全局scss或less，实现不了效果，会编译不了scss和less文件，在每个组件里面引入的话太过麻烦。那就只能从webpack的配置中入手，想要引入全局scss，就需要在**build**目录下的utils文件里面对应的scss设置：
```
    scss: generateLoaders('sass').concat(
      {
        loader: 'sass-resources-loader',
        options: {
          resources: path.resolve(__dirname, 实际项目路径)
        }
      }
    ),
```
在实际项目路径写入需要引入的全局scss就可以使用了。


    

    




