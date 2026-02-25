# CML Polymath — GitHub Pages Landing Page

This is the source for the `index.html` landing page hosted at [cmlpolymath.github.io](https://cmlpolymath.github.io). It serves as a stylized entry point directing visitors to the [Notebooks repository](https://github.com/cmlpolymath/Notebooks/tree/main).

---

## File Structure

```
/
├── index.html      ← The entire page lives here (self-contained)
└── README.md       ← This file
```

Everything — HTML, CSS, and JavaScript — is in a single `index.html` file. There are no build steps, no dependencies to install, and no frameworks. It just works.

---

## Component Overview

### 1. Falling Books Animation (`#rain-container` + `.book-drop`)
A JavaScript `setInterval` loop spawns book emoji elements at random horizontal positions and lets them fall via a CSS `@keyframes fall` animation. They remove themselves after 11 seconds to avoid memory buildup.

**To adjust:** Change the interval (`350`ms) to speed up or slow down the rain. Edit the `emojis` array to change which symbols fall.

### 2. Page Card (`.card`)
The main content container. It uses a parchment background (`#f5efe6`) and a layered `box-shadow` to create a raised, lit effect against the dark background. Animates in on page load via `@keyframes riseIn`.

### 3. Header Band (`.card-header`)
Dark ink background with a gold bottom border and a small gold chevron accent beneath it. Contains:
- **Eyebrow text** — the small uppercase tagline
- **Title** — in Playfair Display (loaded from Google Fonts)
- **Subtitle** — italic descriptor line
- **CTA Button** (`.cta-btn`) — the primary GitHub link. This is the most important navigational element on the page.

### 4. Body Content (`.card-body`)
Parchment-colored section with faint horizontal ruled lines (mimicking notebook paper) applied via a `repeating-linear-gradient` on a `::before` pseudo-element.

Contains the intro paragraph, a decorative gold divider, and the four section cards.

### 5. Section Cards (`.sections-grid` + `.section-item`)
A 2×2 CSS Grid of cards, each describing one structural component of the notebooks (Book Info, Key Takeaways, Notes, Discussion). They have a subtle left gold border and a lift effect on hover.

### 6. Card Footer (`.card-footer`)
A muted aged-parchment strip at the bottom linking to the GitHub profile.

---

## How to Update Content

### Change the tagline or description
Open `index.html` and find the `.card-body` section. The intro paragraph and footer note are plain HTML — just edit the text directly.

### Update the repository link
The CTA button and footer anchor both point to GitHub. Search for `github.com/cmlpolymath` and update any URLs as needed.

### Add or remove section cards
Find the `<div class="sections-grid">` block. Each card follows this pattern — copy, paste, and edit:

```html
<div class="section-item">
  <strong>🔍 New Section</strong>
  <span>A brief description of what this section contains</span>
</div>
```

If you add a 5th card, you may want to change the grid to a single column for balance — update `.sections-grid` in the CSS: `grid-template-columns: 1fr;`

### Change colors
All colors are defined as CSS variables at the top of the `<style>` block:

```css
:root {
  --ink: #1a1410;        /* Dark background */
  --parchment: #f5efe6;  /* Card background */
  --gold: #c9a84c;       /* Accents, borders, button */
  --rust: #8b3a2a;       /* Bold text highlights */
  --forest: #2d4a2d;     /* Section label color */
  --muted: #7a6a5a;      /* Subdued text */
}
```

Edit these and every element using them will update automatically.

### Change fonts
Fonts are loaded from Google Fonts in the `<head>`. The two in use are:
- **Playfair Display** — headings and section titles
- **Crimson Pro** — body text, buttons, labels

To swap them, replace the Google Fonts `<link>` href and update the `font-family` references in the CSS.

---

## Deployment

Any commit to the branch configured under *Settings → Pages* will automatically redeploy the page. There's no build process — GitHub serves `index.html` directly.
