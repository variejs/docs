# Service Container

- [Bindings](#bindings)
  - [Basic Binding](#basic-binding)
  - [Singleton Binding](#singleton-binding)
  - [Binding Interfaces to Implementations](#binding-interfaces-to-implementations)
- [Resolving Dependencies](#resolving-dependencies)
- [Component Injection](#component-injection)

The service container is a way to manage dependencies and performing dependency injection. We have wrapped [Inversify](http://inversify.io) for our container. It is important to understnad this concept as Varies core its built with the injection system.

## Bindings

You should for the most part always bind in a service provider, and we have provided one for you to get started in `app/providers`.

### Basic Binding

Within your service provider you have access to `this.app` which is your app instance and can bind things to it. We are able to bind and resolve with the `app` object.

```js
this.app.value("$searchService", () => {
  return new SearchService(this.app.make("$httpClient"));
});
```

### Singleton Binding

We also can bind a singleton instance so we may only want to resolve once.

```js
this.app.singleton("$searchService", () => {
  return new SearchService(this.app.make("$httpClient"));
});
```

### Binding Interfaces to Implementations

Binding a interafce to an implemenation allows us to inject its implementation just based on the interface we want to use. For instance, we have a `HttpInterface`. Then we have a implementation of that interface, lets say `Axios`. Now we can resolve `$httpClient` to Axios.

```js
this.app.bind < HttpInterface > ("$httpClient", Axios);
```

By doing this it allows us switch out implementations quickly without changing the rest of our application!

## Resolving Dependencies

To resolve from the container, we just need to make a simple call from the app

```js
let $httpClient = this.app.make("$httpClient");
```

### Component Injection

Its also important to note that you can do automatic injection within components :

```vuejs
export default Vue.extend({
  $inject: ["$httpClient"]
});
```

This will bind `$httpClient` to the component just like any other method.
