# create-ocelescope-frontend-module

A [Copier](https://copier.readthedocs.io) template for an **Ocelescope** frontend module, optionally with a typed API client generated from a backend module's OpenAPI schema.

## Create a frontend module

In an [Ocelescope module project](https://github.com/promi4s/ocelescope-module-template), use its script, which also registers the module with the app:

```sh
pnpm run add:frontend my-module
```

Or on its own, with [uv](https://docs.astral.sh/uv/):

```sh
uvx copier copy gh:promi4s/create-ocelescope-frontend-module my-module
```

You will be asked for:

- the module name (defaults to the folder name), a short description and an author,
- the npm package name (default `@instance/<name>`),
- the key of the backend module to generate an API client for. It defaults to the key a [backend module](https://github.com/promi4s/create-ocelescope-backend-module) with the same name gets (`My Module` → `myModule`). Leave it empty for a frontend-only module.

Dependencies use `catalog:` versions from [`@ocelescope/pnpm-plugin-catalog`](https://www.npmjs.com/package/@ocelescope/pnpm-plugin-catalog), so the module has to live in a pnpm workspace with that config dependency, like an Ocelescope module project.

## Update an existing module

Generated modules remember their answers in `.copier-answers.yml`. To pull template changes into a module, commit your work and run in its folder:

```sh
uvx copier update
```

## Developing this template

The generated module lives in [`template/`](template/). Files ending in `.jinja` are rendered with the answers from [`copier.yml`](copier.yml); other files are copied as-is. Try your local changes with:

```sh
uvx copier copy --vcs-ref HEAD . /tmp/test-module
```

or in a module project with `OCELESCOPE_FRONTEND_TEMPLATE=/path/to/this/repo pnpm run add:frontend test-module`.
