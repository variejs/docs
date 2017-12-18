## Service Providers

Service providers allow to us to bind things to our application. In fact Varie it self uses service providers to boot 
all the necessary components to create the actual application.

These providers are meant for registering things. You can bind services, middleware , constants, routes and more. Most 
of the application providers are deferred and are only loaded when actually called from the container.  

## Creating a Service Provider
Each provider extends the `varie/lib/support/ServiceProvider` class. The service provider will require the use of the register method and optionally the boot method.
Register should only bind things into the service container. The boot method occurs after ALL service providers have been registered and have availability to them through the 
service container.

The Varie CLI tool can generate a new service provider for you via `varie make:provider <provider-name>`

### The Register Method
The register method is meant to bind things to the service container. You can review how to bind things to the container in the
service container documentation(TODO - make a link to the service container page).

An example :

```js
    import { injectable } from "inversify";
    import ServiceProvider from "varie/lib/support/ServiceProvider";
    import DocumentationService from "@app/services/DocumentationService";
    
    @injectable()
    export default class DocumentationProvider extends ServiceProvider {
      public register() {
        this.app.singleton("$documentationService", DocumentationService);
      }
    }
```

Above the provider is binding a implementation of a `$documentationService` to the container. 


### The Boot Method

$the boot method only occurs after all service providers have been registered and thus has the availability to inject them
through the service container.

TODO - look to see if we can do method injection

### Registering the Provider
All service providers are registered in `config/app.ts`. This file contains other service providers already added to 
application. Just add your provider by adding it to the array.