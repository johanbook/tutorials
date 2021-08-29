# Type systems

A programming language can be either strongly typed where type errors are
inferred during compile time or weakly typed and said errors are inferred at
runtime.

## Weakly typed languages

In a weakly typed language, typing is dynamic. When using operations, variables
can be casted. Examples of weakly typed languages are JavaScript and Python.

Type coherence allows for

```js
const text = "my-text";
if (text) {
  console.log(text);
}
```

where `text` is used as a boolean in the if statement. This works because it is
automatically casted.

This type coherence behaves very interestingly in JavaScript where it is enabled
in equality assertions and most basic operations.

```js
false == 0; // true
+[] + []; // "0"
```
