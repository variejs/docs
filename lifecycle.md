This document gives a high overview on how Varie works. This will help you
understand what happens each time someone hits your page for the first time.

## Entry

First, the browser hits the `app/app` file which imports the varie framework it self.
When then start to boot the application up, and register the application to
one of its few global handlers `$app`.

There are two phases that happen while bootstrapping the application up.

### Register Phase

During the register phase, each service provider is binding services
to the application to make them available for \$app to use.

### Boot Phase

Once all service providers have been register, each provider is given a
chance to set setup the application based on that provider needs.
During this phase you have access all all services as they have been registered already.

## Finally Vue Takes Over

Once those phases are completed, Vue finally gets to take over and act like any other VueJS application.

## Takeaway

The entire application is built upon this premise of these service providers. Take a look in
the `config/app` file and you can see how the application builds it self.
