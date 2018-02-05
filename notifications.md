# Notifications

* [Creating a Notification](#creating-a-notification)

Varie comes with built in notification system that you can customize.

> Feel free to rip this out entirely as its just a service provider `NotificationsServiceProvider`.

<a name="creating-a-notification"></a>

## Creating a Notification

You can create notifications by injecting the notification service

```js
    export default Vue.extend({
      $inject: ["$notifications"]
    },
    methods : {
    	showNotifications() {
    		this.$notifications.showError('error', 'This is an Error Notification');
            this.$notifications.showInfo('info', 'This is an Info Notification')
            this.$notifications.showSuccess('sucess', 'This is an Success Notification, that never goes away', 0)
            this.$notifications.showWarning('warning', 'This is an Warning Notification with 10 second delay before it goes away', 10000)
    	}
    });
```
