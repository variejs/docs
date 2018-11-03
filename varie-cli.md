The Varie CLI helps you create repetitive tasks and templates to help
rapidly develop your applications.

## Installation

To install the Varie CLI you should install it globally `$ npm install -g varie-cli`.

## Usage

### `new {name}`

Creates a new project in the current folder with the given name.

### `make:component {name}`

Creates a Global Vue component in the `app/components` directory.

### `make:directive {name}`

Creates a Global Vue directive in the `app/directives` directory.

### `make:filter {name}`

Creates a Global Vue filter in the `app/filters` directory.

### `make:mixin {name}`

Creates a Global Vue mixin in the `app/mixins` directory.

### `make:model {name}`

Creates a model in the `app/models` directory

### `make:provider {name}`

Creates a new provider in the `app/providers` directory.

### `make:store {name}`

Creates a Vuex store / submodule in the store directory based on the path provided.

Running `$ varie make:store user` creates a store in :
`app/stores/user`

Running `$ varie make:store user/alerts` creates a store in :
`app/stores/user/modules/alerts`

### `make:request-middleware {name}`

Creates a new request middleware in the `app/middleware` directory.

### `make:route-middleware {name}`

Creates a new route middleware in the `routes/middleware` directory.

### `make:rule {name}`

Creates a rule in the `app/rules` directory.

### `make:validator {name}`

Creates a validator in the `app/validators` directory.

### `publish`

Publishes assets from Varie plugins
