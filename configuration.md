## Environment Configuration

Most likely you will have multiple environments for the application `dev`, `qa`, `prod`. You may want to change some of configration based on what type of environemnt your running in.

Luckily Varie has it built in with dot-env. In your root directory you will find a `.env-example`. This file should be copied over into `.env` if not already created. In that file you are able to customize per environment.

// TODO - Further more these values will be merged into the configurations inside your app so you can use them throught the application.

## Determining the Current Environnment inside the application

Your apps enviroment is determined by the `APP_ENV` value inside your `.env` file. It is also bound to your app container :

```js
$app.environment; // local
```

## Accessing Configuration Values

You can easily access the configuraiton values by using our help `$config`

```js
let value = $config.get("app.name");
```

You can also easily set the value

```js
$config.set("app.name", "My New App Name!");
```
