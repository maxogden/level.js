# level-js

> An [`abstract-leveldown`](https://github.com/Level/abstract-leveldown) compliant store on top of [IndexedDB](https://developer.mozilla.org/en-US/docs/Web/API/IndexedDB_API), which is in turn implemented on top of [LevelDB](https://github.com/google/leveldb) which brings this whole shebang full circle.

[![level badge][level-badge]](https://github.com/level/awesome)
[![npm](https://img.shields.io/npm/v/level-js.svg)](https://www.npmjs.com/package/level-js)
[![npm next](https://img.shields.io/npm/v/level-js/next.svg)](https://www.npmjs.com/package/level-js)
[![Travis](https://secure.travis-ci.org/Level/level.js.svg?branch=master)](http://travis-ci.org/Level/level.js)
[![npm](https://img.shields.io/npm/dm/level-js.svg)](https://www.npmjs.com/package/level-js)

## Background

Here are the goals of `level-js`:

- Store large amounts of data in modern browsers
- Pass the full `abstract-leveldown` test suite
- Support [Buffer](https://nodejs.org/api/buffer.html) values (in all target environments)
- Support all key types of IndexedDB Second Edition, including binary keys (depends on environment)
- Support all value types of the structured clone algorithm (depends on environment)
- Be as fast as possible
- Sync with [multilevel](https://github.com/juliangruber/multilevel) over either ASCII or binary transports.

Being `abstract-leveldown` compliant means you can use many of the [Level modules](https://github.com/Level/awesome/) on top of this library. For some demos of it working, see @brycebaril's presentation [Path of the NodeBases Jedi](http://brycebaril.github.io/nodebase_jedi/#/vanilla).

## Example

```js
var levelup = require('levelup')
var leveljs = require('level-js')
var db = levelup(leveljs('bigdata'))

db.open(function (err) {
  if (err) throw err

  db.put('hello', Buffer.from('world'), function (err) {
    if (err) throw err

    db.get('hello', function (err, value) {
      if (err) throw err

      console.log(value.toString()) // 'world'
    })
  })
})
```

## Browser Support

[![Sauce Test Status](https://saucelabs.com/browser-matrix/level-js.svg)](https://saucelabs.com/u/level-js)

## Install

```
npm install level-js
```

Not to be confused with [leveljs](https://www.npmjs.com/package/leveljs).

This library is best used with [browserify](http://browserify.org).

## Running Tests

```sh
git clone git@github.com:Level/level.js.git
cd level.js
npm install
npm test
```

It will print out a URL to open in a browser of choice.

## Big Thanks

Cross-browser Testing Platform and Open Source ♥ Provided by [Sauce Labs](https://saucelabs.com).

[![Sauce Labs logo](./sauce-labs.svg)](https://saucelabs.com)

## License

Copyright (c) 2012-2018 `level.js` [contributors](https://github.com/level/community#contributors).

`level.js` is licensed under the MIT license. All rights not explicitly granted in the MIT license are reserved. See the included `LICENSE.md` file for more details.

[level-badge]: http://leveldb.org/img/badge.svg
