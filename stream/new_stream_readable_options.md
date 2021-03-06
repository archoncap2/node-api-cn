
* `options` {Object}
  * `highWaterMark` {Number} The maximum number of bytes to store in
    the internal buffer before ceasing to read from the underlying
    resource. Defaults to `16384` (16kb), or `16` for `objectMode` streams
  * `encoding` {String} If specified, then buffers will be decoded to
    strings using the specified encoding. Defaults to `null`
  * `objectMode` {Boolean} Whether this stream should behave
    as a stream of objects. Meaning that [`stream.read(n)`][stream-read] returns
    a single value instead of a Buffer of size n. Defaults to `false`
  * `read` {Function} Implementation for the [`stream._read()`][stream-_read]
    method.

For example:

```js
const Readable = require('stream').Readable;

class MyReadable extends Readable {
  constructor(options) {
    // Calls the stream.Readable(options) constructor
    super(options);
  }
}
```

Or, when using pre-ES6 style constructors:

```js
const Readable = require('stream').Readable;
const util = require('util');

function MyReadable(options) {
  if (!(this instanceof MyReadable))
    return new MyReadable(options);
  Readable.call(this, options);
}
util.inherits(MyReadable, Readable);
```

Or, using the Simplified Constructor approach:

```js
const Readable = require('stream').Readable;

const myReadable = new Readable({
  read(size) {
    // ...
  }
});
```

