# Environment Configuration

- [Accessing the Configuration](#accessing-the-configuration)
- [Determining Current Environment](#determining-current-environment)


Most likely you will have multiple environments for the application `dev`, `qa`, `prod`. You may want to change some of configuration based on what type of environment your running in.

Luckily Varie has it built in with dot-env. In your root directory you will find a `.env-example`. This file should be copied over into `.env` if not already created.
In that file you are able to customize per environment.

<a name="accessing-configuration-valuest"></a>
## Accessing the Configuration

You can easily access the configuration values by using our help `$config`

```js
let value = $config.get("app.name");
```

You can also easily set the value

```js
$config.set("app.name", "My New App Name!");
```

<a name="determining-current-environment"></a>
## Determining Current Environment

Your apps environment is determined by the `APP_ENV` value inside your `.env` file. It is also bound to your app container :

```js
$app.environment; // local
```