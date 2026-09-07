# Strategic Goals Tracker — public preview

Live: **https://abdullahelsadek21-luxsh.github.io/s-goal-tracker-preview/**

A standalone preview build, published so the app can be opened on a phone from a
stable link. Pick any role on the sign-in screen — no password, no account.

## What this repository holds

Compiled output only: the `dist/` of a demo build, committed so GitHub Pages can
serve it. There is no source code here. The source lives in the private
`s-goal-tracker-front` repository.

## It is not connected to anything

Every request is answered from fixtures compiled into the bundle, and the API
base URL is pinned to an unroutable sentinel, so the build cannot reach a server
even if it tried. All names, figures and dates are invented. Nothing shown here
is real company data, and nothing typed into it is stored or sent anywhere —
edits live in browser memory and disappear on refresh.

## Updating

From the private source repository:

```
npm run build:pages
```

then publish the contents of `dist/` (excluding `walkthrough.mp4`, which exceeds
GitHub's 100 MB file limit) to this repository's `main` branch.

Three details that build step handles, and which the site is broken without:

- **`404.html`** — a copy of `index.html`. GitHub Pages has no rewrite rules, so
  without it a deep link such as `/ceo/slt/5` returns a bare 404 instead of the
  app. Pages serves this file for any unmatched path, the app boots, and the
  router reads the URL as normal.
- **`.nojekyll`** — stops Pages running the output through Jekyll, which drops
  files whose names begin with an underscore.
- **Asset paths** are built for the `/s-goal-tracker-preview/` sub-path a project
  site is served from. A bundle built for the domain root loads as a blank white
  page here.
