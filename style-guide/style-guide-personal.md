# Personal Branding Style Guide

This guide defines the visual and written standards for all personal output. It is divided into three sections: HTML pages, PDFs, and social/blog posts. Apply the relevant section in full for each output type.

---

## Colour Palette (Shared Across All Formats)

The palette is built on pastel green as the primary brand colour and pastel violet as the secondary, paired with cool-neutral backgrounds.

### Brand colours

| Token                    | Hex       | Use                                              |
|--------------------------|-----------|--------------------------------------------------|
| `--color-primary`        | `#7DBF8E` | Primary accent. Buttons, active tabs, highlights |
| `--color-primary-light`  | `#D6EFDB` | Card backgrounds, table headers, tinted panels   |
| `--color-primary-dark`   | `#4E8C5F` | Hover states, strong emphasis strokes            |
| `--color-secondary`      | `#A89BC9` | Secondary accent. Tags, badges, decorative accents |
| `--color-secondary-light`| `#E8E2F5` | Secondary tinted panels, alternate rows          |
| `--color-secondary-dark` | `#6B5A9E` | Hover states, diagram strokes for violet nodes   |

### Neutrals (60-70% of visual surface)

| Token                | Hex       | Use                                  |
|----------------------|-----------|--------------------------------------|
| `--color-text`       | `#2B2B2B` | Primary body text                    |
| `--color-text-muted` | `#6B6B6B` | Captions, secondary labels           |
| `--color-border`     | `#D9D9D9` | Dividers, table borders              |
| `--color-neutral-bg` | `#F4F6F4` | Page background                      |
| `--color-surface`    | `#FFFFFF` | Cards, panels, content surfaces      |

### Semantic (status indicators only)

| Token               | Hex       |
|---------------------|-----------|
| `--color-warning`   | `#D97706` |
| `--color-warning-bg`| `#FEF3E2` |
| `--color-error`     | `#C0392B` |
| `--color-error-bg`  | `#FEF0EF` |
| `--color-success`   | `#4E8C5F` |
| `--color-success-bg`| `#D6EFDB` |

### Colour proportions

- 60-70% neutral colours (text, grays, white, `#F4F6F4`).
- 25-35% brand colour (green or violet, any shade from the palette above).
- Under 5% semantic colours. Never use semantic colours for decorative purposes.

---

## Typography (Shared Across All Formats)

- Font stack: `'Segoe UI', system-ui, -apple-system, sans-serif`
- Headings use sentence case. Capitalise only the first word and proper nouns.
- Body copy uses standard sentence case.
- Do not use "—" as a sentence breaker. Use a comma or a full stop to start a new sentence.
- No all-caps labels except section/lane headers in diagrams.

| Role                | Size  | Weight | Colour               |
|---------------------|-------|--------|----------------------|
| Page title (h1)     | 22px  | 700    | `--color-text`       |
| Section title (h2)  | 17px  | 600    | `--color-text`       |
| Sub-heading (h3)    | 14px  | 600    | `--color-text`       |
| Body copy           | 14px  | 400    | `--color-text`       |
| Muted / caption     | 12px  | 400    | `--color-text-muted` |
| Diagram node label  | 12px  | 500    | `--color-text`       |
| Diagram sub-label   | 10px  | 400    | `--color-text-muted` |

---

---

# Section 1: HTML Pages

---

## CSS Custom Properties

Every HTML page must define these exact variables on `:root`:

```css
:root {
  /* Brand - Green (primary) */
  --color-primary:         #7DBF8E;
  --color-primary-light:   #D6EFDB;
  --color-primary-dark:    #4E8C5F;

  /* Brand - Violet (secondary) */
  --color-secondary:       #A89BC9;
  --color-secondary-light: #E8E2F5;
  --color-secondary-dark:  #6B5A9E;

  /* Neutrals */
  --color-text:            #2B2B2B;
  --color-text-muted:      #6B6B6B;
  --color-border:          #D9D9D9;
  --color-neutral-bg:      #F4F6F4;
  --color-surface:         #FFFFFF;

  /* Aliases */
  --color-primary-bg:      #D6EFDB;

  /* Semantic */
  --color-warning:         #D97706;
  --color-warning-bg:      #FEF3E2;
  --color-error:           #C0392B;
  --color-error-bg:        #FEF0EF;
  --color-success:         #4E8C5F;
  --color-success-bg:      #D6EFDB;

  /* Spacing */
  --space-xs:  8px;
  --space-sm:  16px;
  --space-md:  24px;
  --space-lg:  40px;
  --space-xl:  56px;
}
```

