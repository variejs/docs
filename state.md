# State Management

- [Creating Stores](#creating-stores)
  - [Using Models](#using-models)
  - [Creating Sub Modules](#creating-submodules)
- [Directory Structure](#directory-structure)
- [Using Stores](#using-stores)

Varie makes it easy to interact with state, with the power of Vuex. Automatic module registration makes it really easy to setup your application quickly.

## Creating Stores

To create a new store use the Varie Cli to create it in the dictory you wish to create it in

`$ varie make:store <store-name>`

### Using Models

Models help to orgnaize and let our IDE how these models will look like and can be useful for displaying , validating,
resuabliity of the data.

To create models by using

`$ varie make:model <model-name>`

And can be used by importing the model wherever you would like :

```js
import UserModel from "@models/UserModel";
let user = new UserModel(data);
```

Using the model inside of the store you should be place it in your `stateInterface` file :

```js
import UserModel from "@models/UserModel";
export interface UsersState {
  users: Array<UserModel>;
}
```

### Creating Submodules

Varie handles making submodules for you as long as you use slashes in the name

`$ varie make:store auth/submodule-name`

## Directory Structure

Each store will contain 6 files to setup your store :

```
actions.ts
getters.ts
index.ts
mutations.ts
state.ts
stateInterface.ts
```

## Using Stores

### Actions / Getters / Mutations / State

These are directly correlated with vuex and you should first learn more about on the vuex resources page. You can
view an example here : (src to notifications plugin store)
