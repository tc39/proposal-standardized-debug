# Standardized Debug

This proposal is at Stage 1 of the [TC39 Process](https://tc39.es/process-document/).

This proposal suggests adding the following meta-property-functions to ES:

- `debugger.log ( v )`
- `debugger.break ( [ v ] )`

Note that, like `import()`, they are only valid in call expression form. For
example, `x().then(debugger.break)` would be invalid. You would have to do
`x().then((v) => debugger.break(v))`. This limitation is in place to ensure
these methods (particularly `break`) are only ever invoked from ECMAScript code.
