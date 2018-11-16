Varie provides an authentication plugin that helps you get auth working quickly.
After publishing the auth package, you are able to use authentication immediately
or you can tweak it to work with your previous auth system.

The system is made up of `guards` and `drivers`. These `guards` allow you to specify how
a user/request should be authenticated. You can have multiple `guards` to allow for more than
one different authentication system to be used.

A `driver` is the authentication workflow that each `guard` must follow to be correctly authenticated.
Varie providers provides two authentication drivers:

- Cookie Auth
- Json Web Tokens

## Installation

To get started, install the auth plugin `$ npm install varie-auth-plugin` and run the publish command.

`$ varie publish varie-auth-plugin`

[{.info} You should have already installed the varie cli globally if not run "$ npm install --global varie-cli"]

You must then register the service provider

You need to add the service provider to the `config/app.ts`

```js
import AuthServiceProvider from "@app/providers/AuthServiceProvider";


providers: {
  ...

  AuthServiceProvider,

  ...
}
```

Import and add the routes to your `routes` file :

```js
import authRoutes from './authRoutes'

export default function($router: RouterInterface) {

  ...

  authRoutes($router);

  ...
```

Update the configuration `config/auth` and update your `app/providers/AuthServiceProvider` to fit your needs.

[{.info} You should read all authentication documentation to learn the internals and how to customize to your application.]

## Protecting Access

There are two ways to protect access, Route Middleware and HTTP requests. If only using one guard you can neglect
using the HTTP Requests as you skip directly into the Route Middleware.

### Route Middleware

To protect areas of your application you will need to setup some middleware to handle these requests. Varie has provided
a default auth middleware that more than likely will handle everything you need.

Example :

```js
  handler(to, from, next) {
    this.authService.isLoggedIn("nameOfGuard").then(isLoggedIn => {
      if (isLoggedIn) {
        return next();
      }
      return next({
        name: "login"
      });
    });
  }
```

To use this middleware add it to the groups middleware

```js
import Auth from "./middleware/Auth";

$router
  .prefix("/admin")
  .middleware([Auth])
  .group(() => {
    $router.route("dashboard", Dashboard);
  });
```

[{.info} The auth package also comes with another middleware called `NoAuth` to make sure authenticated users cannot access these areas.]

### HTTP Requests

HTTP request protection require you to specify which guard to use to access that authenticated route.

For example : If you have two guards "user", "admin". To access the request "disableUser" you may need to use
different credentials than our default of "user". You're able to tell that request that it needs
"admin" guards authentication.

```js
httpService.post("/api/disableUser/777", data, { guard: "admin" });
```

This will tell our request to use the "admin" guard's authentication.

## Drivers

Varie comes with two drivers, CookieDriver and JwtDriver.

### Cooke Driver

The cookie driver is your most basic driver in that it will try to fetch the user. If it cannot fetch the user
the application knows they are not logged in and will send them back to their login page.

### Jwt Driver

The JWT driver uses local storage to keep track of authentication, this allow to check if the token is there and try to fetch the user.
If it cannot fetch the user it will send them back to their login page.

### Custom Drivers

You can create custom drivers which allows you to define how to store your authentication and deal with certain responses from an action.

```js
  loginResponse(response): Promise<any>;
  logoutResponse(response);
  isLoggedIn(guard: string): Promise<boolean>;
  refreshResponse?(response): Promise<any>;
  registerResponse(response): Promise<any>;
  resetPasswordResponse(response): Promise<any>;
  middlewareRequest(config): Promise<any>;
  middlewareResponse(response): Promise<any>;
```

You should look into one of the provided drivers to see how they were built and build yours based on those drivers.

## Auth Store

The published store gives you a basic layout of what you may need for your authentication system.

- State
- Actions
- Getters
- Mutations
- State Interface

Each can be customized to fit your application. The store interacts directly with the driver.
These actions send their responses to the driver, which gives the driver the
opportunity to handle with saving tokens, logging out procedures, etc.

### Guard State

Each guard should have their own user state. This allows us to detect that they are logged in and
can access pages across your app.

`store/auth/state`

```
 guards: {
    user: null
    // ...
  },
```

[{.danger} The drivers shipped with the auth plugin rely on the guard state, and is required.]

## Routes / Views

When running the publish command it provided all the necessary routes and views to get auth up and running quickly.
These views were placed in 'views/auth' and 'routes/authRoutes'. Feel free to customize them as however you wish.

- A Auth Area
- Login Page
- Register Page
- Reset Password Page
- Forgot Password Page

## Auth Service

The auth service has some helpful functions to jump start your application.

### Getting the User Data from the API

You can get the user for a guard by calling the `getUser`.

```js
this.authService.getUser("guard");
this.authService.getUser(); // uses the default guard
```

### Checking to see if the user is logged in

You can check if the user is currently logged in

```js
this.authService.isloggedIn("guard");
this.authService.isLoggedIn(); // uses the default guard
```

### Getting The User In Your Components

To get the user in your components you should use the store getter `auth/user`.

```js
this.$store.getters["auth/user"]("guardName");
this.$store.getters["auth/user"](); // uses the default guard
```
