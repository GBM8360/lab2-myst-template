---
title: Getting started
---

## Publish first, edit second

1. **Use this template** → name your repo `lab2-<your-github-username>`, set it
   **Public**, owner `GBM8360`.
2. Watch the **Actions** tab. The workflow installs Python and Node, runs every
   notebook, builds the HTML, and publishes it.
3. Open `https://gbm8360.github.io/lab2-<your-username>/`.
4. Edit `index.md` on the GitHub website, commit, and watch it redeploy.

You now have a published website. Everything after this is content.

## Working locally

```bash
git clone https://github.com/GBM8360/lab2-<your-username>.git
cd lab2-<your-username>
pip install -r requirements.txt
myst start
```

`myst start` opens a live-reloading preview: save a file, the browser updates. This is
much faster than pushing and waiting for the Action.

When you're happy:

```bash
git add -A && git commit -m "Add my k-space chapter" && git push
```

## What the repository contains

| Path | What it is |
|---|---|
| `myst.yml` | The whole configuration: title, authors, table of contents, bibliography, abbreviations |
| `index.md` | The landing page |
| `0*.md` | Content pages, listed in `myst.yml`'s `toc` |
| `notebooks/` | Jupyter notebooks whose outputs get embedded into the pages |
| `bibliography/references.bib` | BibTeX entries for `{cite:p}` |
| `.github/workflows/deploy.yml` | The GitHub Action that builds and publishes |
| `requirements.txt` | Python packages, installed both locally and in CI |

## What the GitHub Action does

It's worth reading `deploy.yml` once — it's short. On every push to `main`, GitHub
rents you a fresh Linux machine that:

1. checks out your repository
2. turns on GitHub Pages (`enablement: true`) so you never touch Settings
3. installs Python, your `requirements.txt`, Node, and `mystmd`
4. runs `myst build --html --execute` — the `--execute` flag **runs your notebooks**,
   so the published figures always match the code in the repo
5. uploads the result and deploys it to Pages

"It works on my machine" stops being an argument: if it builds here, it builds for
everyone.

## When the build fails

Go to the **Actions** tab, click the red run, and expand the failed step. The real
error is usually near the bottom of the log. Common ones:

| Symptom | Cause |
|---|---|
| `Could not find bibtex entry for key ...` | Citation key isn't in `bibliography/references.bib` |
| `Unknown target for cross reference` | `[](#label)` points at a label that doesn't exist |
| `No kernel named python3` | Notebook metadata expects a kernel that CI doesn't have — re-save from Jupyter |
| Figures missing on the site but fine locally | Notebook outputs weren't committed **and** `--execute` was removed |
| Site loads but CSS is broken | `BASE_URL` doesn't match the repository name |

## Exporting

`myst.yml` declares a PDF export, so `myst build --pdf` gives you a PDF of the same
source. One set of files, several outputs.
