# iacapconf.org

Conference site of the International Association for Computing and Philosophy
(IACAP), served at <https://iacapconf.org> by GitHub Pages.

## Build locally

Ruby is pinned in `.ruby-version`; install that version with rbenv first
(`rbenv install "$(cat .ruby-version)"`).

```sh
bundle install
bundle exec jekyll serve          # http://localhost:4000
```

To run the same link check as CI:

```sh
bundle exec jekyll build
bundle exec htmlproofer _site --disable-external --assume-extension .html \
  --swap-urls '^https?\://(www\.)?iacapconf\.org/:/' --no-enforce-https
```

## Deploy

Pushing to `main` runs `.github/workflows/pages.yml`: build, internal link and
image check, deploy. Pull requests build and check without deploying. The
repository's Settings > Pages > Source must be "GitHub Actions".

## Layout

- `YYYY/`: everything for that year's conference. The current year's
  `index.md` is the home page (`permalink: /`).
- `pages/`: pages that span years (past conferences, code of conduct).
- `_layouts`: the site's own layouts, plain HTML with no JavaScript.
  `default` (header, navigation, footer) wraps `page` (any page) and `home`
  (a year's front page); `post` is `page` with a date.
- `_includes`: the navigation, the per-year sidebar and "On this page" list,
  and the archive notice. `conference-years.html` works out the current year:
  the newest `YYYY/` with an `index.md`. Earlier years' pages then say they are
  archives, and a page added to a year's directory appears in that year's
  sidebar, with no list to edit.
- `_data/navigation.yml`: the header links after the current conference.
- `assets/stylesheets/main.scss`: the whole stylesheet. Fira Sans is served
  from `assets/fonts/fira-sans` (SIL Open Font License). The layouts load
  nothing from other hosts; two archived pages still do (the 2025 schedule
  loads jQuery, the 2026 logistics page a hash-pinned Leaflet map).

## Starting a new conference year (e.g. 2028)

1. Create `2028/index.md` and `2028/cfp.md` (start from 2027's). Give
   `2028/index.md` `permalink: /` and `redirect_from: /2028/`, and move
   `redirect_from: /pages/cfp.html` from `2027/cfp.md` to `2028/cfp.md`.
2. Remove `permalink` and `redirect_from` from `2027/index.md`, so it becomes
   the archive at `/2027/`, and point its "Conference Website" line at `/2027/`.
3. Update `title` in `_config.yml`. The header and sidebars follow by themselves.
4. Add the year to `pages/past_conferences.md`.
