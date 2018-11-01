Varie lets you interact with the cookies.

## Setting

To set something in to the storage :

```js
    this.cookieService.set(
        name: string,
        value: any,
        days?: number,
        path?: string,
        domain?: string,
        secure?: boolean
    );
```

## Getting

To get something in to the storage :

```js
let token = this.cookieService.get("token");
```

## Removing

To remove something in to the storage :

```js
    this.cookieService.remove(name: string, path?: string, domain?: string);
```
