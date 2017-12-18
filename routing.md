# Routing

## Basic Routing

All routes created must contain a view. FOr instance :

```js
$router.route("/", "welcome");
```

Maps to the view `resources/views/welcome.vue`. Also you can map to directories as well with an `index.vue` :

`resources/views/Welcome/index.vue`

```js
$router.route("/", "Welcome");
```

## Routing Groups / Nesting

Router groups allow you to nest your routes with prefixes, middleware , and templates.

##3 Prefix You can easily prefix a group by using the prefix

```js
$router.prefix("/docs").group(() => {
  $router.route(":version?/:page?", "docs").setName("docs"); // `/docs/master/routing`
});
```

##3 Template Areas Template areas are useful to use the same layout for a specific area of the application. For instance each of Varie's documentation pages have the same layout, but the rest of the site has a different layout.

```js
$router.template("/docs", "documentationArea").group(() => {
  $router.route(":version?/:page?", "docs").setName("docs");
});
```

### Middleware

You can easily attach middleware to speific routes by attaching them on the group by writing

```js
$router
  .template("/docs", "documentationArea")
  .middleware("authed")
  .group(() => {
    $router.route(":version?/:page?", "docs").setName("docs");
  });
```

## Redirect / Aliases

$router.redirect('/', '/welcome)

```js
$router.route("/", "welcome").alias("home");
```

## Catch All Routes

```js
$router.route("*", "404");
```
