# Varie Bundler

- [Build](#build)
- [Aliases](#aliaes)
- [Adding Loaders](#adding-loaders)
- [Adding Plugins](#adding-plugins)
- [Adding Entries](#adding-entries)
- [Environment Variables](#environment-variables)

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

## Adding Loaders

Adding a loader is just as easy as using webpack it self, just give us
the rule you want to add and it will inject into the config.

Here is an example of adding markdown loader :

```js
 .addLoader({
      test: /\.md$/,
      use: [
        {
          loader: "html-loader",
        },
        {
          loader: "markdown-loader",
        },
      ],
    })
```

## Adding Plugins

Adding a plugin is just as easy as using webpack it self, just give us
the rule you want to add and it will inject into the config.

Here is an example of adding plugin :

```js
    .addPlugin(
        new webpack.ProvidePlugin({
            $: 'jquery',
            jQuery: 'jquery'
        })
    )
```

## Adding Entries

Adding a new entry consists of the name for the entry (the files output name) ,
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
