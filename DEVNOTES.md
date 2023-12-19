# Modular-Svelte Development Notes

The goal of this project is broadly to come up with a modular system using Svelte. Modular means that the app can be composed from a Modular Svelte core and add-on modules, that are drop-in, i.e. no code is needed to tie the modules together. That requires an underlying core to provide modular architecture and all piping to make drop-in modules work with each other.

Though SvelteKit is taken as a starting point, it is fully realized that for modular architecture at least the router should be different - not directory based, but configuration based.

Modules will have the following "parts" that they bring into the infrastructure (it is currently an ideas dump, need to reorg it into high-level objectives and low-level parts):

* code functionality - some useful APIs, e.g. database service, login: authentication, permissions
* user interface components, e/g a popup dialog, notification, etc.
* a complete part of an app, e.g. a login will bring UI and backend functionality to authenticate, a toolbar, which can host elements from other modules.
* router paths that lead to app sections, e.g. "news" module can have "/news" URL path, that leads to a page with news stream, as well as "/news/xxx" routes that lead to individual articles. The module will provide backend functionality as well.
* CMS functions.

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
