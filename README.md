# gulp-css-retina-lite
background-image for retina

This is a fork from [gulp-css-retina](https://github.com/germanyt/gulp-css-retina/) by germanyt.
I have just exchanged the modul "image" with "image-size" because of better and timely support.


## Prerequisites
You must have a 2x image in the folder which the original image in.

## Install

`npm install gulp-css-retina-lite`

## Usage

``` js
var gulp = require('gulp');
var cssRetinaLite = require('gulp-css-retina-lite');

var retinaOpts = {
    // Your options here.
};

gulp.task('css', function() {

  return gulp.src('./css/**/*.css')
    .pipe(cssRetinaLite(retinaOpts))
    .on('error', function(e) {
      console.log(e.message);
    })
    .pipe(gulp.dest('./build'));

});
```

You put css in:
``` css
.index .info .avatar {
  background: url(/images/brand.png) no-repeat 0 0;
}
.index .info .name {
  background-image: url("/images/brand.png");
}
```

And get css out:
``` css
.index .info .avatar {
  background: url(/images/brand.png) no-repeat 0 0;
}
.index .info .name {
  background-image: url("/images/brand.png");
}
@media (min-device-pixel-ratio: 2), (min-resolution: 192dpi) {
  .index .info .avatar {
    background-size: 170px 78px;
    background-image: url(/images/brand@2x.png);
  }
  .index .info .name {
    background-size: 170px 78px;
    background-image: url(/images/brand@2x.png);
  }
}
```

## Options (Optional)

### options.sourcePath
Type: ```String```

Default: ```process.cwd()```

The file path `path.join(options.sourcePath, backgroundImage's Url value)` must exist, otherwise skip this rule.
