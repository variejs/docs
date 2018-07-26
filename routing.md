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
  - [layouts](#layouts)
- [Route Middleware](#middleware)
  - [Defining Middleware](#defining-middleware)
  - [Registering Middleware](#registering-middleware)

<a name="basic-routing"></a>

## Basic Routing

All routes created must contain a view

```js
$router.route("/", "welcome");
```

Maps to the view `resources/views/welcome.vue`. Also you can map to directories as well with an `index.vue`

`resources/views/Welcome/index.vue`

```js
$router.route("/", "Welcome");
```

<a name="views"></a>

### Named Views

We can also setup named views

```js
$router.route("/", {
  default: "Welcome",
  sideNav: "SideNavOption2"
});
```

<a name="meta"></a>

### Meta

Sometimes its needed to add addtional functionality to our routes, we can add metadata

```js
$router.route("/admin/dashboard", "AdminDashboard").setMeta({
  requiresAuth: true
});
```

<a name="aliases"></a>

### Aliases

```js
$router.route("/", "welcome").setAlias("home");
```

<a name="redirects"></a>

### Redirects

```js
$router.redirect("/", "/welcome");
```

<a name="catch-alls"></a>

### Catch Alls

```js
$router.route("*", "404");
```

<a name="named-routes"></a>

## Named Routes

```js
$router.route("*", "404").setName("error");
```

<a name="route-groups"></a>

## Route Groups

Router groups allow you to nest your routes with prefixes, middleware, layouts, and areas.

<a name="prefixing"></a>

### Prefixing

You can easily prefix a group by using the prefix

```js
$router.prefix("/docs").group(() => {
  $router.route(":version?/:page?", "docs").setName("docs"); // `/docs/master/routing`
});
```

<a name="layouts"></a>

### Layouts

Layouts are useful to use the same layout for a specific area of the application. For instance each of Varie's documentation pages have the same layout, but the rest of the site has a different layout.

```js
$router
  .prefix("/docs")
  .layout("admin")
  .group(() => {
    $router.route(":version?/:page?", "docs").setName("docs");
  });

// Or you can set it per route!
$router
  .prefix("/docs")
  .group(() => {
    $router.route(":version?/:page?", "docs");
    $router.route("admin", "adminDocs").setLayout("admin");
  });
```

### Areas

Areas make it so components can be grouped under a parent. 

```js
$router
  .prefix("/docs")
  .layout("public")
  .area('documentationArea')
  .group(() => {
    $router.route(":version?/:page?", "docs").setName("docs");
  });
```

<a name="middleware"></a>

## Middleware

You can easily attach middleware to specific routes by attaching them on the group

```js
$router
  .prefix("/docs")
  .middleware("authed")
  .group(() => {
    $router.route(":version?/:page?", "docs").setName("docs");
  });
```

<a name="defining-middleware"></a>

### Defining Middleware

Run `varie make route-middleware`, which will create a new file for you to use

<a name="registering-middleware"></a>

### Registering Middleware

You should register your middleware inside the `router/middleware/index.ts` file so its available to use.
