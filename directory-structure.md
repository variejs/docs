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

<a name="the-root-directory"></a>
## The Root Directory

<a name="the-root-app-directory"></a>
#### App Directory

The app directory is how your application is put together and any complex logic should live. Varie tries to help you get organized with some preset folders.

<a name="the-root-config-directory"></a>
### Config Directory

This directory contains your apps configuratinos that are custmmizeable per application. This makes it easy to know what services are capable of.

<a name="the-root-public-directory"></a>
### Public Directory

This directory will exist after building your application, and should be used to display the application. It will container a mix file that allows your backend to read if your using a MVC.

<a name="the-root-resources-directory"></a>
### Resources Directory

This directory should contain all you resources, from views, to images.

<a name="the-root-routes-directory"></a>
### Routes Directory

THis directory contains multiple route files that define how your application should work.


<a name="the-app-directory"></a>
## The App Directory

<a name="the-app-components-directory"></a>
##### Components Directory

Houses all your [components](/docs/{{version}}/components)

<a name="the-app-directives-directory"></a>
##### Directives Directory

Houses all your [directives](/docs/{{version}}/directives)

<a name="the-app-filters-directory"></a>
##### Filters Directory

Houses all your [filters](/docs/{{version}}/filters)

<a name="the-app-mixins-directory"></a>
##### Mixins Directory

Houses all your [mixins](/docs/{{version}}/mixins)

<a name="the-app-providers-directory"></a>
##### Providers Directory

This directory should contain all your [service providers](/docs/{{version}}/service-providers) for your application. These providers bootstrap your application by binding them to the service container.

<a name="the-app-store-directory"></a>
##### Store Directory