# Directory Structure

- [Inside Root Directory](#inside-root-directory)
  - [The `app` Directory](#the-app-directory)
  - [The `config` Directory](#the-config-directory)
  - [The `public` Directory](#the-public-directory)
  - [The `resources` Directory](#the-resources-directory)
  - [The `routes` Directory](#the-routes-directory)
  - [The `store` Directory](#the-store-directory)
  - [The `views` Directory](#the-views-directory)
- [Inside App Directory](#inside-app-directory)
  - [The `components` Directory](#the-components-directory)
  - [The `directives` Directory](#the-directives-directory)
  - [The `filters` Directory](#the-filters-directory)
  - [The `middleware` Directory](#the-middleware-directory)
  - [The `mixins` Directory](#the-mixins-directory)
  - [The `models` Directory](#the-models-directory)
  - [The `providers` Directory](#the-providers-directory)
  - [The `rules` Directory](#the-rules-directory)
  - [The `validators` Directory](#the-validators-directory)

Varie ships with starting point for your application, feel free to change
the structure to meet your needs.

## Inside Root Directory

#### The App Directory

The app directory is how your application is put together and any complex logic should live. Varie tries to help you get organized with some preset folders.

#### The Config Directory

This directory contains your apps configurations that are customizable per application.

#### The Public Directory

This directory will exist after building your application, and should be used to display the application. It will container a mix file that allows your backend to read if your using a MVC.

#### The Resources Directory

This directory should contain images, fonts, downloadable files, etc.

#### The Routes Directory

THis directory contains multiple route files that define how your application should work.

#### The Store Directory

This directory contains all the Vuex stores, you should use the `$ varie make:store {StoreName}` to create these stores.

#### The Views Directory

This directory contains all the views and their components for your application.

## Inside App Directory

#### The Components Directory

// TODO

#### The Directives Directory

// TODO

#### The Filters Directory

// TODO

#### The Middleware Directory

// TODO

#### The Mixins Directory

// TODO

#### The Models Directory

// TODO

#### The Providers Directory

This directory should contain all your [service providers](/docs/{{version}}/service-providers) for your application. These providers bootstrap your application by binding them to the service container.

#### The Rules Directory

// TODO

#### The Validators Directory

// TODO
