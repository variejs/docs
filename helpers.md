Varie has a few helpers that can help speed up your development.

## `app()`

The `app` function returns the [service container](/docs/{{version}}/container) instance:

```js
let container = app;
```

Which you may use a contract name to resolve the service from the container:

```js
$api = app.make("$documentationService");
```

[{.alert} While this is possible, you should try to use the Dependency Injection where possible. ]

## `$config.get('app.name')`

The config function gets the value of a configuration variable.
The configuration values may be accessed using "dot" syntax, which includes the name of the file and the option you wish to access.
A default value may be specified and is returned if the configuration option does not exist:

```js
$config.get("env.ENV", "development");
```
