  ## Components
  Components are auto loaded with kebab casing into the application as long as your using the `autoLoadComponents` provider in your config.
  Only components in the main directory are auto loaded, to allow you to create sub components of your components without 
  auto loading them in. 
  
  ### Examples :
    .
     +-- app
        +-- components
            +-- Notifications.vue
            
  Will auto load the component `<notifications><notifications>`.

    .
     +-- app
        +-- components
            +-- Notifications.vue
            +-- notification_components
                +-- NotificationItem.vue
                
                
  Will not auto load `<notification-item></notification-item>`
  
  > To learn more about components go to [Vue's Documentation](https://vuejs.org/v2/guide/components.html).