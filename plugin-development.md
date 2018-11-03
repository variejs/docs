To develop a Varie plugin there a few things that you must do to
make it usable by Varie.

## Service Provider

You should create a service provider which tells the application how to
register and boot the plugin.

```js
import ServiceProvider from "varie/lib/support/ServiceProvider";

export default class YourPluginServiceProvider extends ServiceProvider {
  public boot() {
    // ...
  }

  public register() {
    // ...
  }
}
```

To understand how to register and boot service providers, check out the
[service container documentation](/docs/{{version}}/container).

## Publishing Assets

If you wish to publish assets for your plugin you must do two things.

1.  Create a directory inside the root of your directory called `publish`
2.  Inside your `package.json` add a new property `variePublishable` and set it to true.

```js
    ...
       "variePublishable": true
    ...
```

This will allow the use of the `varie publish` command which will find your
package to let them publish their assets.
