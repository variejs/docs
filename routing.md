## Basic Routing

To define a route you just need to define a path and a component

```js
$router.route("/", Welcome);
```

### Named Views

We can also setup named views

```js
$router.route("/", {
  default: Welcome,
  sideNav: SideNav,
});
```

### Meta

Sometimes its needed to add additional functionality to our routes, we can add metadata

```js
$router.route("/admin/dashboard", AdminDashboard).setMeta({
  requiresAuth: true,
});
```

### Aliases

```js
$router.route("/", Welcome).setAlias("home");
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

Routes are given a default name based on their path.

```js
$route.prefix("admin").group(() => {
  $router.route("/", Dashboard);
  $router.route("/users", Users);
});
```

The Dashboard route would have its route be `admin` and the Users route would be `admin.users`.

You can override them :

```js
$route.prefix("admin").group(() => {
  $router.route("/", Dashboard).setName("admin.dashboard");
  $router.route("/users", Users);
});
```

## Route Groups

Router groups allow you to nest your routes with prefixes, middleware, layouts, and areas.

### Prefixing

You can prefix a group by using the prefix

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

### Additional Data

Sometimes you need to add some data to a group so it has access to that data.

$router
        .data({ subNavText : "Welcome Back!" })
        .group(() => {
            $router.route(":version?/:page?", Docs).setName("docs");
});

You then can access that data in the component inside the meta.

```js
let subNavText = this.$route.meta.data.subNavText;
```

## Middleware

You can attach middleware to specific routes by attaching them on the group

```js
$router
  .prefix("/docs")
  .middleware(middleware.Auth)
  .group(() => {
    $router.route(":version?/:page?", Docs).setName("docs");
  });
```

### Defining Middleware

Run `$ varie make route-middleware`, which will create a new file for you to use

### Registering Middleware

You should register your middleware inside the `router/middleware/index` file so you can use
them inside your routes file.
