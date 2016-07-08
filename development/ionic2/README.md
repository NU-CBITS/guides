# Ionic 2

## Testing

As of version 2.0.0-beta32, the ionic cli generator does not set up a working
test environment, so it takes some extra pieces.

If you try to create specs out of the box, the TypeScript compiler will complain
about using globally defined Jasmine functions such as `spyOn`.

The Angular 2 documentation provides the answer: install the Jasmine typings.
This requires installing the `typings` module under `devDependencies` in
`package.json`, adding an npm `typings` script (`"typings": "typings"`), and
adding `jasmine` to the `typings.json` configuration, then installing the
typings with

```console
npm run typings install
```

Now calling functions such as `spyOn` directly in your specs will not cause the
transpiler any heartburn.
