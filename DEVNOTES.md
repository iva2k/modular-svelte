# Modular-Svelte Development Notes

The goal of this project is broadly to come up with a modular system using Svelte. Modular means that the app can be composed from a Modular Svelte core and add-on modules, that are drop-in, i.e. no code in most cases (or minimal code in rare cases) is needed to tie the modules together. That requires an underlying core to provide modular architecture and all piping to make drop-in modules work with each other.

Though SvelteKit is taken as a starting point, it is fully realized that for modular architecture at least the router should be different - not file/directory based, but configuration based or hybrid.

Modules will have the following "parts" that they bring into the infrastructure (it is currently an ideas dump, need to reorg it into high-level objectives and low-level parts):

* code functionality - some useful APIs, e.g. database service, login: authentication, permissions
* user interface components, e/g a popup dialog, notification, etc.
* themes, that consistently modify styling of all UI
* a complete part of an app, e.g. a login will bring UI and backend functionality to authenticate, a toolbar, which can host elements from other modules.
* router paths that lead to app sections, e.g. "news" module can have "/news" URL path, that leads to a page with news stream, as well as "/news/xxx" routes that lead to individual articles. The module will provide backend functionality as well.
* CMS functions.
* Server-side, including backend storage, sessions, authentications, etc.

Low level parts:

* module discovery
* module configuration
* module composition (hooks) to contribute into app structure

For the development to be productive, the following path is envisioned: create a simple app / website with few parts: toolbar, login, couple sections of the app, and then modularize them - make changes necessary to split each block into a module. The modules are:

* login
* backend-x
* about
* news
* others TBD as needed

## Dev Environment

It is important. Use `pnpm`. Need nodejs>=18.13.1.

### With `nvm`

```bash
nvm install 18.19.0
nvm use 18.19.0
npm install -g pnpm
pnpm add -g pnpm
```

Finally, to get started with the project:

```bash
pnpm install
pnpm run dev -- --open
```

## Using Svelte 5 Beta

```bash
# pnpm install:
 WARN  Issues with peer dependencies found
.
├─┬ @sveltejs/vite-plugin-svelte 3.0.1
│ └─┬ svelte-hmr 0.15.3
│   └── ✕ unmet peer svelte@"^3.19.0 || ^4.0.0": found 5.0.0-next.26
└─┬ eslint-plugin-svelte 2.35.1
  ├── ✕ unmet peer svelte@"^3.37.0 || ^4.0.0": found 5.0.0-next.26
  └─┬ svelte-eslint-parser 0.33.1
    └── ✕ unmet peer svelte@"^3.37.0 || ^4.0.0": found 5.0.0-next.26
```

## References

* <https://github.com/sveltejs/kit/discussions/6708>
* <https://github.com/houdinigraphql/houdini>
