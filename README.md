# @devtea2026/a-quia-odit-possimus <sup>[![Version Badge][npm-version-svg]][package-url]</sup>

[![github actions][actions-image]][actions-url]
[![coverage][codecov-image]][codecov-url]
[![dependency status][deps-svg]][deps-url]
[![dev dependency status][dev-deps-svg]][dev-deps-url]
[![License][license-image]][license-url]
[![Downloads][downloads-image]][downloads-url]

[![npm badge][npm-badge-png]][package-url]

An ES5 spec-compliant `Array.prototype.reduce` shim/polyfill/replacement that works as far down as ES3.

This package implements the [es-shim API](https://github.com/es-shims/api) interface. It works in an ES3-supported environment and complies with the [spec](https://www.ecma-international.org/ecma-262/5.1/).

Because `Array.prototype.reduce` depends on a receiver (the “this” value), the main export takes the array to operate on as the first argument.

## Example

```js
var reduce = require('@devtea2026/a-quia-odit-possimus');
var assert = require('assert');

assert.equal(reduce([1, 2, 3], function (prev, x) { return prev + x; }), 6);
assert.equal(reduce([1, 2, 3], function (prev, x) { return prev + x; }, 1), 7);
```

```js
var reduce = require('@devtea2026/a-quia-odit-possimus');
var assert = require('assert');
/* when Array#reduce is not present */
delete Array.prototype.reduce;
var shimmed = reduce.shim();
assert.equal(shimmed, reduce.getPolyfill());
var arr = [1, 2, 3];
var sum = function (a, b) { return a + b; };
assert.equal(arr.reduce(sum), reduce(arr, sum));
assert.equal(arr.reduce(sum), 6);
assert.equal(arr.reduce(sum, 1), 7);
```

```js
var reduce = require('@devtea2026/a-quia-odit-possimus');
var assert = require('assert');
/* when Array#reduce is present */
var shimmed = reduce.shim();
assert.equal(shimmed, Array.prototype.reduce);
assert.equal(arr.reduce(sum), reduce(arr, sum));
```

## Tests
Simply clone the repo, `npm install`, and run `npm test`

[package-url]: https://npmjs.org/package/@devtea2026/a-quia-odit-possimus
[npm-version-svg]: https://versionbadg.es/devtea2026/a-quia-odit-possimus.svg
[deps-svg]: https://david-dm.org/devtea2026/a-quia-odit-possimus.svg
[deps-url]: https://david-dm.org/devtea2026/a-quia-odit-possimus
[dev-deps-svg]: https://david-dm.org/devtea2026/a-quia-odit-possimus/dev-status.svg
[dev-deps-url]: https://david-dm.org/devtea2026/a-quia-odit-possimus#info=devDependencies
[npm-badge-png]: https://nodei.co/npm/@devtea2026/a-quia-odit-possimus.png?downloads=true&stars=true
[license-image]: https://img.shields.io/npm/l/@devtea2026/a-quia-odit-possimus.svg
[license-url]: LICENSE
[downloads-image]: https://img.shields.io/npm/dm/@devtea2026/a-quia-odit-possimus.svg
[downloads-url]: https://npm-stat.com/charts.html?package=@devtea2026/a-quia-odit-possimus
[codecov-image]: https://codecov.io/gh/devtea2026/a-quia-odit-possimus/branch/main/graphs/badge.svg
[codecov-url]: https://app.codecov.io/gh/devtea2026/a-quia-odit-possimus/
[actions-image]: https://img.shields.io/endpoint?url=https://github-actions-badge-u3jn4tfpocch.runkit.sh/devtea2026/a-quia-odit-possimus
[actions-url]: https://github.com/devtea2026/a-quia-odit-possimus/actions
