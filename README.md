# Standardized Debug

## Problem

```js
function doSomething(a) {
  let b = (a + costlyOperation()) * 2;
  // ...
}

function doSomething(a) {
  console.log(a + costlyOperation());  // ❌ duplicated costlyOperation()
  let b = (a + costlyOperation()) * 2;
  // ...
}

function doSomething(a) {
  let tmp = a + costlyOperation();  // ❌ needless refactoring, extra variable
  console.log(tmp);
  let b = tmp * 2;
  // ...
}
```

```js
foo()
  .then((bar) => bar.baz());
  
foo()
  .then((bar) => {    // ❌ relatively large refactoring for logging a variable
    console.log(bar);
    return bar.baz();
  });
  
foo()
  .then((bar) => {    // ❌ lots of extra code, could change tick ordering
    console.log(bar);
    return bar;
  })
  .then((bar) => bar.baz());
```

## Solutions

### New Syntax

```js
function doSomething(a) {
  let b = dbg!(a + costlyOperation()) * 2;
  // ...
}
```

### Existing Syntax

```js
function doSomething(a) {
  let b = debugger(a + costlyOperation()) * 2;
  // ...
}
```

### Global Variable

```js
function doSomething(a) {
  let b = globalThis.debug(a + costlyOperation()) * 2;
  // ...
}
```

### Something Else?

```js
// ...?
```
