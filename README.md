# Getting Started Create React App with WebPack

```
    npm init -y

    npm install react react-dom

    npm install @babel/core @babel/preset-env @babel/preset-react babel-loader

    npm install html-webpack-plugin webpack webpack-cli webpack-dev-server



```

# Add the script in the package.json

```
"scripts": {
    "build": "webpack --mode production",
    "start": "webpack serve --mode development"
  },
```

# Create file

## webpack.config.js

```
const path = require("path");
const HtmlWebpackPlugin = require("html-webpack-plugin");
module.exports = {
  entry: "./src/index.js",
  output: {
    filename: "main.js",
    path: path.resolve(__dirname, "build"),
  },
  plugins: [
    new HtmlWebpackPlugin({
      template: path.join(__dirname, "public", "index.html"),
    }),
  ],
  devServer: {
    static: {
      directory: path.join(__dirname, "build"),
    },
    port: 3000,
  },
  module: {
    // exclude node_modules
    rules: [
      {
        test: /\.(js|jsx)$/,
        exclude: /node_modules/,
        use: ["babel-loader"],
      },
    ],
  },
  // pass all js files through Babel
  resolve: {
    extensions: ["*", ".js", ".jsx"],
  },
};

```

## <br/>

---

## .babelrc

---

```
    {
    "presets": [
      "@babel/preset-env",
      ["@babel/preset-react", {
      "runtime": "automatic"
    }]
    ]
  }

```

---

# Create a folder src/ and public/

---

## In the src/ folder

---

## index.js

```
import React from "react";
import ReactDOM from "react-dom/client";
import App from "./App";

const root = ReactDOM.createRoot(document.getElementById("root"));

root.render(<App />);

```

## App.js

```
import React from "react";

const App = () => {
  return (
    <div>
      <h2>App Component</h2>
    </div>
  );
};

export default App;

```

## <br/>

## <br/>

## <br/>

# In the public/ folder

---

## index.html

```
<!DOCTYPE html>
<html lang="en">

<head>
    <title>React with Webpack</title>
</head>

<body>
    <div id="root"></div>
</body>

</html>
```

---

## Folder Structure

---

<img src="./public/image.png"/>
