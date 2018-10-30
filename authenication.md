- [Introduction](#introduction)
- [Installation](#installation)
  - [Config](#installation)
  - [Service Provider](#serviceProvider)
- [Guards](#installation)
  - [Protecting Access](#installation)
    - [Http](#installation)
    - [Route Middleware](#installation)
- [Drivers](#drivers)
- [Store](#installation)
- [Views](#installation)
- [Service](#installation)

While there are many different ways todo auth we took two basics to get you started. You can customize these
by extending the services that we will publish for you.

We tried to make it extensible as possible to make it easy to get you up and running. We have provided two types of
authentication that we support out of the box.

- Cookie Auth
- Json Web Tokens

We publish the following files

- Auth Store
- Auth Config
- Auth Route Middleware
- Auth Service Provider
- Auth Views and Auth Route Middleware

## Installation

To get started, install the auth plugin `$ npm install varie-auth-plugin` and run the publish command.

`$ varie publish:varie-auth-plugin`

[{.info} You should have already installed the varie cli globally if not run "install --global varie-cli"]

You must then register the service provider

You need to add the service provider to the `config/app.ts`

```js
import AuthenticationServiceProvider from "@app/providers/AuthProvider";


providers: {
  ...

  AuthenticationServiceProvider

  ...
}
```

We suggest going through each of the auth documentation areas to configure the auth plugin.

## Guards

Guards define how a user must be authenticated to access the each request in your application.
Varie setups your first guard for you called "user".

The "user" guard by default uses the JWT driver. Each driver determines how to handle authentication between
the server and the user interface.

### Protecting Access

There are two ways to protect access, Route Middleware and HTTP requests. If only using one guard you can neglect
using the HTTP Requests as you skip directly into the Route Middleware.

#### Route Middleware

To protect areas of your application you will need to setup some middleware to handle these requests. We have provided
a default auth middleware that more than likely will handle everything you need.

// TODO - show example

To use this middleware please read the Route middleware documentation here. TODO -- link

#### HTTP Requests

HTTP request protection require you to specify which guard to use to access that authenticated route.

For example : We have two guards "user", "admin". To access the request "disableUser" we may need to use
different credentials than our default of "user". We can tell that request that we wish to use the
"admin" guards authentication.

```js
httpService.post("/api/disableUser/777", data, { guard: "admin" });
```

This will tell our request to use the "admin" guard's authentication.

## Drivers

Varie comes with two drivers , CookieDriver and JwtDriver.

### Cooke Driver

The cookie driver is your most basic driver in that it will try to fetch the user. If it cannot fetch the user we know they are
not logged in and will send them back to their login page.

### Jwt Driver

The JWT driver uses local storage to keep track of authentication, this allow to check if the token is there and try to fetch the user.
If it cannot fetch the user it will send them back to their login page.

### Custom Drivers

You can create custom drivers which allows you to define how to store your authentication and deal with certain actions.

## Store

You should customize the AuthStore to fit your needs, we gave you a skeleton.

## Routes / Views

When running the publish command it provided all the necessary routes and views to get auth up and running quickly.
These views were placed in 'views/auth' and 'routes/authRoutes.ts'.Feel free to customize them as however you wish.
