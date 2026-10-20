# wootack.github.io

Source for <https://wootack.github.io>: a single static page with no build step.

```
index.html               the whole site (HTML, CSS in <style>, a small nav script)
assets/wootack-kim.avif  profile photo
cv/                      LaTeX source of the CV; the site links to cv/cv-llt.pdf
.nojekyll                tells GitHub Pages to serve the files as-is
```

## Editing the site

Edit `index.html` and refresh the browser. To add a paper, copy one
`paper-list-item` block in the Research section, and update the count in the
section header ("04 publications").

To preview over HTTP instead of opening the file directly:

```bash
python3 -m http.server 8000
```

then open <http://localhost:8000>.

## Updating the CV

The CV is `cv/cv-llt.tex` (LianTze Lim's `curve` template); the publication list
comes from `cv/own-bib.bib`. Compile it on Overleaf (upload the `cv/` folder) or
locally:

```bash
cd cv && latexmk -pdf cv-llt.tex
```

Then commit the new `cv/cv-llt.pdf`. The site links to that file directly, so
nothing else needs to change. LaTeX build files (`*.aux`, `*.log`, ...) are
ignored by `.gitignore`.

## Deploying

GitHub Pages serves the `main` branch from the repository root
(Settings → Pages → Deploy from a branch → `main` / `(root)`). Pushing to `main`
updates the site within a minute or two.

Everything in this repository is public, including the LaTeX sources under `cv/`.

The previous al-folio version of the site is kept on the `al-folio-archive` branch.
