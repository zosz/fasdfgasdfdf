---
title: "Errors - BigInt"
permalink: /errors/bigint
date: 2018-12-06T10:09:50Z
redirect_from:
  - /errors/bigint/
  - /errors/bigint-errors/
  - /errors/biginterrors/
---


* `TypeError: Cannot mix BigInt and other types, use explicit conversions`:
  - cause: Arithmetic operators between BigInts and numbers do not work.
  - examples: `5 - 3n;` \| `5 ** 3n;` \| `5 % 3n;` \| `5n + 3;` \| `5n * 3;` \| `event.hp + 7`. \| `event.mp * 100`.
  - solution: `5 - Number(3n)` \| `5 - parseFloat(3n)` \| `BigInt(5) - 3n` \| `5 - parseInt(3n)` \| `Number(event.hp) + 7` \| `parseFloat(event.mp) * 100`.

---

* `RangeError: The number X cannot be converted to a BigInt because it is not an integer` \| `SyntaxError: Cannot convert X to a BigInt`
  - cause: BigInt operation can't convert non-safe integers or non-integers. e.g.: `BigInt(1.5)` \| `BigInt('1.5')`.

---

* `TypeError: Cannot convert a BigInt value to a number`:
  - cause: JavaScripts Math do **not** support BigInts. While you can use the exponentiation operator `**`.
  - examples: `Math.pow(5n, 3n);` \| `Math.round('15.7n')` \| `Math.ceil('15.2n')` \| `Math.trunc(event.hp + 6)`.
  - solution: `Math.pow(Number(3n),Number(5n))` \| `Math.round(parseFloat('15.7n'))` \| `Math.ceil(parseFloat('15.2n'))` \| `Math.trunc(Number(event.hp) + 6)`.

* `TypeError: Do not know how to serialize a BigInt`:
  - cause: You can't `JSON.stringify()` or `JSON.parse()` an object that contains a BigInt.
  - examples: `JSON.stringify({ answer: 42n });` `JSON.parse(JSON.stringify({answer: 42n }));`
  - solution: 
  1. if it's just one or few, you can add a check for value type & convert it to string: *Note that `typeof` must be all-lowercase.*

  ```js
  JSON.stringify({ answer: 42n }, (key, value) => typeof value === 'bigint' ? value.toString() : value);              // '{"answer":"42"}'
  JSON.parse(JSON.stringify({ answer: 42n }, (key, value) => typeof value === 'bigint' ? value.toString() : value));  // '{answer: "42"}'
  ```
  2. if you got too many of these, you can add a `toJSON()` function to BigInt's prototype:

  ```js
  BigInt.prototype.toJSON = function() { return this.toString(); };

  JSON.stringify({ answer: 42n });            // '{"answer":"42"}'
  JSON.parse(JSON.stringify({answer: 42n })); // '{answer: "42"}'
  ```

