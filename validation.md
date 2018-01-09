# Validation

```js
import AddressRule;

class User extends Model {
  	private _rules : {
  	  name : 'required|string|maxLength:6',
  	  email : 'email',
  	  address : AddressRule,
  	}

  	private _messages : {
  	  name : 'This is an invalid name'
  	}
}
```

Usage :

```js
let user = new User({
  name: "luke",
  email: "luke@lukepolo.com",
  address: {
    line_1: "5121 Main Street"
  }
});

user.name; // luke
user.get("name"); // luke
user.set("name", "newName");
user.name = "newName"; // TODO - this may not be possible as it may not be watchable?

user.isValid(); // true || false
user.error("email"); // gets the error for name || or null
user.errors(); // gets all the errors
```

Models set / get

```js
$userModel.set("email", "luke@lukepolo.com");
$userModel.set("address.first_line", "5121 Main Street");

$userModel.get("email");
$userModel.get("address.first_line");
```

Custom Rules

```js
class AddressRule extends Rule {

  public passes() {
  	  // some logic that returns a boolean that it passes or fails
  }

  public message() {
  	// message if it fails
  }
}
```

Static Messages

```json
{
  "string": "You must supply a valid string",
  "email": "You must supply a valid email address"
}
```
