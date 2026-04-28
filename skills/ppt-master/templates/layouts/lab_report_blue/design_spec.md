# 实验室蓝白汇报 (lab_report_blue) - Design Specification

## I. Template Overview

- **Template ID**: `lab_report_blue`
- **Display Name**: 实验室蓝白汇报
- **Category**: scenario
- **Applicable Scenarios**: Quarterly reports, project progress updates, formal review meetings, technical briefings in semiconductor/research lab settings
- **Tone Summary**: Restrained, data-driven, professional — suitable for formal meeting settings
- **Theme Mode**: Light theme (white background + blue accent + red ending)
- **Design Style**: Minimal decoration, structured layout, authoritative color palette. Derived from a SOT-MRAM quarterly review PPTX, simplified for serious meeting use by removing content-specific images and decorative masks while preserving structural elements (top title bar, bottom info bar, page indicators).

## II. Canvas Specification

- **Format**: PPT 16:9
- **ViewBox**: `0 0 1280 720`
- **Width**: 1280px
- **Height**: 720px

## III. Color Scheme

| Role | Color | HEX | Usage |
|------|-------|-----|-------|
| Primary | Dark Blue | `#2f5597` | Titles, key text, section headings |
| Secondary | Medium Blue | `#3f629f` | Footer/info bars, section numbers, decorative lines |
| Accent | Dark Red | `#c00000` | Ending page banner |
| Text Primary | Dark Gray | `#333333` | Body text |
| Text Secondary | Medium Gray | `#666666` | Captions, secondary info |
| Text Light | White | `#FFFFFF` | Text on dark backgrounds |
| Background | White | `#FFFFFF` | Page background |
| Divider | Light Blue | `#d6e4f0` | Subtle divider lines |
| Highlight | Gold | `#ffc000` | Page number accent (subtle) |

## IV. Typography System

| Role | Font Family | Size (px) | Weight |
|------|-------------|-----------|--------|
| Cover Title | Microsoft YaHei, SimHei, sans-serif | 50 | Bold |
| Cover Subtitle | Microsoft YaHei, SimHei, sans-serif | 28 | Bold |
| Page Title | Microsoft YaHei, SimHei, sans-serif | 33 | Bold |
| Section Number | Microsoft YaHei, SimHei, sans-serif | 27 | Bold |
| Section Heading | Microsoft YaHei, SimHei, sans-serif | 27 | Bold |
| Body Text | Microsoft YaHei, SimHei, sans-serif | 24 | Normal |
| Body Text Bold | Microsoft YaHei, SimHei, sans-serif | 24 | Bold |
| Footer Text | Microsoft YaHei, SimHei, sans-serif | 37 | Bold |
| Page Number | DengXian, Arial, sans-serif | 16 | Bold |

## V. Page Structure

### Common Layout Elements

- **Top margin**: 0px (content extends to top with title bar)
- **Left margin**: 60px
- **Right margin**: 60px
- **Footer bar height**: 56px (from bottom)
- **Title bar area**: Full width, no separate background — uses blue text on white
- **Top decorative line**: Thin blue line (3px height, `#3f629f`) below title, spanning full content width

### Footer Bar (Content Pages)
- Position: Bottom of page, full width
- Height: 56px
- Fill: `#3f629f`
- Content: Centered white text slogan/slide topic (left-aligned within bar)
- Page number: Top-right corner above footer bar, in `#ffc000` (small, subtle)

## VI. Page Types

### 01_cover.svg — Cover Page

- White background
- Centered layout
- Top decorative blue line (full width, 4px, `#3f5597`)
- Title: `{{TITLE}}` (50px, Bold, `#2f5597`, centered)
- Subtitle: `{{SUBTITLE}}` (28px, Bold, `#2f5597`, centered, below title)
- Date: `{{DATE}}` (24px, Normal, `#666666`, centered)
- Author: `{{AUTHOR}}` (24px, Normal, `#666666`, centered)
- Bottom blue line accent (same as top, 4px)

### 02_chapter.svg — Chapter Page

- White background
- Large chapter number: `{{CHAPTER_NUM}}` (80px, Bold, `#3f629f`, left-aligned, vertically centered)
- Chapter title: `{{CHAPTER_TITLE}}` (44px, Bold, `#2f5597`, below number)
- Optional description: `{{CHAPTER_DESC}}` (24px, Normal, `#666666`)
- Bottom blue line accent (4px, `#3f629f`)
- Left vertical accent bar (6px wide, `#3f629f`, near left margin)

