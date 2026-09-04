# Buildings SharePoint — Homepage Design Specification

This document is the single source of truth for recreating the **Buildings SharePoint / Architecture** intranet homepage pixel-faithfully. It captures every visible element of the reference design: layout, colors, typography, spacing, component anatomy, and the exact content inventory.

---

## 1. Overview

- **Page type:** Corporate intranet homepage (SharePoint-style hub) for an Architecture discipline.
- **Aesthetic:** Clean, minimal, modern-SaaS. Light theme only. Generous whitespace, soft rounded corners, subtle borders and shadows.
- **Color story:** Warm light-gray page background, pure white cards, near-black text, and a single **dark emerald green** accent used for the logo, buttons, links, icons, and the selected calendar day.
- **Page order (top → bottom):**
  1. Sticky top navigation bar
  2. Full-width hero with photo and welcome text
  3. Card grid row 1: Calendar · News · Leadership
  4. Card grid row 2: Discipline Standards · Industry Links · Orientation
  5. Full-width card: Featured Projects
  6. Dark footer

---

## 2. Design Tokens

Use these as CSS custom properties. Hex values are matched to the reference design.

```css
:root {
  /* ---- Color: brand ---- */
  --green-900: #12463B;   /* button hover, deep accents */
  --green-800: #1D6152;   /* PRIMARY: buttons, logo, selected calendar day, doc icons */
  --green-700: #257A61;   /* footer links on cards ("View all …"), hyperlinks */
  --green-100: #E4EFEA;   /* soft green tint (icon chip hover, badges) */

  /* ---- Color: neutrals ---- */
  --bg-page: #F4F5F3;     /* page background behind cards */
  --bg-card: #FFFFFF;     /* card + nav background */
  --bg-row: #F7F8F7;      /* inner list rows (documents, orientation items) */
  --bg-footer: #101413;   /* footer, near-black with green undertone */

  --text-primary: #1A1F1E;   /* headings, titles, nav links */
  --text-secondary: #5C6461; /* subtitles, dates, role labels */
  --text-muted: #9AA19E;     /* adjacent-month calendar days, eyebrow */
  --text-inverse: #FFFFFF;   /* text on green buttons and footer */

  --border: #E6E8E6;         /* card borders, dividers, input borders */
  --border-strong: #D6D9D6;  /* secondary button outline */

  /* ---- Typography ---- */
  --font-sans: "Inter", "Segoe UI", -apple-system, system-ui, sans-serif;

  --fs-hero: 60px;        /* H1 "Architecture SharePoint" (2 lines) */
  --fs-eyebrow: 12px;     /* "WELCOME TO" */
  --fs-card-title: 18px;  /* "Calendar", "News", … */
  --fs-body: 14px;        /* card subtitles, list item titles */
  --fs-small: 12.5px;     /* dates, roles, meta text */
  --fs-nav: 14px;

  /* ---- Shape ---- */
  --radius-card: 14px;    /* white cards */
  --radius-row: 10px;     /* inner list rows, thumbnails */
  --radius-img: 12px;     /* orientation photo, project images */
  --radius-btn: 8px;      /* buttons */
  --radius-input: 8px;    /* search input */
  --radius-full: 9999px;  /* avatars, org logos, selected calendar day */

  /* ---- Elevation ---- */
  --shadow-card: 0 1px 2px rgba(16, 20, 19, 0.04),
                 0 4px 12px rgba(16, 20, 19, 0.04);

  /* ---- Layout ---- */
  --content-max: 1200px;  /* centered content column */
  --gap-grid: 24px;       /* gap between cards */
  --pad-card: 24px;       /* inner card padding */
}
```

### Typography scale

