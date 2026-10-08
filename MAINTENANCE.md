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
| `/` | `_pages/about.md` | `profile.yml`, `news.yml` |
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
| Award, challenge or competition result | `awards.yml` + `news.yml` |
| Invited talk | `talks.yml` |
| Press coverage | `news.yml` with an `outlet` field |
| Patent filed or granted | `patents.yml` |
| Reviewer / committee role | `service.yml` |

**Every quarter** — put it in the calendar

- Re-read `profile.yml`: is the bio still what you actually do?
- Trim `news.yml` to roughly the last two years.
- Check the bio in `profile.yml` still names the right research areas.
- Click every link in `publications.yml` — preprint URLs go stale on publication.
- Re-upload the CV PDF and confirm the link in `_pages/cv.html` still resolves.

**Once a year**

- Update `beyond.yml` volunteer hours and any giving.

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
automatically, so their order in the file does not matter. Competition and
challenge results with no paper belong in `awards.yml`, not here.

```yaml
journal:
  - year: 2026
    title: "..."
    authors: "Lee, S., **Jeong, S.**, Kong, H. J."
    venue: "Surgery"
    venue_detail: "24(1), 278"               # optional
    metrics: "Q1, IF 13.9, ranked #1 of 89"  # optional, bold in parentheses
    note: "1st Author"                       # optional, bold at the end
    links:
      - { label: "Paper", href: "https://doi.org/..." }
    desc: "One or two sentences."
```

The first entry in `links` also becomes the link on the title.

### Emphasis

There are no coloured badges or pills anywhere on the site. Emphasis is plain
bold text, and it comes from two optional fields:

- `metrics` renders as **(Q1, IF 13.9, ranked #1 of 89)** right after the venue.
  Use it for quartile, impact factor and category rank.
- `note` renders bold at the end of the meta line. Use it for author position
  (`1st Author`, `Co-first Author`), presentation type (`Oral Presentation`,
  `Poster`, `Proceedings`), or a combination separated by `&middot;`.

Inside any `authors`, `team`, `inventors` or `details` value, `**text**`
renders as bold.

### `_data/awards.yml`

`scope` decides which section the entry lands in on `/awards/`, so the page has
one **International** heading and one **Domestic** heading instead of repeating
a label on every row. Keep each scope newest first.

```yaml
- date: "2025.12"
  scope: "domestic"        # domestic | international
  title: "Grand Prize"
  org: "Capstone Design Competition"
  project: "..."
  team: "Choi, D. H., **Jeong, S.**, Kong, H. J."
  links:
    - { label: "Demo video", href: "https://..." }
```

Challenge and competition placings live here too — that is the only place they
appear, unless the entry also produced a peer-reviewed paper, in which case the
paper goes under `conference` as well.
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

Site-specific styling — entry rows, keyword chips, the news list, stat cards — lives
in `_sass/_custom.scss`. It is written against the theme's own CSS variables, so
it follows whichever scheme you pick, in both light and dark mode.

Everything else under `_sass/`, `_includes/`, `_layouts/`, and `assets/` is
stock Academic Pages. Leave it alone unless you are deliberately customising the
theme — upstream updates are easier to pull in that way.
