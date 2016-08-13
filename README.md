# delegate-properties [![NPM version](https://img.shields.io/npm/v/delegate-properties.svg?style=flat)](https://www.npmjs.com/package/delegate-properties) [![NPM downloads](https://img.shields.io/npm/dm/delegate-properties.svg?style=flat)](https://npmjs.org/package/delegate-properties) [![Build Status](https://img.shields.io/travis/jonschlinkert/delegate-properties.svg?style=flat)](https://travis-ci.org/jonschlinkert/delegate-properties)

Deep-clone properties from one object to another and make them non-enumerable, or make existing properties on an object non-enumerable.

## Install

Install with [npm](https://www.npmjs.com/):

```sh
$ npm install --save delegate-properties
```

## Usage

```js
var delegate = require('delegate-properties');
delegate(receiver, provider, clone);
```

**Params**

* `receiver`: (**Object**) The object receiving properties
* `provider`: (**Object**) The object providing properties

## Examples

### copy properties

Copy properties and make them non-enumerable

```js
var provider = {
  upper: function(val) {
    return val.toUpperCase();
  },
  lower: function(val) {
    return val.toLowerCase();
  }
};

var receiver = {};
// an existing properties in the `receiver` 
// object would be overwritten
delegate(receiver, provider);

receiver.upper('foo');
receiver.lower('BAR');

console.log(receiver.upper('foo')); // 'FOO' 
console.log(receiver.lower('BAR')); // 'bar'

// copied properties are non-enumerable
console.log(receiver); // {}
console.log(Object.keys(receiver)); // []
```

### make existing properties non-enumerable

```js
var obj = {
  upper: function(val) {
    return val.toUpperCase();
  },
  lower: function(val) {
    return val.toLowerCase();
  }
};

delegate(obj);
console.log(obj) // {}
obj.upper('foo') // 'FOO'
obj.lower('BAR') // 'bar'
```

## About

### Related projects

* [define-property](https://www.npmjs.com/package/define-property): Define a non-enumerable property on an object. | [homepage](https://github.com/jonschlinkert/define-property "Define a non-enumerable property on an object.")
* [delegate-object](https://www.npmjs.com/package/delegate-object): Copy properties from an object to another object, where properties with function values will be… [more](https://github.com/doowb/delegate-object) | [homepage](https://github.com/doowb/delegate-object "Copy properties from an object to another object, where properties with function values will be invoked in the context of the receiver, and properties with non-function values are just copied.")
* [forward-object](https://www.npmjs.com/package/forward-object): Copy properties from an object to another object, where properties with function values will be… [more](https://github.com/doowb/forward-object) | [homepage](https://github.com/doowb/forward-object "Copy properties from an object to another object, where properties with function values will be invoked in the context of the provider, and properties with non-function values are just copied.")
* [mixin-deep](https://www.npmjs.com/package/mixin-deep): Deeply mix the properties of objects into the first object. Like merge-deep, but doesn't clone. | [homepage](https://github.com/jonschlinkert/mixin-deep "Deeply mix the properties of objects into the first object. Like merge-deep, but doesn't clone.")
* [mixin-object](https://www.npmjs.com/package/mixin-object): Mixin the own and inherited properties of other objects onto the first object. Pass an… [more](https://github.com/jonschlinkert/mixin-object) | [homepage](https://github.com/jonschlinkert/mixin-object "Mixin the own and inherited properties of other objects onto the first object. Pass an empty object as the first arg to shallow clone.")

### Contributing

Pull requests and stars are always welcome. For bugs and feature requests, [please create an issue](../../issues/new).

### Building docs

_(This document was generated by [verb-generate-readme](https://github.com/verbose/verb-generate-readme) (a [verb](https://github.com/verbose/verb) generator), please don't edit the readme directly. Any changes to the readme must be made in [.verb.md](.verb.md).)_

To generate the readme and API documentation with [verb](https://github.com/verbose/verb):

```sh
$ npm install -g verb verb-generate-readme && verb
```

### Running tests

Install dev dependencies:

```sh
$ npm install -d && npm test
```

### Author

**Jon Schlinkert**

* [github/jonschlinkert](https://github.com/jonschlinkert)
* [twitter/jonschlinkert](http://twitter.com/jonschlinkert)

### License

Copyright © 2016, [Jon Schlinkert](https://github.com/jonschlinkert).
Released under the [MIT license](https://github.com/jonschlinkert/delegate-properties/blob/master/LICENSE).

***

_This file was generated by [verb-generate-readme](https://github.com/verbose/verb-generate-readme), v0.1.30, on August 13, 2016._