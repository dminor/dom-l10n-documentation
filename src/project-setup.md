# Setting up a project

This tutorial will walk you through setting up a basic project with [Node Package Manager (npm)](https://www.npmjs.com/) and [Parcel](https://parceljs.org/) to use Fluent DOM.

If you don't have `npm` installed, please refer to the [previous section](./npm.md) on installing `npm`.

---

First let's create a new directory called `fluent-playground`.

```
mkdir fluent-playground
cd fluent-playground
```

Next we will create a new project using `npm`

```
npm init
```

You should now have a `package.json` file that looks something like this:

```json
{
  "name": "fluent-playground",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "",
  "license": "ISC"
}
```

---

Next we will need to add our `src` directory and some basic `index.html` and `index.js` files.

```
mkdir src
touch src/index.html
touch src/index.js
```
> ```
> fluent-playground
> ├── src
> │  ├── index.html
> │  └── index.js
> └── package.json
> ```

Populate your `index.html` with some minimal content:

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8" />
    <script defer src="index.js"></script>
  </head>
  <body>
    <h1 id="welcome">Hello</h1>
  </body>
</html>
```

---

Now we need to add the Parcel bundler to run our project.

```
npm install parcel-bundler
```

>>> :dminor: I get a warning that parcel-bundler is deprecated and we should use parcel.

You should now see that `parcel-bundler` has been added as a dependency in `package.json`

```json
"dependencies": {
  "parcel-bundler": "^1.12.5"
}
```

---

We need to add this line to `index.js`

```JavaScript
import "regenerator-runtime/runtime";
```

And then add these lines to `package.json`

```json
"browserslist": [
  "since 2019-01"
]
```

---

Next we need to tell `npm` to use `Parcel` when it starts by adding the following line to the `scripts` section in `package.json`.

```json
"start": "parcel src/index.html",
```
> ```json
> "scripts": {
>   "start": "parcel src/index.html",
>   "test": "echo \"Error: no test specified\" && exit 1"
> },
> ```

Verify that everything is working by running
```
npm start
```

which should serve your html page on `localhost`. You should see the `<h1>` element that says **Hello**.

---

In the [next section](./fluent-files.md) we will create some Fluent (`.ftl`) files and cover how to get parcel to add them as assets to your project.
