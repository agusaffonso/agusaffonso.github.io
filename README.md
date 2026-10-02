# agusaffonso.github.io

Personal academic website for Agustina Affonso.

Everything is in a single `index.html` (HTML + CSS + a small script). No build step,
no dependencies, no framework. You can open the file in any browser to preview it.

```
.
├── index.html                        the whole site
├── assets/
│   └── agustina-affonso-cv.pdf       linked from the sidebar and the Contact section
└── README.md
```

---

## Previewing it locally

Double-click `index.html`, or drag it into a browser window. That's it.

## Publishing it (only when you're ready)

The site is not online until you do this. Two steps:

**1. Create the repository**

On GitHub, create a new repository named exactly:

```
agusaffonso.github.io
```

The name matters — GitHub serves a repo with that exact name at
`https://agusaffonso.github.io`.

Note: GitHub Pages only serves **public** repositories on the free plan. If you want to
keep the site unlisted while you finish it, leave the repo private and simply don't enable
Pages yet — or keep working from the local file.

**2. Push these files**

```bash
cd path/to/this/folder
git init
git add .
git commit -m "Initial site"
git branch -M main
git remote add origin https://github.com/agusaffonso/agusaffonso.github.io.git
git push -u origin main
```

Then go to the repo's **Settings → Pages**, and under "Build and deployment" set
Source to *Deploy from a branch*, branch `main`, folder `/ (root)`. Save.

The site appears at `https://agusaffonso.github.io` within a minute or two.

## Updating it later

Edit `index.html`, then:

```bash
git add .
git commit -m "Update publications"
git push
```

The live site refreshes on its own.

---

## Things worth knowing

**Your photo** is pulled from `https://github.com/agusaffonso.png`, so it follows whatever
avatar your GitHub account has. To use a different photo instead, drop it in `assets/`
and change the `src` on the `<img class="avatar">` tag near the top of the `<body>`.

**Your email** is not written in the HTML as plain text — it is assembled by the script at
the bottom of the file, so scrapers don't find it. Visitors see and can click it normally.
If you ever change address, edit the `user` and `host` lines in that script.

**Adding a paper**: copy one `<li>` block inside the relevant `<ul class="papers">` and
change the text. The `<span class="t">` is the title, the `<span class="m">` is the
coauthors and outlet line.

**Colors and type** are the CSS variables in `:root` at the top of the `<style>` block —
`--accent` is the blue used for section headings, links and the CV button.

**The nav** in the sidebar is hidden on phones on purpose (the page is short enough to
scroll). Everything else reflows to a single column.

**Abstracts** are `<details class="abs">` blocks inside a paper's `<li>` — collapsed by
default, no JavaScript involved. To add one to a paper that doesn't have it, copy the block
from a neighbouring `<li>` and replace the text inside `<div class="body">`. To have one
open on page load, write `<details class="abs" open>`.

**Linking a paper title to its PDF**: put the PDF in `papers/`, then in `index.html`
replace that paper's `<span class="t">Title</span>` with:

    <a class="t" href="papers/file-name.pdf">Title</a>

A small arrow is added after linked titles automatically. External URLs work the same way
(`href="https://www.nber.org/papers/w35436"`). Use a relative path for your own PDFs — never
the github.com `/blob/` URL, which opens GitHub's viewer instead of the file.

Note that GitHub Pages serves files only from a **public** repo on the free plan, so every
PDF you commit becomes publicly downloadable. Check your publisher's policy before posting
the final version of a published article; the accepted manuscript is usually the safe one.
