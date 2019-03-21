Forms allow you to organize data, keep track of that data, and even validation.

## Creating Forms

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

## Checking for Dirty Forms

You can check to see if the form is dirty by

```js
form.$isDirty();
```

## Filling Data

Filling data strips any keys that were not there when the form was created.

```js
let form = new Form({ name : 'varie' })
form.$fill({ url : 'https://varie.io' });

form.$data() // OUTPUT
{
 name : 'varie',
}
```

## Setting Data

Setting data allows you to set data even if that key did not exist before.

```js
let form = new Form({ name : 'varie' })
form.$set({ url : 'https://varie.io' });

form.$data() // OUTPUT
{
 name : 'varie',
 url : 'https://varie.io'
}
```

## Removing Data

When using forms, you have to use the `remove` method because of the [Vue lack of reactivity
in some cases](https://vuejs.org/v2/guide/reactivity.html).

```js
let form = new Form({ name : 'varie' }, { url : 'https://varie.io' })

form.$remove('url');

form.$data() // OUTPUT
{
 name : 'varie',
}
```

## Set Original Data

Setting the original data is useful after requests were made and you don't want your users to be able to reset the data to
their previous values.

```js
form.$setAsOriginalData();
```

```js
let form = new Form({ name : 'varie' })
form.$set({ url : 'https://varie.io' }).$setAsOriginalData();

form.$fill({
  name : 'varie is awesome!'
})

form.$reset().$data() // OUTPUT
{
 name : 'varie',
 url : 'https://varie.io'
}
```

## Reset Form Data

To reset the data to its original form just use the reset function

```js
let form = new Form({ name : 'varie' })
form.$set({ url : 'https://varie.io' });

form.$reset().$data() // OUTPUT
{
 name : 'varie',
}
```

Or you can use `$resetToInitial()` to go back to the initial state when newing up the form

```js
let form = new Form({ name : 'varie' }, { url : 'https://varie.io' })
form.$fill({ name : 'varie is awesome!'});

form.$set({ url : 'https://varie.io' }).$setAsOriginalData();

form.$resetToInitial().$data() // OUTPUT
{
 name : 'varie',
 url : 'https://varie.io'
}
```

## Validation

The form class is directly connected to the validation service, make sure you include a validation service provider
for the validation to work properly. To learn more, check out the [validation documentation](/docs/{{version}}/validation).
