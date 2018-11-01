# Alerts

- [Creating a Alert](#creating-a-alert)

Varie comes with built in alert system that you can customize.
There as been have included the component already in the base install, but feel free to customize it.

## Creating a Alert

You can create alerts by injecting the alert service

```js
    export default Vue.extend({
      $inject: ["AlertService"]
    },
    methods : {
    	shotAlerts() {
    	    this.alertService.showInfo('info message', 'This is an Info Alert')
    		this.alertService.showError('error message', 'This is an Error Alert');
            this.alertService.showSuccess('success message', 'This is an Success Alert, that never goes away', 0)
            this.alertService.showWarning('warning message', 'This is an Warning Alert with 10 second delay before it goes away', 10000)
    	}
    });
```
