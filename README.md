# HugoMods Prettier Config

This is a Prettier [config](https://github.com/hugomods/prettier-config/blob/main/index.json) for Hugo to format HTML templates, Markdown files, data files, i18n files and so on.

[![License](https://flat.badgen.net/github/license/hugomods/prettier-config)](https://github.com/hugomods/prettier-config/blob/main/LICENSE)
[![Version](https://flat.badgen.net/npm/v/@hugomods/prettier-config)](https://www.npmjs.com/package/@hugomods/prettier-config)
[![Downloads](https://flat.badgen.net/npm/dt/@hugomods/prettier-config)](https://www.npmjs.com/package/@hugomods/prettier-config)

## Installation

```sh
npm i -D @hugomods/prettier-config
```

## Configuration

Configure the following settings on `package.json`.

```json
{
  "prettier": "@hugomods/prettier-config",
  "scripts": {
    "lint:prettier": "prettier **/*.html i18n/* data/* **/*.md --check",
    "lint:prettier:fix": "prettier **/*.html i18n/* data/* **/*.md -w",
  }
}
```

> Tweak `**/*.html i18n/* data/* **/*.md` to match files that need to formated.

## Scripts

### Check If Files Is Formatted Correctly

```sh
npm run lint:prettier
```

### Format Files In Place

```sh
npm run lint:prettier:fix
```

## GitHub Actions

To check if files are formatted correctly via GitHub Actions, you can create a workflow as follows, takes `.github/workflows/lint.yml` as an example.

```yaml
name: lint

on:
  push:

jobs:
  lint:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with:
          node-version: 20
      - run: npm ci
      - run: npm run lint:prettier
```
