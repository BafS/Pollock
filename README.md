# [Pollock](http://edri.github.io/Pollock/)

### Install & Run

 1. `npm install`
 2. Run server with `npm start`.
 3. Go to http://localhost:3000/.

*PS*: Do not forget to also run mongodb (sometimes with `mongod`)

## Dev

 - `gulp.setup`, copy angular2 javascript bundle to the public folder
 - `gulp ts` for the Angular part, compile typescript files to javascript
 - `gulp watch.ts` for the Angular part, watch typescript files and compile to javascript
 - `gulp sass` for the SASS part, compile sass files to css
 - `gulp watch.sass` for the SASS part, watch sass files and compile to css
 - `gulp watch` watch both Angular and SASS part
 - `gulp` alias to setup and then watch both Angular and SASS part

You can also watch both if you simply run `gulp`.

### Watch Sass and TypeScript

 - First install **gulp** if you want to watch and automatically update Sass and TypeScript project's files.
 - Run the `gulp` command into the root directory of the project.

### Add a new view

If you want to add a new view to the project, there are several steps. You have to know that views are grouped by components.
- First of all, create your new Jade view in the "*/server/view/components/*" directory.
- Once done, create a new folder containing the TypeScript file related to your new view in the "*/client/components/*" directory. In this file, you'll have to set the view's selector and template's URL (indicating where in the Jade file), write a directive for the application's router and export the view's class. You can help yourself by building the file on what already exists.
- Then, register your new view in the application's bootstrap file ("*/client/bootstrap.ts*") under the **@RouteConfig** annotation. Don't forget to import your new view's class in the header!
- Finally, you also have to link your view with the Express' router, by adding a clause on the "*/server/routes/components.js*" file. You will be able to use it if you want to communicate with the database, for example.

# How we build the app

## Angular2

We choose to use Angular2 with Typescript. Gulp is used to compile the typescript files to javascript (ES5).

 - Source files are in the `client/` folder
 - tsconfig.json is the configuration file used by *tsc* (typescript compiler) the compile typescript files to `public/javascript/` folder. `emitDecoratorMetadata` and `experimentalDecorators` are ES7 features and need to be activated for Angular2
 - We use *System.js* to load files in different folders. `config.js` is loaded to know how to load javascript files. We can then import files as modules and just load the bootstrap file with `System.import('javascripts/bootstrap.js')`
 - `tsd.json` was generated with `tsd`, it load interfaces for installed modules to add types to javascript code


---

# Documentation

You can find the Heroku apps here : https://pollockweb.herokuapp.com/ ; you can find our product page here : http://edri.github.io/Pollock/.