## Page Background and Surface

Set `background: var(--color-neutral-bg)` on `body`. Content surfaces (cards, main panel) use `--color-surface` (`#FFFFFF`).

## Header Bar

The page header uses a light green background with a 3px green bottom border. The decorative initials mark "SD" sits to the left of the title as a personal brand identifier.

```html
<div class="banner">
  <div class="banner-inner">
    <div class="banner-mark">SD</div>
    <div class="banner-text">
      <h1>Page title here</h1>
      <p class="subtitle">Subtitle here.</p>
    </div>
  </div>
</div>
```

```css
.banner {
  background: var(--color-primary-light);
  padding: var(--space-md) var(--space-lg);
  border-bottom: 3px solid var(--color-primary);
}
.banner-inner { display: flex; align-items: center; gap: var(--space-sm); }
.banner-mark {
  width: 44px;
  height: 44px;
  border-radius: 50%;
  background: var(--color-primary);
  color: #ffffff;
  font-size: 15px;
  font-weight: 700;
  display: flex;
  align-items: center;
  justify-content: center;
  letter-spacing: 0.05em;
  flex-shrink: 0;
}
.banner-text h1 { color: var(--color-text); font-size: 22px; font-weight: 700; margin: 0; }
.banner-text .subtitle { color: var(--color-text-muted); font-size: 13px; margin: 0; }
```

## Cards

Cards use a white background with a subtle shadow and 8px border radius. Do not use a general border on standard cards. The shadow provides visual separation.

```css
.card {
  background: var(--color-surface);
  border-radius: 8px;
  box-shadow: 0 1px 4px rgba(0, 0, 0, 0.08);
  padding: var(--space-md);
  margin-bottom: var(--space-md);
}

/* Green accent card */
.card--highlight {
  background: var(--color-primary-light);
  border-left: 4px solid var(--color-primary);
  border-radius: 0 8px 8px 0;
  box-shadow: none;
}

/* Violet accent card */
.card--secondary {
  background: var(--color-secondary-light);
  border-left: 4px solid var(--color-secondary);
  border-radius: 0 8px 8px 0;
  box-shadow: none;
}

/* Warning card */
.card--warning {
  background: var(--color-warning-bg);
  border-left: 4px solid var(--color-warning);
  border-radius: 0 8px 8px 0;
  box-shadow: none;
}
```

## Tables

```css
table { width: 100%; border-collapse: collapse; font-size: 14px; }
th    { background: var(--color-primary-light); color: var(--color-text); font-weight: 600; text-align: left; padding: var(--space-xs) var(--space-sm); }
td    { padding: var(--space-xs) var(--space-sm); border-bottom: 1px solid var(--color-border); }
tr:nth-child(even) td { background: var(--color-neutral-bg); }
```

## Navigation (Radio Button Pattern)

Use hidden radio inputs and the `:checked` CSS selector to show and hide sections. Do not use anchor links.

```html
<input type="radio" name="nav" id="tab-overview" checked>
<input type="radio" name="nav" id="tab-details">

<nav>
  <label for="tab-overview">Overview</label>
  <label for="tab-details">Details</label>
</nav>

<section class="tab-panel" id="panel-overview"> ... </section>
<section class="tab-panel" id="panel-details"> ... </section>
```

```css
input[type="radio"] { display: none; }
.tab-panel { display: none; }

#tab-overview:checked ~ main #panel-overview,
#tab-details:checked  ~ main #panel-details { display: block; }

nav label {
  cursor: pointer;
  padding: var(--space-xs) var(--space-sm);
  border-bottom: 2px solid transparent;
  color: var(--color-text-muted);
}

#tab-overview:checked ~ nav label[for="tab-overview"],
#tab-details:checked  ~ nav label[for="tab-details"] {
  border-bottom-color: var(--color-primary);
  color: var(--color-primary-dark);
  font-weight: 600;
}
```

## Layout

- Use semantic HTML5 elements: `<header>`, `<main>`, `<section>`, `<article>`, `<footer>`.
- Mobile-first CSS. Use media queries to scale up to wider viewports.
- Outer page padding: `40px` on all sides. No content touches the viewport edge.
- Align content to a 20px grid where possible.

## Technical Constraints

- HTML and CSS only. No JavaScript of any kind.
- No `<script>` tags, no `onclick` handlers, no event listeners.
- No external dependencies. No Google Fonts, no CDN links, no external images or stylesheets.
- All images must be embedded as base64 data URIs.
- The entire output is a single self-contained `.html` file with CSS embedded in a `<style>` block inside `<head>`.
- Set `html, body { width: 100%; }`. Do not use `min-height: 100vh`.

