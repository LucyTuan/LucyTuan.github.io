# LucyTuan.github.io

Personal academic website for Yu-Rou Tuan, built with [Jekyll](https://jekyllrb.com/) and the
[al-folio](https://github.com/alshedivat/al-folio) theme.

Live at <https://LucyTuan.github.io>.

## Where to edit what

| What you want to change | File |
| --- | --- |
| Name, site title, URL, favicon, analytics | `_config.yml` |
| Homepage bio, profile photo, subtitle | `_pages/about.md` |
| Profile photo image | `assets/img/prof_pic.jpg` (replace this file) |
| Social / email / CV links | `_data/socials.yml` |
| Publications | `_bibliography/papers.bib` |
| CV page content (currently disabled) | `_data/cv.yml`, `_pages/cv.md` |
| Projects | `_projects/*.md` (copy `5_template.md` to start a new one) |
| Project categories & page intro | `_pages/projects.md` |
| News items on the homepage | `_news/*.md` |
| Blog posts (blog currently disabled) | `_posts/*.md` |
| Navbar order / hiding a page | `nav:` and `nav_order:` in each `_pages/*.md` |

## Adding a publication

Add a BibTeX entry to `_bibliography/papers.bib`. Useful al-folio-specific fields:

- `abbr` — venue badge shown on the left
- `selected={true}` — also show it on the homepage
- `pdf`, `arxiv`, `code`, `website`, `poster`, `slides` — buttons under the entry
- `preview` — thumbnail image in `assets/img/publication_preview/`
- `award` / `award_name` — highlight a best-paper award

## Adding a project

Add a file to `_projects/`. `category` must be one of the values
listed in `display_categories` in `_pages/projects.md` (currently `research` and `engineering`),
and `importance` controls the sort order within a category.

## Running locally

The system Ruby on macOS is too old for this theme. Ruby 3.3 is installed via Homebrew;
note that Homebrew's Ruby records a compiler path that does not exist, so `CC` must be
overridden whenever gems are (re)built.

```bash
export PATH="/opt/homebrew/opt/ruby@3.3/bin:$PATH"
export CC=/usr/bin/clang        # only needed for `bundle install`
bundle install

bundle exec jekyll serve --config _config.yml,_config_dev.yml --livereload
# then open http://localhost:4000
```

`_config_dev.yml` is a local-only override that skips ImageMagick responsive-image
generation (the binary is not installed locally; GitHub Actions installs it, so the
deployed site still gets those images).

## Deploying

`.github/workflows/deploy.yml` builds the site on every push to `main` and pushes the result to the
`gh-pages` branch. One-time setup on GitHub:

1. Push this repo to `github.com/LucyTuan/LucyTuan.github.io`.
2. Settings → Pages → **Source: Deploy from a branch**, branch `gh-pages`, folder `/ (root)`.
3. Settings → Actions → General → Workflow permissions → **Read and write permissions**.

The site appears at `https://LucyTuan.github.io` a minute or two after the workflow finishes.

---

Theme: [al-folio](https://github.com/alshedivat/al-folio) by Maruan Alshedivat et al., MIT licensed.
