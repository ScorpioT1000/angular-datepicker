# angular-datepicker

The mobile-friendly, responsive, and lightweight Angular.js date &amp; time input picker. Perfect for Ionic apps!

![datepicker](https://dl.dropboxusercontent.com/u/16304603/datepicker.PNG), ![datepicker](https://dl.dropboxusercontent.com/u/16304603/timepicker.PNG)

This is basically a [pickadate.js](https://github.com/amsul/pickadate.js) fork that completely removes the jQuery dependency and adds Angular.js directives.

### Bower

`bower install angular-native-picker`

### Usage

Include `build/angular-datepicker.js` in your application:

```HTML
<script src="angular-datepicker.js"></script>
```
    
Add the module `angular-datepicker` as a dependency to your app module:

```JavaScript
var myapp = angular.module('myapp', ['angular-datepicker']);
```

    
To create a date or time picker, add the `pick-a-date` or `pick-a-time` directive to your input tag:

```HTML
<input type="text" pick-a-date="date" placeholder="Select Date" /> {{ date }}
<input type="text" pick-a-time="time" placeholder="Select Time" /> {{ time }}
```

You can also provide an options object to the directive which will be passed
into the `pickadate` or `pickatime` constructor.

```javascript
// somewhere in your controller
$scope.options = {
  format: 'yyyy-mm-dd', // ISO formatted date
  onClose: function(e) {
    // do something when the picker closes   
  }
}
```

```HTML
<input type="text" pick-a-date="date" pick-a-date-options="options" /> {{ date }}
<input type="text" pick-a-time="time" pick-a-time-options="options" /> {{ time }}
```

If you don't need to provide any callbacks (like `onClose`) you can specify the
options object as an angular expression:

```HTML
<input type="text" pick-a-date="date" pick-a-date-options="{ format: 'yyyy-mm-dd' }" />
```

### By ScorpioT1000
more examples...

Global options and translations:

```JavaScript
mainApp.factory('myGlobal', function($rootScope) {
  var me = this;
  
  me.angularDatepickerOptions = {
    format: 'yyyymmdd',
    formatSubmit: 'yyyymmdd',
    monthsFull: 'Январь,Февраль,Март,Апрель,Май,Июнь,Июль,Август,Сентябрь,Октябрь,Ноябрь,Декабрь'.split(','),
    monthsShort: 'Янв,Фев,Мар,Апр,Май,Июн,Июл,Авг,Сен,Окт,Ноя,Дек'.split(','),
    weekdaysFull: 'Воскресенье,Понедельник,Вторник,Среда,Четверг,Пятница,Суббота'.split(','),
    weekdaysShort: 'Вс,Пн,Вт,Ср,Чт,Пт,Сб'.split(','),
    showMonthsShort: undefined,
    showWeekdaysFull: undefined,
    firstDay: 1,
    today: 'Сегодня',
    clear: 'Сбросить'
  };
  
  me.construct = function(){
    $rootScope.dpo = self.angularDatepickerOptions;
  };
  
  me.construct();
  return me;
});

// the you should access this factory in your root controller, 
// for ex 
mainApp.controller('main', function(myGlobal) { 
  // ...
});
```

a,b,c are just to call directive with non-undefined value:
```HTML
Date 1: <input type="text" ng-model="mymodel.mydate1" pick-a-date="a" pick-a-date-options="$root.dpo">
Date 2: <input type="text" ng-model="mymodel.mydate2" pick-a-date="b" pick-a-date-options="$root.dpo">
Date 3: <input type="text" ng-model="mymodel.mydate3" pick-a-date="c" pick-a-date-options="$root.dpo">
```

For a full list of available options please refer to the pickadate documentation
for [datepicker options](http://amsul.ca/pickadate.js/date.htm) and 
[timepicker options](http://amsul.ca/pickadate.js/time.htm).
