# Components

- [Creating a component](#creating-a-component)

Components are auto loaded with kebab casing into the application as long as your using the `autoLoadComponents` provider in your config. 
Only components in the main directory are auto loaded, to allow you to create sub components of your components without auto loading them in.

    .
     +-- app
        +-- components
            +-- LeftNav.vue
            +-- Notifications.vue
            +-- notification_components
                +-- NotificationItem.vue
                
Above structure will auto load the components `<left-nav><left-nav>` and `<notifications><notifications>`.

<a name="creating-a-component"></a>
## Creating a component

> To learn more about components go to [Vue's Documentation](https://vuejs.org/v2/guide/components.html).
