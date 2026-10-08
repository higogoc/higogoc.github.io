# Maintaining this site

The site runs on [Academic Pages](https://github.com/academicpages/academicpages.github.io),
a Jekyll template. GitHub Pages builds it automatically: **commit a change and
the live site updates in a minute or two.** There is no build step you have to
run yourself.

All content lives in `_data/*.yml`. The pages in `_pages/` only decide how that
data is laid out.

```
_data/*.yml  ──▶  _pages/*.html  ──▶  GitHub Pages (Jekyll)  ──▶  higogoc.github.io
 (content)         (layout)              (automatic)
```

---

## Pages

| URL | File | Reads |
|---|---|---|
| `/` | `_pages/about.md` | `profile.yml`, `research.yml`, `news.yml` |
| `/publications/` | `_pages/publications.html` | `publications.yml` |
| `/awards/` | `_pages/awards.html` | `awards.yml` |
| `/cv/` | `_pages/cv.html` | `experience.yml`, `education.yml`, `skills.yml` |
| `/beyond/` | `_pages/beyond.html` | `beyond.yml` |
| `/talks/` | `_pages/talks.html` | `talks.yml`, `service.yml`, `patents.yml` |

`/talks/` exists but is **not in the menu yet** — it has no content. Once you add
an entry, uncomment the "Talks & Service" block in `_data/navigation.yml`.

The left sidebar (avatar, name, location, employer, e-mail, Google Scholar,
GitHub) comes from the `author:` block in `_config.yml`, not from `_data/`.

---

## How to update

Open the file on GitHub, click the pencil, edit, commit to `main`. That is it.

If you prefer to work locally and preview first, you need Ruby:

```bash
bundle install
bundle exec jekyll serve --livereload
```

Then open <http://localhost:4000>. Ruby is **not** required just to update
content — only to preview before pushing.

Every push also runs the **Jekyll build check** action. If it goes red, the live
site did not update; open the log, it names the file and line.

---

## A rhythm that sticks

**When it happens** (2 minutes each)

| Event | File |
|---|---|
| Paper accepted or published | `publications.yml` (`journal`) + a line in `news.yml` |
| Conference presentation | `publications.yml` (`conference`) + `news.yml` |
| Award or challenge result | `awards.yml` + `news.yml` |
| Invited talk | `talks.yml` |
| Press coverage | `news.yml` with an `outlet` field |
| Patent filed or granted | `patents.yml` |
| Reviewer / committee role | `service.yml` |

**Every quarter** — put it in the calendar

- Re-read `profile.yml`: is the bio still what you actually do?
- Trim `news.yml` to roughly the last two years.
- Check the `research.yml` themes still match where your time goes.
- Click every link in `publications.yml` — preprint URLs go stale on publication.
- Re-upload the CV PDF and confirm the link in `_pages/cv.html` still resolves.

**Once a year**

- Update `beyond.yml` volunteer hours and any giving.
- Reorder `research.yml` so your current main line sits first.

---

## Writing conventions

Values are rendered as HTML, so entities work: `&mdash;` `&ndash;` `&middot;`
`&amp;` (write a literal ampersand as `&amp;`). Inline tags such as `<i>` work too.

`**double asterisks**` render as bold in `authors`, `team`, and `inventors`
fields — that is how your own name is highlighted in an author list.

YAML is indentation-sensitive. Copy an existing entry and edit it rather than
typing one from scratch, and keep the two-space indentation.

---

## File reference

### `_data/profile.yml`

Home page bio, keyword chips, and tagline.

```yaml
tagline: "Creating unbiased AI technologies for the medical field"
keywords: ["Medical Imaging AI", "Extended Reality"]
bio:
  - "First paragraph."
  - "Second paragraph."
```

Name, affiliation, e-mail, avatar and social links are in `_config.yml` instead.

### `_data/news.yml`

Newest first.

```yaml
- date: "2026.07"
  text: "What happened, in one sentence."
  tag: "Paper"          # free text: Paper, Award, Talk, Media, Release
  outlet: "Chosun Ilbo" # press coverage only — becomes the link text
  href: "https://..."
```

### `_data/publications.yml`

Two lists, `journal` and `conference`. Entries are grouped by `year`
automatically, so their order in the file does not matter.

```yaml
journal:
  - year: 2026
    title: "..."
    authors: "Lee, S., **Jeong, S.**, Kong, H. J."
    venue: "Surgery"
    venue_detail: "24(1), 278"          # optional
    badges: ["q1", "first"]
    links:
      - { label: "Paper", href: "https://doi.org/..." }
    tags: ["Deep Learning"]
    desc: "One or two sentences."
```

The first entry in `links` also becomes the link on the title.

### Badges

Keys are defined in `_data/badges.yml`:

`q1` `q2` `top10` `first` `cofirst` `corresponding` `presenter` `oral` `poster`
`challenge` `proceedings` `intl` `domestic` `invited`

For a one-off label, write `"award:1st Prize"` or `"note:Best Paper"` — the text
after the colon is used verbatim, and the part before it picks the styling.
Three styles exist: `neutral` (outline), `accent` (coloured), `strong` (filled).

### `_data/awards.yml`

```yaml
- date: "2025.12"
  title: "Grand Prize"
  scope: "domestic"        # domestic | international
  org: "Capstone Design Competition"
  project: "..."
  team: "Choi, D. H., **Jeong, S.**, Kong, H. J."
  links:
    - { label: "Demo video", href: "https://..." }
```

### `_data/talks.yml`, `service.yml`, `patents.yml`

All three render on `/talks/`.

```yaml
# talks.yml
- date: "2026.05"
  title: "..."
  venue: "KOSOMBE 2026"
  detail: "Seoul, Korea"
  badges: ["invited"]

# service.yml
- period: "2025 – Present"
  role: "Reviewer"
  org: "npj Digital Medicine"

# patents.yml
- date: "2025.03"
  title: "..."
  number: "10-2025-XXXXXXX"
  status: "Filed"
  inventors: "**Jeong, S.**, Kong, H. J."
```

### `_data/experience.yml`, `education.yml`, `skills.yml`

```yaml
# experience.yml / education.yml
- period: "03.2021 &ndash; Present"
  title: "Research Assistant"
  org: "Seoul National University Hospital"
  location: "Seoul, Republic of Korea"
  badges: ["note:Summa Cum Laude"]   # optional
  details:
    - "bullet one"
    - "bullet two"

# skills.yml
- group: "Deep Learning"
  items: ["PyTorch", "TensorFlow"]
```

### `_data/research.yml`

The themes on the home page. Keep this to 3–5 and put the one you spend most of
your time on first.

```yaml
- title: "Medical Imaging AI"
  summary: "One sentence on what the theme is."
  topics: ["specific study or system", "another one"]
  keywords: ["Deep Learning", "Segmentation"]
  links:
    - { label: "Talk", href: "https://..." }
```

### `_data/beyond.yml`

```yaml
intro: "One line of framing."
stats:
  - { value: "500+", label: "Hours of volunteer service" }
groups:
  - title: "Volunteering"
    items:
      - period: "2019 – Present"
        title: "..."
        org: "..."
        detail: "..."
```

A group with an empty `items` list is skipped, so unused categories stay out of
the way until you fill them in.

---

## Looks

The theme ships five colour schemes. Change `site_theme` in `_config.yml` to
`default`, `air`, `sunrise`, `mint`, `dirt`, or `contrast`.

Site-specific styling — badges, entry rows, research themes, stat cards — lives
in `_sass/_custom.scss`. It is written against the theme's own CSS variables, so
it follows whichever scheme you pick, in both light and dark mode.

Everything else under `_sass/`, `_includes/`, `_layouts/`, and `assets/` is
stock Academic Pages. Leave it alone unless you are deliberately customising the
theme — upstream updates are easier to pull in that way.
