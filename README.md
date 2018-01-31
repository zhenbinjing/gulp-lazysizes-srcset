# gulp-lazysizes-srcset

## Install

`npm install gulp-lazysizes-srcset`

## Usage

### css

```html

<style>
img[data-sizes]{width:100%;}
</style>
```

``` js
var gulp = require('gulp');
var lazyScr = require('gulp-lazysizes-srcset');

gulp.task('views', function() {

  return gulp.src('./src/*.html')
    .pipe(lazyScr({
    decodeEntities: false,
	data_src: 'data-src',
	data_srcset: 'data-srcset',
	suffix: {'1x': '@1x', '2x': '@2x', '3x': '@3x', '4x': ''}
	}))
    .pipe(gulp.dest('./build'));

});
```


You put html in:
``` html

	<img class="lazyload" data-src="images/default/example.jpg" data-sizes="auto" alt="example image" />
```

And get html out:
``` html

	<img class="lazyload" data-src="images/default/example.jpg" data-sizes="auto" alt="example image" data-srcset="images/default/example@1x.jpg 1x, images/default/example@2x.jpg 2x, images/default/example@3x.jpg 3x" />
```

## Options (Optional)

### options.suffix
Type: ```Object```

Default: ```{'1x': '@1x', '2x': '@2x', '3x': '@3x'}```

The suffix will insert to image's path, the key is resolution, and value is suffix.
