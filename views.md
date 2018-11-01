Your views are just vue components. But we do make a suggestion on how to organize your components with layouts and
directory structures.

[{.info} To learn more about components go to [Vue's Documentation](https://vuejs.org/v2/guide/components.html).]

## Layouts

By default we provide a public layout, by adding more you are able to use different layouts.

```tree
  +-- views
      +-- layouts
          ./Public.vue
```

[{.info} To learn more about layouts read the [routing](/routing#layouts) documentation.]

### Directory Structure

We suggest making areas folders for your site, which allows you to keep a tidy folder structure and also can keep component folders inside of those.

```tree
  +-- views
      +-- Profile
        ./index.vue
        +-- components
            ./NewPasswordForm.vue
            ./ProfileImageUploader.vue
```

As you can see your can create sub component's in this manner that are not necessarily reusable components but components to keep your code tidy.

### Component Dependency Injection

To inject dependencies into your components by using the `$inject` property in your Vue Component.

```js
export default Vue.extend({
  $inject: ["DocumentationService"]
  computed : {
    menu() {
        return this.documentationService.getMenu();
    }
  }
});
```
