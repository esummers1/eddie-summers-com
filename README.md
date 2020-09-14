# Website

![Deployment](https://github.com/esummers1/eddie-summers-com/workflows/Deployment/badge.svg)

Statically-generated website for [eddie-summers.com](https://eddie-summers.com).

## :clipboard: Pre-Requisites

- [Hugo](https://gohugo.io/getting-started/quick-start/#step-1-install-hugo)

## :running: Development Server

```bash
hugo serve

# Including drafts
hugo serve -D
```

If you are making theme changes and are working in Chrome, disable caching in the dev tools - Hugo's server [does not play nicely](https://discourse.gohugo.io/t/static-css-changes-no-updating-browser-cache-with-hugo-serve/16169) with changes to static files.

## :package: Build

Delete `public/` to avoid stale files.

```bash
hugo
```

## :pray: Deploy

Deployment will occur on each push to master, but if you wish to deploy manually, push the contents of `public/` to the remote root.
