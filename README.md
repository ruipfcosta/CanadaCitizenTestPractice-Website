# Canada Citizen Test Practice — website

Landing page for the [Canada Citizen Test Practice](https://apps.apple.com/us/app/canada-citizen-test-practice/id6827146081) iOS app.

Plain HTML and CSS. No build step and no JavaScript. Hosted on GitHub Pages (`.nojekyll` turns Jekyll off).

```
index.html               Homepage
privacypolicy/index.html Privacy policy (the App Store links to /privacypolicy)
404.html                 Not found page
styles.css               All styles
robots.txt, sitemap.xml  SEO
assets/img/              App icon sizes, App Store badge
assets/screenshots/      App screenshots (placeholders for now)
```

## Preview locally

```sh
python3 -m http.server 8000
# open http://localhost:8000
```

## Replacing the screenshots

The files in `assets/screenshots/` are blank placeholders at 1206 × 2622. To swap them, save simulator screenshots over these files and keep the same names:

| File               | Shown in                     |
| ------------------ | ---------------------------- |
| `home.png`         | Hero                         |
| `mock-test.png`    | "Practise under real test conditions" |
| `explanations.png` | "Understand it, don't just memorize it" |
| `mistakes.png`     | "Turn mistakes into marks"   |
| `progress.png`     | "Know when you're ready"     |

Use the raw screenshot without a device frame, because the page draws the phone frame in CSS. If the new device has a different resolution, update `aspect-ratio` in `.phone` and the `width`/`height` attributes on the `<img>` tags.

To keep the page fast, compress the screenshots before you commit them (for example, `cwebp -q 82` to WebP, then change the extensions in `index.html`).

## Ratings and reviews

The app has no App Store ratings yet, so the rating, reviews section and live rating script from the UK site were left out. Bring them back from that site once there are some.

## When details change

Question and test counts (500+, 50 practice tests) come from `ContentImporter/Canada/build_seed.py` in the app repo, and appear both in the page and in the JSON-LD block in `<head>` of `index.html`. Update both together. If the site moves to a custom domain, replace `https://ruipfcosta.github.io/CanadaCitizenTestPractice-Website/` everywhere: the canonical and `og:` tags, the JSON-LD, `robots.txt` and `sitemap.xml`. Also update the absolute paths in `404.html`.
