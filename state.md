# State Management

* [Creating Stores](#creating-stores)
  * [Creating Sub Modules](#creating-submodules)
* [Directory Structure](#directory-structure)
* [Using Stores](#using-stores)

Varie makes it easy to interact with state, with the power of Vuex. Automatic module registration makes it really easy to setup your application quickly.

<a name="createing-stores"></a>

## Creating Stores

To create a new store use the Varie Cli to create it in the dictory you wish to create it in

`varie make:store <store-name>`

<a name="creating-submodules"></a>

### Creating Submodules

Varie handles making submodules for you as long as you use slashes in the name

`varie make:store auth/submodule-name`

<a name="createing-stores"></a>

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
