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
form.isDirty();
```

## Filling Data

Filling data allows you to add additional data than what the form started with.

```js
let form = new Form({ name : 'varie' })
form.fill({ url : 'https://varie.io' });

form.data() // OUTPUT
{
 name : 'varie',
 url : 'https://varie.io'
}
```

## Merging Data

Merging allows you to strip any data that you don't want in the object when filling.

```js
let form = new Form({ name : 'varie' })
form.merge({ url : 'https://varie.io' });

form.data() // OUTPUT
{
 name : 'varie',
}
```

## Removing Data

When using forms, you have to use the `remove` method because of the [Vue lack of reactivity
in some cases](https://vuejs.org/v2/guide/reactivity.html).

```js
let form = new Form({ name : 'varie' }, { url : 'https://varie.io' })

form.remove('url');

form.data() // OUTPUT
{
 name : 'varie',
}
```

## Set Original Data

Setting the original data is useful after requests were made and you don't want your users to be able to reset the data to
their previous values.

```js
form.setOriginaldata();
```

## Reset Form Data

To reset the data to its original form just use the reset function

```js
let form = new Form({ name : 'varie' })
form.fill({ url : 'https://varie.io' });

form.reset() // OUTPUT
{
 name : 'varie',
}
```

Or you can use initial() to go back to the initial state when newing up the form

```js
let form = new Form({ name : 'varie' }, { url : 'https://varie.io' })
form.fill({ name : 'varie is awesome!'});
form.setOriginaldata();

form.initial() // OUTPUT
{
 name : 'varie',
 url : 'https://varie.io'
}
```

## Validation

The form class is directly connected to the validation service, make sure you include a validation service provider
for the validation to work properly. To learn more, check out the [validation documentation](/docs/{{version}}/validation).
