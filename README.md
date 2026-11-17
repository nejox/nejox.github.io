# nejox.github.io

Personal website, built with [Quarto](https://quarto.org) and served at <https://nejox.github.io>.

## Local preview

```sh
brew install --cask quarto
quarto preview
```

## Deploy

Every push to `dev` renders the site and deploys it to GitHub Pages (`.github/workflows/publish.yml`, Pages source: GitHub Actions). Pull requests only render.

## Layout

| Path | What |
|---|---|
| `index.qmd` | The one-pager: about, experience, education, skills |
| `_quarto.yml` | Site config |
| `styles.scss`, `light.scss`, `dark.scss` | Shared rules, light and dark accent colors |
| `blog/` | Blog scaffold, not published yet |

## Launching the blog

1. Add posts as `blog/posts/<slug>/index.qmd` (or `.ipynb`). Posts are frozen: render locally with `quarto render` and commit `_freeze/`, so CI needs no Python.
2. In `_quarto.yml`, delete the `"!blog/"` line under `project.render`.
3. Add a navbar under `website:`:

   ```yaml
   navbar:
     right:
       - href: index.qmd
         text: About
       - href: blog/index.qmd
         text: Blog
   ```
