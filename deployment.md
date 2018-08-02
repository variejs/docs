## Deployment

- [Server Configuration](#server-configuration)
- [Environment Variables](#environment-variables)
- [Deploying with CodePier](#deploying-with-codepier)

When deploying Varie there are a few steps you must do before building the application.

### Server Configuration

#### Nginx

// TODO

#### Apache

// TODO

### Environment Variables

There are a couple of ways to manage the environment variables on your server :

- Use the .env file , this should `NOT` be committed into your codebase
- Use [environment variables](https://help.ubuntu.com/community/EnvironmentVariables) stored on your server

[{.alert} This is required before you build your application, it will otherwise fail to build!]

### Deploying with CodePier

If you aren't quite comfortable managing your own server with the proper
configurations, [CodePier](https://codepier.io) is a alternative that
helps you build and deploy applications with zero-downtime and
automated deployments.