### 03_content.svg — Content Page

- White background
- Top: Section heading in `#2f5597` (33px, Bold, left-aligned at x=10)
  - Format: "（章节号）. 章节标题"
- Thin blue line below heading (3px, `#3f629f`, full width at y≈280)
- Content area: x=10 to x=950 (leaving room right side), y=296 to y=480
  - Placeholder: `{{CONTENT_AREA}}`
- Footer bar at bottom: rect fill `#3f629f` (full width, height ~66px from bottom)
  - White centered bold text: `{{KEY_MESSAGE}}` — current page summary/key takeaway
- Page number: `{{PAGE_NUM}}` in `#ffc000` (16px, top-right area)

### 04_ending.svg — Ending Page

- White background
- Center: Red banner band (`#c00000`)
  - Full width, centered vertically, height ~116px
  - White text: `{{THANK_YOU}}` (48px, Bold, centered)
- Subtitle below band: `{{ENDING_SUBTITLE}}` (24px, `#666666`)
- Contact info: `{{CONTACT_INFO}}` (20px, `#666666`, lower area)

### 02_toc.svg — Table of Contents (Optional)

- White background
- Top: "目录" title in `#2f5597` (33px, Bold)
- Thin blue divider line (2px, `#d6e4f0`)
- Numbered list of TOC items:
  - Each item: `{{TOC_ITEM_1_TITLE}}` (24px, `#333333`) with optional `{{TOC_ITEM_1_DESC}}`
  - Item numbers in `#3f629f`
- Bottom blue line accent

## VII. Layout Modes

### Content Page — Single Column (Default)
- Body text fills left ~70-80% of slide width
- Right ~20-30% available for side annotations or illustrations

### Content Page — Two Column
- Left column: x=10, ~440px wide
- Right column: x=500, ~440px wide
- Gap: 60px

## VIII. Spacing Specification

| Element | Spacing |
|---------|---------|
| Title to body | 20px |
| Section heading to content | 16px |
| Paragraph spacing | 12px |
| Bullet item spacing | 8px |
| Footer bar to content end | 20px |

## IX. SVG Technical Constraints

- viewBox must be `0 0 1280 720`
- No `<mask>` elements (use solid fills or `fill-opacity` instead)
- No `<style>` or `class` attributes
- No `<foreignObject>`, `<symbol>/<use>`, `textPath`, `@font-face`, `<animate>`, `<script>`
- All fonts must end with a pre-installed fallback (Microsoft YaHei, SimHei, Arial)
- Colors in HEX format only, transparency via `fill-opacity`/`stroke-opacity`
- Minimal decoration — no decorative images, masks, or complex clip paths in templates

## X. Placeholder Specification

| Placeholder | Purpose | Applicable Template |
|------------|---------|-------------------|
| `{{TITLE}}` | Main title | Cover |
| `{{SUBTITLE}}` | Subtitle/project info | Cover |
| `{{DATE}}` | Date | Cover |
| `{{AUTHOR}}` | Presenter/organization | Cover |
| `{{CHAPTER_NUM}}` | Chapter number | Chapter page |
| `{{CHAPTER_TITLE}}` | Chapter title | Chapter page |
| `{{CHAPTER_DESC}}` | Chapter description | Chapter page |
| `{{PAGE_TITLE}}` | Page title | Content page |
| `{{CONTENT_AREA}}` | Content area | Content page |
| `{{SECTION_NAME}}` | Section name for footer | Content page (legacy) |
| `{{KEY_MESSAGE}}` | Current page summary/key takeaway (white text in footer bar) | Content page footer |
| `{{PAGE_NUM}}` | Page number | Content page |
| `{{THANK_YOU}}` | Thank-you message | Ending page |
| `{{ENDING_SUBTITLE}}` | Ending subtitle | Ending page |
| `{{CONTACT_INFO}}` | Contact info | Ending page |
| `{{TOC_ITEM_N_TITLE}}` | TOC item title | TOC page |
| `{{TOC_ITEM_N_DESC}}` | TOC item description | TOC page |