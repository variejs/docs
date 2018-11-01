## Installation

To get started quickly, install the Varie CLI tool globally `$ npm install -g varie-cli` and create your application

`$ varie new blog`

This will fetch the latest version of Varie and install its dependencies for you.

[{.info} If your using NVM make sure to install it globally under the version of node you wish to use. By default Varie uses Node.js Version 8.12.0]

Then to start development, you will run :

`$ npm run watch`

This will open your application into [http://localhost:3000](http://localhost:3000).

[{.info} The watch command runs in Hot Module Replacement (HMR) mode, and will pickup all changes and load them into your browser without refreshing]

## Configuration

After installing, Varie does not need any configuration changes to work, but you amy want
to familiarize yourself with the documentation before heading straight
into the code base.

### Configuration Files

You should look through the configuration files that are stored
in `config` directory, to help understand your applications behavior.

### Environment File

You can add additional environment variables such as public api keys,
these will be passed to the application and can be retrieved with

```js
$app.env.SOME_API_KEY;
```
