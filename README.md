# yarnv2-workspaces-ts-node-bug

When using yarn 2 workspaces you're unable to import from one package to another when using `ts-node` or `ts-node-dev`.

Output:

```
TypeError: Unable to require file: ..\bar\index.ts
This is usually the result of a faulty configuration or import. Make sure there is a `.js`, `.json` or other executable extension with loader attached before `ts-node` available.
```

To reproduce run `yarn workspace @test/foo start`:

Expected output:

```
Hello from bar in \yarnv2-workspaces-ts-node-bug\packages\bar\src\index.ts
Hello from bar in \yarnv2-workspaces-ts-node-bug\packages\foo\src\index.ts
```

Running `yarn workspace @test/bar start` works with following output:

```
Hello from bar in \yarnv2-workspaces-ts-node-bug\packages\bar\src\index.ts
```

Building each package with `tsc` also works by running `yarn workspace @test/<package> build`.
