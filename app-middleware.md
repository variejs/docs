# App Middleware

- [Defining Middleware](#defining-middleware)
- [Registering Middleware](#registering-middleware)

<a name="defining-middleware"></a>

## Defining Middleware

Start by using the Varie CLI

`varie make:app-middleware your-middleware-name`

You will have three functions

```js
    public request(config: object) {
      return config;
    }

    public response(response: object) {
      return response;
    }

    public responseError(error) {
      return Promise.reject(error);
    }
```

You have availability to customize how you want the request / response and what the responseError should do if it does indeed fail.
You can take a look at the included middleware `app/middleware/LoadingScreen.ts` for a example of what you might do.

<a name="registering-middleware"></a>

## Registering Middleware

To register you will need to open the `index.ts` file inside the middleware folder and add it in the correct spot.
This allows you to customize the order of your middleware.
