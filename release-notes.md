[{.alert} Assume each minor version contains breaking versions until stable release!]

## 0.4.0 - 0.9.0 (Beta)

- The injection for `routerService` was renamed to `RouterService`
- The injection for `storeService` was renamed to `StateService` across the entire application
- Route middleware now expects the actual middleware class instead of the string
- [Provider Import names were updated](https://github.com/variejs/varie/blob/75a772221171c86b3f4198e902c149e7fc6b46ce/config/app.ts)
- Notifications was renamed to Alerts
- The injection for `notificationService` was renamed to `AlertService`

## 0.3.0 (Beta)

Contains breaking changes for routes / state (store) management :

- We no longer allow strings to be passed into the router
- We no longer auto register stores (caused lots of headaches with development, having to restart webpack etc.)

Also these changes allow us to do better code splitting by areas and can dynamically
register services, stores, components.

## 0.2.0 (Beta)

Contains breaking changes for app / route middleware :

- Added DI for Middleware
- Updated folder structure to emphasize the Store, Views

---

## 0.1.0 (Beta)

We are releasing Varie as a beta to start out. The reason is, we want
more opinions to come in and change before we start solidifying the API.
While we don't expect things to change drastically, the API may change.
All breaking changes will be posted here as well as how to upgrade.

Please head over to our [GitHub](https://github.com/variejs/framework) page to submit suggestions / bugs / ideas.

---
