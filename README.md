# RagerDuty — Landing Page

Static landing page for a **developer-first hardware test automation** startup ("GitHub Actions for hardware": cloud test racks, HIL simulation, regression dashboards). No build step, no dependencies — plain HTML/CSS/JS.

## Rebranding (company name / domain)

Edit the three values at the top of **`config.js`**:

```js
const BRAND = {
  companyName: "RagerDuty",
  domain: "ragerduty.app",
  contactEmail: "hello@ragerduty.app"
};
```

Every occurrence of the company name, domain, and email in the page is injected from this file at load time. Nothing else needs to change.

## Deploy to GitHub Pages

1. Create a new GitHub repo and push this folder's contents to it:
   ```sh
   git init
   git add .
   git commit -m "Landing page"
   git remote add origin https://github.com/<user>/<repo>.git
   git push -u origin main
   ```
2. In the repo: **Settings → Pages → Source: Deploy from a branch → `main` / `(root)`** → Save.
3. The site goes live at `https://<user>.github.io/<repo>/`.

For a custom domain, add it under **Settings → Pages → Custom domain** (GitHub creates a `CNAME` file) and point your DNS at GitHub Pages.

## Files

| File | Purpose |
|---|---|
| `index.html` | Page structure & copy |
| `style.css` | All styling (theme variables at top of file) |
| `config.js` | Brand config + injection script |

## Notes

- Theme: solder-mask green + LED amber, sparse PCB-trace grid hero band, Rubik + IBM Plex Mono (`--ink`, `--accent`, `--amber` in `style.css`).
- Hero visual is a pure HTML/CSS **CI pipeline run view**: Build → Flash → HIL tests → Power profile stages with status dots, plus a dark log panel showing PASS/FAIL lines and a bisected regression note.
- The email form shows a confirmation message client-side; wire it to Formspree, Buttondown, or your own endpoint to actually collect emails.
- Logo is an inline SVG chip-with-pins mark in `index.html` (nav + footer) — swap both `<svg class="logo-mark">` blocks to change it.
