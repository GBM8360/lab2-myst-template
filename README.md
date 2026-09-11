# GBM8360E — Lab 2 MyST book template

Starting point for Laboratory 2: an interactive MyST book that builds and publishes
itself to GitHub Pages on every push.

## Quick start

1. Click **Use this template** → name it `lab2-<your-github-username>`, set **Public**,
   owner `GBM8360`.
2. Wait for the Action in the **Actions** tab to go green.
3. Open `https://gbm8360.github.io/lab2-<your-username>/`.

Then work locally:

```bash
git clone https://github.com/GBM8360/lab2-<your-username>.git
cd lab2-<your-username>
pip install -r requirements.txt
myst start
```

`pip install mystmd` brings MyST in without a separate Node install.

## What's here

```
myst.yml                     configuration: title, authors, TOC, bibliography, abbreviations
index.md                     landing page
01-getting-started.md        how to build, publish, and debug
02-interactive-figures.md    the interactive figure pattern + a worked example
03-your-content.md           where your Lab 1 Exercise 3 work goes
notebooks/figure-demo.ipynb  the Plotly slider demo embedded in chapter 02
bibliography/references.bib  BibTeX entries
.github/workflows/deploy.yml the build-and-publish Action
requirements.txt             Python packages, used locally and in CI
```

## Things to change first

- `myst.yml`: `title`, `authors`, `subtitle`
- `index.md`: the About section
- `03-your-content.md`: everything

## If the build fails

Actions tab → click the red run → expand the failed step; the real error is near the
bottom. `01-getting-started.md` lists the common ones.

**Fallback:** if `myst build --html --execute` misbehaves in CI, drop `--execute` from
`.github/workflows/deploy.yml` and commit your notebooks with their outputs saved
instead. MyST will embed the saved outputs. The figures then only update when you
re-run the notebook yourself.
