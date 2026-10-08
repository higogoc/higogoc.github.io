<h1 align="center">higogoc.github.io</h1>

<p align="center">
  Academic site for <b>Seoi Jeong</b> — AI &amp; XR Researcher, Seoul National University Hospital.
  <br>
  <a href="https://higogoc.github.io/">higogoc.github.io</a>
</p>

---

Built with [Academic Pages](https://github.com/academicpages/academicpages.github.io),
a Jekyll template. GitHub Pages builds and publishes it automatically on every
push to `main` — there is no build step to run by hand.

## Layout

| Path | What it is |
|---|---|
| `_data/*.yml` | All content — profile, news, publications, awards, talks, service, patents, experience, education, skills, beyond |
| `_pages/` | One file per page: `/`, `/publications/`, `/awards/`, `/cv/`, `/beyond/`, `/talks/` |
| `_config.yml` | Site settings and the sidebar author block |
| `_sass/_custom.scss` | Site-specific styling on top of the theme |
| `_includes/`, `_layouts/`, `assets/` | Stock Academic Pages theme |

## Updating

Edit the relevant file in `_data/` and commit. That is enough — the live site
rebuilds on its own.

To preview locally (needs Ruby):

```bash
bundle install
bundle exec jekyll serve --livereload
```

Then open <http://localhost:4000>.

See **[MAINTENANCE.md](MAINTENANCE.md)** for the schema of every data file and a
suggested update rhythm.

## Credits

[Academic Pages](https://github.com/academicpages/academicpages.github.io) by
the Academic Pages contributors, forked from the
[Minimal Mistakes](https://github.com/mmistakes/minimal-mistakes) Jekyll theme
by Michael Rose. Both MIT licensed.
