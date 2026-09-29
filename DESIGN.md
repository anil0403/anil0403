---
name: Anil Shrestha — GitHub profile
description: Recruiter-facing developer front door that leads with shipped, live work.
colors:
  signal-red: "#c8372d"
  linkedin-blue: "#0a66c2"
  github-ink: "#24292f"
  card-link-blue: "#0366d6"
  card-muted-slate: "#586069"
  card-muted-slate-dark: "#77909c"
  contribution-green: "#40c463"
  canvas-light: "#ffffff"
  canvas-dark: "#0d1117"
typography:
  display:
    fontFamily: "GitHub system stack (-apple-system, Segoe UI, Noto Sans, Helvetica, Arial, sans-serif)"
    fontWeight: 600
  headline:
    fontFamily: "GitHub system stack"
    fontWeight: 600
  body:
    fontFamily: "GitHub system stack"
    fontWeight: 400
  label:
    fontFamily: "ui-monospace, SFMono-Regular, Menlo, monospace"
    fontWeight: 400
rounded:
  badge: "0px"
  card: "6px"
components:
  contact-badge-email:
    backgroundColor: "{colors.signal-red}"
    textColor: "{colors.canvas-light}"
    rounded: "{rounded.badge}"
    height: "28px"
  contact-badge-linkedin:
    backgroundColor: "{colors.linkedin-blue}"
    textColor: "{colors.canvas-light}"
    rounded: "{rounded.badge}"
    height: "28px"
  contact-badge-follow:
    backgroundColor: "{colors.github-ink}"
    textColor: "{colors.canvas-light}"
    rounded: "{rounded.badge}"
    height: "28px"
---

# Design System: Anil Shrestha — GitHub profile

## Overview

**Creative North Star: "The Shipped Workbench"**

A developer's front door that reads like a bench of finished work: who he is in one line, a way to reach him in one click, then the live projects laid out side by side. The page lives inside GitHub's own chrome, so it borrows GitHub's typography, canvas, and light/dark behavior wholesale and spends its limited expressive budget on three places: the brand-colored contact badges, the two-column project cards, and the coding illustration (`coding.gif`) that opens the page as its human face.

Everything visual arrives as markup GitHub allows (headings, tables, `<picture>`, `<img>`, `<code>`) or as images. There is no CSS, no custom font, no script. Depth, color, and personality come from the images themselves and from structure.

The owner has explicitly rejected a neutralized version of this page (gray badges, plain Markdown tables, no illustration; commit `0730c93`, reverted). Color and the card layout are part of the identity, not noise.

**Key Characteristics:**
- Centered hero: the coding illustration, then name, role, one-line promise, contact badges.
- Left-aligned body that ends on a plain-text contact line, not on metrics.
- Brand-colored, square-cornered contact badges as the primary call to action.
- Projects as a 2×2 card grid with live links, never a bare list.
- Every data image paired light/dark through `<picture>`.
- Calm, professional copy; one line of personality.

## Colors

GitHub's neutral canvas with three brand-true accents confined to the contact row.

### Primary
- **Signal Red** (`signal-red`): the Email badge. The single most important action on the page (contacting him) gets the warmest color.

### Secondary
- **LinkedIn Blue** (`linkedin-blue`): the LinkedIn badge only; it is LinkedIn's own brand color, which makes it instantly recognizable.
- **GitHub Ink** (`github-ink`): the Follow badge; reads as GitHub-native in both themes.

### Neutral
- **Card Link Blue / Card Muted Slate / Contribution Green**: colors baked into the generated summary cards (`github` theme). Their dark counterparts come from the `github_dark` theme (`card-muted-slate-dark`, `canvas-dark`). These are owned by the card generator; do not restyle them by hand.
- **Canvas**: GitHub's own page background; the README never paints a background.

### Named Rules
**The Accents-Stay-Up-Top Rule.** Saturated brand color appears only in the contact badge row. Body sections stay on GitHub's neutral text colors so the projects, not the chrome, carry the eye.

