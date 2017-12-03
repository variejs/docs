## Filters

Filters are auto loaded into the application as long as your using the `autoLoadFilters` provider in your config.

### Examples :

    .
     +-- app
        +-- filters
            +-- LowercaseText.ts


```js
export default value => {
  return value.toLowerCase()
}
```

    > To learn more about filters go to [Vue's Documentation](https://vuejs.org/v2/guide/filters.html).
