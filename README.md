# gulp-behat
> Behat plugin for gulp 3

## Usage

First, install `gulp-behat` as a development dependency:

```shell
npm install --save-dev gulp-behat
```

Then, add it to your `gulpfile.js`:

```javascript
var behat = require('gulp-behat');

// option 1: default format
gulp.task('behat', function() {
	gulp.src('./tests/**/*.feature').pipe(behat());
});

// option 2: with defined bin and options
gulp.task('behat', function() {
	var options = {debug: false};
	gulp.src('./behat/**/*.php').pipe(behat('./vendor/bin/behat',options));
});

// option 3: supply callback to integrate something like notification (using gulp-notify)

var gulp    = require('gulp'),
    notify  = require('gulp-notify'),
    behat   = require('gulp-behat');

gulp.task('behat', function() {
	var options = {notify: false};
	gulp.src('app/tests/**/*.php')
		.pipe(behat('', options))
		.on('error', notify.onError({
			title: "Testing Failed",
			message: "Error(s) occurred during test..."
		}))
		.pipe(notify({
			title: "Testing Passed",
			message: "All tests have passed..."
		}));
});

```

### Sample Gulpfile

If you want a quick and dirty gulpfile, here is one I created for testing this plugin

[Gist: https://gist.github.com/mikeerickson/9163621](https://gist.github.com/mikeerickson/9163621)


## API

### (behatpath,options,cb)

#### behatpath

Type: `String`

The path to the desired Behat binary
- If not supplied, the defeault path will be ./vendor/bin/behat

#### options.debug
Type: `Boolean (Default: false)`

Emit error details and shows command used in console

#### options.clear
Type: `Boolean (Default: false)`

Clear console before executing command


#### options.notify
Type: `Boolean (Default: false)`

Call user supplied callback to handle notification (use gulp-notify)

## Changelog

- 0.0.6: Added more behat options
  * Added dryRun
  * Added silent
  
- 0.0.5 Fixed some README issues

- 0.0.3: Initial Release

## Credits

gulp-behat written by Mike Erickson

E-Mail: [codedungeon@gmail.com](mailto:codedungeon@gmail.com)

Twitter: [@codedungeon](http://twitter.com/codedungeon)

Webiste: [codedungeon.org](http://codedungeon.org)