# Forms

- [Creating Forms](#creating-forms)
- [Checking Dirty](#checking-for-dirty-forms)
- [Reset The Form](#reset-form-data)
- [Set Original Data](#setting-original-data)

Forms allow us to organize our data so we can submit and validate easily.

### Creating Forms

To create a form in your component you just need to call `createForm` inside your data property :

```js
    data() {
        return {
          form: this.createForm({
            user : {
                name : 'Varie'
            }
          }),
        }
    }
```

### Checking for Dirty Forms

You can check to see if the form is dirty by

```js
form.isDirty();
```

### Reset Form Data

To reset the data to its orignal form just use the reset function

```html
<button @click="form.reset()">Reset</button>
```

### Set Original Data

Setting the original data is useful after requests were made and you dont want your users to be able to reset the data to
their previous values.

```js
form.setOriginaldata();
```
