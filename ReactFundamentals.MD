# React Fundamentals

Create empty direcory and `yarn init` hitting enter until prompt ends then add react
```
yarn add react react-dom
```

## Create `src/index.js`

In index.js import React and ReactDOM from react and react-dom respectively. (Expose react global and react dom global)

Create a component <App> and `reactDOM.render` it to `document.getElementById('app')`

```js
import React from 'react'
import ReactDOM from 'react-dom'

const App = () => <div>hello</div>

ReactDOM.render(<App />, document.getElementById('app'))
```

## Configure babel

Install [babel-loader](https://github.com/babel/babel-loader) and @babel/core for transpiling JS files

Install [@babel/preset-react](https://babeljs.io/docs/en/babel-preset-react)
for the purpose of transforming JSX to react
```js
<div> // React.createElement('div')
```
Also install [@babel/preset-env](https://babeljs.io/docs/en/babel-preset-env) which will let us use the latest JS

```
yarn add --dev babel-loader @babel/core @babel/preset-react @babel/preset-env
```

Create the `.babelrc` and add

```js
{
  "presets": [
    "@babel/preset-react",
    "@babel/preset-env",
  ]
}
```
## Configure webpack

Add webpack for bundling our assets
```
yarn add --dev webpack webpack-dev-server webpack-cli
```


Create a file called `webpack.config.js` and populate it after [docs](#sample-webpack-config)

## HTML file

Add `src/index.html` with a div with id="app" something like:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
      <meta charset="utf-8">
  </head>
  <body>
    <div id="app"></div>
  </body>
</html>
```

```
yarn add html-webpack-plugin --dev
```
and add it to module.exports in webpack config:
```js
const HtmlWebpackPlugin = require('html-webpack-plugin')
...
  plugins: [
    new HtmlWebpackPlugin({
      template: './src/index.html'
    })
  ]
```

```
yarn webpack-dev-server --open
```

## What about styling?

```
yarn add --dev css-loader style-loader
```

These will handle importing css files into react component files. However, check out [css-modules](https://github.com/css-modules/css-modules) for locally scoping CSS.

## Make a .gitignore

node_modules, dist

[React .gitignore](https://github.com/facebook/react/blob/master/.gitignore)

## Sample webpack config
(February 2020)

```js
const HtmlWebpackPlugin = require('html-webpack-plugin')

module.exports = {
  module: {
    rules: [
      {
        test: /\.js$/,
        exclude: /node_modules/,
        use: {
          loader: 'babel-loader'
        }
      },
      {
        test: /\.css$/i,
        use: ['style-loader', 'css-loader'],
      },
    ]
  },
  plugins: [
    new HtmlWebpackPlugin({
      template: './src/index.html'
    }),
  ]
}
```





