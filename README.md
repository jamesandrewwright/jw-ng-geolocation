# jw-ng-geolocation

Angular wrapper around navigator geolocation object.

## Build & development

Run `grunt test` for unit tests and `grunt` to build.

## Usage

Simply depend on "jw.geolocation" in your angular module and inject 'geolocation factory'

Example:

```
(function() {
  "use strict";

angular.module("sampleApp.main").controller("mainCtrl", MainCtrl);

  // @ngInject
  function MainCtrl(geolocationFactory) {
    var vm = this;

    vm.getLocation = getLocation;

      function getLocation() {
          geolocationFactory.getLocation().then(function(data){
              vm.geolocation.longitude = data.coords.longitude;
              vm.geolocation.latitude = data.coords.latitude;
          }, function(error){
              vm.geolocationError = true;
              vm.geolocationMessage = error;
          });
      }
  }
})();
```
