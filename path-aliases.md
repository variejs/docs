# Path Aliases

* [Standard Paths](#standard-paths)
* [Custom Paths](#custom-paths)

Varie comes with some path aliases to help out with development. These are customizable but cannot be removed as packages, and internal providers may use these.

<a name="standard-paths"></a>

## Standard Paths

```js
 "@app": path.join(__dirname, "app"),
 "@routes": path.join(__dirname, "routes"),
 "@config": path.join(__dirname, "config"),
 "@store": path.join(__dirname, "app/store"),
 "@models": path.join(__dirname, "app/models"),
 "@resources": path.join(__dirname, "resources"),
 "@views": path.join(__dirname, "resources/views"),
 "@components": path.join(__dirname, "app/components")
```

To customize change the locations in your `webpack.mix.js` and `tsconfig.json` files.
