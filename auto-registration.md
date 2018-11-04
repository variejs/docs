Vue offers ways to have globals for multiple different types of files.
Varie takes advantage of this to allow auto registration of these for you.

## Components

Components are auto loaded with kebab casing into the application as long as your using the `autoLoadComponents` provider in your config.
Only components in the main directory are auto loaded, to allow you to create sub components of your components without auto loading them in.

```tree
     +-- app
        +-- components
            +-- LeftNav.vue
            +-- Alerts.vue
            +-- alert-components
                +-- Alert.vue
```

Above structure will auto load the components `<left-nav></left-nav>` and `<alerts></alerts>`.

[{.alert} While global components are handy, they can decrease the developer experience and suggest to use it sparingly]

## Mixins

Mixins are auto loaded into the application as long as your using the `autoLoadMixins` provider in your config.

[{.info} To learn more about mixins go to [Vue's Documentation](https://vuejs.org/v2/guide/mixins.html).]

## Filters

Filters are auto loaded into the application as long as your using the `autoLoadFilters` provider in your config.

[{.info} To learn more about filters go to [Vue's Documentation](https://vuejs.org/v2/guide/filters.html).]

## Directives

Directives are auto loaded into the application as long as your using the `autoLoadDirectives` provider in your config.

[{.info} To learn more about directives go to [Vue's Documentation](https://vuejs.org/v2/guide/custom-directive.html).]