**The Paired-Image Rule.** Any image that contains a background or text color (the coding illustration, stats, streak, snake) ships as a `<picture>` with a `prefers-color-scheme: dark` source. A light-only data image is a bug.

## Typography

**Display / Body Font:** GitHub's system stack (not controllable).
**Label Font:** GitHub's monospace, used only via `<code>` for tech tags.

**Character:** Neutral, native, legible; hierarchy comes from heading level and weight, never from fonts.

### Hierarchy
- **Display** (`<h1>`, centered): the name, once.
- **Headline** (`##`): section titles — About, Featured projects, Tech stack, GitHub activity, Elsewhere.
- **Title** (`<h3>` inside cards): project names, each linked to the live site.
- **Body**: one- or two-sentence descriptions; About uses bold lead-ins (`**What I do:**`).
- **Label** (`<code>`): stack tags under each project, 3–5 per card.

### Named Rules
**The One-H1 Rule.** The name is the only `<h1>`. Headings never skip a level.

## Layout

Single column at GitHub's README width (~830px desktop, full width on mobile). The header is centered and opens with `coding.gif` at 420px (light) / `coding-dark.gif` (dark) in a `<picture>`; everything after it is left-aligned. No floated images: floats squeeze text into a sliver on mobile. GitHub activity sits inside a closed `<details>` so the scroll path runs hero → About → projects → stack → contact. Featured projects use a two-column `<table>` with `width="50%"` cells and `valign="top"`; on narrow screens GitHub lets the table scroll horizontally rather than stacking. Data cards pair at `width="49%"` side by side, or run `width="100%"` alone.

Section rhythm comes from GitHub's heading margins plus one `<br>` after the header block. Don't add stacks of `<br>` for spacing.

## Elevation & Depth

Flat. GitHub's table borders are the only structural lines; there are no shadows or layered surfaces, and none can be added.

## Shapes

Square-cornered `for-the-badge` shields in the contact row; GitHub's own rounded table cells and code chips elsewhere. Skill icons from skillicons.dev bring their own rounded-square tiles.

## Components

### Contact badges
- **Shape:** square, 28px tall (shields.io `for-the-badge`).
- **Style:** brand color background, white logo and text; label names the action ("Email me", "LinkedIn · Connect", "Follow").
- **Alt text:** states the action and destination, e.g. "Email dev.shresthaanil@gmail.com".

### Project card
- **Structure:** `<h3>` linked name → 1–2 sentence description → row of `<code>` stack tags → bold "Live site →" link (plus "Code →" when the repo is public and relevant).
- **Container:** one `<td width="50%" valign="top">` in a 2-column table.
- **Content rule:** only projects with a working live deployment or public code.

### Skill-icon row
- **Style:** skillicons.dev strip per category in a two-column label/icons table.
- **Alt text:** comma-separated list of every icon in the strip, so the stack is readable without images.

### Hero illustration
- **Structure:** centered `<picture>`; light source `coding.gif` (white background), dark source `coding-dark.gif` (background swapped to `canvas-dark`, outlines touching it rimmed in light gray so they stay visible). Regenerate the dark file whenever the light one changes.

### Themed data card
- **Structure:** `<picture>` with a dark `<source>` and a light `<img>` fallback, explicit `width`, descriptive `alt`.

## Do's and Don'ts

### Do:
- **Do** lead with shipped, live projects; every card has a working link whose text names its destination ("Visit SajiloTools →", not a repeated "Live site →").
- **Do** end the page on the contact line.
- **Do** pair every colored data image with a dark variant via `<picture>`.
- **Do** keep brand color in the contact badges (`signal-red`, `linkedin-blue`, `github-ink`).
- **Do** write alt text that carries the same information as the image.

### Don't:
- **Don't** neutralize the contact badges to gray or replace the project cards with a plain Markdown table (tried and reverted in `0730c93`).
- **Don't** add badge walls, typing-SVG banners, or trophy grids; skill icons are the one stack visualization.
- **Don't** invent metrics, employers, or years of experience.
- **Don't** rely on anything GitHub strips: `style`, `class`, `<script>`, custom fonts.