| Role | Size / weight / treatment |
|---|---|
| Hero H1 | 56–64px, weight 600–700, color `--text-primary`, line-height ~1.05, slight negative tracking (-0.02em). Breaks as two lines: "Architecture" / "SharePoint". |
| Hero eyebrow | 12px, weight 600, UPPERCASE, letter-spacing 0.12em, color `--text-muted`. |
| Hero subtext | 15px, weight 400, `--text-secondary`, line-height 1.5. |
| Card title | 18px, weight 600, `--text-primary`. |
| Card subtitle | 14px, weight 400, `--text-secondary`, line-height 1.45. |
| List item title | 14px, weight 500–600, `--text-primary`. |
| List item meta (date/role) | 12.5px, weight 400, `--text-secondary`. |
| Card footer link | 13.5px, weight 500, color `--green-700`, no underline (underline on hover). |
| Nav links | 14px, weight 500; active item weight 600 in `--text-primary`, inactive in `--text-secondary`. |

---

## 3. Top Navigation Bar

Full-width, background `--bg-card` (white), height **64px**, bottom border 1px `--border`. Sticky at top. Inner content constrained to `--content-max`, horizontally space-between, vertically centered.

**Left — logo lockup:**
- Logo mark: a simple green building/skyline glyph in `--green-800`, ~28px.
- Wordmark, two stacked lines: line 1 **"BUILDINGS"** (12px, weight 800, uppercase, `--text-primary`); line 2 "SharePoint" (12px, weight 400, `--text-secondary`).

**Center — nav links (horizontal, ~28px gap):**
1. **Home** — active state: weight 600, `--text-primary` (optionally a subtle 2px green underline).
2. Resources ⌄ (with small chevron-down icon)
3. Projects ⌄
4. Company ⌄
5. Help ⌄

Inactive links use `--text-secondary`; hover → `--text-primary`.

**Right — utilities (horizontal, ~14px gap):**
1. Search input: width ~220px, height 36px, radius `--radius-input`, 1px `--border`, background white/`#FAFAFA`, left magnifier icon, placeholder **"Search this site"** in `--text-muted`.
2. Bell (notifications) icon button, 20px line icon, `--text-secondary`.
3. Waffle / app-launcher icon (3×3 grid of dots), `--text-secondary`.
4. User avatar: 32px circle, photo, no border.

---

## 4. Hero

Full-width section directly under the nav, height **~460px**.

- **Background:** photograph of a modern multi-story glass-and-panel office building surrounded by trees under a bright sky. The photo dominates the right two-thirds; the left third fades into a very light neutral (off-white → transparent left-to-right gradient overlay: `linear-gradient(90deg, #F5F4F1 0%, #F5F4F1 30%, transparent 60%)`) so text stays readable.
- **Text block:** left-aligned, vertically centered, inset to the content column (left edge aligns with the card grid below). Max width ~480px.
  1. Eyebrow: **"WELCOME TO"** (eyebrow style above).
  2. H1: **"Architecture SharePoint"** — two lines, hero style above.
  3. Subtext: **"Your hub for tools, standards, projects, and collaboration."** — may wrap to two lines.
  4. Button row (16px top margin, 12px gap):
     - **Primary button — "Explore Resources":** background `--green-800`, text `--text-inverse`, 14px weight 600, padding ~12px 22px, radius `--radius-btn`. Hover: `--green-900`.
     - **Secondary button — "Site Overview":** background white, 1px border `--border-strong`, text `--text-primary`, same size/padding/radius. Hover: light gray background.

---

## 5. Main Content Area

Background `--bg-page`. Vertical padding ~40px top and bottom. Content column centered at `--content-max`.

**Grid:** `display: grid; grid-template-columns: repeat(3, 1fr); gap: var(--gap-grid);`
- Row 1: Calendar · News · Leadership
- Row 2: Discipline Standards · Industry Links · Orientation
- Row 3: Featured Projects spans all 3 columns (`grid-column: 1 / -1`).

### Shared card anatomy

Every card uses the same shell and header pattern:

- **Shell:** background `--bg-card`, radius `--radius-card`, 1px border `--border`, shadow `--shadow-card`, padding `--pad-card`.
- **Header:** horizontal row —
  - *Icon chip:* 36×36px rounded square (radius 10px), 1px border `--border`, transparent/white fill, containing a 18–20px dark line icon representing the card's theme.
  - *Title:* card-title style, 12px left of chip.
