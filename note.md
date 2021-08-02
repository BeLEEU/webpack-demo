
```
npm init -y
npm install webpack webpack-cli -D
npm run build
npm install html-webpack-plugin -D
npm install webpack-dev-server -D
```

```
### webpack.config.js 文件
const path = require('path')
const HtmlWebpackPlugin = require('html-webpack-plugin')
module.exports = {
    mode: 'development',//production
    entry: path.join(__dirname, 'src', 'index.js'),
    output: {
        filename: 'bundle.js',
        path: path.join(__dirname, 'dist')
    },
    plugins: [
        new HtmlWebpackPlugin({
            template: path.join(__dirname, 'src', 'index.html'),
            filename: 'index.html'
        })
    ],
    devServer: {
        port: 3000,
        contentBase: path.join(__dirname, 'dist')
    }
}
```
## webpack配置步骤
1.首先用```npm init -y```初始化```package.json```环境，然后再安装```npm install webpack webpack-cli -D```，创建```webpack.config.js```文件

2.创建src，并添加index的js和html文件，在```package.json scripts```中配置```"build": "webpack --config webpack.config.js"```，执行```npm run build```

3.安装```npm install html-webpack-plugin -D``` 和 ```npm install webpack-dev-server -D```，再在```package.json scripts```中配置```"dev": "webpack server --config webpack.config.js"```

4.执行```npm run dev```
 
 ## babel配置步骤
1.安装 ```npm install @babel/core @babel/preset-env babel-loader -D```

2.创建```.babelrc```,在里面写
```
{
    "presets": ["@babel/preset-env"]
}
```
3.在```webpack.config.js```里面添加
```
 module: {
        rules: [
            {
                test: /\.js$/,
                use: ['babel-loader'],
                include: path.join(__dirname, 'src'),
                exclude: /node_modules/
            }
        ]
    },
```


