# Terraria Forest Template - Design Specification

> Suitable for game introductions, tech talks, creative showcases, programming tutorials, entertainment events, and any scenario that benefits from a vibrant pixel-art adventure aesthetic.

---

## I. Template Overview

| Property | Description |
|----------|-------------|
| **Template Name** | terraria (Terraria Pixel Forest Template) |
| **Use Cases** | Game introductions, creative showcases, tech talks, entertainment presentations, youth events |
| **Design Tone** | Bright pixel-art adventure, nature exploration, playful, retro-game warmth |
| **Theme Mode** | Light theme (bright sky-blue background + pixel-art wooden UI panels + vibrant green accents) |

---

## II. Canvas Specification

| Property | Value |
|----------|-------|
| **Format** | Standard 16:9 |
| **Dimensions** | 1280 × 720 px |
| **viewBox** | `0 0 1280 720` |
| **Page Margins** | Left/Right 80px, Top 60px, Bottom 50px |
| **Safe Area** | x: 80–1200, y: 60–670 |

---

## III. Color Scheme

### Sky & Background Colors

| Role | Value | Notes |
|------|-------|-------|
| **Sky Blue (mid)** | `#5578B4` | Sky from forest_bg1/bg2 — used as accent bg |
| **Bright Sky** | `#7DA7D9` | Lighter sky, hover states |
| **Content Page BG** | `#C8E0F8` | Very light sky-blue — all content/TOC pages |
| **Panel Cream** | `#F7F0E0` | Inner content panel fill — bright and warm |

### Forest & Ground Colors

| Role | Value | Notes |
|------|-------|-------|
| **Forest Green Dark** | `#1A4D2A` | Deep canopy overlay |
| **Ground Green** | `#2D6B34` | Grass/ground strip |
| **Grass Bright** | `#3EAA4A` | Grass top highlight tiles |
| **Dirt Brown** | `#3A2010` | Below-grass dirt layer |

### UI Panel Colors (Terraria Wooden Chest Style)

| Role | Value | Notes |
|------|-------|-------|
| **Panel Border** | `#1A0D00` | Outermost pixel border |
| **Panel Fill** | `#5C3A1E` | Wooden panel body |
| **Panel Highlight** | `#8C5A32` | Top/left highlight edge |
| **Panel Shadow** | `#3A1E08` | Bottom/right shadow edge |

### Accent & Text Colors

| Role | Value | Usage |
|------|-------|-------|
| **Gold** | `#FFD700` | Main titles on dark panels, corner pixels |
| **Leaf Green** | `#A0E060` | Info text in dark strips |
| **Cream Text** | `#F0E0C0` | Subtitle text on panels |
| **Dark Text** | `#2A1A0A` | Body text on light backgrounds |
| **Blue Header Text** | `#FFFFFF` | Text on sky-blue header bars |
| **Muted Green** | `#6A9050` | Labels/secondary text in dark strips |

---

## IV. Typography System

### Font Stack

**Title Font**: `"Courier New", "Consolas", "Monaco", monospace`  
→ Pixel aesthetic, monospaced for game-UI feel

**Body Font**: `"Microsoft YaHei", "Segoe UI", Arial, sans-serif`  
→ Readable body text, CJK-friendly

### Font Size Hierarchy

| Level | Usage | Size | Weight |
|-------|-------|------|--------|
| H1 | Cover main title | 54px | Bold |
| H2 | Chapter number | 130px | Bold |
| H3 | Chapter title / Page title | 36px | Bold |
| H4 | Subtitle | 28px | Normal |
| Body | Body text / TOC items | 22–24px | Normal |
| Caption | Labels, footer info | 14–18px | Normal |

---

## V. Page Structure

### Cover
- Full-page `forest_bg2.png` background (xMidYMin slice)
- `logo.png` centered in bright sky area (top)
- Central pixel-art wooden panel: main title + subtitle
- Dark ground strip at bottom: date, author, slime/boulder decorations

### Chapter
- Full-page `forest_bg1.png` background (xMidYMin slice)
- Dark forest-green semi-transparent panel on left side
- Pixel border on right edge of panel
- Chapter number (large, gold) + chapter title
- Right side: bright forest background naturally illuminates scene

### Content
- Solid bright sky-blue `#C8E0F8` background (no image — ensures maximal brightness)
- Sky-blue header bar (80px): page title in white
- Pixel-art bordered content panel (cream interior)
- Forest-green footer bar (46px): page number
- Light-green pixel border strip at very top

