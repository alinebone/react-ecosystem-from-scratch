# Building a React ecosystem from scratch

**What do we need?**

- An entry point   
- Support ES6 and JSX
- Building and serving with Webpack
- React-hot-loader

---

## An entry point
1. Create a folder to hold the project
2. Go to this folder and run `npm init -y` to initialize a new npm package 
3. Create a `public` folder to hold our static code
4. Create a `src` folder to hold our React code 
5. Create an `index.html` file inside the `public` folder. This is what is sent to the client when a request to our website is made by the user.
6. Create a `div` with `id="root"` in the `index.html`. This `div` will receive the React content.
7. Add a `script` tag to load the React code: `<script src="../dist/bundle.js"></script>` (it doesn't exist yet)

## Support ES6 ans JSX
1. Install Babel compiler `npm i --save-dev @babel/core @babel/cli @babel/preset-env @babel/preset-react`
2. Create a `.babelrc` file in the root of the project to tell Babel which presets and plugins should be used to transpile the code
3. Insert a json object inside this file with *preset-env* (transform ES6 in VanillaJS) and *preset-react* (understands JSX): `{"presets": ["@babel/preset-env", "@babel/preset-react"]}`

## Building and serving with Webpack
1. Install `react` and `react-dom` to be able to run a React project: `npm i react react-dom`
2. Create the `index.js` and `App.js` files inside the `src` folder to start coding the application

index.js
```jsx
import React from "react";
import ReactDOM from "react-dom";
import App from "./App";

ReactDOM.render(<App/>, document.getElementById("root"));
```
App.js
```jsx
import React from "react";

const App = () => <div>Hello</div>;

export default App;
```
3. Install `webpack` to build and serve the project `npm i --save-dev webpack webpack-cli webpack-dev-server style-loader css-loader babel-loader`
4. Create a `webpack.config.js` file in the root directory and add:
```javascript
const path = require('path');
const webpack = require('webpack');

module.exports = {
  entry: './src/index.js',
  mode: 'development',
  module: {
    rules: [
      {
        test: /\.(js|jsx)$/,
        exclude: /(node_modules)/,
        loader: 'babel-loader',
        options: { presets: ["@babel/env"] }
      },
      {
        test: /\.css$/,
        use: ["style-loader", "css-loader"]
      }
    ]
  },
  resolve: { extensions: ['*', '.js', '.jsx'] },
  output: {
    path: path.resolve(__dirname, 'dist/'),
    publicPath: '/dist/',
    filename: 'bundle.js'
  },
  devServer: {
    contentBase: path.join(__dirname, 'public/'),
    port: 3000,
    publicPath: 'http://localhost:3000/dist/',
    hotOnly: true
  },
  plugins: [new webpack.HotModuleReplacementPlugin()]
};

```
5. Run the server `npx webpack-dev-server --mode development`. It will run in the port 3000.
6. To make it easier, add the following script in the `package.json file`: `"dev": "npx webpack-dev-server --mode development"`

## React-hot-loader
1. Enable auto-reload installing react-hot-loader `npm i --save-dev react-hot-loader`
2. Add `import {hot} from "react-auto-loader"` and `export default hot(module)(App)` in the `App.js` file
