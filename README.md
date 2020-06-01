# Building a React ecosystem from scratch

**What do we need?**

- An entry point   
- Support ES6 and JSX
- Webpack
- A root component
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