## Diagrams in HTML Pages

Apply the shared diagram rules below. Use the personal brand palette in place of any other colours:

- Primary subject: fill `#D6EFDB`, stroke `#4E8C5F`
- Secondary/support: fill `#E8E2F5`, stroke `#6B5A9E`
- External/passive: fill `#F5F5F5`, stroke `#999999`
- Neutral container: fill `#FAFAFA`, stroke `#CCCCCC` dashed

## HTML Anti-Patterns

- No JavaScript of any kind.
- No external fonts, stylesheets, or image URLs.
- No anchor link navigation.
- No `min-height: 100vh` on `html` or `body`.
- No rainbow colour schemes (more than 2-3 ramps).
- No saturated or dark background fills on content nodes.
- No decorative shadows, gradients, or glows.

---

---

# Section 2: PDFs

---

PDF output is intended for documents that will be printed or shared as standalone files. Reports, proposals, CVs, and reference documents fall into this category.

## Page Setup

- Page size: A4 portrait by default. Use landscape only for wide tables or diagrams.
- Margins: 25mm top and bottom, 20mm left and right.
- Content width: approximately 170mm on A4 portrait.
- Always include page numbers in the footer, right-aligned.

## Colour Usage in PDFs

PDFs are often printed. Follow these constraints:

- Use `--color-primary` (`#7DBF8E`) and `--color-secondary` (`#A89BC9`) sparingly. Prefer their light variants for background fills.
- Avoid using saturated fills on large areas. Light tints (`--color-primary-light`, `--color-secondary-light`) are safe for section headers, table headers, and callout boxes.
- Black text on white is the default. Coloured text is allowed for headings only.
- Do not rely on colour alone to convey meaning. Use labels, icons, or borders as a secondary signal.

## Typography in PDFs

- Body font: `'Segoe UI', system-ui, sans-serif` (or embed a web-safe equivalent).
- Body size: 11pt. Line height: 1.5.
- Heading sizes: h1 18pt, h2 14pt, h3 12pt. All bold.
- Captions and footnotes: 9pt, muted colour.
- Minimum font size anywhere in the document: 8pt.

## Cover Page

The first page of every PDF document uses a dedicated cover layout. The SD mark and document title are stacked vertically, centred on the page. They must never sit on the same horizontal line.

**Layout (top to bottom, centred):**

1. SD mark: a 56pt circle in `--color-primary` (`#7DBF8E`) with white bold initials at 20pt. Placed in the upper third of the page, centred horizontally.
2. Vertical gap: 32pt below the circle.
3. Document title: 24pt, bold, `--color-text` (`#2B2B2B`), centred.
4. Subtitle or date: 12pt, `--color-text-muted` (`#6B6B6B`), centred, 8pt below the title.
5. A 2pt horizontal rule in `--color-primary` spanning 40% of the page width, centred, 24pt below the subtitle.

The cover page has no running header or footer. Page numbering begins on page 2.

## Running Page Header and Footer

Every page after the cover should include a consistent header and footer:

**Header:** Personal name or document title on the left in 9pt. Document date or version on the right in 9pt muted. A 1pt line in `--color-primary` below the header row.

**Footer:** Page number on the right (format: `Page N of N`). Optional tagline or website on the left in 9pt muted text. A 1pt line in `--color-border` above the footer row.

## Section Headings in PDFs

- h1: 18pt, bold, colour `--color-primary-dark` (`#4E8C5F`). Use for major document sections.
- h2: 14pt, bold, colour `--color-text` (`#2B2B2B`). Use for subsections.
- h3: 12pt, bold, colour `--color-text`. Use for sub-subsections.
- Add 6pt spacing above each heading and 3pt below.

## Tables in PDFs

- Table header row: background `--color-primary-light` (`#D6EFDB`), bold text, 10pt.
- Alternate row shading: even rows use `--color-neutral-bg` (`#F4F6F4`).
- Cell padding: 4pt vertical, 6pt horizontal.
- Border: 0.5pt in `--color-border` (`#D9D9D9`) on all cells.
- Keep tables within the content width. For very wide tables, use landscape orientation.

## Callout Boxes in PDFs

Use a left border and tinted background to highlight notes, tips, and warnings:

