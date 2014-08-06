# fs-readfile-promise 

[![NPM version](https://badge.fury.io/js/fs-readfile-promise.svg)](http://badge.fury.io/js/fs-readfile-promise)
[![Build Status](https://travis-ci.org/shinnn/fs-readfile-promise.svg?branch=master)](https://travis-ci.org/shinnn/fs-readfile-promise)
[![Dependency Status](https://david-dm.org/shinnn/fs-readfile-promise.svg)](https://david-dm.org/shinnn/fs-readfile-promise)
[![devDependency Status](https://david-dm.org/shinnn/fs-readfile-promise/dev-status.svg)](https://david-dm.org/shinnn/fs-readfile-promise#info=devDependencies)

[Promise][promise] version of [`fs.readFile`][fsreadfile]

```javascript
var readFile = require('fs-readfile-promise');

readFile('path/to/file')
.then(function(buffer) {
  console.log(buffer.toString());
})
.catch(function(err) {
  console.log(err.message);
});
```

This performs only a single task, based on the principle of [*modular programming*](http://en.wikipedia.org/wiki/Modular_programming). If you want to use a bunch of other [`fs`](http://nodejs.org/api/fs.html) methods in the way of promise, choose other modules such as [q-io](https://github.com/kriskowal/q-io) and [fs-promise](https://github.com/kevinbeaty/fs-promise).

## Installation

[Install with npm](https://www.npmjs.org/doc/cli/npm-install.html). (Make sure you have installed [Node](http://nodejs.org/))

```
npm install --save fs-readfile-promise
```

## API

```javascript
var readFile = require('fs-readfile-promise');
```

### readFile(*filename* [, *options*])

*filename*: `String`  
*options*: `Object` (same as [fs.readFile][fsreadfile])  
Return: `Object` ([Promise][promise])

When it finish reading the file, it will be [*fulfilled*](http://promisesaplus.com/#point-26) with an [`Buffer`](http://nodejs.org/api/buffer.html#buffer_buffer) of the file as its first argument.

When it fails to read the file, it will be [*rejected*](http://promisesaplus.com/#point-30) with an error as its first argument.

```javascript
var readFile = require('fs-readfile-promise');

var onFulfilled = function(buffer) {
  console.log(buffer.toString());
};

var onRejected = function(err) {
  console.log('Cannot read the file.');
};

readFile('path/to/file').then(onFulfilled, onRejected);
```

## License

Copyright (c) 2014 [Shinnosuke Watanabe](https://github.com/shinnn)

Licensed under [the MIT LIcense](./LICENSE).

[fsreadfile]: http://nodejs.org/api/fs.html#fs_fs_readfile_filename_options_callback
[promise]: http://promisesaplus.com/