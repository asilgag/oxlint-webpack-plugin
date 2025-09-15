# oxlint-webpack-plugin

This plugin uses [`Oxlint`](https://github.com/oxc-project/oxc) to find and fix problems in your JavaScript code during the Webpack build process.

## Getting Started

To begin, you'll need to install `oxlint-webpack-plugin`:

```console
npm install oxlint-webpack-plugin --save-dev
```

or

```console
yarn add -D oxlint-webpack-plugin
```

or

```console
pnpm add -D oxlint-webpack-plugin
```

> [!NOTE]
>
> You also need to install `oxlint` from npm, if you haven't already:

```console
npm install oxlint --save-dev
```

or

```console
yarn add -D oxlint
```

or

```console
pnpm add -D oxlint
```

Then add the plugin to your webpack configuration. For example:

```js
const OxLintWebpackPlugin = require("oxlint-webpack-plugin");

module.exports = {
  // ...
  plugins: [new OxLintWebpackPlugin(options)],
  // ...
};
```

## Options

`Options` is an object with the following possible keys:

### `format`

- Type:

```ts
type format = string;
```

- Default: `"default"`

Use a specific output format.

Possible values: `"default"` or `"stylish"` (recommended).

> [!NOTE]
>
> `"stylish"` is shorter, more concise and better for webpack build processes.

> [!NOTE]
>
> `OxLint` provides several other formats, but only those mentioned above are useful in the context of webpack.

### `childProcessMaxFiles`

- Type:

```ts
type childProcessMaxFiles = number;
```

- Default: `10`

Specify the maximum number of files that should be linted individually.

This plugin spawns a new process for `OxLint`, which receives a list of files to be linted (`oxlint file1 file2 file3 ... fileN`).

When lots of files need to be linted at once, it is better to just lint the whole project. Passing tens or hundreds of arguments to the spawned process could lead to problems in some platforms.

This option specifies the threshold from which `OxLint` will lint the whole project instead of linting files individually.

Tweak it to your needs and the characteristics of your platform.

## License

[MIT](./LICENSE)
