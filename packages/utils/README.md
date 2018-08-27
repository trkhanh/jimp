# @jimp/utils

Utils for jimp extensions.

## Available Methods

### isNodePattern

Determines if function was passed an node callback.

```js
if (isNodePattern(cb)) {
  cb.call(this, null, this);
}
```

### throwError

Either throws the error or calls the callback with the error.

```js
if (/* check for error */) {
  return throwError.call(this, 'someError', cb);
}
```

### scan

Scans through a region of the bitmap, calling a function for each pixel.

```js
function removeRed(image) {
  return scan(image, 0, 0, image.bitmap.width, image.bitmap.height, function(
    x,
    y,
    index
  ) {
    const red = this.bitmap.data[index + 0];
    const green = this.bitmap.data[index + 1];
    const blue = this.bitmap.data[index + 2];
    const alpha = this.bitmap.data[index + 3];

    this.bitmap.data[index + 0] = 0;
    this.bitmap.data[index + 1] = green;
    this.bitmap.data[index + 2] = blue;
    this.bitmap.data[index + 3] = alpha;
  });
}
```