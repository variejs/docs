# State Management

- [Creating Stores](#creating-stores)
  - [Using Models](#using-models)
  - [Creating Sub Modules](#creating-submodules)
- [Directory Structure](#directory-structure)

Varie makes it easy to interact with state, with the power of Vuex.

## Creating Stores

To create a new store use the Varie Cli to create it in the dictory you wish to create it in

`$ varie make:store <store-name>`

Then register it within your `StateServiceProvider`

```js
this.$store.registerStore(YourNewStore);
```

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

`$ varie make:store auth/moduleName`

After creating you can then add the module by navigating the store that you want to attach it to

```js
this.setName("auth")
  .addState(state)
  .addActions(actions(httpService))
  .addMutations(mutations)
  .addGetters(getters)
  .addModule(ModuleName);
```

## Directory Structure

Each store will contain 6 files to setup your store :

```tree
actions.ts
getters.ts
ModuleName.ts
mutations.ts
state.ts
stateInterface.ts
```
