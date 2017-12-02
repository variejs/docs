## Directory Stucture
// TODO - get them to link to below

    .
     +-- app
        +-- components
        +-- directives
        +-- filters
        +-- mixins
        +-- providers
        +-- store
     +-- config
     +-- public
     +-- resources
        +-- assets
        +-- views
     +-- routes 
        +-- middleware
        
#### App Directory
The app directory is how your application is put together and any complex logic should live.
Varie tries to help you get organized with some preset folders.

###### Components Directory
Houses all your [components](/docs/{{version}}/components)

###### Directives Directory
Houses all your [directives](/docs/{{version}}/directives)

###### Filters Directory
Houses all your [filters](/docs/{{version}}/filters)

###### Mixins Directory
Houses all your [mixins](/docs/{{version}}/mixins)

###### Providers Directory
THis directory should contain all your  [service providers](/docs/{{version}}/service-providers) for your application.
These providers bootstrap your application by binding them to the service container. 

##### Store Directory
// TODO - link to store

#### Config Directory
This directory contains your apps configuratinos that are custmmizeable per application. This makes it easy to know
what services are capable of.

#### Public Directory
This directory will exist after building your application, and should be used to display the application.
It will container a mix file that allows your backend to read if your using a MVC.

#### Resources Directory
This directory should contain all you resources, from views, to images.

###### Assets Directory
This directory contains assets such as images, PDFs, json files, etc.

###### Views Directory
This directory should contain all of your `.vue` files that you wish to render when routing.

#### Routes Directory
THis directory contains multiple route files that define how your application should work.

###### Middleware Directory
This directory contains route middleware that you can use within your route files.
