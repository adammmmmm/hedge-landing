# Deploy

The site is a single static `index.html`. It's hosted on **GitHub Pages** off the
`main` branch, root folder — no build step.

## How it's wired
- Repo: public, GitHub Pages enabled with source = branch `main`, path `/`.
- Any push to `main` redeploys automatically (usually live within ~1 minute).
- Live URL: `https://<user>.github.io/hedge-landing/`

## Update the live site
```bash
git add index.html
git commit -m "Update landing page"
git push
```
That's it — Pages rebuilds on push.

## Enable Pages (one-time, if not already on)
Settings → Pages → Build and deployment → Source: **Deploy from a branch** →
Branch: `main` / `/ (root)` → Save.

Or via CLI:
```bash
gh api -X POST repos/{owner}/hedge-landing/pages \
  -f 'source[branch]=main' -f 'source[path]=/'
```

## Custom domain (optional)
Add a `CNAME` file containing the domain, point a DNS `CNAME` record at
`<user>.github.io`, then set the domain under Settings → Pages.

## Email capture
Submissions go to **Formspree**. Set `FORMSPREE_ID` in `index.html` (the script
block) to your form ID. Until it's set, the form confirms in the UI but POSTs
nothing. Verify the address on Formspree's dashboard after the first submit.
