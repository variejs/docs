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

- Custom Bundlers
- [Bundle Analyzer](https://github.com/webpack-contrib/webpack-bundle-analyzer)
- Modern builds with legacy fallback

### Basic Example

```js
import { WebBundler } from "varie-bundler";

export default function(env) {
  return new WebBundler(env)
    .entry("app", ["app/app.ts", "resources/sass/app.scss"])
    .aliases({
      "@app": "app",
      "@views": "views",aliases
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

To build your application you just need to run

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

## Aggressive Vendor Splitting

Aggressive vendor splitting splits all of your vendors into individual bundles to leverage HTTP2. This should
increase the loading performance of your application.

```js
    .aggressiveVendorSplitting()
```

## Copying Files

To copy a directory / file you can multiple copy commands.

```js
    .copy('resources/assets/fonts') // outputs to fonts
    .copy('resources/assets/fonts', 'resources/fonts') // outputs to resources/fonts
```

## Stopping Cleaning of Dist Folder

Sometimes you don't want to clean the dist folder entirely.

```js
    .dontClean('public/index.php')
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

## ESLint

To enable EsLint checking

```js
  .eslint()
```

## Global Sass Sheets

You can add global styles to your Vue components.

```js
    .globalSassIncludes([
        "resources/sass/variables/index"
    ])
```

## Loading HTML files

If your application needs to parse through html files you can add the html loader

```js
  .html()
```

## HTML Variables

If you want to add some variables to your index.html such as a version number or envrioment variable

```js
    .htmlVariables({
        VERSION : '1.0'
    })
```

## Custom Varie Bundler Plugins

You can add custom Varie plugins by sending the entire plugin to the bundler.

```js
   .plugin(MyCustomPlugin)
```

An example plugin is [Varie Tailwindcss Plugin](https://github.com/variejs/tailwincss-builder-plugin)

## Proxying Requests

You may need to proxy your requests to your backend.

This example will proxy anything that is `http://localhost/api*` to `http://varie.test/api/*` :

```js
  .proxy("/api", "http://varie.test")
```

## PurgeCss

To purge unused CSS you can easily add the purge css plugin

```js
  .purgeCss(["app", "views", "node_modules/varie"])
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

### Adding a Loader / Plugin using Webpack Chain

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
export default {
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

### Purge CSS

To remove unused CSS from your application, you can use the `.purgeCss` method to scan all files for those classes.

```js
   .purgeCss([
     'app',
     'views',
     'node_modules/varie'
   ], {
    whiteListPatterns: [],
    whitelistSelectors: [],
    whitelistPatternsChildren: [],
})
```

To Learn more about white listing please visit the PurgeCSS webpack plugin's documentation [https://github.com/FullHuman/purgecss-webpack-plugin](https://github.com/FullHuman/purgecss-webpack-plugin).

#### JSX

To enable JSX pass `jsx` in the babel options.

```js
// babel.config.js
export default {
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
import { WebBundler } from "varie-bundler";

export default function(env) {
  return new WebBundler(env, {
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
}
```

## UMD Bundler

If you need to build a UMD modules for you application use the `UmdBundler`

```js
import { WebBundler, UmdBundler, multiCompiler } from "varie-bundler";

export default function(env) {
  let configs = {};

  configs["web"] = new WebBundler(env).entry("app", [
    "app/app.ts",
    "resources/sass/app.scss",
  ]);

  configs["some-plugin"] = new UmdBundler(
    env,
    "PluginName",
    "plugin/some-plugin.ts",
  );

  return multiCompiler(configs);
}
```

[{.alert} The `multiCompiler` function is only required when using multiple bundlers!]

## Custom Bundlers

Since we are using typescript it is easy to create your own bundlers based on the Varie Bundler.

A good starting point is just to look at one of the bundlers we provide such as the `WebBundler`:

```js
export default class WebBundler extends AbstractBundler {
  constructor(
    mode: EnvironmentTypes = EnvironmentTypes.Development,
    config: DeepPartial<BundlerConfig> = {},
  ) {
    super(mode, config);

    new loaders.Vue(this, this.config.vue);

    new loaders.Sass(this, {
      hashType: this.config.hashType,
    });

    new loaders.Fonts(this);
    new loaders.Images(this);

    new plugins.Html(this);
    new plugins.Clean(this, this.config.plugins.clean);
  }
}

[{.alert} Your custom bundler should include entries to allow webpack to parse the data!]
```
