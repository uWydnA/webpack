# loaders

## css-loader,style-loader

> 解决css文件的引入

### 安装

```js
npm i --save css-loader style-loader
```

### 配置

```js
module:{
    rules:[{
        test:/\.css$/,
        loader:'style-loader!css-loader'
    }]
}
```



## sass-loader

> 解析scss文件

### 安装

```
npm i --save sass-loader none-sass
```

### 配置

```js
module: {
	rules: [{
		test:/\.scss$/,
         loader:'style-loader!css-loader!sass-loader'
	}]
}
```



## post-css

> 解决css兼容问题

### 安装

```
npm i --save postcss-loader autoprefixer postcss
```

### 新建配置文件postcss.config.js

```js
module.exports = {
  plugins:[
    require('autoprefixer')(
      // 'last 100 versions'
      {
        browsers:[
          'last 10 Chrome versions',
          'last 5 Chrome versions',
          'Safari>=6',
          'ie>=8',
          'iOS>=8',
          'Android>=4.4',
        ]
      }
    )
  ]
}
```

### 配置

```js
module: {
	rules: [{
		test:/\.css$/,
       	 loader:'style-loader!css-loader!postcss-loader'
	},{
         test:/\.scss$/,
         loader:'style-loader!css-loader!postcss-loader!sass-loader'
    }]
}
```



## babel-loader

### 安装

```
npm i --save babel-loader@7 babel-core babel-preset-es2015
```

### 配置

```js
module: {
    rules: [{
        test:/\.js$/,
        loader:'babel-loader',
        exclude:/node_module/,//排除文件夹
        query: {
            presets: ['es2015']
        }
    }]
}
```



## vue-loader

### 安装

```js
npm i --save vue-loader vue-template-compiler
```

### 配置

```js
const {VueLoaderPlugin} = require("vue-loader");
module.exports = {
	module: {
		rules: [{
			test:/\.vue$/,
             loader:'vue-loader'
		}]
	},
    plugins: [
        new VueLoaderPlugin()
    ]
}
```

引入Vue（main.js）

```js
import Vue from 'vue';
import App from './App.vue'
new Vue({
	render:h=>h(App)
}).$mount('#app')
```