| Type    | Background               | Left border (4pt)        |
|---------|--------------------------|--------------------------|
| Note    | `--color-primary-light`  | `--color-primary`        |
| Tip     | `--color-secondary-light`| `--color-secondary`      |
| Warning | `--color-warning-bg`     | `--color-warning`        |
| Error   | `--color-error-bg`       | `--color-error`          |

## Images and Diagrams in PDFs

- Embed all images. Do not link to external files.
- SVG diagrams should be exported as high-resolution PNG (minimum 150 DPI) for PDF embedding if SVG is not natively supported by the export tool.
- Centre diagrams on the page with a caption below in 9pt muted text.
- Apply the same brand colour rules as HTML diagrams: green for primary, violet for secondary, neutrals for everything else.

## PDF Anti-Patterns

- No dark or heavily saturated page backgrounds.
- No coloured body text (headings only).
- No font sizes below 8pt.
- No reliance on colour alone to convey status or meaning.
- No external image links.
- Do not omit page numbers.

---

---

# Section 3: Posts (Social and Blog)

---

Posts include LinkedIn articles, short-form social updates, and blog entries. They are text-primary. Visual formatting is minimal and platform-constrained.

## Tone and Voice

- Write in first person. Clear, direct, and confident.
- Avoid corporate jargon and filler phrases.
- Do not use "—" as a sentence breaker. Use a comma or a full stop to start a new sentence.
- Aim for clarity over cleverness. One idea per sentence.
- Short paragraphs (2-4 lines). One blank line between paragraphs on platforms that support it.

## Structure

Every post should follow one of these structures:

**Hook, body, close.** The first sentence earns attention. The body delivers the idea. The close invites a reaction or summarises the takeaway.

**Problem, insight, implication.** State a problem briefly. Share what you learned or observed. Explain why it matters.

**Numbered list with context.** Lead with a sentence framing the list. Keep items parallel and concrete. Close with a single-sentence reflection.

## Length

| Format              | Recommended length              |
|---------------------|---------------------------------|
| LinkedIn short post | 3-5 paragraphs, under 300 words |
| LinkedIn article    | 600-1200 words                  |
| Blog post           | 800-2000 words                  |
| Twitter/X thread    | 4-8 tweets, one idea each       |

## Formatting Rules for Posts

- Avoid decorative formatting. Let the writing carry the post.
- Use bullet lists sparingly. Prose reads better than fragmented bullets on most social platforms.
- No headers inside short posts. Headers are acceptable in LinkedIn articles and blog posts.
- All caps is never acceptable, even for emphasis.
- For LinkedIn specifically, all formatting must use unicode characters. See Section 3b for the full LinkedIn unicode formatting rules.

## Hashtags

- LinkedIn: 3-5 hashtags, placed at the end of the post. Use specific and relevant tags.
- No hashtags in blog posts or articles. Tags or categories at the platform level are fine.

## Visuals Attached to Posts

When attaching an image or graphic to a post:

- Use a 1200x628px image for LinkedIn link previews and article covers.
- Apply the brand palette: pastel green (`#7DBF8E`) and violet (`#A89BC9`) as brand colours, white or `#F4F6F4` as background.
- Font on graphics: bold, sentence case, high contrast against the background.
- Keep text in graphics to a single short phrase (under 8 words). The post copy carries the message.
- No cluttered layouts. One focal point per image.

## Cover Image Colour Guide for Posts

| Purpose               | Background               | Accent                   |
|-----------------------|--------------------------|--------------------------|
| Announcement / launch | `--color-primary-light`  | `--color-primary-dark`   |
| Insight / reflection  | `--color-neutral-bg`     | `--color-secondary`      |
| Tutorial / how-to     | `--color-secondary-light`| `--color-secondary-dark` |
| Opinion / commentary  | `#FFFFFF`                | `--color-primary`        |

## Post Anti-Patterns

- No all-caps text.
- No excessive hashtags (more than 5 on LinkedIn).
- No walls of unbroken text. Break into paragraphs.
- No passive voice where active voice is possible.
- No vague closers like "Thoughts?" in isolation. Ask a specific question or make a clear point.

---

---

# Section 3b: LinkedIn Post Formatting

---

LinkedIn does not support HTML or markdown. All visual structure comes from unicode characters, spacing, and plain text conventions. These rules apply exclusively to LinkedIn posts and articles.

## Core Principles

- No emojis. They undermine the professional tone of the post.
- No black line separators (────────── or similar). They look decorative and break reading flow.
- No dividers of any kind, horizontal rules, dotted lines, or repeated punctuation used as visual breaks.
- Clean white space is the only separator. A blank line between paragraphs is sufficient.
- The post should look like it was written by a thoughtful professional, not formatted by a social media tool.

