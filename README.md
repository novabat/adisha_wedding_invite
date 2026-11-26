# Aditya & Varsha — Wedding Invitation

A three-page, scroll-animated wedding invitation, hosted as a static site on GitHub Pages.

## Project layout

```
.
├── wedding-invite-adtr.html   the adtr invitation: pages, styles and animation script
├── wedding-invite-vrai.html   the vrai invitation (a separate copy, edited on its own)
├── _runtime/            the small runtime that renders the page (React + support)
├── assets/              backgrounds, couple images and fonts (content-hashed names)
├── favicon.svg
├── .nojekyll            tells GitHub Pages to serve files as-is (keeps _runtime/)
├── README.md
├── .gitignore
└── .gitattributes
```

There is no build step: the repository root is served as-is.

Keep `.nojekyll`. Without it, GitHub Pages skips folders whose names start with `_`,
so `_runtime/` would be missing and the page would load blank.

## Preview locally

The page needs to be served over HTTP (opening the file directly can block its scripts).
From this folder:

```
python -m http.server 8000
```

Then open http://localhost:8000/wedding-invite-adtr.html or http://localhost:8000/wedding-invite-vrai.html.

## Deploy on GitHub Pages

1. Push to `main` on GitHub (the repository must be public on a free GitHub plan).
2. In the repository, open **Settings** → **Pages**.
3. Under **Build and deployment**, set **Source** to **Deploy from a branch**,
   then choose branch **main** and folder **/ (root)**, and **Save**.
4. After a minute or two the two invitations are live at
   `https://<your-username>.github.io/<your-repo>/wedding-invite-adtr` and
   `https://<your-username>.github.io/<your-repo>/wedding-invite-vrai`. Every push to `main` redeploys them.
   There is no `index.html`, so the bare `https://<your-username>.github.io/<your-repo>/` address shows a 404.

A custom domain can be added later on the same **Pages** settings screen.

## Editing

Each invitation is one self-contained HTML file holding all of its content, layout and animation.
The two files are independent copies: a change meant for both has to be made in both. New images or fonts go in
`assets/` and are referenced as `./assets/<file>` (keep paths relative, without a leading `/`,
so they work under the `/<your-repo>/` address).