- **Subtitle:** one–two lines, card-subtitle style, ~8px under the header, wrapping naturally (e.g. "View upcoming events / and important dates.").
- **Body:** card-specific (below), ~16px under subtitle.
- **Footer:** full-width 1px top divider `--border` (~16px above), then footer link in `--green-700`, left-aligned, 12–14px below divider. Cards in the same row bottom-align their footers.

---

### 5.1 Card: Calendar (row 1, col 1)

- **Icon:** calendar glyph. **Title:** "Calendar".
- **Subtitle:** "View upcoming events and important dates."
- **Body — month calendar** inside a light bordered container (1px `--border`, radius `--radius-row`, padding 12px):
  - Header row: left chevron ‹ · **"May 2025"** (14px, weight 600, centered) · right chevron ›.
  - Weekday row: **S M T W T F S** — 11px, `--text-muted`.
  - 5 date rows (7 columns, ~32px cells, 12–13px text):
    - Row 1: 27 28 29 30 1 2 3 (27–30 muted, prior month)
    - Row 2: 4 5 6 7 8 9 10
    - Row 3: 11 12 13 **14** 15 16 17 — day 14 highlighted with a subtle outline/tint circle (secondary event marker)
    - Row 4: 18 19 **20** 21 22 23 24 — **day 20 = today/selected:** filled circle `--green-800`, white text
    - Row 5: 25 26 27 28 29 30 31
- **Footer link:** "View full calendar"

### 5.2 Card: News (row 1, col 2)

- **Icon:** newspaper glyph. **Title:** "News".
- **Subtitle:** "Stay up to date with the latest announcements."
- **Body — 3 stacked news rows** (each: 1px border `--border`, radius `--radius-row`, padding 10px, 10px vertical gap). Row layout: thumbnail left + text right.
  - Thumbnail: 56×56px, radius 8px, object-fit cover.
  - Title: list-item-title style, up to 2 lines. Date below in meta style.

  | # | Thumbnail | Title | Date |
  |---|---|---|---|
  | 1 | modern glass building exterior | Project Update: Riverside Civic Pavilion | May 16, 2025 |
  | 2 | dark door hardware close-up | New Standard: Door Hardware | May 12, 2025 |
  | 3 | team meeting around a table | Team Spotlight: Design Excellence | May 8, 2025 |

- **Footer link:** "See all news"

### 5.3 Card: Leadership (row 1, col 3)

- **Icon:** person glyph. **Title:** "Leadership".
- **Subtitle:** "Meet the leadership team driving our vision."
- **Body — 4 people rows** (no borders; ~16px vertical spacing). Row: 44px circular photo avatar left; right column: name (list-item-title) over role (meta style).

  | Name | Role |
  |---|---|
  | Alex Morgan | Chief Executive Officer |
  | Jordan Lee | Chief Operations Officer |
  | Taylor Smith | Director of Design |
  | Casey Brown | Director of Engineering |

- **Footer link:** "View leadership team"

### 5.4 Card: Discipline Standards (row 2, col 1)

- **Icon:** document-with-lines glyph. **Title:** "Discipline Standards".
- **Subtitle:** "Access our standards, templates, and guidelines for Architecture."
- **Body — 3 document rows** (background `--bg-row`, radius `--radius-row`, padding 12px, 10px gap). Row: green document line-icon (20px, `--green-800`) left; right: document name (list-item-title) over updated date (meta style).

  | Document | Meta |
  |---|---|
  | Design Standards Manual | Updated May 1, 2025 |
  | Drawing Standards | Updated April 28, 2025 |
  | Specification Template | Updated April 20, 2025 |

- **Footer link:** "View all standards"

### 5.5 Card: Industry Links (row 2, col 2)

- **Icon:** globe/link glyph. **Title:** "Industry Links".
- **Subtitle:** "Quick access to trusted industry resources."
- **Body — 4 link rows** (1px border `--border`, radius `--radius-row`, padding 10px 12px, 10px gap). Row layout: 32px circular organization logo left · label center (list-item-title, may wrap to 2 lines) · small external-link icon (↗ in square, `--green-700`) pinned right.

  | Logo | Label |
  |---|---|
  | AIA round mark (dark) | AIA – The American Institute of Architects |
  | CSI round mark (dark) | CSI – Construction Specifications Institute |
  | USGBC round mark (green) | USGBC – U.S. Green Building Council |
  | ASCE round mark (blue) | ASCE – American Society of Civil Engineers |