## Unicode Formatting for Emphasis

LinkedIn renders plain text only. Markdown symbols like `**bold**` or `_italic_` appear as literal characters and will not render. All visual emphasis must come from unicode character sets that mimic styled text at the font level.

Use these unicode styles where emphasis is genuinely needed. Do not overuse them. One styled phrase per section at most.

| Purpose           | Method                          | Example                        | When to use                        |
|-------------------|---------------------------------|--------------------------------|------------------------------------|
| Strong heading    | Unicode bold sans-serif         | 𝗪𝗵𝗮𝘁 𝗜 𝗹𝗲𝗮𝗿𝗻𝗲𝗱               | Opening line or section label only |
| Subtle emphasis   | Unicode italic serif            | 𝘛𝘩𝘪𝘴 𝘪𝘴 𝘵𝘩𝘦 𝘴𝘩𝘪𝘧𝘵             | A key phrase, not whole sentences  |
| No emphasis       | Plain text                      | This is the shift              | Default for all body copy          |

To produce unicode bold sans-serif, use a unicode font converter tool and paste the result directly into the post. Do not type markdown and expect LinkedIn to render it. Plain text is the default for all body copy. Reach for unicode bold only for the opening hook or a section label.

## Structure and Spacing

- Separate every paragraph with one blank line. Do not double-space within a paragraph.
- Keep each paragraph to 2-4 lines. A paragraph longer than 4 lines should be split.
- Lists are written as plain text lines with a simple prefix. Use a filled circle (·) or a plain number. Do not use dashes or arrows as list markers.
- The opening line stands alone on its own line. It is the hook. It should be plain text, unformatted, and punchy.
- The closing line also stands alone. It ends with a direct thought or a specific question.

## Spacing Example

```
𝗪𝗵𝗮𝘁 𝗺𝗮𝗸𝗲𝘀 𝗮𝗻 𝗛𝗥 𝗮𝗴𝗲𝗻𝘁 𝗮𝗰𝘁𝘂𝗮𝗹𝗹𝘆 𝘂𝘀𝗲𝗳𝘂𝗹?

Most agents answer questions. The useful ones take action.

I have spent the last year building AI tools inside HR systems. The pattern I keep seeing is this: the teams that get value are the ones who give agents a defined scope and real data access.

· Clear task boundaries
· Live system integration
· A human in the loop for edge cases

The technology is not the hard part. The design is.

What has your experience been building or deploying agents at scale?

#AgenticAI #HRTechnology #FutureOfWork
```

## LinkedIn Anti-Patterns

- No emojis anywhere in the post.
- No horizontal line separators of any kind.
- No all-caps words or phrases.
- No more than one unicode-styled phrase per paragraph.
- No decorative symbols used as bullets (arrows, chevrons, stars).
- No tagging people or companies unless directly relevant to the post content.
- No posts that are a single wall of text. Always use paragraph breaks.

---

---

# Section 4: Content Generation Guidelines

---

These rules apply to all written content generated on my behalf, across every format and platform. They define my writing style and must be followed without exception.

## Punctuation

- Never use an em dash ("—") anywhere in generated content. If a sentence would use one, either split it into two sentences or replace it with a comma.
- Never use a semicolon. If a sentence would use one, replace it with a full stop and start a new sentence, or restructure using a comma.
- These are not stylistic preferences. They are hard rules that reflect how I write.

## Sentence Construction

- Write in short, direct sentences. One idea per sentence.
- When a sentence feels too long, break it at the natural pause point. Start a new sentence rather than chaining clauses together.
- Commas are acceptable for joining closely related clauses, but they should not substitute for a full stop when the two ideas are distinct.

## Voice and Tone

- Write in first person where the content is personal or opinion-based.
- Use active voice. Rewrite passive constructions before delivering output.
- Avoid filler phrases such as "it is worth noting that", "it goes without saying", or "as previously mentioned".
- Avoid hedging language unless genuine uncertainty needs to be communicated.

## Contact Details

- Always use the email address siddhartha.dhamankar@icloud.com. Do not use any other email address.
- Do not invent, guess, or substitute a different address if this one is not visible in context. Leave a placeholder and flag it instead.

## Review Checklist

Before delivering any written content, check for:

- Any "—" character. Remove and rewrite.
- Any semicolons. Remove and rewrite.
- Any sentences over 30 words. Break them up.
- Any passive voice constructions. Rewrite in active voice.

