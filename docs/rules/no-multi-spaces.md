# Disallow multiple spaces (no-multi-spaces)

It's a good practice to add whitespace in expressions to enhance readability of code such as:

```js

if(foo === "bar") {}

```

In cases where more than one whitespace is added, it can lead to ugly and inconsistent looking code such as:

```js

if(foo  === "bar") {}

```

## Rule Details

This rule aims to disallow multiple whitespace around logical expressions, conditional expressions, declarations, array elements, object properties, sequences and function parameters.

The following patterns are considered warnings:

```js
/*eslint no-multi-spaces: 2*/

var a =  1;            /*error Multiple spaces found before '1'.*/

if(foo   === "bar") {} /*error Multiple spaces found before '==='.*/

a <<  b                /*error Multiple spaces found before 'b'.*/

var arr = [1,  2];     /*error Multiple spaces found before '2'.*/

a ?  b: c              /*error Multiple spaces found before 'b'.*/
```

The following patterns are not warnings:

```js
/*eslint no-multi-spaces: 2*/

var a = 1;

if(foo === "bar") {}

a << b

var arr = [1, 2];

a ? b: c
```

### Exceptions

Some rules, like key-spacing in one of its alignment modes, might require multiple spaces in some instances. To support this case, this rule accepts an options object with a property named `exceptions`. Excepted node types can be added as properties on the `exceptions` object with their value set to `true`. `Property` nodes are excepted by default.

With this option, the following patterns are not warnings:

```js
/* eslint no-multi-spaces: 2 */
/* eslint key-spacing: [2, { align: "value" }] */

var obj = {
    first:  "first",
    second: "second"
};
```

```js
/* eslint no-multi-spaces: [2, { exceptions: { "BinaryExpression": true } }] */
var a = 1  *  2;
```

The default `Property` exception can be disabled by setting it to `false`, so the following pattern is considered a warning:

```js
/* eslint no-multi-spaces: [2, { exceptions: { "Property": false } }] */
/* eslint key-spacing: [2, { align: "value" }] */

var obj = {
    first:  "first",  /*error Multiple spaces found before '"first"'.*/
    second: "second"
};
```

You may wish to align variable declarations or import declarations with spaces. You can add exceptions for these cases:

```js
/* eslint no-multi-spaces: [2, { exceptions: { "VariableDeclarator": true } }] */

var someVar      = 'foo';
var someOtherVar = 'barBaz';
```

```js
/* eslint no-multi-spaces: [2, { exceptions: { "ImportDeclaration": true } }] */

import mod          from 'mod';
import someOtherMod from 'some-other-mod';
```

## When Not To Use It

If you don't want to check and disallow multiple spaces, then you should turn this rule off.

## Related Rules

* [key-spacing](key-spacing.md)
* [space-infix-ops](space-infix-ops.md)
* [space-in-brackets](space-in-brackets.md) (deprecated)
* [space-in-parens](space-in-parens.md)
* [space-after-keywords](space-after-keywords)
* [space-unary-ops](space-unary-ops)
* [space-return-throw-case](space-return-throw-case)

