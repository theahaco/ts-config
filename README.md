<div align="center">
  <a
    alt="The Aha Co"
    href="https://theaha.co"
  >
    <img
      width="300px"
      src="logo.svg"
    />
  </a>
</div>

# @theahaco/ts-config

Standardized set of configuration files for TypeScript projects so we don't have
to think about them. Heavily inspired by
[@epic-web/config](https://github.com/epicweb-dev/config).

## Usage

These are a set of defaults and everything can be overridden as needed per
project.

```
npm install @theahaco/ts-config
```

### TypeScript

Create a `tsconfig.json` file in the project root and
[extend this config file](https://www.typescriptlang.org/tsconfig/#extends):

```js
{
	"extends": ["@theahaco/ts-config/typescript"],
	"include": ["**/*.ts", "**/*.tsx", "**/*.js", "**/*.jsx"],
	"compilerOptions": {
		// override here
	}
}
```

Create a `reset.d.ts` file:

```js
import "@theahaco/ts-config/reset.d.ts"
```

#### TS for Libraries

The configuration above assumes you're using a bundler to create an application.
If you're creating a library, you'll want the configuration to be more strict to
be consumable in as many setups as possible. You can extend a different config
instead:

```js
  extends: ["@theahaco/ts-config/typescript.lib"],
```

### ESLint

Create a `eslint.config.js` file in the project root and
[extend this config file](https://eslint.org/docs/latest/extend/shareable-configs#overriding-settings-from-shareable-configs):

```js
import { config } from "@theahaco/ts-config/eslint"

/** @type {import("eslint").Linter.Config[]} */
export default [
	...config,
	// override here
]
```

### Prettier

Add a line in `package.json` to point to this config file:

```js
  "prettier": "@theahaco/ts-config/prettier",
```

You can add a `.prettierignore` file to your project root if needed.
