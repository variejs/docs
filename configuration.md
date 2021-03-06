Most likely you will have multiple environments for the application `dev`, `qa`, `prod`.
You may want to change some of configuration based on what type of environment your running in.

In your root directory you will find a `.env-example`. This file
should be copied over into `.env` if not already created. In that file
you are able to customize per environment.

## Environment Variables

You can pass environment variables through webpack

```js
    // webpack.config.js
    .varieConfig({
        app : {
            someKey : "someValue"
        }
    })
```

and can access them with :

```js
let version = $config.get("app.version");
```

## Accessing the Configuration

You can access the configuration values by using our helper `$config`

```js
let value = $config.get("app.name");
```

You can also set the value:

```js
$config.set("app.name", "My New App Name!");
```

## Path Aliases

Varie comes with some path aliases to help out with development.
These are customizable but cannot be removed as internal and plugin providers may use these.

```js
    {
      "@app": "app",
      "@views": "views",
      "@store": "store",
      "@config": "config",
      "@routes": "routes",
      "@models": "app/models",
      "@resources": "resources",
      "@components": "app/components",
    }
```

To customize the aliases, change the values in the `webpack.config.js` and `tsconfig.json` files.

[{.alert} Currently our CLI cannot determine what paths you have set, if your using the CLI please do not change these values]

## Custom Varie Path

If your change the location of your Varie instance (ex. /resources/assets/js), inside `package.json` add a new key :

```js
  ...

  "variePath": "resources/js",

  ...
```
