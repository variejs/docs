# Helpers 

- [Available Helpers](#available-helpers)

<a name="available-helpers"></a>
#### `app()` {#helper-method}

The `app` function returns the [service container](/docs/{{version}}/container) instance:

    let container = app;

You may contract name to resolve it from the container:

    $api = app.make("$documentationService")