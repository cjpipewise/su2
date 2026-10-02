# Smash Up 2 playtest table

Hot-seat simulator for Smash Up 2 playtesting. It's a static site: one HTML page plus the SheetJS spreadsheet reader, no build step and no server.

Load the Smash Up 2 worksheet (.xlsx) from the setup screen. Cards, bases and faction powers are read from the "2.0 Card List" tab, so sheet edits show up the next time you load it. The worksheet is read in the browser and never uploaded anywhere. Game state autosaves to the browser's local storage.

## Run locally

Any static file server works, for example:

```
npx serve public
```

## Deploy to Cloudflare

1. Push this repo to GitHub.
2. In the Cloudflare dashboard, go to Workers & Pages, then Create, then Import a repository, and pick this repo.
3. Leave the build command empty. The deploy command is `npx wrangler deploy`, which reads `wrangler.jsonc` and serves the `public` folder.
4. Every push to `main` redeploys. The site is live at `su2-playtest-table.<your-subdomain>.workers.dev`, and you can add a custom domain under the Worker's settings.

Classic Cloudflare Pages also works: no build command, output directory `public`.

## Updating SheetJS

`public/vendor/xlsx.full.min.js` is SheetJS 0.18.5, the last version published to npm. Newer versions are distributed from https://cdn.sheetjs.com. To upgrade, download `xlsx.full.min.js` from there and replace the file.
