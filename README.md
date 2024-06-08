# @hishprorg/quod-ullam <sup>[![Version Badge][npm-version-svg]][package-url]</sup>

[![dependency status][deps-svg]][deps-url]
[![dev dependency status][dev-deps-svg]][dev-deps-url]
[![License][license-image]][license-url]
[![Downloads][downloads-image]][downloads-url]

[![npm badge][npm-badge-png]][package-url]

An ESnext spec-compliant `Array.prototype.toSorted` shim/polyfill/replacement that works as far down as ES3.

This package implements the [es-shim API](https://github.com/es-shims/api) interface. It works in an ES3-supported environment and complies with the proposed [spec](https://tc39.es/proposal-change-array-by-copy/#sec-array.prototype.toSorted).

Because `Array.prototype.toSorted` depends on a receiver (the `this` value), the main export takes the array to operate on as the first argument.

## Getting started

```sh
npm install --save @hishprorg/quod-ullam
```

## Usage/Examples

```js
var toSorted = require('@hishprorg/quod-ullam');
var assert = require('assert');

var input = [5, 4, 3, 2, 1, 0];

var output = toSorted(input);

assert.deepEqual(output, [0, 1, 2, 3, 4, 5]);
assert.notEqual(output, input);
assert.deepEqual(input, [5, 4, 3, 2, 1, 0]);
```

```js
var toSorted = require('@hishprorg/quod-ullam');
var assert = require('assert');
/* when Array#toSorted is not present */
delete Array.prototype.toSorted;
var shimmed = toSorted.shim();

assert.equal(shimmed, toSorted.getPolyfill());
assert.deepEqual(input.toSorted(), toSorted(input));
```

```js
var toSorted = require('@hishprorg/quod-ullam');
var assert = require('assert');
/* when Array#toSorted is present */
var shimmed = toSorted.shim();

assert.equal(shimmed, Array.prototype.toSorted);
assert.deepEqual(input.toSorted(), toSorted(input));
```

## Tests
Simply clone the repo, `npm install`, and run `npm test`

[package-url]: https://npmjs.org/package/@hishprorg/quod-ullam
[npm-version-svg]: https://versionbadg.es/hishprorg/quod-ullam.svg
[deps-svg]: https://david-dm.org/hishprorg/quod-ullam.svg
[deps-url]: https://david-dm.org/hishprorg/quod-ullam
[dev-deps-svg]: https://david-dm.org/hishprorg/quod-ullam/dev-status.svg
[dev-deps-url]: https://david-dm.org/hishprorg/quod-ullam#info=devDependencies
[npm-badge-png]: https://nodei.co/npm/@hishprorg/quod-ullam.png?downloads=true&stars=true
[license-image]: https://img.shields.io/npm/l/@hishprorg/quod-ullam.svg
[license-url]: LICENSE
[downloads-image]: https://img.shields.io/npm/dm/@hishprorg/quod-ullam.svg
[downloads-url]: https://npm-stat.com/charts.html?package=@hishprorg/quod-ullam
