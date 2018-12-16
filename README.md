# AngularPwaApp

This project was generated with [Angular CLI](https://github.com/angular/angular-cli) version 7.0.5.

## Development server

Run `ng serve` for a dev server. Navigate to `http://localhost:4200/`. The app will automatically reload if you change any of the source files.

## Code scaffolding

Run `ng generate component component-name` to generate a new component. You can also use `ng generate directive|pipe|service|class|guard|interface|enum|module`.

## Build

Run `ng build` to build the project. The build artifacts will be stored in the `dist/` directory. Use the `--prod` flag for a production build.

## Running unit tests

Run `ng test` to execute the unit tests via [Karma](https://karma-runner.github.io).

## Running end-to-end tests

Run `ng e2e` to execute the end-to-end tests via [Protractor](http://www.protractortest.org/).

## Further help

To get more help on the Angular CLI use `ng help` or go check out the [Angular CLI README](https://github.com/angular/angular-cli/blob/master/README.md).


=====================================================================================================
To know more about service worker configuration (i.e configuring ngsw-config.json visit) -
https://angular.io/guide/service-worker-config


ngsw-config.json -> Where we configure our service-worker
{
  "index": "/index.html", // page which we want to cache
  "assetGroups": [ // static resources which we want to cache in the service worker client browser we                     // can configure it in assestGroup
    {
      "name": "app",
      "installMode": "prefetch", // can be prefetch or lazy (loading static file in service-worker lazly                            // or prefetch way)
      "resources": { 
        "files": [
          "/favicon.ico",
          "/index.html",
          "/*.css",
          "/*.js"
        ],
        "urls": [ // static url which we want to cache in the service worker's client browser
          "https://fonts.googleapis.com/css?family=Oswald:300,700"
        ]
      }
    }, {
      "name": "assets",
      "installMode": "lazy",
      "updateMode": "prefetch",
      "resources": {
        "files": [
          "/assets/**"
        ]
      }
    }
  ],
  "dataGroups":[ // if we have dynamic data which we want to cahce in the sevice worker we can configure                //that in this dataGroup
    {
      "name": "myPostsUrl",
      "urls": [ // dynamic url (http calls from server) which we want to cache in service worker
        "https://jsonplaceholder.typicode.com/posts" 
      ],
      "cacheConfig": { // how to configure the caching in service worker
        "maxSize": 5, // how many response that we want to cache
        "maxAge": "6h", // how old data in the cache should be before we get rid of it and fetch new data
        "timeout": "10s", // Client is waiting for live/fresh data/response from server suppose from 10s
                          // if no response comes from server then use cached data avaliable in service // worker (i.e-old cached data which is present in service worker)     
        "strategy": "freshness" // can be freshness or performance
      }
    }
  ]
}


freshness-> means will service worker will use -> timeout concept
performance-> means will service worker will use -> maxAge concept
