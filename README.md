Angular modular Seed
===================


This is and seed with modular approach, which is created, thing the performance of application and easy development for the developer. Every functionality is deviced into seperate folders acting as thei own independent components. Seed was creted considering the speed of developers working on single project but different modules in project.


[http://nisostech.com/angularjs-seed-project-a-modular-approach/](http://nisostech.com/angularjs-seed-project-a-modular-approach/)

----------



Features
-------------

 1. Lazy loading of Contoller, factory, service, directive and javascript libraries
 2. Using bower and npm to load front end dependencies
 3. Application configuration file in json (development.json, production.json , staging.json)
 4. CSS and scripts are loaded from json file (Prevent a large index.html)
 5. Folder structure are in terms of Features in your application.



> **Note:**

> - This seed include contibtribution from many people from my organization and github, Its not standards seed


#### <i class="icon-file"></i> Setup the seed

To set up the seed you need to follow the following step;

Open node js and execute following command

    git clone https://github.com/tushariscoolster/angular-modular-seed
    npm install
    bower install
    npm install grunt -g
    npm install grunt-cli -g

#### <i class="icon-folder-open"></i> Working with seed

Working with seed is very easy
Seed has very few core concepts you need to follow
Seed has three type of json file **development.json** **staging.json** **production.json**
This json files are in folder location here [Click Here](https://github.com/tushariscoolster/angular-modular-seed/tree/master/config)

When you run

    grunt server:development
Configuration are taken from development.json

#### <i class="icon-pencil"></i> Loading Assets files
 
 This seed has example of login functionality,
 Folder login contains the following files carrying out their indepedent role in the application
 
 ####  File Structure
 
 ## login.route.js
 
 Contains the routes required for login modules, this files get merge by grunt task automatically to create the common routes
```javascript
angular
     .module('seed').config(['$stateProvider', 'RouteHelpersProvider',
function ($stateProvider, helper) {
             'use strict';

             $stateProvider
                 .state('app.login', {
                     url: '/login',
                     title: 'Single View',
                     templateUrl: 'modules/login/login.html',
                     controller: 'LoginController',
                     controllerAs: 'login',
                     resolve: helper.resolveFor( 'login')
                 })



}]);
```
## login.assets.json

All dependencies required for login modules is mentioned in login.assests.son

```javascript
{
    "app": [
        {
            "serie": false,
            "name": "login",
            "files": ["modules/login/login.controller.js", "modules/login/login.factory.js", "common/directive/sweetalert.directive.js","modules/login/login.constant.js","modules/login/login.error.js","modules/login/login.url.js"]
         }
        
    ]
}
```



#### <i class="icon-trash"></i> Generating dist copy

To generate the dist copy of you app
run 

    grunt build:production

> **Note:-** production indicates configuration will be picked from production.json

Throught the seed have followed the style guide of [Johnpapa](https://github.com/johnpapa/angular-styleguide)


#### <i class="icon-hdd"></i> Integration with back-end

My motive to create this seed was, front end should be created with static json and does not ahve to wai for apis for backend

So i created url.js

      'development': {
            'login': 'api/login'

        },
        'mock': {
            'login': 'assets/json/login.json'
        }

When user run 

    grunt server:development
Automatically login api will be called by application where as when user run

    grunt server:mock
automatically all backend url will get chage to static.json

Before that you need to write the factories in following way

     function login() {
            var url = APP_URL[$enviornment.urlname].login;
            var postType = restangularParams('post', $enviornment.urlname);
            return Restangular.withConfig(function (RestangularConfigurer) {
                RestangularConfigurer.setBaseUrl($enviornment.backendurl);
            })[postType.value](url)[postType.type]({
                status: status
            });
        }
Where login indicate the key value in url.js

You can seed the sample of login module i  have implemented in below seed



----------

## Contributing

Open an issue first to discuss potential changes/additions. If you have questions with the guide, feel free to leave them as issues in the repository. If you find a typo, create a pull request. The idea is to keep the content up to date and use github’s native feature to help tell the story with issues and PR’s, which are all searchable via google. Why? Because odds are if you have a question, someone else does too! You can learn more here at about how to contribute.

*By contributing to this repository you are agreeing to make your content available subject to the license of this repository.*

### Process
    1. Discuss the changes in a GitHub issue.
    2. Open a Pull Request, reference the issue, and explain the change and why it adds value.
    3. The Pull Request will be evaluated and either merged or declined.

## License

 Use this guide. Attributions are appreciated._

### Copyright

Copyright (c) 2014-2015 [Tushar Borole](http://www.tusharborole.com)

### (The MIT License)
Permission is hereby granted, free of charge, to any person obtaining
a copy of this software and associated documentation files (the
'Software'), to deal in the Software without restriction, including
without limitation the rights to use, copy, modify, merge, publish,
distribute, sublicense, and/or sell copies of the Software, and to
permit persons to whom the Software is furnished to do so, subject to
the following conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED 'AS IS', WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY
CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT,
TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE
SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

