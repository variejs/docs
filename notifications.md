# Notifications

- [Creating a Notification](#creating-a-notification)

Varie comes with built in notification system that you can customize.
We have included the component already in the base install, but feel free to customize it.

## Creating a Notification

You can create notifications by injecting the notification service

```js
    export default Vue.extend({
      $inject: ["$notifications"]
    },
    methods : {
    	showNotifications() {
    		this.notificationService.showError('error message', 'This is an Error Notification');
            this.notificationService.showInfo('info message', 'This is an Info Notification')
            this.notificationService.showSuccess('success message', 'This is an Success Notification, that never goes away', 0)
            this.notificationService.showWarning('warning message', 'This is an Warning Notification with 10 second delay before it goes away', 10000)
    	}
    });
```
