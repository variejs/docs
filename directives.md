## Directives

Directives are auto loaded into the application as long as your using the `autoLoadDirectives` provider in your config.

### Examples :

    .
     +-- app
        +-- directives
            +-- Focus.ts

```js
Vue.directive("focus", {
  // When the bound element is inserted into the DOM...
  inserted: function(el) {
    // Focus the element
    el.focus()
  },
})
```

    > To learn more about directives go to [Vue's Documentation](https://vuejs.org/v2/guide/custom-directive.html).
