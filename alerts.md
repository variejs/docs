Varie comes with built in alert system that includes base components that are ready to be customized.
Alerts are useful for notifying HTTP errors, validation messages, and other events.

## Creating a Alert

The alert system includes a mixin that allows you to access the alert service anytime inside your components.

```js
    methods : {
    	showAlert() {
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
this.alertService.info("Message", "Info", 3000);
this.alertService.error("Message", "Error", 0);
this.alertService.warning("Message", "Warning", 5000);
this.alertService.success("Message", "Success", 3000);
```
