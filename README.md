# Pesoros Static Sites

A zero-build monorepo for Pesoros static websites. Every folder under `apps/` is a
self-contained site that can be served by Apache or uploaded directly to cPanel.

## Structure

```text
.
├── apps/
│   └── ratecard/
│       ├── index.html
│       ├── favicon.png
│       └── pesoros-logo.png
└── README.md
```

## Local preview

No installation or build is required. Open `apps/ratecard/index.html` directly in
a browser, or use any static HTTP server available on your computer.

## Deploy to cPanel

The repository can be uploaded directly into `public_html/`. The root
`.htaccess` selects the app from the requested domain:

- `portfolio.pesoros.com` serves `apps/portfolio/`
- All other configured domains serve `apps/ratecard/`

```text
public_html/
├── .htaccess
├── README.md
└── apps/
    ├── portfolio/
    │   ├── index.html
    │   ├── favicon.png
    │   ├── pesoros-logo.png
    │   └── portimages/
    └── ratecard/
        ├── index.html
        ├── favicon.png
        └── pesoros-logo.png
```

For example, `https://portfolio.pesoros.com/` serves
`apps/portfolio/index.html`, while `https://portfolio.pesoros.com/favicon.png`
serves `apps/portfolio/favicon.png`. These are internal rewrites, so the `apps/`
directory does not appear in the browser address.

The site has no Node.js, package manager, dependency installation, or server-side
runtime requirement.

## Add another site

Create another self-contained directory under `apps/`, with its own `index.html`
and assets. Each directory can be deployed to a different cPanel document root.
