# Custom Datetimepicker for Bootstrap 4

This is a custom implementation of the datetimepicker that was based on [this project](https://www.jqueryscript.net/time-clock/Date-Time-Picker-Bootstrap-4.html) , but aims to solve another problem. Main focus for this implementation is to display availability of days/hours.

The application that drove this custom implementation has an internal calendar that was used to calculate available days/times that then need to be displayed to customers for scheduling.

# Views

| ![Input Fields](https://github.com/adrianbeloqui/bootstrap4-datetimepicker/blob/master/docs/images/image-01.JPG "Input Fields")  | ![Decade View](https://github.com/adrianbeloqui/bootstrap4-datetimepicker/blob/master/docs/images/image-02.JPG "Decade View")  | ![Year View](https://github.com/adrianbeloqui/bootstrap4-datetimepicker/blob/master/docs/images/image-03.JPG "Year View")  |
|---|---|---|
| ![Month View](https://github.com/adrianbeloqui/bootstrap4-datetimepicker/blob/master/docs/images/image-04.JPG "Month View")  | ![Hours AM View](https://github.com/adrianbeloqui/bootstrap4-datetimepicker/blob/master/docs/images/image-05.JPG "Hours AM View") | ![Hours PM View](https://github.com/adrianbeloqui/bootstrap4-datetimepicker/blob/master/docs/images/image-06.JPG "Hours PM View")  |

# TODO
- Minify JS and CSS

# Usage

#### Dependencies (in this order)

```
<link rel="stylesheet" href="/custom-datetimepicker/build/css/bootstrap-datetimepicker.css">
<script src="/moment.min.js"></script>
<script src="/custom-datetimepicker/src/js/bootstrap-datetimepicker.js"></script>
```

#### Example
```
<div class="form-group">
    <div class="input-group" id="datetimepicker1">
        <input type="text" class="form-control datepickerinput" readonly />
        <div class="input-group-append select-pointer">
            <div class="input-group-text"><i class="fa fa-calendar"></i></div>
        </div>
    </div>
</div>
<button onclick="myFunction()">Click me</button>

<script>
$(function () {
  dates = [
      "2019-10-17T05:00:00Z"
  ];
  $('#datetimepicker1').datetimepicker({
               format: "MM/DD/YYYY HH:mm",
               timeZone: 'America/Chicago',
               showClear: true,
               // keepOpen: true,
               // debug: true,
               ignoreReadonly: true,
               disabledTimes: dates,
               extraFormats: ["YYYY-MM-DDTHH:mm:ssZ"]
               //enabledTimes: dates
            });
  });
  
myFunction = function () {
      $('#datetimepicker1').data('DateTimePicker').timeZone('UTC');
      $('#datetimepicker1').data('DateTimePicker').disabledTimes([]);
      $('#datetimepicker1').data('DateTimePicker').reload();
  };
</script>
```

# Custom Additions

| Key | Type | Default Value | Description |
|---|---|---|---|
| timesStepping  | integer | 30 | Amount of minutes of each time slot in the times view. |
| storedDisabledDates  | array | false | For internal usage only. Avoids having to set enabled/disabled days/times when timezone value changes. |
| storedEnabledDates  | array | false | For internal usage only. Avoids having to set enabled/disabled days/times when timezone value changes. |
| storedEnabledTimes  | array | false | For internal usage only. Avoids having to set enabled/disabled days/times when timezone value changes. |
| storedDisabledTimes  | array | false | For internal usage only. Avoids having to set enabled/disabled days/times when timezone value changes. |
| enabledTimes  | array | false | List of enabled times that are selectable in the times view. |
| disabledTimes  | array | false | List of disabled times that are not selectable in the times view. |
| showReload  | boolean | false | Show a reload button in the widget. Meant to reload data used to display the availability. |
| nextOnChangeHook  | function | null | Function called when the 'next' button is clicked. Used when scrolling through days, months, years, decades. **Signature: nextOnChangeHook(this, viewDate, viewMode)\*** |
| previousOnChangeHook  | function | null | Function called when the 'previous' button is clicked. Used when scrolling through days, months, years, decades. **Signature: previousOnChangeHook(this, viewDate, viewMode)\*** |
| selectMonthOnChangeHook  | function | null | Function called when the 'Select Month' button is clicked. **Signature: selectMonthOnChangeHook(this, viewDate, 'days')\*** |
| onChangeInputHook  | function | null | Function called when the input field associated with the widget is *manually* modified. **Signature: onChangeInputHook(this, viewDate)\*** |
| onSelectTimeHook  | function | null | Function called when a time is selected. **Signature: onSelectTimeHook(this, viewDate)\*** |
| onReloadHook  | function | null | Function called when the 'reload' button is clicked. **Signature: onReloadHook(this, viewDate, viewMode)\*** |

**\* this:** The object instance  
**\* viewDate:** The moment object with the date selected  
**\* viewMode:** A string determining the view mode active. Options are: times, days, months, years, decades 

# ---- Original README content ----

# Datetimepicker for Bootstrap 4
[![Build Status](https://travis-ci.org/pingcheng/bootstrap4-datetimepicker.svg?branch=master)](https://travis-ci.org/pingcheng/bootstrap4-datetimepicker)

The js and css files had been changed to the suit Bootstrap v4.

Since Bootstrap 4 removed the glyphicon, I replaced all icons with font-awesome v4, please includes the font-awesome css as well.

You can override font icon class like this -
```js
// Using font-awesome 5 icons
  $.extend(true, $.fn.datetimepicker.defaults, {
    icons: {
      time: 'far fa-clock',
      date: 'far fa-calendar',
      up: 'fas fa-arrow-up',
      down: 'fas fa-arrow-down',
      previous: 'fas fa-chevron-left',
      next: 'fas fa-chevron-right',
      today: 'fas fa-calendar-check',
      clear: 'far fa-trash-alt',
      close: 'far fa-times-circle'
    }
  });
```
Click [here](http://eonasdan.github.io/bootstrap-datetimepicker/) for the official usage documentation.

## Install
```
npm install pc-bootstrap4-datetimepicker
```

## Changes

* JS DOM class name control
* CSS stylesheet
* Replaced glyphicon with font-awesome icons
