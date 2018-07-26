# Directory Structure

- [The Root Directory](#the-root-directory)
  - [The `app` Directory](#the-root-app-directory)
  - [The `config` Directory](#the-root-config-directory)
  - [The `public` Directory](#the-root-public-directory)
  - [The `resources` Directory](#the-root-resources-directory)
  - [The `routes` Directory](#the-root-routes-directory)
- [The App Directory](#the-app-directory)
  - [The `components` Directory](#the-app-components-directory)
  - [The `directives` Directory](#the-app-directives-directory)
  - [The `filters` Directory](#the-app-filters-directory)
  - [The `mixins` Directory](#the-app-mixins-directory)
  - [The `providers` Directory](#the-app-providers-directory)
  - [The `store` Directory](#the-app-store-directory)

## The Root Directory

#### App Directory

The app directory is how your application is put together and any complex logic should live. Varie tries to help you get organized with some preset folders.

### Config Directory

This directory contains your apps configuratinos that are custmmizeable per application. This makes it easy to know what services are capable of.

### Public Directory

This directory will exist after building your application, and should be used to display the application. It will container a mix file that allows your backend to read if your using a MVC.

### Resources Directory

This directory should contain all you resources, from views, to images.

### Routes Directory

THis directory contains multiple route files that define how your application should work.

## The App Directory

##### Components Directory

Houses all your [components](/docs/{{version}}/components)

##### Directives Directory

Houses all your [directives](/docs/{{version}}/directives)

##### Filters Directory

Houses all your [filters](/docs/{{version}}/filters)

##### Mixins Directory

Houses all your [mixins](/docs/{{version}}/mixins)

##### Providers Directory

This directory should contain all your [service providers](/docs/{{version}}/service-providers) for your application. These providers bootstrap your application by binding them to the service container.

##### Store Directory
