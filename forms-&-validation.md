# Forms & Validation

* [Forms](#forms)
  * [Creating Forms](#creating-forms)
  * [Checking Dirty](#checking-for-dirty-forms)
  * [Reset The Form](#reset-form-data)
  * [Set Original Data](#setting-original-data)
* [Validating Forms](#validating-your-forms)

  * [Attaching Errors To Inputs](#attaching-errors-to-inputs)
  * [Available Validation Rules](#available-validation-rules)
  * [Custom Error Messages](#custom-error-messages)
  * [Custom Validation Rules](#custom-validation-rules)
  * [Validation Language Files](#validation-language-files)

<a name="forms"></a>

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

<a name="checking-for-dirty-forms"></a>

### Checking for Dirty Forms

You can check to see if the form is dirty by `form.isDirty()`

<a name="reset-form-data"></a>

### Reset Form Data

To reset the data to its orignal form just use the reset function

<button @click="form.reset()">Reset</button>

<a name="setting-original-data"></a>

### Setting Original Data

Setting the original data is useful after requests were made and you dont want your users to be able to reset the data to
their previous values.

```js
form.setAsOriginalData();
```

<a name="validating-your-forms"></a>

## Validating Your Forms

You can easily validate your forms by adding [validation rules](#available-validation-rules).

```js
 data() {
    return {
      form: this.createForm({
        user: new UserModel({
          name: "varie",
          email: "varie@varie.iom"
        }),
      }).validation({
        rules: {
          user: {
            name: "required|min:2|max:255",
            email: "required|email"
          },
        },
      })
    };
  }
```

You can then use `form.isValid()` and `form.errors()` to add additional functionality to your forms

```vue
    <pre>
        {{ form.errors() }}
    </pre>
    <button :disabled="!form.isValid()">Submit</button>
```

<a name="attaching-errors-to-inputs"></a>

### Attaching Errors to inputs

To attach errors to your inputs we can use the varie form directive along with what fields you wish to validate

```vue
    <form v-form="form" @submit.prevent="doSomeAction()">
        <input type="text" name="user.name" v-model="form.user.name" validate>
        <input type="text" name="user.email" v-model="form.user.email" validate>
        <button :disabled="!form.isValid()">Submit</button>
    </form>
```

> Important : you must map to your values location in the form by using the name attribute

<a name="available-validation-rules"></a>

## Available Validation Rules

[after](#rule-after)
[alpha](#rule-alpha)
[alpha_dash](#rule-alpha-dash)
[alpha_num](#rule-alpha-num)
[alpha_spaces](#rule-alpha-spaces)
[before](#rule-before)
[between](#rule-between)
[confirmed](#rule-confirmed)
[date_between](#rule-date-between)
[date_format](#rule-date-format)
[decimal](#rule-deciaml)
[digits](#rule-digits)
[email](#rule-email)
[in](#rule-in)
[max](#rule-max)
[min](#rule-min)
[not_in](#rule-not-in)
[regex](#rule-regex)
[required](#rule-required)
[size](#rule-size)
[url](#rule-url)

<a name="custom-error-messages"></a>

### Custom Error Messages

To use custom error messages add a messages object :

```js
 data() {
    return {
      form: this.createForm({
        user: new UserModel({
          name: "varie",
          email: "varie@varie.iom"
        }),
      }).validation({
        rules: {
          user: {
            name: "required|min:2|max:255",
            email: "required|email"
          },
        },
        messages: {
        	user : {
        		name : 'This is not a valid name'
        	}
        }
      })
    };
  }
```

<a name="custom-validation-rules"></a>

## Custom Validation Rules

TODO

<a name="validation-language-files"></a>

### Validation Language Files

If you would like the :attribute portion of your validation message to be replaced with a custom attribute name, you may specify the custom name in the attributes array of your resources/lang/xx/validation.php language file:

'attributes' => [
'email' => 'email address',
],
