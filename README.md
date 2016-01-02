# ngLiferay-plugin

### Prerequisite
* Liferay server is running.
* Install [nodejs](https://nodejs.org/) and git.
* Install `grunt-cli` & `bower`. These commands will require administrator privileges.
  * `npm install -g grunt-cli bower`


### Steps to create new ngLiferay plugin
* Download or clone this repository.  
* Create new file `lr-override.properties` parallel to `lr.properties` file. Configure Liferay server's configuration in the new file. Change Liferay theme id and name.
* Change the folder name to `ngLiferay-plugin` to `ngLiferay-xxx`.
The `ngLiferay-xxx` is the angular module name for new plugin.
* In `Gruntfile.js`, replace all `ngLiferay-plugin` to `ngLiferay-xxx`. Save and close.
* Change the package name in `package.json` & `bower.json` to new one.
* In `app\index.html`, change `ng-app` to `ngLiferay-xxx`, so as to configure new plugin with angular.
* Also in `app\js\app.js` & `app\js\devNgFixes.js`, change the angular module name to  `ngLiferay-xxx` and change the plugin name
* Now install packages by executing 2 commands, to install npm & bower packages.
  - `npm install`

  - `bower install`
* After installing required packages, will start development of plugin. Execute following commands in new plugin:
  * `grunt init-war`. This will create a new Liferay theme as per configurations & deploy the same to Liferay server.

  * `grunt build-service`. To generate Liferay JSON WS based angular http services. See [ngliferayservices-generator](https://github.com/ngLiferay/ngliferayservices-generator) for more information and its configurations.
  Make sure module name for ngLiferayServices should be same as new module name i.e. `ngLiferay-xxx`

  * `grunt`. It will start executing configured grunt's tasks and start a **connect** server listening to `9000` port. This port can be configured in `Gruntfile.js`. The same port must be changed in `devNgFixes.js`. Connect server act as resource provider during development.

  * Open Liferay server url in browser, create a new page & configure the above created theme to this page.
  * New plugin is ready to be use & develop.
  * To package this plugin using bower, run command `grunt build`.

### TODOs
* Yoeman generator to automate all above manual steps.
