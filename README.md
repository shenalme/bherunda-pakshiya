# Bherunda Pakshiya (භේරුණ්ඩ පක්ෂියා) — film site

A single-page site for Sarath Dharmasiri's 2006 film and the novel it was adapted from.

## Page order

1. **Title page** — the stills cycle in the background behind the title. Small brass ticks at the
   bottom right let a visitor jump between them; the sequence pauses when the tab isn't visible
   and doesn't run at all for anyone who has reduced motion turned on.
2. **Awards**, with the trailer's laurel card
3. **The story**
4. **Trailer**
5. **The novel it came from**, with the buy link
6. **Cast and crew**
7. **On location**
8. **Archive** — every source the page draws on

## Files

```
index.html                          the whole site (no build step, no dependencies)
404.html                            shown for any wrong address
robots.txt                          crawler instructions
sitemap.xml                         page and image sitemap
favicon.svg                         browser-tab icon
.nojekyll                           tells GitHub to serve files as-is
images/
  hero-pitangane-jasmine.jpg        title carousel (first slide)
  temple-courtyard.jpg              title carousel
  hill-country-ride.jpg             title carousel
  window-bars.jpg                   title carousel
  threading-jasmine.jpg             title carousel
  verandah.jpg                      title carousel
  pitangane-portrait.jpg            title carousel + story section
  trailer-title-card.jpg            awards section
  on-set-sarath-dharmasiri.jpg      on location
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

## Before you announce it: search setup

Everything below is already in the files. These are the steps only you can do.

### 1. Set your real URL (one find-and-replace)

`https://YOURNAME.github.io/bherunda-pakshiya` appears as a placeholder in `index.html`,
`robots.txt` and `sitemap.xml`. Replace every occurrence with your live URL. On a Mac or Linux
machine, from inside the folder:

```
grep -rl "YOURNAME.github.io/bherunda-pakshiya" . | xargs sed -i '' \
  's|https://YOURNAME.github.io/bherunda-pakshiya|https://your-real-url|g'
```

(Drop the `''` after `-i` on Linux.) Search engines treat a wrong canonical URL as an instruction
to ignore the page, so don't skip this one.

### 2. Register the site

- **Google Search Console** — add the property, verify with the HTML-file method, submit
  `sitemap.xml`, then use "Request indexing" on the homepage. This is the single biggest lever;
  a brand-new page can otherwise sit undiscovered for weeks.
- **Bing Webmaster Tools** — same, and it imports straight from Search Console.

### 3. Get linked from somewhere

Search engines find niche pages through links, not keywords. The highest-value ones here:

- Add the site as the external link on the film's **IMDb** page and **Wikidata** item.
- Create a short **Wikipedia** article (English and Sinhala) if the film doesn't have one; it
  meets notability through the Presidential and Sarasaviya awards, and the Sunday Times
  reports in the archive section are usable citations.
- Put the URL in the **YouTube trailer description** and pinned comment.
- Ask **films.lk** to link the page from record 1704.

Four or five real links from those places will do more than any amount of on-page tuning.

### What's already built in

- **Structured data** for the film, the novel (with ISBN, publisher and the Lakpura offer), the
  trailer and the site, as a single JSON-LD block. Test it at
  [validator.schema.org](https://validator.schema.org/) after setting your URL.
- **Both romanisations** — "Bherunda" and "Berunda" — appear in the page text and in the
  structured data, since catalogues are split between them.
- **Sinhala text is tagged `lang="si"`**, including a Sinhala summary in the story section, so
  Sinhala-language searches can reach the page.
- **Image sitemap** listing all eight stills with descriptive titles, plus real `alt` text on
  every image. Film stills are a genuine source of traffic through Google Images.
- **Fast loading** — the YouTube player only loads when someone clicks the trailer, the hero
  image is preloaded, and every image has explicit dimensions so nothing shifts as the page
  settles. Page speed is a ranking factor and this page is light.
- `robots.txt`, `sitemap.xml`, a `404.html` and a favicon.

### One thing to verify

The trailer's `uploadDate` in the structured data is set to `2017-01-15`. Check the real date on
the YouTube video and correct it if needed — search for `uploadDate` in `index.html`.

### Worth knowing

Google withdrew FAQ rich results for most sites in 2023, so a bolted-on FAQ section would add
nothing. Ranking here will come from the structured data, the inbound links, and the fact that
this is the most complete page about the film that exists.

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