### TOC
- Solid light blue `#C8E0F8` background
- Central panel: sky-blue header + alternating cream/offwhite item rows
- Green pixel bullet for each item
- Bottom: small pixel decorations (slime, boulder)

### Ending
- Full-page `forest_bg2.png` background (xMidYMin slice)
- Light overlay (0.30 opacity) to slightly deepen contrast — keeps bright outdoor feel
- Central wooden panel: thank-you + contact
- Bottom ground strip with multiple slime decorations

---

## VI. Page Types

| # | Filename | Type | Description |
|---|----------|------|-------------|
| 01 | `01_cover.svg` | Cover | Forest bg, logo decoration, title panel |
| 02 | `02_chapter.svg` | Chapter | Forest bg, left info panel, chapter num+title |
| 02alt | `02_toc.svg` | TOC | Bright sky bg, inventory-style item list |
| 03 | `03_content.svg` | Content | Bright solid bg, header + content panel + footer |
| 04 | `04_ending.svg` | Ending | Forest bg, closing wooden panel, slimes |

---

## VII. Layout Modes

- **Cover/Ending**: Full-bleed background + centered overlay panel
- **Chapter**: Left-split (panel ~40% + forest view ~60%)
- **Content/TOC**: Solid bright background + structural panel

---

## VIII. Spacing Specification

| Element | Value |
|---------|-------|
| Header bar height | 80–94px |
| Footer bar height | 40–46px |
| Panel border thickness | 6–8px |
| Panel highlight strip | 12–14px |
| Content safe margin | 80px left/right |
| Pixel corner decoration size | 12–14px |
| Item row height (TOC) | 68px |

---

## IX. SVG Technical Constraints

- `viewBox`: `0 0 1280 720` on all SVGs
- **Banned**: `clipPath`, `mask`, `<style>`, `class`, `foreignObject`, `<symbol>` + `<use>`, `textPath`, `@font-face`, `<animate*>`, `<script>`, `marker`, `<iframe>`
- **Transparency**: use `fill-opacity` / `stroke-opacity` only (no rgba, no group opacity)
- **Fonts**: system fonts only — `Courier New`, `Microsoft YaHei`, `Arial`
- **Images**: `<image href="filename.png" .../>` — same-directory relative paths
- **Grouping**: use `<g>` for structural grouping (no `<g opacity="...">`)

---

## X. Placeholder Specification

| Placeholder | Purpose | Template |
|-------------|---------|---------|
| `{{TITLE}}` | Main title | Cover |
| `{{SUBTITLE}}` | Subtitle | Cover |
| `{{DATE}}` | Date | Cover |
| `{{AUTHOR}}` | Author / Organization | Cover |
| `{{CHAPTER_NUM}}` | Chapter number | Chapter |
| `{{CHAPTER_TITLE}}` | Chapter title | Chapter |
| `{{CHAPTER_DESC}}` | Chapter description | Chapter |
| `{{PAGE_TITLE}}` | Page title | Content |
| `{{CONTENT_AREA}}` | Content area | Content |
| `{{SECTION_NAME}}` | Section name | Content footer |
| `{{PAGE_NUM}}` | Page number | Content, Ending |
| `{{THANK_YOU}}` | Thank-you message | Ending |
| `{{ENDING_SUBTITLE}}` | Ending subtitle | Ending |
| `{{CONTACT_INFO}}` | Contact info | Ending |
| `{{COPYRIGHT}}` | Copyright info | Ending |
| `{{TOC_ITEM_1_TITLE}}` | TOC item 1 title | TOC |
| `{{TOC_ITEM_2_TITLE}}` | TOC item 2 title | TOC |
| `{{TOC_ITEM_3_TITLE}}` | TOC item 3 title | TOC |
| `{{TOC_ITEM_4_TITLE}}` | TOC item 4 title | TOC |
| `{{TOC_ITEM_5_TITLE}}` | TOC item 5 title | TOC |

---

## XI. Asset Inventory

| File | Role |
|------|------|
| `forest_bg1.png` | Pine-tree forest background (Chapter, Ending) — style guide reference |
| `forest_bg2.png` | Deciduous-tree forest background (Cover, Ending) |
| `logo.png` | Terraria logo with tree — cover page decoration (required) |
| `green_slime.png` | Green pixel slime — decorative element |
| `slimes.png` | Multi-slime scene — optional accent |
| `tree.png` | Single pixel tree — header/footer accent |
| `tree_forest.png` | Tall thin pixel tree — edge decoration |
| `boulder.png` | Grey pixel boulder — ground decoration |
| `biome_trees.png` | Biome tree variety panel — reference / accent |
