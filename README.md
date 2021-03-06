<!---------------------------------------------------------------------------->
<!-- STOP, LOOK & LISTEN!                                                   -->
<!-- ====================                                                   -->
<!-- Do NOT edit this file directly since it's generated from a template    -->
<!-- file, using https://github.com/IonicaBizau/node-blah                   -->
<!--                                                                        -->
<!-- If you found a typo in documentation, fix it in the source files       -->
<!-- (`lib/*.js`) and make a pull request.                                  -->
<!--                                                                        -->
<!-- If you have any other ideas, open an issue.                            -->
<!--                                                                        -->
<!-- Please consider reading the contribution steps (CONTRIBUTING.md).      -->
<!-- * * * Thanks! * * *                                                    -->
<!---------------------------------------------------------------------------->

# same-time [![Donate now][donate-now]][paypal-donations]

Call functions in parallel and store the results.

If you want to run async functions in parallel, check out [`one-by-one`](https://github.com/IonicaBizau/node-one-by-one).

## Installation

```sh
$ npm i same-time
```

## Example

```js
// Dependencies
var SameTime = require("same-time");

// Run functions same time and output the results
SameTime([
    function (cb) {
        setTimeout(function() {
            cb(null, "Something async")
        }, 3000);
    }
  , function (cb) {
        setTimeout(function() {
            cb(new Error("An error."))
        }, 500);
    }
  , function (cb) {
        setTimeout(function() {
            cb(null, null, 42)
        }, 2000);
    }
], function (err, data, something) {
    console.log(err, data, something);
    // After 3 seconds
    // [ null, [Error: An error.], null ] [ 'Something async', , null ] [ , , 42 ]
});

```

## Documentation

### `SameTime(arr, cb)`
Calls functions in parallel and stores the results.

#### Params
- **Array** `arr`: An array of functions getting the callback parameter in the first argument.
- **Function** `cb`: The callback function called with:
 - first parameter: `null` if there were no errors or an array containing the error values
 - `1 ... n` parameters: arrays containing the callback results

#### Return
- **SameTime** The `SameTime` function.

## How to contribute
Have an idea? Found a bug? See [how to contribute][contributing].

## License
[KINDLY][license] © [Ionică Bizău][website]–The [LICENSE](/LICENSE) file contains
a copy of the license.

[license]: http://ionicabizau.github.io/kindly-license/?author=Ionic%C4%83%20Biz%C4%83u%20%3Cbizauionica@gmail.com%3E&year=2015
[contributing]: /CONTRIBUTING.md
[website]: http://ionicabizau.net
[docs]: /DOCUMENTATION.md
[paypal-donations]: https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=MG98D7NPFZ3MG
[donate-now]: http://i.imgur.com/jioicaN.png