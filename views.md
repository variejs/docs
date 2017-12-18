# Views

Your views are just `.vue` files that contain your html / javascript / css as normal. But we make a suggestion on how to organize your views.

### Layouts

We suggest using the layouts folder to use with our router. This allows you to easily understand how the app can be used. An example below : . +-- resources +-- assets +-- views +-- layouts ./Public.vue ./App.vue This couples with our router system which you can use `$router.layout('App').group(....`

### Component Structure

We suggest making areas folders for your site, which allows you to keep a tidy folder structure and also can keep component folders inside of those. Example :

      .
       +-- resources
          +-- assets
          +-- views
              +-- Profile
                ./index.vue
                +-- Components
                    ./NewPasswordForm.vue
                    ./ProfileImageUploader.vue

As you can see your can create sub component's in this manner that are not necessarily reusable components but components to keep your code tidy.
