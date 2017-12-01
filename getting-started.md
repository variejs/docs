# # Getting Started
   
  <a name="overview"></a>
  ## Overview
  
  Varie was built to jump start your development with a bit of elegance. 
  
  * A simple routing Engine built on top of Vue Router
  * Routing Middleware
  * State management - Vuex with a bit of magic
  * A dependency injection container
  * Web pack configuration made easy (Mix)
  * HTTP Middleware
  * Plugins
  * And more!
  
  <a name="installation"></a>
  ## Installing Varie
  
  ```npm install -g varie-cli``` 
  
  or
  
  ```yarn add -g varie-cli```
   
   After installation the `varie new` command will be available to create a fresh Varie instance in the folder specified.
   
   ```varie new blog```
   
  <a name="configuration"></a>
  ##Configuration
 
  You are set to start developing! Although there is no other setup needed, you may wish to review
  `config/app.ts` and configure it to your liking.
  
  ## Developing
  Varie uses a elegant wrapper (<a href="https://github.com/JeffreyWay/laravel-mix">Laravel Mix</a>) around webpack to 
  make bundling quick and appealing.
  
  To start developing you just need to run `npm run watch`. Running this command launches a browser and uses browser sync 
  to help make your development expeierence better. You should also review the other commands within `package.json` 
  on how to run production builds. 