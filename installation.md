## Installation

To get started quickly, install the Varie CLI tool globally `$ npm install -g varie-cli`.

`$ varie new blog`

This will fetch the latest version of Varie and install its dependencies for you.

[{.info} If your using NVM make sure to install it globally under the version of node you wish to use. By default Varie uses Node.js Version 10.15.3]

Then to start development, you will run :

`$ npm run watch`

This will open your application into [http://localhost:8080](http://localhost:8080).

[{.info} The watch command runs in Hot Module Replacement (HMR) mode, and will pickup all changes and load them into your browser without refreshing]

## Configuration

After installing, Varie does not need any configuration changes to work, but you amy want
to familiarize yourself with the documentation before heading straight
into the code base.

### Configuration Files

These configuration files determine your service providers work. You should look through the configuration files that are stored
in `config` directory, to help understand your applications behavior.

### Environment File

You can add additional environment variables such as public api keys through the [bundler](/docs/{{version}}/varie-bundler#environment-variables).
