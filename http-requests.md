# Http Requests

- [Requests](#requests) \*[Unregister App Middleware for a route](#unregister-app-middleware-for-a-route)

<a name="requests"></a>

## Requests

To make a request you will need to inject the `$http` service.

```js
$http.get("url", config);
$http.head("url", config);
$http.options("url", config);
$http.put("url", data, config);
$http.patch("url", data, config);
$http.post("url", data, config);
$http.delete("url", config);
```

Each returns a promise so you can get the response :

```js
$http.get("url").then(response => {
  this.data = response.data;
});
```

<a name="unregister-app-middleware-for-a-route"></a>

### Unregister App Middleware for a route

To disable a app middleware for a particular route you can use the unregistere method

```js
import MiddlewareClass from "app/middleware/MiddlewareClass";

$http
  .unregisterMiddleware(MiddlewareClass)
  .get("url")
  .then(response => {
    this.data = response.data;
  });
```
