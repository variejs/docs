# Routing

- [Basic Routing](#basic-routing)
  - [Views](#views)
  - [Meta](#meta)
  - [Aliaes](#aliases)
  - [Redirects](#redirects)
  - [Catch All](#catch-alls)
- [Named Routes](#named-routes)
- [Route Groups](#route-groups)
  - [Prefixing](#prefixing)
  - [Layouts](#layouts)
  - [Areas](#areas)
- [Route Middleware](#middleware)
  - [Defining Middleware](#defining-middleware)
  - [Registering Middleware](#registering-middleware)
  - [Global Middleware](#global-middleware)

## Basic Routing

All routes created must contain a view

```js
$router.route("/", Welcome);
```

### Named Views

We can also setup named views

```js
$router.route("/", {
  default: Welcome,
  sideNav: SideNav
});
```

### Meta

Sometimes its needed to add addtional functionality to our routes, we can add metadata

```js
$router.route("/admin/dashboard", AdminDashboard).setMeta({
  requiresAuth: true
});
```

### Aliases

```js
$router.route("/", "welcome").setAlias("home");
```

### Redirects

```js
$router.redirect("/", "/welcome");
```

### Catch All

```js
$router.route("*", ErrorPages.Error404);
```

## Named Routes

```js
$router.route("*", "404").setName("error");
```

## Route Groups

Router groups allow you to nest your routes with prefixes, middleware, layouts, and areas.

### Prefixing

You can easily prefix a group by using the prefix

```js
$router.prefix("/docs").group(() => {
  $router.route(":version?/:page?", Docs).setName("docs");
});
```

### Layouts

Layouts are useful to use the same layout for a specific area of the application. For instance each of Varie's documentation pages have the same layout, but the rest of the site has a different layout.

```js
$router
  .prefix("/docs")
  .layout("admin")
  .group(() => {
    $router.route(":version?/:page?", Docs).setName("docs");
  });

// Or you can set it per route!
$router.prefix("/docs").group(() => {
  $router.route(":version?/:page?", Docs);
  $router.route("admin", AdminDocs).setLayout("admin");
});
```

### Areas

Areas make it so components can be grouped under a parent.

```js
$router
  .prefix("/docs")
  .layout("public")
  .area(DocumentationArea)
  .group(() => {
    $router.route(":version?/:page?", Docs).setName("docs");
  });
```

## Middleware

You can easily attach middleware to specific routes by attaching them on the group

```js
$router
  .prefix("/docs")
  .middleware("authed")
  .group(() => {
    $router.route(":version?/:page?", Docs).setName("docs");
  });
```

### Defining Middleware

Run `$ varie make route-middleware`, which will create a new file for you to use

### Registering Middleware

You should register your middleware inside the `router/middleware/index.ts` file so its available to use.

## Global Route Middleware

// TODO

### Global Terminal Route Middleware

// TODO
