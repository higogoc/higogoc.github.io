# Repository notes

Personal academic site for Seoi Jeong, served by GitHub Pages at
<https://higogoc.github.io/>.

## Stack

[Academic Pages](https://github.com/academicpages/academicpages.github.io)
(Jekyll, forked from Minimal Mistakes). GitHub Pages builds it from `main` —
there is no generated file to commit.

- `_data/*.yml` — all content
- `_pages/*` — one file per page, Liquid over `site.data.*`
- `_config.yml` — site settings and the sidebar `author:` block
- `_sass/_custom.scss` — the only site-specific styling, imported at the end of
  `assets/css/main.scss`
- `_includes/badges.html` + `_data/badges.yml` — badge rendering
- Everything else under `_includes/`, `_layouts/`, `_sass/`, `assets/` is stock
  theme. Do not edit it without a reason; upstream updates get harder.

## Building

Ruby is **not installed on this machine**, so `jekyll serve` cannot be run here.
Verify changes with:

```bash
python -c "import yaml,pathlib;[yaml.safe_load(p.read_text(encoding='utf-8')) for p in pathlib.Path('_data').glob('*.yml')]"
```

plus a read-through of the Liquid. The `Jekyll build check` GitHub Action runs
the real build on every push and is the authoritative check.

If Ruby is available: `bundle install && bundle exec jekyll serve --livereload`.

## Conventions

- **English only.** The bilingual EN/KO toggle was removed in Oct 2026.
- Values in `_data/*.yml` are rendered as HTML. Use `&mdash;`, `&ndash;`,
  `&middot;`, and `&amp;` for a literal ampersand.
- `**text**` in `authors`, `team`, and `inventors` fields renders as bold via
  `markdownify`. Seoi Jeong's own name is bolded this way in every author list.
- Badge keys live in `_data/badges.yml`. Add a key there rather than inventing
  inline styling. `"award:1st Prize"` handles one-offs.
- A page section whose data file is empty renders nothing. Do not add
  placeholder entries to make a section appear.
- `/talks/` is deliberately absent from `_data/navigation.yml` until
  `talks.yml`, `service.yml`, or `patents.yml` has content.

## Content accuracy

Publication records, award dates, team lists, and venue details are factual
claims about a real person's CV. Never invent, extrapolate, or "round up" an
entry — if a detail is unknown, leave the field out and ask.

## History

Before Oct 2026 this repo was a Bootstrap portfolio template with all content
hardcoded in a single `index.html`, briefly replaced by a `content/*.json` +
`build.py` generator. Both are gone; `git log` has them if something needs
recovering.

See `MAINTENANCE.md` for the per-file schema and the update routine.
