# Forms & Validation

- [Forms](#forms)
  - [Creating Forms](#creating-forms)
  - [Checking Dirty](#checking-for-dirty-forms)
  - [Reset The Form](#reset-form-data)
  - [Set Original Data](#setting-original-data)

## Forms

Forms allow us to organize our data into submittable and validatable methods.

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

You can check to see if the form is dirty by `form.isDirty()`

### Reset Form Data

To reset the data to its orignal form just use the reset function

<button @click="form.reset()">Reset</button>

### Set Original Data

Setting the original data is useful after requests were made and you dont want your users to be able to reset the data to
their previous values.

```js
form.setOriginaldata();
```
