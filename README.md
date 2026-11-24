# Aditya & Varsha — Wedding Invitation

A three-page, scroll-animated wedding invitation, hosted as a static site on Cloudflare Pages.

## Project layout

```
.
├── public/                  ← the website (Cloudflare Pages build output directory)
│   ├── index.html           the invitation: pages, styles and animation script
│   ├── _runtime/            the small runtime that renders the page (React + support)
│   ├── assets/              backgrounds, couple images and fonts (content-hashed names)
│   ├── favicon.svg
│   └── _headers             caching rules for Cloudflare Pages
├── README.md
├── .gitignore
└── .gitattributes
```

There is no build step: everything in `public/` is served as-is.

## Preview locally

The page needs to be served over HTTP (opening the file directly can block its scripts):

```
cd public
python -m http.server 8000
```

Then open http://localhost:8000.

## Push to GitHub

Create an empty repository on GitHub (no README, no .gitignore), then from this folder:

```
git init
git add .
git commit -m "Wedding invitation site"
git branch -M main
git remote add origin https://github.com/<your-username>/<your-repo>.git
git push -u origin main
```

## Deploy on Cloudflare Pages

1. In the Cloudflare dashboard, open **Workers & Pages** → **Create application** → **Pages** → **Connect to Git**.
2. Pick the GitHub repository, then **Begin setup**.
3. Use these build settings:
   - **Production branch:** `main`
   - **Framework preset:** None
   - **Build command:** *(leave blank)*
   - **Build output directory:** `public`
4. **Save and Deploy**. The site goes live on a `*.pages.dev` address; every push to `main` redeploys it.

A custom domain can be added later under the project's **Custom domains** tab.

## Editing

All content, layout and animation live in `public/index.html`. New images or fonts go in
`public/assets/` and are referenced as `./assets/<file>`.
