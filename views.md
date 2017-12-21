# Views

- [Layouts](#layouts)
- [Directory Structure](#directory-structure)
- [Component Dependency Injection](#component-dependency-injection)

Your views are just vue components. But we do make a suggestion on how to organize your components with layouts and 
directory structures.

> To learn more about components go to [Vue's Documentation](https://vuejs.org/v2/guide/components.html).

<a name="layouts"></a>
## Layouts

We suggest using the layouts folder to use with our router. This allows you to easily understand how the app can be used. An example below : 

    . 
    +-- resources
        +-- views
            +-- layouts 
                ./Public.vue
                 ./App.vue 


<a name="directory-structure"></a>
### Directory Structure

We suggest making areas folders for your site, which allows you to keep a tidy folder structure and also can keep component folders inside of those.

      .
       +-- resources
          +-- views
              +-- Profile
                ./index.vue
                +-- Components
                    ./NewPasswordForm.vue
                    ./ProfileImageUploader.vue

As you can see your can create sub component's in this manner that are not necessarily reusable components but components to keep your code tidy.

<a name="component-dependency-injection"></a>
### Component Dependency Injection

It is also easy to inject dependencies into your components by using the `inject` syntax in your `data` properties 

```js
    data() {
	  return {
	  	'$inject' : 'YourInjectionAbstract'
	  }
    }
```