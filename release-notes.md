[{.alert} Assume each minor version contains breaking versions until stable release!]

## 0.9.0 - 0.12.0 (Beta)

- Alert Service API changed
- Validation Fixes
- Stubs are now included in the framework rather than the CLI
- Route Fixes

Breaking Changes :

- Http Interfaces

Look through all the updates made to the [varie repository](https://github.com/variejs/varie/compare/468c0c4d9c6a737316f50efed81b11041c6fcdeb...master)

## 0.4.0 - 0.9.0 (Beta)

- The injection for `routerService` was renamed to `RouterService`

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
