# Varie Bundler

- [Build](#build)
- [Aliases](#aliaes)
- [Adding Loaders](#adding-loaders)
- [Adding Plugins](#adding-plugins)
- [Adding Entries](#adding-entries)
- [Environment Variables](#environment-variables)
- [Analyzing Configuration](#analyzing-configuration)
- [Inspecting Configuration](#inspecting-configuration)

Varie comes with a bundler so you don't have to worry about configuration.
It also comes with a fluent interface to help modify the webpack config,
just in case you want to have more control over how your application is built.

## Build

This builds the webpack config to be used by webpack or your IDE.

## Aliases

We define some default path aliases for you already, but you can change these
to however you like

```js
  .aliases({
      "@app": path.join(__dirname, "app"),
      "@routes": path.join(__dirname, "routes"),
      "@config": path.join(__dirname, "config"),
      "@store": path.join(__dirname, "app/store"),
      "@models": path.join(__dirname, "app/models"),
      "@resources": path.join(__dirname, "resources"),
      "@views": path.join(__dirname, "resources/views"),
      "@components": path.join(__dirname, "app/components"),
    })
```

[{.alert} The Varie-CLI does not know that these have been changed, and will not correctly put files in the correct locations!]

## Webpack Chaining

The bundler is using [webpack-chain](https://github.com/mozilla-neutrino/webpack-chain), which allows a fluent interface to
add / modify the webpack configuration file.

This allows you to modify the bundler without having to change the bundler itself.

### Adding a Loader

```js
    .chainWebpack((config) => {
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

### Modifying The Config

You should get yourself familar with the [webpack-chain API](https://github.com/mozilla-neutrino/webpack-chain#getting-started)
as well as the source for [varie-bundler](https://github.com/variejs/varie-bundler)

```js
module.exports = {
  chainWebpack: config => {
    config.plugin("webpack-notifier").tap(args => {
      return [
        /* new args to pass to webpack-notifier's constructor */
      ];
    });
  }
};
```

[{.info} Add in the inspect flag, `$ npm run dev -- --inspect`, should help diagnos how to modify the webpack config with webpack-chain.]

## Adding Entries

Adding a new entry consists of the name for the entry (the files output name),
and an array of the entry.

```js
    .entry("admin", ["app/admin.ts", "resources/sass/admin.scss"])
```

## Environment Variables

Adding environment variables to the process can be handy when you
need variables from the bundler it self.

```js
    .variables({
        mode : JSON.stringify(args.mode)
    })
```

[{.alert} You may need to use JSON.stringify so that your application can correctly parse the information]

## Analyzing Configuration

To analyze your bundle with [webpack analyse](https://github.com/webpack/analyse), just add the `analyze` flag to your npm build command.

`$ npm run prod -- --analyze"

## Inspecting Configuration

To inspect your configuration just add the `inspect` flag to your npm build command.

`$ npm run prod -- --inspect"
