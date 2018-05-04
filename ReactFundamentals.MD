# React Fundamentals

A guide to start a react project inspired by [Tyler McGinnis' Course](https://tylermcginnis.com/courses/react-fundamentals/)

Create empty direcory and `npm init` hitting enter until prompt ends.
```
npm install react react-dom -S
```

## Make a .gitignore

node_modules, dist

[React .gitignore](https://github.com/facebook/react/blob/master/.gitignore)

## Create app/index.js and app/index.css

In index.js import React and ReactDOM from react and react-dom respectively. (Expose react global and react dom global)

create a component <App> and `reactDOM.render` it to `document.getElementById('app')`

## Configure Webpack and Babel

```
npm install --save-dev babel-core babel-loader babel-preset-env babel-preset-react css-loader style-loader html-webpack-plugin webpack webpack-dev-server webpack-cli
````

Webpack is going to take your code at entry prop, use loaders to transform, and dum in file specified in output

Create a file called `webpack.config.js` and populate it after [docs](https://webpack.js.org/concepts/) or after [Mcginnis](https://github.com/tylermcginnis/react-fundamentals/blob/first-component/webpack.config.js)

Add `mode: "development"` to exports

Add a babel property to webpack.config.json

```  
"babel": {
    "presets": ["env", "react"]
  },
```

Add `app/index.html` with a div with id="app" like [this](https://github.com/tylermcginnis/react-fundamentals/blob/first-component/app/index.html)

In `package.json` add to scripts object:

`"create": "webpack"`

In terminal 

```
npm run create
```

```
npm install --save-dev webpack-dev-server
```

Change or create start script in `package.json`

`"start": "webpack-dev-server --open"`

## First Components

We will start by explosing React global in index.js

```js
import React from 'react';
import ReactDOM from 'react-dom';
```

Now we can create and display component:

```js
class App extends React.Component {
  render() {
    return (
      <div>
        <Popular />
      </div>
    );
  }
}

ReactDOM.render(<App />, document.getElementById('app'))
```

`npm run start`

Let's move App to a 'components' directory (still inside app). We'll need to import the app into index.js:

```js
import App from './components/App'
```

Build out components from there...






