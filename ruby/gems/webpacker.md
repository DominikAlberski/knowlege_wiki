### Webpacker
ref. [link](https://blog.appsignal.com/2021/02/17/using-webpacker-in-your-ruby-on-rails-app-deep-dive.html)

 - Configuration — it’s placed inside the config/webpacker.yml file and allows you to point Webpacker to the directory where you keep your javascript files and packs
 - Pack — it’s a single entry point from which Webpacker begins compilation. Each library imported and initialized in that file will be automatically compiled.
 - Development server — a simple script that allows you to compile files on the fly, so you don’t have to restart the server each time you modify JavaScript files
 - Compile task — a simple rake task that invokes Webpack and compiles files under the public directory so you can deploy them to the production server and make them available for end-users
 - View helper — helper that allows you to include compiled files inside the views
