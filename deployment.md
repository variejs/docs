When deploying Varie there are a few steps you must do before building the application.

## Server Configuration

Depending on which HTTP server your using requires a different type of config.

### Nginx

```shell
root /var/www/your_site/public;

location / {
	try_files $uri /index.html;
}
```

### Apache

```shell
# To be inside the /public Directory
<IfModule mod_rewrite.c>
    RewriteEngine On
    RewriteBase /
    RewriteRule ^index\.html$ - [L]
    RewriteCond %{REQUEST_FILENAME} !-f
    RewriteCond %{REQUEST_FILENAME} !-d
    RewriteRule . /index.html [L]
 </IfModule>
```

## Environment Variables

There are a couple of ways to manage the environment variables on your server :

1.  Use the .env file , this should `NOT` be committed into your codebase
2.  Use [server environment variables](https://help.ubuntu.com/community/EnvironmentVariables) stored on your server

[{.alert} This is required before you build your application, it will otherwise it may fail to build!]

## Deploying with CodePier

If you are not quite comfortable managing your own server with the proper
configurations, [CodePier](https://codepier.io) is a alternative that
helps you build and deploy applications with zero-downtime and
automated deployments.
