Varie comes with a bundler so you don't have to worry about configuration.
It also comes with a fluent interface to help modify the webpack config,
just in case you want to have more control over how your application is built.

## Features

There is is quite a bit that goes into a webpack bundler. You may need to
customize some options, this is what is being used in our bundler :

- [Babel](https://github.com/babel/babel)
- [SASS](https://github.com/webpack-contrib/sass-loader)
- [HTML](https://github.com/webpack-contrib/html-loader)
- [cssnano](https://cssnano.co/)
- [TypeScript](https://github.com/TypeStrong/ts-loader)
- [Browsersync](https://www.browsersync.io/)
- [autoprefixer](https://github.com/postcss/autoprefixer)
- [Aggressive Code Splitting](https://github.com/webpack/webpack/tree/master/examples/http2-aggressive-splitting)
- [Hot Module Reloading (HMR)](https://webpack.js.org/concepts/hot-module-replacement/)
- [Case Sensitivity Path Checks](https://github.com/Urthen/case-sensitive-paths-webpack-plugin)
- [Automation of cleaning of old builds](https://github.com/johnagan/clean-webpack-plugin)
- [Image optimizations for JPEG / PNG / GIF](https://github.com/tcoopman/image-webpack-loader)
- [Vue](https://vuejs.org/v2/guide/installation.html#Runtime-Compiler-vs-Runtime-only)
  - Uses runtime only
  - To use the runtime and compiler checkout [Using Vue Runtime & Compiler](#using-vue-runtime-compiler).

### Advanced Features

- [Bundle Analyzer](https://github.com/webpack-contrib/webpack-bundle-analyzer)
- Modern builds with legacy fallback

### Basic Example

```js
const VarieBundler = require("varie-bundler");

module.exports = function(env) {
  return new VarieBundler(env)
    .entry("app", ["app/app.ts", "resources/sass/app.scss"])
    .aliases({
      "@app": "app",
      "@views": "views",
      "@store": "store",
      "@config": "config",
      "@routes": "routes",
      "@models": "app/models",
      "@resources": "resources",
      "@components": "app/components",
    })
    .build();
};
```

## Running the build

To build your applicatyion you just need to run

`$ npm run dev` or if you wish to build a modern build `$ npm run dev-modern`

## Aliases

We define some default path aliases for you already, but you can change these
to however you like

```js
  .aliases({
      "@app": "app",
       "@views": "views",
       "@store": "store",
       "@config": "config",
       "@routes": "routes",
       "@models": "app/models",
       "@resources": "resources",
       "@components": "app/components",
    })
```

[{.alert} The Varie-CLI does not know that these have been changed, and will not correctly put files in the correct locations!]

## Adding Entries

Adding a new entry consists of the name for the entry (the files output name),
and an array of the entry.

```js
    .entry("admin", ["app/admin.ts", "resources/sass/admin.scss"])
```

## Aggressive Splitting

Aggressive splitting splits your bundle into smaller chunks to allows the browser to leverage HTTP2. This should
increase the loading performance of your application.

```js
    .aggressiveSplitting(minSize = 30000, maxSize = 50000)
```

## Copying Files

To copy a directory / file you can multiple copy commands.

```js
    .copy(path.join('resources/assets/fonts')) // outputs to fonts
    .copy(path.join('resources/assets/fonts'), 'resources/fonts') // outputs to resources/fonts
```

## Stopping Cleaning of Dist Folder

Sometimes you don't want to clean the dist folder entirely.

```js
    .dontClean(path.join('public/index.php'))
```

## Environment Variables

You may need to setup some variables that are needed per environment within your application.

```js
    .varieConfig({
        app : {
            someKey : "someValue"
        }
    })
```

You then can access them with the `$config` helper

```js
$config.get("app.someKey");
```

## Custom Varie Bundler Plugins

You can add custom Varie plugins by sending the entire plugin to the bundler.

```js
   .plugin(MyCustomPlugin)
```

## proxy

You may need to proxy your requests to your backend.

```js
  .proxy("/api", "http://varie.test")
```

## Web Workers

If you have any web workers, you can enable the loader necessary for those to work correctly.

```js
  .webWorkers()
```

## browserSync

If you wish to use browserSync :

```js
  .browserSync()
```

## Webpack Chaining

The bundler is using [webpack-chain](https://github.com/mozilla-neutrino/webpack-chain), which allows a fluent interface to
add / modify the webpack configuration file.

This allows you to modify the bundler without having to change the bundler itself.

### Modifying The Config

You should get yourself familiar with the [webpack-chain API](https://github.com/mozilla-neutrino/webpack-chain#getting-started)
as well as the source for [varie-bundler](https://github.com/variejs/varie-bundler)

```js
   .chainWebpack((config, env) => {
        config.when(!env.isProduction, () => {
             config.plugin("webpack-notifier").tap(args => {
             return [
               /* new args to pass to webpack-notifier's constructor */
             ];
           });
       });
    });
```

[{.info} Add in the inspect flag, `$ npm run dev -- --inspect`, should help diagnos how to modify the webpack config with webpack-chain.]

### Adding a Loader

```js
    .chainWebpack((config, env) => {
        config.module
          .rule('markdown')
          .test(/\.md$/)
          .use('html')
            loader('html-loader')
            .end()
          .use('markdown')
            .loader('markdown-loader')
            .options({
                //
            })
            .end()
    });
```

### Adding a Plugin

```js
    .chainWebpack((config) => {
        config.plugin('webpack-notifier')
            .use(WebpackNotifierPlugin, [argument1, argument2])
            .end()
    });
```

## Analyzing Configuration

You can analyze your bundle with [webpack analyse](https://github.com/webpack/analyse)

```
$ npm run analyze-dev
$ npm run analyze-prod
```

## Inspecting Configuration

To inspect your configuration add the `inspect` flag to your npm build command.

```
$ npm run inspect-dev
$ npm run inspect-prod
```

## Browser Comparability

Varie provides ways to choose your browser capability with The `.browerlistrc` and the `babel.config.js`.

### BrowserList

The BrowserList file allows to specify which browsers should be compatible with your build. These configurations
will be used by `autoprefixer` and `babel`.

Varie uses `defaults` for its default which you can see on [browserl.ist](https://browserl.ist/)

### Babel.config.js

This config allows you to pass all options into `@babel/preset-env`, you can review those options (here)[https://babeljs.io/docs/en/babel-preset-env].

### Polyfills

```js
// babel.config.js
module.exports = {
  presets: [
    [
      "varie-app",
      {
        polyfills: ["es6.symbol"],
      },
    ],
  ],
};
```

#### JSX

To enable JSX pass `jsx` in the babel options.

```js
// babel.config.js
module.exports = {
  presets: [
    [
      "varie-app",
      {
        jsx: true,
      },
    ],
  ],
};
```

#### BrowserList

BrowserList is a way to manage what browsers you support. There is a file called `browserlistrc` which determines
what features should be compatible with.

### Modern Build

The bundler supports a modern build configuration in which it will build two sets of assets. One that produces a
legacy bundle for older browsers that do not support some of the newer features.

- Browsers that support the `type` of `module` will download the modern build.
- Legacy browsers will not download the modern build and instead will use the legacy build automatically
  - The Safari 10 fix is automatically injected into the template


```
$ npm run dev-modern
$ npm run prod-modern
```


[{.info} While the size may seem small, the code parsing and evaluation should improve overall performance of your app.]

## Using Vue Runtime & Compiler

To use the runtime and compiler you can pass in via the options parameter :

```js
const VarieBundler = require("varie-bundler");

module.exports = function(env) {
  return new VarieBundler(env, {
    vue: {
      runtimeOnly: false,
    },
  })
    .entry("app", ["app/app.ts", "resources/sass/app.scss"])
    .aliases({
      "@app": "app",
      "@views": "views",
      "@store": "store",
      "@config": "config",
      "@routes": "routes",
      "@models": "app/models",
      "@resources": "resources",
      "@components": "app/components",
    })
    .build();
};
```
