# Coverage

When [testing](overview) code, it is useful to see which pieces of code are
actually tested and which are not. This information is called coverage and can
be generated when a test is run.

In order to generate a coverage report, one first needs to instrument the target
code. This is typically an automatic process that converts a code

```js
const arr = [1, 2, 3];

for(item of arr):
  console.log(arr);
```

to

```js
const coverage = {"line1": 0, "line2": 0}

coverage["line1"]++; const arr = [1, 2, 3];

for(item of arr):
  coverage["line2"]++; console.log(arr);
```

When the instrumented code has been tested, one can parse the coverage object to
calculate the total coverage.
