# Juhyun (Tyler) Kim — Portfolio

A static portfolio site. Plain HTML, CSS and vanilla JavaScript, no build step and no
dependencies. Drop it on GitHub Pages as-is.

## Deploying to GitHub Pages

1. Create a repository named `<your-github-username>.github.io`.
2. Copy everything in this folder into the repository root — `index.html` must sit at the top level.
3. Commit and push to the `main` branch.
4. In **Settings → Pages**, set the source to `main` and the folder to `/ (root)`.
5. The site goes live at `https://<your-github-username>.github.io` within a minute or two.

No other configuration is needed. `.nojekyll` is already present so GitHub serves the files
untouched.

## Structure

| Path | What it is |
| --- | --- |
| `index.html` | Home — about, the four positions, selected record, leadership |
| `research.html` | RS·01 — two published papers, research experience, writing |
| `venture.html` | VN·02 — HoopTrust, the problem, how it works |
| `piano.html` | PN·03 — competitions, concerts, jazz |
| `athletics.html` | AT·04 — basketball, baseball, awards |
| `assets/css/style.css` | The whole stylesheet |
| `assets/js/main.js` | Scroll reveals, photo lightbox, mobile nav |
| `assets/img/` | Photographs and video posters |
| `assets/video/` | Web-encoded highlight videos |
| `assets/docs/` | Research PDFs, patent filing, résumé |
| `Materials/` | Original source files — excluded from git by `.gitignore` |

## Design notes

The page is built like a term sheet. A dark cover panel opens the site, then everything below sits
in hard-ruled modular boxes on a flat surface — nothing floats, every block is bounded by a
hairline. Type contrast comes from width, weight and case rather than from mixing a serif with a
sans: section titles are set in wide, heavy uppercase, and all data is monospaced.

The home page has two signature components. **The strands timeline** plots the four commitments
against calendar years, with a dot at each result and an open arrow where the commitment is still
running. **The index rows** replace the usual card grid: four full-width numbered rows that pull
their hue across the row on hover.

| Position | No. | Colour |
| --- | --- | --- |
| Research | 01 | Ultramarine `#1b3a8f` |
| Venture | 02 | Cerulean `#0b7397` |
| Piano | 03 | Indigo `#4a45a6` |
| Athletics | 04 | Azure `#1f6fbf` |

Typefaces are Archivo for display (variable, using both the weight and width axes), Inter for body
text and JetBrains Mono for data labels, all from Google Fonts.


## Editing content

Everything is hand-written HTML, so text edits happen directly in the page files. The repeated
pieces are the masthead `<nav>`, the `.contact` block and the `<footer>` — if you change one,
change it in all five pages.

To restyle a section's colour, edit the four custom properties under `/* the four positions */`
in `assets/css/style.css`. Nothing else needs to change; every accent on the page reads from
`--pos`.

## Media

Source video was re-encoded for the web with ffmpeg:

```
ffmpeg -i "source.mp4" -vf "scale=1280:-2,fps=30" -c:v libx264 -crf 25 -preset slow \
  -pix_fmt yuv420p -movflags +faststart -c:a aac -b:a 96k out.mp4
```

The basketball reel went from 158 MB to 8.1 MB, which keeps it under GitHub's 100 MB per-file
limit. Re-run that command if you replace the footage.

## Still to fill in

- The Ethiopian Embassy and Korea Football Association internships are not on the site — the
  résumé has no descriptions for them yet.
- Several piano competition results have no date in the résumé and currently show `—` in the
  ledger on `piano.html`.
- The Sports Council entry has no dates.
- There is no piano audio or video. A recording would strengthen `piano.html` considerably.
