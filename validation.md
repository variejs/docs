## Validating Your Forms

You can validate your forms by adding [validation rules](#available-validation-rules) to your form data.

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
  <input type="text" name="user.name" v-model="form.user.name" validate />
  <input type="text" name="user.email" v-model="form.user.email" validate />
  <button :disabled="!form.isValid()">Submit</button>
</form>
```

[{.alert} Important : you must map to your values location in the form by using the name attribute]

## Available Validation Rules

<div class="collection-list">

[accepted](#accepted)

[after](#after)

[after_or_equal](#after_or_equal)

[alpha](#alpha)

[alpha_num](#alpha-num)

[array](#array)

[before](#before)

[before_or_equal](#before_or_equal)

[between](#between)

[boolean](#boolean)

[confirmed](#confirmed)

[date](#date)

[different](#different)

[email](#email)

[image](#image)

[integer](#integer)

[max](#max)

[mimetypes](#mimetypes)

[min](#min)

[numeric](#numeric)

[regex](#regex)

[required](#required)

[required_if](#required_if)

[required_unless](#required_unless)

[required_with](#required_with)

[required_with_all](#required_with_all)

[required_without_all](#required_without_all)

[same](#same)

[size](#size)

[string](#string)

[url](#url)

</div>

#### accepted

The field under validation must be yes, on, 1, or true.

#### after:date

The field under validation must be a date (JavaScripts `Date` / ISO8601 / RFC3339 format) that's after the specified date (defaults to now).

#### after_or_equal:date

The field under validation must be a date (JavaScripts `Date` / ISO8601 / RFC3339 format) that's after or equal to the specified date (defaults to now).

#### alpha

The field under validation must contains only letters (a-zA-Z).

#### alpha_num

The field under validation must contains only letters and numbers.

#### array

The field under validation must be an array.

#### before:date

The field under validation must be a date (JavaScripts `Date` / ISO8601 / RFC3339 format) that's before the specified date (defaults to now).

#### before_or_equal:date

The field under validation must be a date (JavaScripts `Date` / ISO8601 / RFC3339 format) that's before or equal to the specified date (defaults to now).

#### between:min,max

The field under validation must have a size between the given min and max. Strings, numerics, arrays, and files are evaluated in the same fashion as the size rule.

#### boolean

The field under validation must be able to be cast as a boolean. Accepted input are true, false, 1, 0, "1", and "0".

#### confirmed

The field under validation must have a matching field of fooConfirmation. For example, if the field under validation is password, a matching passwordConfirmation field must be present in the input.

#### date

The field under validation must be a valid date.

#### different:field

The field under validation must have a different value than field.

#### email

The field under validation must be a valid email.

#### image

The file under validation must be an image (jpg, jpeg, png, bmp, gif, or svg)

#### integer

The field under validation must be an integer.

#### max:value

The field under validation must be less than or equal to a maximum value. Strings, numerics, arrays,
and files are evaluated in the same fashion as the size rule.

#### mimetypes:text/plain,...

The file under validation must match one of the given MIME types.

#### min:value

The field under validation must be greater than or equal to a minimum value. Strings, numerics, arrays,
and files are evaluated in the same fashion as the size rule.

#### nullable

The field under validation may be null. This is particularly useful when validating primitive such as strings and integers that can contain null values.

#### numeric

The field under validation must be numeric.

#### regex:pattern

The field under validation must match the given regular expression.

#### required

The field under validation must be present in the input data and not empty. A field is considered "empty" if one of the following conditions are true:

```
- The value is null.
- The value is an empty string.
- The value is an empty array or empty Countable object.
```

#### required_if:anotherField,value

The field under validation must be present and not empty if the anotherfield field is equal to any value.

#### required_unless:anotherField,value

The field under validation must be present and not empty unless the anotherfield field is equal to any value.

#### required_with:foo,bar,...

The field under validation must be present and not empty only if any of the other specified fields are present.

#### required_with_all:foo,bar,...

The field under validation must be present and not empty only if all of the other specified fields are present.

#### required_without:foo,bar,...

The field under validation must be present and not empty only when any of the other specified fields are not present.

#### required_without_all:foo,bar,...

The field under validation must be present and not empty only when all of the other specified fields are not present.

#### same:field

The given field must match the field under validation.

#### size:value

The field under validation must have a size matching the given value.
For string data, value corresponds to the number of characters.
For numeric data, value corresponds to a given integer value.
For an array, size corresponds to the count of the array.
For files, size corresponds to the file size in kilobytes.

#### string

The field under validation must be a string. If you would like to allow the field to also be null, you should assign the nullable rule to the field.

#### url

The field under validation must be a valid URL.

## Custom Error Messages

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

To create custom validation rules use the varie cli tool which will place the new rule inside the `app/rules` folder :

`$varie make:rule NewRule`

You then can define how the validation passes, and the message that it will display to the user.

<a name="validation-language-files"></a>

### Validation Language Files

If you would like change your phrasing of the errors you can change that inside your `resources/lang/xx/validation` language file.

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
