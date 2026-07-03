# Handoff: Flockr Trade-Show Kiosk — Two-Screen Booth Rig

## Overview
Two portrait touchscreen displays for a physical trade-show booth for **Flockr**, a livestock marketplace platform (Africa). They're meant to sit side by side:

- **Display 1 — Info Loop**: an unattended, auto-advancing product story (6 slides) — attract-mode marketing, no touch required.
- **Display 2 — QR Standby**: a static, always-on screen showing only a QR code and offer. Visitors scan it with their own phone to reach a lead-capture / free-guide landing page (not included in this bundle).

## Running it
No build step, no dependencies beyond the Google Fonts `@import` in `tokens/typography.css`. Open either `index.html` directly in a browser, or for kiosk hardware run it full-screen in a locked-down kiosk browser (e.g. Chromium `--kiosk "file:///path/to/ui_kits/Kiosk Display 1 - Info Loop/index.html"`). Each screen is a fixed 460×940 logical canvas that scales itself (via a JS `fit()` on load/resize) to whatever the actual screen resolution is, preserving aspect ratio.

## Fidelity
High-fidelity. Colors, type, spacing, copy, and motion timings are final-intent, ported pixel-for-pixel from the design source.

## Screens

### Display 1 — Info Loop (`ui_kits/Kiosk Display 1 - Info Loop/index.html`)
6 slides, auto-advance every 8s, opacity-crossfade 550ms, loops forever: Hero → Opportunity → Capabilities → Trust/Escrow → Footprint → Closer (bridges to Display 2). Signature visual motif: an oversized brand-mark watermark bled off a different edge each slide. Fully automatic — no touch targets by design.

### Display 2 — QR Standby (`ui_kits/Kiosk Display 2 - QR Standby/index.html`)
Static screen: logo, pulsing "Scan to get started" pill, headline, breathing QR card with a scan-ring, a human-typeable fallback URL (`flockr.africa/guide`), and a 2-stat trust strip. Never changes — no interaction.

**⚠️ The QR code is currently a striped placeholder graphic — swap in the real destination QR before print/production.**

## Known gap: real photography missing
Display 1 references four real photographs (`assets/photos/hands-smartphone.jpeg`, `herder-savanna.jpeg`, `loading-ramp.jpeg`, `market-traders.jpeg`) that are approved, final images per the design source — **not** decorative placeholders. They could not be pulled into this repo: each file exceeds the design tool's 256 KiB per-file read cap, so the fetch came back truncated. The `.photo-ph` containers currently render as an empty dark tinted panel (graceful fallback) instead of a broken image. To complete the build, export those 4 JPEGs from the Claude Design project directly and drop them into `assets/photos/` with the exact filenames above — the HTML already points at the correct paths, no code changes needed.

## Design Tokens
`tokens/colors.css`, `tokens/typography.css`, `tokens/spacing.css` (imported via `styles.css`). Brand brown `#744214` (logo-exact) as `--brand-600`, savanna gold accent (`--gold-*`), trust green reserved for escrow/verified states. Fonts: Lora (display/headlines) + Work Sans (body/UI).

## Assets
`assets/logo/` — 4 official Flockr logo files (mark, horizontal/vertical/white lockups), final brand assets, do not restyle.
