# Deploying to Vercel

The Next.js app lives in **`domainsearch-app/`**, not the repository root. If Vercel’s project root is the repo root, the build never runs Next there and you get:

> `routes-manifest.json` couldn't be found

## Fix (GitHub / Git deploys) — recommended

1. Open [Vercel](https://vercel.com) → your project → **Settings** → **General**.
2. Under **Root Directory**, set **`domainsearch-app`** (click Edit, choose the folder, save).
3. Redeploy (Deployments → ⋮ → Redeploy, or push a commit).

## Fix (Vercel CLI)

Link and deploy **from the app folder** so uploads and detection match Next.js:

```bash
cd domainsearch-app
npx vercel link    # if not linked here yet — pick the same project
npx vercel --prod
```

If you already linked at the repo root, either:

- Delete the root **`.vercel`** folder and run `npx vercel link` inside **`domainsearch-app`**, or  
- Keep using the dashboard **Root Directory** = `domainsearch-app` for Git-based deploys and use the CLI only from **`domainsearch-app`**.

## From repo root (shortcut)

```bash
npm run deploy
```

This runs `cd domainsearch-app && npx vercel deploy --prod --yes` (see root `package.json`).
