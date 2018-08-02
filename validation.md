# Validation

- [Validating Forms](#validating-your-forms)
  - [Attaching Errors To Inputs](#attaching-errors-to-inputs)
  - [Available Validation Rules](#available-validation-rules)
  - [Custom Error Messages](#custom-error-messages)
  - [Custom Validation Rules](#custom-validation-rules)
  - [Validation Language Files](#validation-language-files)

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

`$varie make:rule NewRule`

You then can define how the validation passes, and the message that it will display to the user.

<a name="validation-language-files"></a>

### Validation Language Files

If you would like change your phrasing of the errors you can change that inside your resources/lang/xx/validation.php language file.

## Models

Models allow you to define what data may look like when you retrieve it from an API.
This also allows you to write functions to do multiple things to the model such as setting
default values or displaying some of the information.

```js
    import Model from "varie/lib/support/Model";

    export default class UserModel extends Model {
        public id : number;
        public name : string;
        public email : string

        protected defaults() {
            this.name  = 'Varie';
        }
    }
```
