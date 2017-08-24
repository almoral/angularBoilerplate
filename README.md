# AngularBoilerplate

This project was generated with [Angular CLI](https://github.com/angular/angular-cli) version 1.3.2.

## Creating a component to use in LiveSite
When developing a component for use in LiveSite there are a few things to remember.

* We don't upload index.html. Instead, we create a copy of the AngularBoilerplate component and use that in LiveSite. The component contains the 'base' tag set to the root of the current workarea. It also contains the application root, e.g. 'app-root' as well as links to the js files for the application.

* In order to use the LiveSite component for configuration, we need to create a global variable in the LiveSite component. We then use XPath to grab the value from the datum defined in the component. 
  #### For example:
  ```angular2html
  <script>
    {
      configurationVariable = "$MODEL{/Properties/Data/Datum[@Name='Department']}";
    }
  </script>
  ```
  
  > **Note:**
  > If you need to find the XPath for the value, you can preview the component in Firefox. There is a review frame in the bottom left-hand corner that prints out the XML for the component.
  
* To include the js files for the application, you must specify the path to each file using the $URL_PREFIX token. The token generates the path to the current workarea. 

  #### For example:
  ```angular2html
  <script 
    type="text/javascript" 
    src="$URL_PREFIX[resources/components/{componentName}/js/{fileName.js}]">
  </script>
  ```
 


## Notes on routing:
When using routing in a component that will live inside of TeamSite, we use the 'skipLocationChange' feature.
This is to keep the component from changing the url whenever routing to a different view. 

## Development server

Run `ng serve` for a dev server. Navigate to `http://localhost:4200/`. The app will automatically reload if you change any of the source files.

## Code scaffolding

Run `ng generate component component-name` to generate a new component. You can also use `ng generate directive|pipe|service|class|guard|interface|enum|module`.

## Build

Run `ng build` to build the project. The build artifacts will be stored in the `dist/` directory. Use the `-prod` flag for a production build. Also remember to upload the generated files to LiveSite. The location for the files will be in the BETA branch. 

> The path is:
>
> BETA > Miamidade > workarea > WA1 > resources > components > {componentName} > js.



## Running unit tests

Run `ng test` to execute the unit tests via [Karma](https://karma-runner.github.io).

## Running end-to-end tests

Run `ng e2e` to execute the end-to-end tests via [Protractor](http://www.protractortest.org/).
Before running the tests make sure you are serving the app via `ng serve`.

## Further help

To get more help on the Angular CLI use `ng help` or go check out the [Angular CLI README](https://github.com/angular/angular-cli/blob/master/README.md).
