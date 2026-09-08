# Bherunda Pakshiya (භේරුණ්ඩ පක්ෂියා) — film site

A single-page site for Sarath Dharmasiri's 2006 film and the novel it was adapted from.

## Files

```
index.html                          the whole site (no build step, no dependencies)
images/
  hero-pitangane-jasmine.jpg        hero
  pitangane-portrait.jpg            story section
  temple-courtyard.jpg              stills
  hill-country-ride.jpg             stills
  threading-jasmine.jpg             stills
  window-bars.jpg                   stills
  verandah.jpg                      stills
  on-set-sarath-dharmasiri.jpg      on location
  trailer-title-card.jpg            trailer section
  social-preview.jpg                link preview image (1200x630)
```

All filenames are lowercase ASCII with hyphens, so nothing breaks on GitHub Pages.

## Publishing on GitHub Pages

1. Create a repository, e.g. `bherunda-pakshiya`.
2. Upload `index.html`, the `images` folder and `.nojekyll` to the root of the `main` branch.
3. In the repo, go to **Settings → Pages**, set Source to **Deploy from a branch**, branch `main`, folder `/ (root)`, and save.
4. The site appears at `https://YOURNAME.github.io/bherunda-pakshiya/` within a minute or two.

`.nojekyll` tells GitHub to serve the files as-is rather than running them through Jekyll. Keep it.

## Two things to finish

**Link previews.** In `index.html`, find the `og:image` tag near the top and replace the
relative path with your full published URL, for example:

```html
<meta property="og:image" content="https://YOURNAME.github.io/bherunda-pakshiya/images/social-preview.jpg">
```

Facebook, WhatsApp and X need an absolute URL here.

**The book cover.** The novel section looks for `images/novel-cover.jpg` first. If that file
isn't there it falls back to the cover image hosted on Lakpura, and if that also fails it shows
a typographic cover plate instead — so the section never breaks. Best result: save a copy of the
cover as `images/novel-cover.jpg` so the site doesn't depend on anyone else's server.

## Editing

Everything is in `index.html` — one file, plain HTML and CSS, no framework. Colours are CSS
variables at the top of the `<style>` block:

```css
--ink      page background
--brass    rules, accents, the buy button
--ochre    the one red accent
--jasmine  body text
--moss     captions and secondary text
```

Fonts are Abhaya Libre (Sinhala and Latin display) and Barlow, both loaded from Google Fonts.

## Credits and rights

Stills, the trailer and the production photograph belong to the film's producers and rights
holders. The novel cover and price come from Lakpura's product listing.

Sources used for the credits and awards are listed in the site footer. The 2007 Presidential and
Sarasaviya ceremonies are inconsistently documented online and the awards section says so.
