# Buildings Sector — SharePoint Redesign

**Live mockup:** https://bermelloajamil.github.io/buildings-sharepoint/

Redesign of the Woolpert **Buildings Sector** SharePoint site
(`https://woolpert.sharepoint.com/sites/Buildings_Sector`, page `SitePages/Sector-Wireframe.aspx`).

**Current goal:** an interactive HTML mockup of the redesigned site, framed in real
SharePoint chrome, to present to management for approval. Implementation on actual
SharePoint comes after sign-off.

## Files

| File | What it is |
|---|---|
| **[index.html](index.html)** | ⭐ The presentation mockup — open this in a browser. SharePoint chrome (blue suite bar, labeled app bar, BS-tile nav with right-aligned search, rounded floating content sheet with internal scroll, Copilot bubble) around the new page design. Interactive: nav dropdowns, app launcher, live calendar month paging. |
| [assets/hero.webp](assets/hero.webp) | Hero photo (data center building at dusk). **Required by the mockup** — keep the `assets` folder next to the HTML when sharing/moving it. |
| [design.md](design.md) | Full design specification (tokens, layout, all 7 cards, exact copy). §11 records the hero v2 revisions made during mockup review. |

## Current state (as of Sep 3, 2026)

Mockup is presentation-ready after several review rounds:

- Hero: inset rounded photo banner, blue-slate left→right gradient scrim, left-aligned content —
  outline "Woolpert Buildings" pill, "Architecture" title (weight 600, 56–82px),
  tagline ("Designing spaces that inspire…"), 600px search bar with green Search button,
  text-only stats row (200+ Completed Projects · 25+ Design Awards · 40+ Years of Excellence).
- Content: white sheet flush to screen bottom (top corners rounded), 1440px content column,
  7 design cards (Calendar / News / Leadership / Discipline Standards / Industry Links /
  Orientation / Featured Projects), dark footer.
- Editing command bar and mockup badge intentionally removed (reader view for the demo).

## To resume

1. Open `index.html` in a browser (or the live site above) to see where things stand.
2. Continue fine-tuning it, or move to the next phase: present it for approval. Once the design
   is signed off, ask Claude to generate a fresh SharePoint implementation guide against the
   final design (site theme + header/nav/footer settings, web-part mapping, what needs IT),
   or an SPFx scaffold for pixel-perfect fidelity.
3. If emailing the mockup: send the HTML **plus the `assets` folder** (or ask Claude to
   inline the photo as base64 for a single-file version).
