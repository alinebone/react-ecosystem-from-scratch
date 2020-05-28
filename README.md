# Building a React ecosystem from scratch

**What do we need**

- An entry point   
- Support ES6
- Webpack
- A root component
- React-hot-loader

---

## An entry point
1. Create a folder to hold the project
2. Go to this folder and run `npm init -y` to initialize a new npm package 
3. Run `git init` to start a git project *(optional)*
4. Create a `public` folder to hold our static code
5. Create a `src` folder to hold our React code 
6. Create an `index.html` file inside the `public` folder. This is what is sent to the client when a request to our website is made by the user.
7. Create a `div` with `id="root"` in the `index.html`. This `div` will receive the React content.
8. Add a `script` tag to load the React code: `<script src="../dist/bundle.js"></script>` (it doesn't exist yet)