---

---

# Shared Diagram Rules

These rules apply to every SVG diagram across HTML pages and PDFs.

## Philosophy

- Each diagram teaches one idea. If it needs a paragraph to explain itself, split it.
- Flat, clean, minimal. No gradients, drop shadows, textures, or decorative flourishes.
- Visual hierarchy replaces verbal explanation. The eye should move in the intended reading order.
- All diagrams in the same document must be visually consistent.

## Canvas and Layout

- ViewBox: `0 0 900 560` landscape (default), `0 0 660 800` portrait.
- Outer padding: 40px on all sides. No element touches the edge.
- Reading direction: left-to-right or top-to-bottom. Establish one and hold it throughout.
- Align all elements to a 20px grid.
- Diagram title: top-left at `x=40, y=28`. Legend (if needed): bottom-left.

## Shapes and Their Meanings

| Shape              | Meaning                                  |
|--------------------|------------------------------------------|
| Rectangle          | Process, component, concept, entity      |
| Rounded rectangle  | State, stage, phase                      |
| Diamond            | Decision / branch point                  |
| Circle / oval      | Start / end terminal, actor              |
| Parallelogram      | Input / output / data                    |
| Cylinder           | Storage / database                       |
| Dashed rectangle   | External system, out-of-scope            |
| Bold outline rect  | Emphasis / primary subject               |

## Sizing

- Standard node: 130-160px wide, 44-54px tall.
- Small/leaf node: 100-120px wide, 36-44px tall.
- Large container/group: sized to contents plus 24px internal padding.
- Decision diamond: 70x70px.
- Terminal circle: 44x44px.
- Corner radius: `rx="8"` for rounded rects, `rx="12"` for containers.

## Spacing

- Minimum gap between any two nodes: 40px horizontal, 36px vertical.
- Inside a container/group: 24px internal padding.
- Between groups or swim lanes: 56px or more.
- Connector label clearance: 8px from the line to the label text.

## Colour System for Diagrams

Use at most 2 colour ramps per diagram. All fills must be light tints only.

| Role               | Fill        | Stroke      |
|--------------------|-------------|-------------|
| Primary subject    | `#D6EFDB`   | `#4E8C5F`   |
| Secondary/support  | `#E8E2F5`   | `#6B5A9E`   |
| External/passive   | `#F5F5F5`   | `#999999`   |
| Warning/risk       | `#FEF3E2`   | `#D97706`   |
| Negative/stop      | `#FEF0EF`   | `#C0392B`   |
| Success/positive   | `#D6EFDB`   | `#4E8C5F`   |
| Neutral container  | `#FAFAFA`   | `#CCCCCC` dashed |

Add a legend at the bottom whenever colour encodes a category. Keep it to 5 entries or fewer.

## Arrows and Connectors

- Default stroke: 1.5px, colour `#555555`.
- Primary or critical path: 2px, matching the source node's stroke colour.
- Arrowhead: small filled triangle, `markerWidth="6" markerHeight="6"`, `refX="5"`.
- Prefer orthogonal (right-angle) routing. Avoid diagonal lines.
- Connectors enter and exit at the center of a box side, not a corner.
- Label a connector only when the relationship is non-obvious. Keep labels to 3 words or fewer.

| Flow type      | Style                            |
|----------------|----------------------------------|
| Sequential     | Solid, single arrowhead          |
| Bidirectional  | Solid, arrowheads both ends      |
| Optional/weak  | Dashed `stroke-dasharray="5,4"`  |
| Async/event    | Dashed `stroke-dasharray="6,3"`  |
| Dependency     | Dotted `stroke-dasharray="2,3"`  |

## Diagram Density

- Maximum 20 nodes per diagram. Split into overview and detail views beyond that.
- Maximum 4 boxes in a single horizontal row at full canvas width.
- If a legend exceeds 5 entries, the diagram has too many categories. Simplify first.
- If connectors cross more than twice, restructure the layout before adding more nodes.
- Prefer two focused diagrams over one cluttered diagram.

## Diagram Anti-Patterns

- No font sizes above 15px inside diagrams or below 10px anywhere.
- No all-caps node labels. Only section/lane headers use uppercase.
- No diagonal connectors in flowcharts.
- No connector crossings more than twice per diagram.
- No decorative shadows, gradients, or glows.
- No mixing shape conventions within one diagram.
- No unlabeled decision branches in flowcharts.
- No rainbow colour schemes (more than 2-3 ramps).
