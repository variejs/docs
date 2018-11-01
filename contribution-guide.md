## Features / Bug Reports

Varie's source code is managed on GitHub and there are repositories for each of its elements

- [Varie](https://github.com/variejs/varie)
- [Varie CLI](https://github.com/variejs/varie-cli)
- [Varie Bundler](https://github.com/variejs/varie-bundler)
- [Varie Framework](https://github.com/variejs/framework)
- [Varie Auth Plugin](https://github.com/variejs/varie-auth-plugin)

### Setup

To work with the Varie framework its best to follow these installation steps.

    1. git clone git@github.com:variejs/framework.git
        * run `$ npm install`
        * run `$ npm link` inside the varie-framework folder
    2. git clone git@github.com:variejs/varie.git
        * run `$ npm install`
        * run `$ npm link varie` inside the varie folder
    3. Building
        * `$ npm run dev` - builds the framework / application once
        * `$ npm run watch` - watches for change and rebuilds the application

## Coding Style

Varie follows the prettier and should be ran before making a Pull Request.
