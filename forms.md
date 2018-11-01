Forms allow you to organize your data, so that you can submit and validate to your backend.

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

### Filling Data

// TODO

### Merging Data

// TODO

### Removing Data

// TODO

### Reset Form Data

To reset the data to its original form just use the reset function

```html
<button @click="form.reset()">Reset</button>
```

Or you can use initial() to go back to the initial state when newing up the form

```html
<button @click="form.intial()">Reset</button>
```

### Set Original Data

Setting the original data is useful after requests were made and you don't want your users to be able to reset the data to
their previous values.

```js
form.setOriginaldata();
```

## Validation

// TODO - go to validation docs
