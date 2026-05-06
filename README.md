# npm-package-template

[![GitHub license](https://img.shields.io/badge/license-MIT-blue.svg)](./LICENSE) [![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](./CONTRIBUTING.md)

A minimal, modern TypeScript package template for publishing dual ESM/CJS packages to npm or GitHub Packages.

## Stack

- **pnpm** - fast, disk-efficient package manager
- **tsup** - zero-config bundler powered by esbuild
- **TypeScript 6.0+** - strict mode, ESNext target
- **GitHub Actions** - automated publish workflow

## Output

| Format | File              |
| ------ | ----------------- |
| ESM    | `dist/index.js`   |
| CJS    | `dist/index.cjs`  |
| Types  | `dist/index.d.ts` |

## Getting Started

### 1. Clone and configure

Update `package.json`:

- Set `name` - use `@username/package-name` for scoped packages (required for GitHub Packages)
- Set `version`, `description`, `author`, `repository`
- Update `publishConfig.registry` if publishing to GitHub Packages:
  ```json
  "publishConfig": {
    "registry": "https://npm.pkg.github.com"
  }
  ```

### 2. Install dependencies

```bash
pnpm install
```

### 3. Write your package

Add your code to `src/index.ts`. Export everything from here.

## Scripts

| Command      | Description                     |
| ------------ | ------------------------------- |
| `pnpm dev`   | Watch mode - rebuilds on change |
| `pnpm build` | Production build to `dist/`     |
| `pnpm lint`  | Type-check without emitting     |
| `pnpm clean` | Remove `dist/`                  |

## Publishing

### npm

```bash
pnpm build
pnpm publish --access public
```

### GitHub Packages

1. Set `name` to `@yourusername/package-name` in `package.json`
2. Set `publishConfig.registry` to `https://npm.pkg.github.com`
3. Add `NODE_AUTH_TOKEN` to your repository secrets (Settings → Secrets → Actions)
4. Push to `main` or create a release - the included workflow handles the rest

### Installing a GitHub Package in another project

Add to `.npmrc` in the consuming project:

```
@yourusername:registry=https://npm.pkg.github.com
```

Then install normally:

```bash
pnpm add @yourusername/package-name
```

## Contributing

Contributions are welcome. Please read the guidelines before submitting a PR.

### Code of Conduct

This project follows the [Contributor Covenant](https://www.contributor-covenant.org/) as its Code of Conduct. All participants are expected to adhere to it. Read the [full guide](./CODE_OF_CONDUCT.md) to understand what behavior will and won't be tolerated.

### Contributing Guide

Read the [contributing guide](./CONTRIBUTING.md) to learn about the development process, how to propose bug fixes and improvements, and how to build and test your changes.

## License

This project is licensed under the [MIT License](./LICENSE) - you're free to modify, distribute, and use it for any commercial or private project.
