# CETC Hikvision 中电海康集团 - Design Specification

## I. Template Overview

| Property | Description |
| --- | --- |
| **Template Name** | cetc_hikvision |
| **Display Name** | 中电海康集团企业模板 (CETC Hikvision Corporate Template) |
| **Use Cases** | 企业内部汇报、项目提案、产品发布、年度总结、培训材料 |
| **Design Tone** | Corporate, authoritative, red-dominant, brand-consistent |
| **Theme Mode** | Hybrid theme (brand-red cover/chapter/ending + white content pages with red header strip) |

## II. Canvas Specification

| Property | Value |
| --- | --- |
| **Format** | Standard 16:9 |
| **Dimensions** | 1280 × 720 px |
| **viewBox** | `0 0 1280 720` |
| **Safe Margins** | 64px left/right, 48px top (below header), 30px bottom (above footer) |
| **Content Area** | x: 64–1216, y: 120–690 |

## III. Color Scheme

| Role | Color Value | Usage |
| --- | --- | --- |
| **Brand Red** | `#C8161D` | Cover/chapter/ending backgrounds, header strips |
| **Dark Red** | `#9B1019` | Cover bottom bar, depth accents |
| **Diamond Orange** | `#CC4500` | Diagonal diamond decorative pattern |
| **Diamond Orange Light** | `#CC4500` at 0.65 opacity | Staggered row of diamond pattern |
| **Footer Gray** | `#595959` | Footer right bar, secondary UI |
| **Dark Text** | `#1A1A1A` | Main body text on white pages |
| **Medium Gray** | `#555555` | Secondary text |
| **Light Gray** | `#E8E8E8` | Dividers, card borders |
| **White** | `#FFFFFF` | Content page background, reverse text on red |

## IV. Typography System

| Level | Usage | Size | Weight |
| --- | --- | --- | --- |
| **H1** | Cover title | 48px | Bold |
| **H2** | Chapter title | 40px | Bold |
| **H3** | Content page title | 26px | Bold |
| **H4** | TOC items / card titles | 18px | Bold |
| **Body** | Paragraph text | 16px | Regular |
| **Caption** | Footer / metadata | 12px | Regular |
| **Display Num** | Chapter numerals | 180px | Bold |

**Font Stack**: `"Microsoft YaHei", "PingFang SC", "Helvetica Neue", Arial, sans-serif`

## V. Decorative Diamond Pattern

The signature design element: rows of orange parallelograms on red backgrounds.

| Property | Value |
| --- | --- |
| **Shape** | Parallelogram (diamond): width=90px, height=32px, skew=12px |
| **Bounding box** | 102 × 32px |
| **Horizontal pitch** | 110px (20px gap) |
| **Vertical pitch** | 44px (12px gap) |
| **Row stagger** | 55px (half of pitch) |
| **Bright row** | `#CC4500` fill-opacity=`0.85` |
| **Staggered row** | `#CC4500` fill-opacity=`0.65` |
| **Pattern start** | Varies: cover ~x=380, header strip ~x=720 |

SVG pattern tile (110×88, two staggered rows):
```
Row 1: points="0,32 12,0 102,0 90,32"
Row 2 main: points="55,76 67,44 157,44 145,76"
Row 2 wrap: points="-55,76 -43,44 47,44 35,76"
```

## VI. Logo Usage

| Context | Asset |
| --- | --- |
| White pages (content/TOC) | `cetc_logo.jpeg` (colored logo on white bg) |
| Red pages (cover/chapter/ending) | SVG text: `CETC` + `海康集团` in white |
| Content header HIKVISION mark | SVG text: `HIK` in `#C8161D` + `VISION` in `#595959` |

## VII. Page Structure

### Common Elements

**Red header strip** (content/toc pages): y=0..72, red background with diamond pattern (x≥720) + white CETC text logo (right-aligned).

**Footer bar** (content/toc pages): y=704..720
- Red segment: x=0..1060, fill=`#C8161D`
- Gray segment: x=1060..1280, fill=`#595959`
- Page number in gray segment: white, 12px

### Page Types

#### 1. Cover (`01_cover.svg`)
- Full red background (#C8161D)
- Diamond pattern from x=380 to right edge
- Fade-in gradient on left edge of pattern (x=380..560)
- Darker bottom bar: y=638..720
- Title (left-aligned, y≈270): white, 48px bold
- Subtitle (y≈330): white, 22px
- Author/Date (y≈440–470): white, 17px/15px
- CETC logo + slogans in bottom bar

#### 2. Table of Contents (`02_toc.svg`)
- White background
- Red header strip with diamond + HIKVISION logo
- Section number column (red accent) + title column + page-num column
- Up to 6 TOC items

#### 3. Chapter (`02_chapter.svg`)
- Full red background
- Diamond pattern right portion (x≥640)
- Large chapter number: white, 180px, bottom-left
- Chapter title: white, 38px, left-aligned
- Thin white divider line

#### 4. Content (`03_content.svg`)
- White background
- Red header strip with diamond + CETC logo (white)
- Page title: dark, 26px bold, below header (y≈108)
- Content area: x=64..1216, y=120..690
- Footer bar

#### 5. Ending (`04_ending.svg`)
- Full red background (same as cover)
- Diamond pattern
- Centered "Thank You" layout
- CETC logo + contact info

## VIII. Placeholder Contract

| Page | Placeholders |
| --- | --- |
| Cover | `{{TITLE}}`, `{{SUBTITLE}}`, `{{DATE}}`, `{{AUTHOR}}` |
| Chapter | `{{CHAPTER_NUM}}`, `{{CHAPTER_TITLE}}` |
| TOC | `{{TOC_ITEM_1_TITLE}}` … `{{TOC_ITEM_6_TITLE}}`, `{{TOC_ITEM_1_PAGE}}` … `{{TOC_ITEM_6_PAGE}}` |
| Content | `{{PAGE_TITLE}}`, `{{CONTENT_AREA}}`, `{{PAGE_NUM}}` |
| Ending | `{{THANK_YOU}}`, `{{CONTACT_INFO}}` |
