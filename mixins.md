## Mixins

Mixins are auto loaded into the application as long as your using the `autoLoadMixins` provider in your config.

### Examples :

    .
     +-- app
        +-- mixins
            +-- Helpers.ts


```js
Vue.mixin({
  // your mixin component
})
```

    > To learn more about mixins go to [Vue's Documentation](https://vuejs.org/v2/guide/mixins.html).
