# Varie CLI

- [Installation](#installation)
- [Usage](#usage)

The Varie CLI helps you create repetitive tasks and templates to help
radpily develop your applications.

## Installation

To install the Varie CLI you should install it globally `$ npm install -g varie-cli`.

## Usage

### `new {ProjectName}`

Creates a new project in the current folder with the given name.

#### `make:component`

Creates a Global Vue component in the `app/components` directory.

#### `make:directive`

Creates a Global Vue directive in the `app/directives` directory.

#### `make:filter`

Creates a Global Vue filter in the `app/filters` directory.

#### `make:mixin`

Creates a Global Vue mixin in the `app/mixins` directory.

#### `make:model`

Creates a model in the `app/models` directory

#### `make:provider`

Creates a new provider in the `app/providers` directory.

#### `make:store`

Creates a Vuex store / submodule in the store directory based on the path provided.

Running `$ varie make:store user` creates a store in :
`app/stores/user`

Running `$ varie make:store user/notifications` creates a store in :
`app/stores/user/notification`

#### `make:request-middleware`

Creates a new request middleware in the `app/request-middleware` directory.

#### `make:route-middleware`

Creates a new route middleware in the `routes/middleware` directory.

#### `make:rule`

Creates a rule in the `app/rules` directory.

#### `make:validator`

Creates a validator in the `app/validators` directory.
