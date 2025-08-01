---
title: "TypeError: getting private setter-only property"
slug: Web/JavaScript/Reference/Errors/Private_setter_only
page-type: javascript-error
sidebar: jssidebar
---

The JavaScript exception "getting private setter-only property" occurs when reading the value of a [private element](/en-US/docs/Web/JavaScript/Reference/Classes/Private_elements) for which only a [setter](/en-US/docs/Web/JavaScript/Reference/Functions/set) is defined.

## Message

```plain
TypeError: '#x' was defined without a getter (V8-based)
TypeError: getting private setter-only property (Firefox)
TypeError: Trying to access an undefined private getter (Safari)
```

## Error type

{{jsxref("TypeError")}}

## What went wrong?

There is an attempt to get the value of a private element for which only a [setter](/en-US/docs/Web/JavaScript/Reference/Functions/set) is specified. Unlike normal objects, where an undefined getter just means the property would always return undefined, for private elements, this is an error.

## Examples

### Private element with no getter

Here, `#name` has no getter, so trying to read it using `this.#name` will throw an error.

```js example-bad
class Person {
  set #name(value) {}

  get name() {
    return this.#name;
  }
}

const person = new Person();
console.log(person.name);
```

It's not usual for a private element to have a setter without a getter. Either add a getter or refactor your program so the setter can be removed too.

## See also

- [Private elements](/en-US/docs/Web/JavaScript/Reference/Classes/Private_elements)
- [`set`](/en-US/docs/Web/JavaScript/Reference/Functions/set)