- **Footer link:** "View all links"

### 5.6 Card: Orientation (row 2, col 3)

- **Icon:** presentation/monitor glyph. **Title:** "Orientation".
- **Subtitle:** "New to the team? Start here."
- **Body:**
  1. Featured photo: full card width, ~120px tall, radius `--radius-img`, object-fit cover — a group of colleagues talking and smiling in a bright office.
  2. **3 item rows** below the photo (background `--bg-row` or 1px border, radius `--radius-row`, padding 12px, 10px gap). Row: 20px dark line icon left; right: item title (list-item-title) over one-line description (meta style).

  | Icon | Title | Description |
  |---|---|---|
  | monitor/welcome glyph | Welcome Guide | Learn about our culture and mission. |
  | gears/setup glyph | IT Onboarding | Get set up with the tools you need. |
  | map-pin glyph | Site Tour | Explore key systems and resources. |

- **Footer link:** "View orientation hub"

### 5.7 Card: Featured Projects (row 3, full width)

- **Icon:** building glyph. **Title:** "Featured Projects".
- **Subtitle:** "Explore some of our recent architecture projects."
- **Body — 4 project tiles** in one row (`grid-template-columns: repeat(4, 1fr); gap: 20px;`). Each tile:
  - Image: full tile width, ~150px tall, radius `--radius-img`, object-fit cover.
  - Name: list-item-title style, 10px under image.
  - Category: meta style, 2px under name.

  | Image subject | Name | Category |
  |---|---|---|
  | angular glass civic building | Riverside Civic Pavilion | Community |
  | tall glass office tower | Market Street Office Tower | Commercial |
  | curved glass + timber school building | Greenway Education Center | Education |
  | timber-clad apartment block | Harborview Residences | Residential |

- **Footer link:** "View all projects"

---

## 6. Footer

Full-width bar, background `--bg-footer`, ~72px tall, content constrained to `--content-max`, three zones space-between, vertically centered:

1. **Left:** logo lockup identical to the nav but inverted — green building glyph + stacked "BUILDINGS" (white, bold) / "SharePoint" (light gray `#9AA19E`).
2. **Center:** links, 13px, light gray `#B9BFBC`, ~28px gap, hover → white: **Privacy Policy · Terms of Use · Contact IT**
3. **Right:** "© 2025 Buildings SharePoint. All rights reserved." — 13px, light gray.

---

## 7. Reusable Component Summary

| Component | Used in | Key spec |
|---|---|---|
| Card shell | all 7 cards | white, radius 14px, 1px `--border`, `--shadow-card`, 24px padding |
| Icon chip + title header | all 7 cards | 36px rounded-square outlined chip + 18px semibold title |
| Bordered list row | News, Industry Links | 1px border, radius 10px, thumb/logo + text (+ trailing icon) |
| Tinted list row | Discipline Standards, Orientation | `--bg-row` fill, radius 10px, icon + title + meta |
| Person row | Leadership | 44px circle avatar + name/role stack, borderless |
| Card footer link | all 7 cards | top divider + green 13.5px link |
| Primary button | hero | green fill, white text, radius 8px |
| Secondary button | hero | white fill, gray outline, dark text |
| Calendar grid | Calendar | 7-col grid, filled green circle = today, outlined = event |
| Project tile | Featured Projects | image + name + category stack |

---

## 8. Assets Required

Placeholders (solid tints or stock photos) are acceptable until final assets exist.

