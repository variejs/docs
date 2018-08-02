# Forms & Validation

- [Forms](#forms)

  - [Creating Forms](#creating-forms)
  - [Checking Dirty](#checking-for-dirty-forms)
  - [Reset The Form](#reset-form-data)
  - [Set Original Data](#setting-original-data)
  - [Models](#models)

- [Validating Forms](#validating-your-forms)
  - [Attaching Errors To Inputs](#attaching-errors-to-inputs)
  - [Available Validation Rules](#available-validation-rules)
  - [Custom Error Messages](#custom-error-messages)
  - [Custom Validation Rules](#custom-validation-rules)
  - [Validation Language Files](#validation-language-files)

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

### Models

TODO

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

### Attaching Errors to inputs

To attach errors to your inputs we can use the varie form directive along with what fields you wish to validate

```vue
    <form v-form="form" @submit.prevent="doSomeAction()">
        <input type="text" name="user.name" v-model="form.user.name" validate>
        <input type="text" name="user.email" v-model="form.user.email" validate>
        <button :disabled="!form.isValid()">Submit</button>
    </form>
```

[{.alert} Important : you must map to your values location in the form by using the name attribute]

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

## Custom Validation Rules

To cretae custom validation rules use the varie cli tool which will place the new rule inside the `app/rules` folder :

`varie make:rule NewRule`

You then can define how the validation passes, and the message that it will display to the user.

<a name="validation-language-files"></a>

### Validation Language Files

If you would like change your phrasing of the errors you can change that inside your resources/lang/xx/validation.php language file.
