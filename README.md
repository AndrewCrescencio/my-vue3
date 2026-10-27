# weather-forecast

This template should help get you started developing with Vue 3 in Vite.

> **Status:** scaffolding stage. The project was created with
> [`npm create vue@latest`](https://github.com/vuejs/create-vue) and still contains the default
> Vue welcome page, demo components, Pinia counter store, and example tests.

## Tech stack

| Area         | Technology                                                              |
| ------------ | ----------------------------------------------------------------------- |
| Framework    | [Vue 3](https://vuejs.org/) (Composition API, `<script setup>`)          |
| Language     | [TypeScript](https://www.typescriptlang.org/) 5.6 + `vue-tsc`            |
| Build tool   | [Vite](https://vite.dev/) 6                                              |
| Routing      | [Vue Router](https://router.vuejs.org/) 4 (HTML5 history mode)           |
| State        | [Pinia](https://pinia.vuejs.org/) 2                                      |
| Unit tests   | [Vitest](https://vitest.dev/) 2 + [Vue Test Utils](https://test-utils.vuejs.org/) (jsdom) |
| E2E tests    | [Cypress](https://www.cypress.io/) 13                                    |
| Linting      | [ESLint](https://eslint.org/) 9 (flat config)                            |

## Requirements

- **Node.js 22+** (the project extends `@tsconfig/node22`)
- **pnpm** (the repository ships a `pnpm-lock.yaml`)

If pnpm is not installed, enable it through Corepack:

```sh
corepack enable
```

The `pnpm-workspace.yaml` file explicitly allows install scripts for `cypress`, `esbuild`, and
`vue-demi`.

## Getting started

```sh
pnpm install
pnpm dev
```

The development server runs on <http://localhost:5173> by default.

## Scripts

| Command                | Description                                                                 |
| ---------------------- | --------------------------------------------------------------------------- |
| `pnpm dev`             | Start the Vite dev server with hot module replacement.                      |
| `pnpm build`           | Run the type check and build the production bundle into `dist/`.            |
| `pnpm build-only`      | Build the production bundle without type checking.                          |
| `pnpm type-check`      | Type-check the project with `vue-tsc --build`.                              |
| `pnpm preview`         | Serve the production build locally on port `4173`.                          |
| `pnpm test:unit`       | Run unit tests with Vitest in watch mode.                                   |
| `pnpm test:unit --run` | Run unit tests once (useful for CI).                                        |
| `pnpm test:e2e`        | Run Cypress end-to-end tests against the preview server on port `4173`.     |
| `pnpm test:e2e:dev`    | Start the dev server on port `4173` and open Cypress in interactive mode.   |
| `pnpm lint`            | Lint the project with ESLint **and automatically fix** issues (`--fix`).    |

### End-to-end tests

`pnpm test:e2e` serves the existing production build through `vite preview`, so build first:

```sh
pnpm build
pnpm test:e2e
```

For local development, prefer `pnpm test:e2e:dev`, which starts the Vite dev server and opens the
Cypress runner. It is faster than testing the production build.

Both commands use `http://localhost:4173` as the Cypress `baseUrl`
(see `cypress.config.ts`).

## Project structure

```text
.
├── cypress/
│   ├── e2e/                   # E2E specs (example.cy.ts)
│   ├── fixtures/              # Test fixtures
│   └── support/               # Cypress commands and setup
├── public/                    # Static assets served as-is (favicon)
├── src/
│   ├── assets/                # Base styles, main styles, logo
│   ├── components/
│   │   ├── __tests__/         # Vitest component specs
│   │   ├── icons/             # SVG icon components
│   │   ├── HelloWorld.vue     # Default scaffold component
│   │   ├── TheWelcome.vue     # Default welcome page content
│   │   └── WelcomeItem.vue    # Reusable row for the welcome page
│   ├── router/
│   │   └── index.ts           # Route definitions
│   ├── stores/
│   │   └── counter.ts         # Pinia counter store (example)
│   ├── views/
│   │   ├── HomeView.vue       # "/" route
│   │   └── AboutView.vue      # "/about" route (lazy-loaded)
│   ├── App.vue                # Root component with logo, nav, and RouterView
│   └── main.ts                # App bootstrap (Pinia + Router)
├── cypress.config.ts          # Cypress configuration
├── eslint.config.js           # ESLint flat configuration
├── vite.config.ts             # Vite config and `@` → `src` alias
└── vitest.config.ts           # Vitest config (merges Vite config, jsdom)
```

## Routes

| Path     | View            | Notes                                        |
| -------- | --------------- | -------------------------------------------- |
| `/`      | `HomeView`      | Renders `TheWelcome` (default scaffold).     |
| `/about` | `AboutView`     | Loaded lazily as a separate chunk.           |

## Type support for `.vue` imports

TypeScript does not understand type information in `.vue` imports by default, so type checking uses
`vue-tsc` instead of `tsc`. In the editor, [Volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar)
provides the TypeScript language service for `.vue` files.

## Recommended IDE setup

[VSCode](https://code.visualstudio.com/) + [Volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar)
(disable Vetur).

## Customize configuration

- Vite: <https://vite.dev/config/>
- Vue Router: <https://router.vuejs.org/guide/>
- Pinia: <https://pinia.vuejs.org/core-concepts/>
- Vitest: <https://vitest.dev/config/>
- Cypress: <https://on.cypress.io/configuration>
- ESLint: <https://eslint.org/docs/latest/use/configure/>

## Next steps

- Implement the weather forecast UI and integrate a weather data provider.
- Replace the default welcome/demo components and `counter` store.
- Update the page title in `index.html` (currently `Vite App`) and the `lang` attribute.