| Asset | Count | Notes |
|---|---|---|
| Hero photo | 1 | modern glass office building with trees; ≥1600px wide |
| News thumbnails | 3 | building exterior; door hardware; team meeting |
| Leadership avatars | 4 | professional headshots, square crop → circle |
| Org logos | 4 | AIA, CSI, USGBC, ASCE round marks |
| Orientation photo | 1 | colleagues talking in office |
| Project photos | 4 | one per featured project |
| User avatar (nav) | 1 | current user headshot |
| Logo glyph | 1 | green building mark (inline SVG preferred) |

---

## 9. Responsive Behavior

The reference is a desktop layout (~1280px+). Adapt as follows:

- **≤1024px:** card grid 3 → 2 columns (Featured Projects still spans full width; its tiles wrap 4 → 2). Hero H1 scales down to ~44px.
- **≤680px:** card grid → 1 column; project tiles → 1 per row; nav center links collapse behind a hamburger menu; search shrinks to an icon; footer stacks its three zones vertically, centered; hero height reduces and text block goes full-width over a stronger overlay.
- Wide content (calendar grid) must never overflow the card — cells shrink fluidly.

---

## 10. Fidelity Checklist

When implementing, verify against this list — all must match:

- [ ] Nav: logo lockup, 5 links (Home active), search "Search this site", bell, waffle, avatar
- [ ] Hero: "WELCOME TO" / "Architecture SharePoint" (2 lines) / subtext / 2 buttons
- [ ] Calendar: May 2025, day 20 filled green, day 14 outlined, muted leading days
- [ ] News: 3 items with exact titles + dates
- [ ] Leadership: 4 people with exact names + roles
- [ ] Discipline Standards: 3 documents with exact "Updated" dates
- [ ] Industry Links: 4 orgs with external-link icons
- [ ] Orientation: photo + 3 items with descriptions
- [ ] Featured Projects: 4 tiles with names + categories
- [ ] Footer: dark, 3 links, © 2025 line
- [ ] All 7 card footer links present, green, above-divider pattern
- [ ] Single accent color (dark emerald) used consistently; no other saturated hues except org logos

---

## 11. Revisions — Hero v2 & SharePoint mockup (Sep 2–3, 2026)

During mockup review the hero was redesigned; `sharepoint-mockup.html` is the implemented
reference. Where this section conflicts with §4, **this section wins**.

**Hero v2** (replaces §4's hero):
- Inset rounded banner inside the white page sheet: margin 18px 22px 0, radius 16px,
  height `clamp(460px, 30vw, 570px)`.
- Background: real photo `assets/hero.webp` (cover, center) — no vector illustration.
- Scrim: blue-slate gradient left→right —
  `linear-gradient(90deg, rgba(15,27,44,.82) 0%, rgba(15,27,44,.50) 34%, rgba(15,27,44,.02) 68%)`.
- Content left-aligned, vertically centered, white text; column `width:100%; max-width:920px`
  (the explicit width matters — without it the column shrink-wraps and children with % widths collapse):
  1. Outline pill (no fill): building icon + "Woolpert Buildings"
  2. H1 "Architecture" — `clamp(56px, 5.2vw, 82px)`, weight 600
  3. Tagline: "Designing spaces that inspire, function seamlessly, / and stand the test of time." (two lines)
  4. Search bar: 600px white, radius 12px, magnifier + input
     ("Search for standards, projects, news, and more...") + green "Search" button
  5. Stats row, text only (no icons): **200+** Completed Projects · **25+** Design Awards ·
     **40+** Years of Excellence (26px bold numbers, 12.5px labels)
- Removed from v1: "WELCOME TO" eyebrow, "SharePoint" in the title, the two hero buttons,
  the white left fade.

**Content area changes:**
- Page sheet background pure white (not gray); cards separate via border + shadow.
- Content column max-width **1440px** (was 1200px).
- Sheet runs flush to the viewport bottom; only top corners rounded (12px); internal scroll.

**SharePoint chrome (mockup framing):** blue `#0178D4` suite bar (pill search centered,
theme/cast/headset/gear/help icons + avatar), 64px labeled app bar (Home/Discover/Publish/
Build/OneDrive), site nav = BS tile + 5 links + muted "Edit navigation" + right-aligned
"Search this site" box + "…", no page command bar (reader view), Copilot bubble bottom-right.
