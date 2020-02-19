# webpack介绍

> 基于node.js的一个打包工具

## 作用

- 优化：工程化,vue,react, cli（可能对vue和react脚手架进行添加与修改的操作）
- 打包：将多个文件进行压缩，打包成一个文件
- 转换：es6,ts,jsx,less,sass

## 目标

- 可能通过webpack对公司现有的项目进行从0开始的搭建
- webpack当中的一些原理、流程

## 结构

- 入口：entry
- 出口：output
- 插件：plugins
- devServer
- 转换：loades
- module
- 模式：mode
  - 开发模式
  - 生产模式

## mode

- 开发（devolopment）：敲打代码的位置
- 生产（production）：打完包以后放置到服务器上所属的环境







## 安装

webpack：webpack的核心模块

webpack-cli：来执行webpack的相关命令行

```
npm i webpack webpack-cli -g
```



查看当前安装的版本号：

```
webpack-v
```





## 打包

将一个文件打包的同时，与其相关联的文件也会一起打包

0配置：不需要额外的任何配置就可以直接打包，有默认配置项

默认将src下的index.js打包到dist下的main.js

```
webpack
```



在开发环境下打包，不会进行压缩：

```
webpack --mode development
```



只打包src文件内的某一个文件：

```
webpack src/one.js --mode development
```

```
webpack src/one.js src/two.js --mode development
```



修改输出的文件名字或地址

```
webpack src/one.js src/two.js --output haha.js
```

```
webpack src/one.js src/two.js --mode development --output haha.js
```

```
demo4>webpack src/one.js src/two.js --mode development --output my/haha.js //会在根目录创建一个文件夹my
```



## 设置

### webpack.config.js

在根目录下新建webpack.config.js文件

```js
//webpack基于node
const path = require('path');//内置模块
module.exports={
    mode:'development', //--mode
    entry:'./src/user.js', //入口文件
    output:{ //出口。是一个对象，有自己的属性
        filename:'haha.js', //指定打包的文件名,默认是打包在你的dist文件当中
        // filename:'my/haha.js', //如果加了地址，那么my文件夹也是在dist里面的：dist->my->haha.js
        // path:path.resolve(__dirname,'../')+'/my', //绝对地址  在根目录外创建my
        path:__dirname +'/my', //绝对地址  在根目录下创建my
    }
}
```

#### output





### package.js

在根目录下新建package.json文件

```
npm init -y
```

```
{
  "scripts": {
    "build":"webpack src/one.js src/two.js --mode development --output dist/man.js"
  }
}
```

