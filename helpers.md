# Helpers

* [Available Helpers](#available-helpers)

<a name="available-helpers"></a>

#### `app()` {#helper-method}

The `app` function returns the [service container](/docs/{{version}}/container) instance:

    let container = app;

Which you may use a contract name to resolve the service from the container:

    $api = app.make("$documentationService")
