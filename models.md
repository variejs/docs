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
