Varie makes use of the Vuex system the only difference is the registration of the stores.

## Creating Stores

To create a new store use the Varie Cli to create it in the directory you wish to create it in

`$ varie make:store <store-name>`

Then register it within your `StateServiceProvider`

```js
this.$store.registerStore(YourNewStore);
```

### Using Models

Models help to organize and let our IDE how these models will look like and can be useful for displaying , validating,
reusability of the data.

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

`$ varie make:store user/cats`

After creating you can then add the submodule module

```js
this.setName("user")
  .addState(state)
  .addActions(actions(httpService))
  .addMutations(mutations)
  .addGetters(getters)
  ...
  .addModule(UserCatStore);
```

## Directory Structure

Each store will contain 6 files to setup your store :

```tree
actions
getters
StoreName
mutations
state
stateInterface
```
