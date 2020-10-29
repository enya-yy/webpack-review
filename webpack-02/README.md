# webpack

## 预览

- [image文件处理](#image)
- [filter-loader参数](#file-loader)

## image文件处理 <a name = "image"></a>

js中引入图片
```javascript
// main.js
const src = require('./images/a.png')
const image = new Image()
image.src = src
document.body.appendChild(image)
```
css中引入图片
```css
// index.css
.avatar {
  width: 100px;
  height: 100px;
  border-raidus: 50%l
  background-image url('./images/a.png')
}
```

```javascript
// webpack.config.js
const WebpackWithImageLoader = require('webpack-withimage-loader')
module.exports = {
  entry: './src/main.js',
  output: {
    path: path.resolve(__dirname, 'dist'),
    filename: 'bundle.js'
  },
  module: {
    rules: [
      {
        test: /\.(png|jpg|gif|svg|bmp)$/,
        use: 'file-loader'
      },
      {
        test: /\.(html|htm)/,
        use: 'html-withimage-loader'
      }
    ]
  }
}
```

html中引入图片
```html
  <div>
    <img src="./images/a.png">
  </div>
```

filer-loader是解析图片地址，把图片从源位置拷贝到目标位置并且修改原引用地址。
可以处理任意的二进制数据。

在html中引入图片时，需要借助html-withimage-loader将html中的图片路径改为file-loader拷贝的文件路径。

## file-loader参数 <a name = "file-loader"></a>

```javascript
  module: {
    rules: [
      {
        test: /\.(png|jpg|gif|bmp|svg)$/,
        use: {
          loader: 'file-loader',
          options: {
            // 当前处理资源的输出目录
            outputPath: '/images'
          }
        }
      }
    ]
  }
```

```
-dist
--images
---ji1238-23j3i12-213j1i.png
--main.j3j3i1u891j.js
--index.html
```















## Table of Contents

- [About](#about)
- [Getting Started](#getting_started)
- [Usage](#usage)
- [Contributing](../CONTRIBUTING.md)

## About <a name = "about"></a>

Write about 1-2 paragraphs describing the purpose of your project.

## Getting Started <a name = "getting_started"></a>

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes. See [deployment](#deployment) for notes on how to deploy the project on a live system.

### Prerequisites

What things you need to install the software and how to install them.

```
Give examples
```

### Installing

A step by step series of examples that tell you how to get a development env running.

Say what the step will be

```
Give the example
```

And repeat

```
until finished
```

End with an example of getting some data out of the system or using it for a little demo.

## Usage <a name = "usage"></a>

Add notes about how to use the system.
