# webpack基础介绍

> Webpack可以看做是模块打包机： 
>
> 它做的事情是，分析你的项目结构，找到JavaScript模块(commonJs)以及其它的 一些浏览器 不能直接运行的拓展语言（Scss，jsx,.vue等），并将其打包为合适的格式以供浏 览器使 用。

## 基本配置项讲解

### 安装

```
npm init
```

```
npm i --save webpack webpack-cli
```

### 修改package.json

开发环境：

```
webpack ‐‐mode development ‐‐watch
```

生产环境

```
webpack --mode production
```



## 入口与出口及单页面与多页面

### 创建webpack.config.js

### entry

```js
//可以多个入口
entry: {
	'name'  : __dirname+'/src/index.js',
	'name2' ：__dirname+'/src/main.js'
}
```



### output

```js
output: {
    path: __dirname+'/dist',
    filename: "[name].bundle.js",
    publicPath:"/dist/" //webpack output is served from,把文件放在内存中，虚拟的路径可以访问到我们的生成文件
}
```



## webpack-dev-server

### 安装

```
npm i --save webpack-dev-server
```

### 配置

```js
devServer: {
    contentBase: './',//根目录在当前文件目录
    port: '8080',
    inline: true,//实时刷新
    proxy:{}//反向代理
}
```

运行

```
 webpack‐dev‐server ‐‐mode development //不会生成dist文件
```



## source-map

> 映射源代码， 方便调试

由于经过webpack进行dev或者build后，原js文件会套用webpack的模板，甚至压缩，从而使得当代码出现错误时，定位到的经过修改的js文件上，会显得晦涩难懂，因此我们需要source-map用于映射源码，从而方便我们查看源码查找错误来源

### 配置

```js
devtool: 'source‐map'
```

