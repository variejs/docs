Varie comes with Dependency Injection built in. Its a critical to learn how to use
it within Varie to help you access services across the application.

## Constructor Injection

This is the most common way to resolve your dependencies, and is widely used throughout
the framework :

```js
import { injectable, inject } from "inversify";
import HttpServiceInterface from "varie/lib/http/HttpServiceInterface";

@injectable()
export default class SubscriptionService {
  private httpService: HttpServiceInterface;

  constructor(
    @inject("HttpService") httpService,
  ) {
    this.httpService = httpService;
  }
}

```

## Extending A Injectable Class

Sometimes you wish to extend a injectable class, but typescript will complain

```
The number of constructor arguments in the derived class X must be >= than the number of constructor arguments of its base class.
```

To fix it we should use the `@unmanaged()` helper :

```js
import { injectable, inject } from "inversify";
import RestServiceClass from "@app/services/RestServiceClass";

@injectable()
export default class NotificationProviderService extends RestServiceClass {
  constructor(
    @inject("HttpService") httpService,
    @inject("ApiRouteService") apiRouteService
  ) {
    super(
      httpService,
      apiRouteService,
      "AuthProvidersNotificationProvidersController"
    );
  }
}
```

```js
import { injectable, unmanaged } from "inversify";

@injectable()
export default class RestServiceClass {
  protected httpService;
  protected $apiRouteService;
  protected $controllerClass;

  constructor(
    httpService,
    apiRouteService,
    @unmanaged() controllerClass: string,
  ) {
    this.httpService = httpService;
    this.$apiRouteService = apiRouteService;
    this.$controllerClass = controllerClass;
  }
}
```

## Resolving from app

```js
let documentationService = app.make("DocumentationService");
```

## Component Injection

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
