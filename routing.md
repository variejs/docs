# Routing

* [Basic Routing](#basic-routing)
  * [Views](#views)
  * [Meta](#meta)
  * [Aliaes](#aliases)
  * [Redirects](#redirects)
  * [Catch All](#catch-alls)
* [Named Routes](#named-routes)
* [Route Groups](#route-groups)
  * [Prefixing](#prefixing)
  * [Templates](#templates)
* [Route Middleware](#middleware)
  * [Defining Middleware](#defining-middleware)
  * [Registering Middleware](#registering-middleware)

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

### Views

// show how we can use multiple components / single component , setting meta and name here too

<a name="meta"></a>

### Meta

<a name="aliases"></a>

### Aliases

```js
$router.route("/", "welcome").alias("home");
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

<a name="route-groups"></a>

## Route Groups

Router groups allow you to nest your routes with prefixes, middleware , and templates.

<a name="prefixing"></a>

### Prefixing

You can easily prefix a group by using the prefix

```js
$router.prefix("/docs").group(() => {
  $router.route(":version?/:page?", "docs").setName("docs"); // `/docs/master/routing`
});
```

<a name="templates"></a>

### Templates

Template areas are useful to use the same layout for a specific area of the application. For instance each of Varie's documentation pages have the same layout, but the rest of the site has a different layout.

```js
$router.template("/docs", "documentationArea").group(() => {
  $router.route(":version?/:page?", "docs").setName("docs");
});
```

<a name="middleware"></a>

## Middleware

You can easily attach middleware to specific routes by attaching them on the group

```js
$router
  .template("/docs", "documentationArea")
  .middleware("authed")
  .group(() => {
    $router.route(":version?/:page?", "docs").setName("docs");
  });
```

<a name="defining-middleware"></a>

### Defining Middleware

<a name="registering-middleware"></a>

### Registering Middleware
