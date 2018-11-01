The service container is a way to manage dependencies and performing dependency injection. We have wrapped [Inversify](http://inversify.io) for our container. It is important to understand this concept as Varies core its built with the injection system.

## Bindings

You should for the most part always bind in a service provider, and we have provided one for you to get started in `app/providers`.

### Basic Binding

Within your service provider you have access to `this.app` which is your app instance and can bind things to it. We are able to bind and resolve with the `app` object.

```js
this.app.value("$searchService", () => {
  return new SearchService(new SomeSearchClass());
});
```

### Singleton Binding

We also can bind a singleton instance so we may only want to resolve once.

```js
this.app.singleton("$searchService", () => {
  return new SearchService(new SomeSearchClass());
});
```

### Binding Interfaces to Implementations

Binding a interface to an implementation allows us to inject its implementation just based on the interface we want to use.
For instance, we have a `DocumentationInterface`. Then we have a implementation of that interface, lets say `VarieDocumentationService`. Now we can resolve `DocumentationService` to VarieDocumentationService.

```js
this.app.bind <
  DocumentationInterface >
  ("DocumentationService", VarieDocumentationService);
```

By doing this it allows us switch out implementations quickly without changing the rest of our application!

## Resolving Dependencies

To resolve from the container, we just need to make a call from the app

```js
let documentationService = this.app.make("DocumentationService");
```

### Component Injection

Its also important to note that you can do dependency injection within components :

```js
 $inject: ["DocumentationService"]
  computed : {
    menu() {
        return this.documentationService.getMenu();
    }
  }
```

This will bind `$http` to the component just like any other method.

### Framework Services Available

Varie registers some services that help boot the application. And are available to you
to help development.

- `formService` : [Forms](/docs/{{version}}/forms)
- `httpService` : [Http Requests](/docs/{{version}}/requests)
- `stateService` : [State Management](/docs/{{version}}/state)
- `alertService` : [Alerts](/docs/{{version}}/alerts)
- `configService` : [Configuration](/docs/{{version}}/configuration)
- `cookieService` : [Cookies](/docs/{{version}}/cookies)
- `storageService` : [Storage](/docs/{{version}}/storage)
- `routingService` : [Routing](/docs/{{version}}/routing)
- `validationService` : [Validation](/docs/{{version}}/container)
