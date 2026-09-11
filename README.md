# Totally Accurate Gender Detector™

A parody "AI face analysis" web app that looks like an over-engineered lab
console and does absolutely nothing scientific. Upload a photo (or use your
camera), watch a fake scan sequence, and get a completely random result.

**This is a joke.** It does not perform facial recognition, does not identify
people, and does not determine anyone's actual gender. Every number on the
result card is randomly generated and has zero connection to the photo.

---

## What it does

- **Photo intake** — drag-and-drop upload, file picker, or live camera capture
- **Fake scan sequence** — a terminal-style log ("Consulting extremely
  questionable AI…") with a progress bar and an animated scan line over the
  photo
- **Random result card**, including:
  - **Male Dominance / Female Dominance** — two independently randomized
    percentages (they don't need to add up to 100 — that's intentional)
  - **Hormone Readout** — joke "Testosterone" / "Estrogen" bars with absurd
    non-medical units ("0.003 Hulks", "Off the scale (there is no scale)")
  - **Confidence** — a deliberately silly value (`127%`, `∞%`, `Ask again
    later`, etc.)
  - **Advanced AI Diagnostics** — five random nonsense stats (Quantum Gender
    Field, Pixel Vibes, etc.)
  - Occasionally, a wildcard result instead of the bars ("Probably a
    toaster", "Gender.exe has stopped working", …)
- **Scan Again** — reruns the whole thing with fresh random numbers

## What it does NOT do

- No facial recognition or biometric matching
- No identity lookups or database matching
- No real inference of gender, age, or any other trait from the photo
- No photo upload, storage, or transmission — everything happens locally in
  your browser and disappears when you close or refresh the tab
- No real hormone or medical data of any kind

## Running it

It's a single self-contained HTML file. No build step, no dependencies.

1. Download `totally-accurate-gender-detector.html`
2. Open it in any modern browser (Chrome, Firefox, Safari, Edge)

That's it. Photo upload works immediately.

### About the camera button

Browsers only allow camera access (`getUserMedia`) on a **secure context**
— that means `https://` or `localhost`. If you open the file directly
(`file://…`), most browsers will block the camera and the app will show an
explanatory alert. To use the camera locally, serve the folder instead of
double-clicking it:

```bash
python3 -m http.server 8000
# then open http://localhost:8000/totally-accurate-gender-detector.html
```

Or deploy it anywhere that serves over HTTPS (Replit, GitHub Pages, Netlify,
Vercel, etc.) — the camera will work there too.

## Deploying to Replit

1. Create a new Replit (HTML/CSS/JS template)
2. Replace the generated `index.html` with this project's file (or rename
   the file to `index.html`)
3. Hit **Run** — Replit serves it over HTTPS automatically, so the camera
   button works out of the box

## Customizing

Everything lives in one file, split into three sections:

| Section         | What to edit                                                |
|-----------------|--------------------------------------------------------------|
| `<style>`       | Colors are CSS variables at the top (`--magenta`, `--cyan`, `--yellow`, etc.) — change the palette in one place |
| `<script>`      | All the joke content lives in arrays near the top: `SCAN_LINES`, `WILDCARD_RESULTS`, `CONFIDENCES`, `DIAG_LABELS`, `DIAG_VALUES`, `HORMONE_READOUTS`, `BAR_NOTES` |
| HTML body       | Copy/labels (headings, disclaimers, footer text) |

To change how often the wildcard result shows up instead of the percentage
bars, edit this line in the script:

```js
const showWildcard = Math.random() < 0.15; // 15% chance
```

## Tech

Plain HTML, CSS, and JavaScript. No frameworks, no build tools, no external
scripts except two Google Fonts (Chakra Petch, Space Mono) loaded via
`<link>`. Works offline once fonts are cached, and degrades gracefully to
system fonts if the fonts can't load.

## License / disclaimer

This is a parody/demo project for entertainment purposes only. It has no
scientific validity, is not a real gender or identity classifier, and
should not be used to make any decision about anyone. All results are
randomly generated. Do not deploy this as an actual product that claims to
detect or verify anyone's gender, identity, or biological attributes.

---

**Totally Accurate Gender Detector™** — 0% scientifically validated.
