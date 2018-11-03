Varie comes with built in alert system that includes base components that are ready to be customized.
Alerts are useful for notifying HTTP errors, validation messages, and other events.

## Creating a Alert

The alert system includes a mixin that allows you to access the alert service anytime inside your components.

```js
    methods : {
    	shotAlerts() {
    	    this.alertService.info('info message', 'This is an Info Alert')
    	}
    });
```

## Alert Types

    - info
    - error
    - success
    - warning

Each alert can be customized with a message, title, and a delay.

```js
this.alertService.warning("Message", "Title", 10000);
```
