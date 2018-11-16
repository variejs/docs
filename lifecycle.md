By explaining the lifecycle we hope that it gives you a foundation on how
Varie builds things together. This will help to conceptually understand
when things load and how you can effectively build upon Varie.

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

## Its All About them Service Providers

The entire application is built upon this premise of these service providers. Take a look in
the `config/app` file and you can see how the application builds it self, the entire application is
built from that list.

This gives the you the developer greater control of the application and build it how you want.
