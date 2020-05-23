# Website

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

```bash
hugo
```

## :pray: Deploy

Deploy `public/` to your remote root.
