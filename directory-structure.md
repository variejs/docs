Varie ships with starting point for your application, feel free to change
the structure to meet your needs.

## Inside Root Directory

#### The App Directory

The app directory is how your application is put together and any complex logic should live. Varie tries to help you get organized with some preset folders.

#### The Config Directory

This directory contains your apps configurations that are customizable per application.
To learn more, check out the [configuration documentation](/docs/{{version}}/configuration).

#### The Public Directory

This directory will exist after building your application, and should be used to display the application. It will container a mix file that allows your backend to read if your using a MVC.

#### The Resources Directory

This directory should contain images, fonts, downloadable files, etc.

#### The Routes Directory

THis directory contains multiple route files that define how your application should work.
To learn more, check out the [routing documentation](/docs/{{version}}/routing).

#### The Store Directory

This directory contains all the Vuex stores, you should use the `$ varie make:store {StoreName}` to create these stores.
To learn more, check out the [state management documentation](/docs/{{version}}/state).

#### The Views Directory

This directory contains all the views and their components for your application.
To learn more, check out the [views documentation](/docs/{{version}}/views).

## Inside App Directory

#### The Middleware Directory

This directory should contain all your app middleware for your application. These providers bootstrap your application by binding them to the service container.
To learn more, check out the [HTTP requests documentation](/docs/{{version}}/requests).

#### The Providers Directory

This directory should contain all your service providers for your application. These providers bootstrap your application by binding them to the service container.
To learn more, check out the [service providers documentation](/docs/{{version}}/service-providers).

#### The Models Directory

Coming Soon!

#### The Rules Directory

This directory should contain any custom validation rules for your application. You can run `varie make:rule` to create a new custom rule.
To learn more, check out the [validation documentation](/docs/{{version}}/validation).

#### The Validators Directory

This directory should contain any custom validation objects for your application.
To learn more, check out the [validation documentation](/docs/{{version}}/validation).
