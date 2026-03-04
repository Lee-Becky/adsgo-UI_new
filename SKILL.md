---
name: adsgo-new-ui-skill
description: Use this skill to build any UI for AdsGo.ai — the AI-powered ad management SaaS platform. Invoke immediately whenever the user wants to create, modify, or review any visual element: pages, dashboards, campaign tables, AI analysis panels, optimization consoles, modals, drawers, sidebars, forms, or interactive states. Trigger even when the user just mentions AdsGo, says "make it look like the app", or asks for a component that "matches the design". This skill provides the complete 2026 AdsGo design system: Outfit font, #7033F5 purple primary, pixel-perfect component specs, CSS variables, and AI-specific components unique to AdsGo (Smart Optimization Console, AI Analysis Panel, budget allocation cards). Do not attempt AdsGo UI work without this skill — the brand is distinctive and must stay consistent. Also trigger for: Ads Manager, Campaign Table, Performance Overview, Optimization Hub, Brand Performance Goal, onboarding guides, and any screen shown in the AdsGo product.
---

# AdsGo.ai UI/UX Design System (2026)

Read this file fully before writing any code. Then consult the reference files below as needed — they contain complete CSS code, HTML patterns, and detailed specs.

## MANDATORY — Primary Brand Rules

These three rules are absolute and apply to EVERY AdsGo page or component. Never deviate.

1. **Font: Outfit (Google Fonts)** — Every single text element uses `font-family: 'Outfit', sans-serif`. No exceptions, no fallback mixing. Import: `@import url('https://fonts.googleapis.com/css2?family=Outfit:wght@400;500;600;700&display=swap');`

2. **Primary Color: `#7033F5`** — This purple is the core identity of AdsGo. It is used for:
   - All primary buttons (`background: #7033F5`)
   - Active navigation items (left accent bar `4px solid #7033F5` + bg `#F5F1FF`)
   - Toggle ON state (`background: #7033F5`)
   - Input focus border (`border-color: #7033F5`)
   - Active pagination page (`background: #7033F5`)
   - Action icon hover (`color: #7033F5`)
   - AI/sparkle accents (`color: #7033F5`)
   - Links and interactive text highlights
   - Hover dark variant: `#5221CF`

3. **Pill-shaped buttons** — All buttons use `border-radius: 9999px`. Never use rectangular or slightly rounded buttons. This is AdsGo's signature look.

If any generated code uses a different font, a different primary color, or rectangular buttons — it is WRONG and must be corrected.

---

## Reference Files

| File | Contents | When to read |
|---|---|---|
| `references/components.md` | Button, Badge, Tag, Toggle, Input, Dropdown, Modal, Alert, Tooltip, Drawer | Building interactive UI components |
| `references/layout.md` | Full page shell, Sidebar, Header, content grid patterns | Setting up a new page or layout |
| `references/data-display.md` | Campaign tables, KPI cards, stats rows, pagination, status states | Displaying campaign data or metrics |
| `references/ai-components.md` | AI Analysis Panel, Optimization Console, Budget Allocation, AI Pending state | Building AI/optimization features |

---

## 1. Brand Identity

### Purple Color System (core of AdsGo's visual identity)

| Token | Value | Usage |
|---|---|---|
| **Primary purple** | **`#7033F5`** | Buttons, toggles ON, active states, focus rings, pagination, links |
| Dark purple (hover) | `#5221CF` | Button hover, pressed states |
| Darker purple | `#4D18C2` | Emphasis variants |
| Light purple bg | `#F5F1FF` | Active nav item bg, action icon hover bg |
| Mid purple bg | `#EDE8FF` | Active platform tab bg, Pending tag bg |
| Light purple fill | `#F7F4FF` | Upgrade card bg |
| Accent purple text | `#5E26D6` / `#501DC7` | Purple text on light bg, platform tab active text |
| Purple gradient | `#C4B5FD → #DDD6FE` | AI container accent borders |

### Neutral Colors

| Token | Value |
|---|---|
| Dark text | `#1D293D` / `#314158` / `#404040` |
| Body text | `#45556C` |
| Muted text | `#62748E` / `#90A1B9` |
| Border light | `#F1F5F9` |
| Border medium | `#E2E8F0` |
| Page background | `#F9F9F9` |
| Content area bg | `#F9FAFC` |
| Card / panel bg | `#FFFFFF` |
| Soft fill | `#FAFAFA` / `#F7F8FA` |

### Semantic / Status Colors

| Token | Value |
|---|---|
| Danger | `#FB2C36` / bg `#FFEDEF` / border `#D4004A` |
| Success | `#00941E` / bg `#E1FAE1` |
| Warning | `#FF8E2B` / bg `#FFF5E6` / bg-light `#FFF3E9` |
| Teal accent | `#0799B6` |

### AI Console Colors (blue tint — NOT purple)

| Token | Value |
|---|---|
| Blue tint bg | `#F2F8FF` / `#E0EEFF` / `#EEF6FF` / `#F1F7FF` |
| Blue gradient (active mode) | `#3080E3 → #285388` |

Note: The Smart Optimization Console uses blue tints, not purple. This is intentional — it visually separates the AI optimization panel from the rest of the purple brand UI.

---

## 2. Typography Scale

**Font: Outfit (mandatory for ALL text).** No other font is used anywhere in AdsGo.

```css
@import url('https://fonts.googleapis.com/css2?family=Outfit:wght@400;500;600;700&display=swap');
* { font-family: 'Outfit', sans-serif; }
```

| Role | Size / Weight | Color |
|---|---|---|
| Page title | 20px / 600 | `#1D293D` |
| Section title | 16px / 600 | `#1D293D` |
| Body default | 14px / 400 | `#404040` |
| Body medium | 14px / 500 | `#1D293D` |
| Sub-label | 12px / 400 | `#90A1B9` |
| Breadcrumb | 14px / 400 | `#62748E` |
| Active breadcrumb | 14px / 500 | `#404040` |
| Table header | 12px / 500 uppercase | `#45556C` |
| Table cell | 14px / 400 | `#1D293D` |
| Stats number | 24–32px / 700 | `#1D293D` |
| Metric value | 18px / 600 | `#1D293D` |
| AI insight text | 13px / 400 | `#45556C` |
| Tag / badge | 12px / 500 | varies |

---

## 3. Layout Structure

```
┌──────────────────────────────────────────────────────────┐
│  SIDEBAR (232px)  │          HEADER (64px)               │
│                   │──────────────────────────────────────│
│  Logo (68px)      │                                      │
│  Brand Selector   │         MAIN CONTENT AREA            │
│  (54px)           │         margin-left: 232px           │
│  ─────────────    │         padding: 24px                │
│  Nav items        │                                      │
│  (48px each)      │                                      │
│  ─────────────    │                                      │
│  Upgrade Card     │                                      │
└──────────────────────────────────────────────────────────┘
```

**Sidebar:** 232px fixed, white, `border-right: 1px solid #F1F5F9`. Read `references/layout.md` for the full CSS shell and internal layout.

**Header:** 64px sticky, white, `border-bottom: 1px solid #F1F5F9`. Contains breadcrumbs left, timezone pill + bell + user avatar right.

**Active nav item:** background `#F5F1FF` + left accent bar `4px solid #7033F5` with `border-radius: 0 9999px 9999px 0`. This is mandatory — it's the signature AdsGo nav style.

---

## 4. CSS Variables (MUST include in every page)

```css
:root {
  /* PRIMARY — the #7033F5 purple that defines AdsGo */
  --color-primary: #7033F5;
  --color-primary-dark: #5221CF;
  --color-primary-bg: #F5F1FF;
  --color-primary-bg-mid: #EDE8FF;
  --color-primary-text: #5E26D6;
  --color-primary-text-dark: #501DC7;
  --color-text-dark: #1D293D;
  --color-text-main: #314158;
  --color-text-body: #45556C;
  --color-text-muted: #62748E;
  --color-text-placeholder: #90A1B9;
  --color-border: #F1F5F9;
  --color-border-medium: #E2E8F0;
  --color-bg: #FFFFFF;
  --color-bg-soft: #F9FAFC;
  --color-bg-page: #F9F9F9;
  --color-bg-panel: #F7F8FA;
  --color-danger: #FB2C36;
  --color-danger-bg: #FFEDEF;
  --color-danger-border: #D4004A;
  --color-success: #00941E;
  --color-success-bg: #E1FAE1;
  --color-warning: #FF8E2B;
  --color-warning-bg: #FFF5E6;
  --color-warning-bg-light: #FFF3E9;
  --color-blue-tint: #F2F8FF;
  --color-blue-tint-deep: #E0EEFF;
  --font-main: 'Outfit', sans-serif;
}
```

---

## 5. Component Quick Reference

These components appear across the product. Detailed CSS is in `references/components.md`.

| Component | Key style |
|---|---|
| Primary button | `background: #7033F5`, `border-radius: 9999px`, `height: 36px` |
| Outline button | `border: 1px solid #6424EF`, `border-radius: 9999px`, transparent bg |
| Icon button | `32×32px`, `border-radius: 8px`, hover → purple bg + color |
| Toggle ON | `background: #7033F5`, knob right |
| Toggle OFF | `background: #CBD5E1`, knob left |
| Input | `height: 36px`, `border: 1px solid #E2E8F0`, `border-radius: 8px` |
| Input focus | `border-color: #7033F5`, ring `rgba(112,51,245,0.1)` |
| Platform tab active | `background: #EDE8FF`, `border: 1px solid #D4C5FA`, text `#5221CF` |
| Dropdown menu | `border-radius: 12px`, shadow `0 6px 20px rgba(0,0,0,0.15)` |
| Modal | `border-radius: 20px`, overlay `rgba(0,0,0,0.50)`, shadow `0 6px 20px rgba(0,0,0,0.15)` |
| Drawer | slides from right, overlay `rgba(0,0,0,0.50)` |
| Toast (notification) | `304×128px`, `border-radius: 8px`, top-right |
| Tooltip (dark) | bg `rgba(0,0,0,0.65)`, `border-radius: 24px`, pad `6px 16px` |
| Tooltip (light) | white, shadow `0 2px 8px rgba(0,0,0,0.15)` |

---

## 6. Status Tags

Status tags are pill-shaped badges used extensively in campaign tables.

| State | Background | Text color |
|---|---|---|
| Active / Running | `#E1FAE1` | `#00941E` |
| Warning / Paused | `#FFF5E6` | `#FF8E2B` |
| Inactive / Default | `#F5F5F5` | `#62748E` |
| Pending | `#EDE8FF` | `#5221CF` |
| AI Generated | transparent | `#7033F5` (with sparkle icon) |

All tags: `border-radius: 25px`, `padding: 1px 8px`, `font-size: 12px`, `font-weight: 500`.

---

## 7. Data Display Quick Reference

Full patterns with HTML + CSS are in `references/data-display.md`.

**KPI metric card:** white card, label 11px/600/uppercase/`#90A1B9`, value 28px/700/`#1D293D`, trend pill (up = green `#D1FAE5`, down = red `#FEF2F2`).

**Campaign table row height:** 120px (accommodates multi-line campaign info). Header bg `#F8FAFC`. See `references/data-display.md` for column widths and expanded adset rows.

**Today's stats:** 4-metric row (Spend, Revenue, ROAS, Conversions) with vertical separators `1px #E2E8F0`.

**Pagination:** Active page `background: #7033F5`, `border-radius: 8px`, white text.

---

## 8. AI Component Quick Reference

These are unique to AdsGo. Full patterns in `references/ai-components.md`.

**AI Analysis Panel:** Header with gradient bg `linear-gradient(135deg, #FAFAFA, #F5F1FF)`, sparkle icon + title. Three insight types: highlight (green left border), optimize (purple left border), risk (amber left border).

**Smart Optimization Console (337×483px):** Background gradient `linear-gradient(#F1F7FF, #FFFFFF)` — blue tint, not purple. Border `1px solid #F5F5F5`. Shadow `-2px 2px 15px rgba(14,0,45,0.06)`. Two modes — Recommendations and Auto-apply: inactive `#F2F8FF`, active gradient `linear-gradient(#3080E3, #285388)` with stroke `#E7F0FF`.

**AI Pending state:** Purple lock icon + countdown ("06h 06m remaining") + timeline steps.

---

## 9. Spacing & Radius Reference

| Context | Value |
|---|---|
| Page padding | `24px` |
| Section gap | `20px` |
| Card padding | `16px` – `20px` |
| Card border-radius | `12px` (small) / `20px` (large/dialog) |
| Button border-radius | `9999px` (always pill) |
| Input border-radius | `8px` |
| Nav item border-radius | `10px` |
| Tag border-radius | `25px` |
| Dropdown border-radius | `12px` |
| Modal border-radius | `20px` |
| Nav item height | `48px` |
| Campaign row height | `120px` |
| Sidebar width | `232px` |
| Header height | `64px` |

---

## 10. Interaction States

| State | Visual |
|---|---|
| Nav item hover | `background: #F8FAFC` |
| Nav item active | `background: #F5F1FF` + left accent bar |
| Table row hover | `background: #F8FAFC` |
| Action icon hover | color `#7033F5`, bg `#F5F1FF` |
| Button hover (primary) | `background: #5221CF` |
| Dropdown open | shadow `0 20px 25px -5px rgba(0,0,0,0.1)` |
| Modal/Drawer open | overlay + slide animation |
| Analyzing / Loading | spinner icon + muted text `#90A1B9` |

---

## 11. Design Principles

These explain why the rules exist — understanding them helps make better design decisions beyond what's listed here.

**`#7033F5` purple IS AdsGo:** The entire product identity is built around this specific purple. It is used for every primary action, every active state, every toggle, every focus ring. When a user sees `#7033F5`, they know "this is interactive / selected". Never substitute with blue, indigo, or any other purple shade for primary elements. The dark variant `#5221CF` is ONLY for hover/pressed states of elements already using `#7033F5`.

**Outfit everywhere:** The brand voice lives in the font. Every heading, every body text, every label, every button — all use Outfit. Mixing in system fonts, Inter, or any other font immediately breaks the AdsGo look. Always import Outfit from Google Fonts with weights 400, 500, 600, 700.

**Purple color hierarchy:**
- `#7033F5` → interactive elements (buttons, toggles, links, active indicators)
- `#F5F1FF` → active background (nav items, icon hover areas)
- `#EDE8FF` → active tab backgrounds, pending badges
- `#5E26D6` / `#501DC7` → purple text on light purple backgrounds
- `#5221CF` → hover/pressed states only

**Pill radius on buttons:** Pill-shaped buttons (`border-radius: 9999px`) give AdsGo its friendly, modern identity. Rectangular buttons look enterprise-generic and break the visual language.

**Light purple bg on active items (`#F5F1FF`):** This soft background + the accent bar form a two-signal active state — legible at a glance without being harsh.

**Trend colors (green/red):** Performance metrics always use green (`#00941E`) for positive, red (`#FB2C36`) for negative. Never use purple for trend indicators — purple is reserved for brand/navigation.

---

## 12. Building a New Page — Checklist

1. **Import Outfit font** from Google Fonts (weights 400, 500, 600, 700) and set as `font-family` on `*` or `body`
2. **Include CSS variables** from Section 4 — especially `--color-primary: #7033F5`
3. Read `references/layout.md` for the page shell (sidebar + header + content area)
4. Mark the correct sidebar nav item active (left bar `4px solid #7033F5` + bg `#F5F1FF`)
5. Use `#7033F5` (via `var(--color-primary)`) for all primary buttons, toggles, focus states, and active indicators
6. Add platform tabs if the page handles campaign/ad data (Meta / Google / TikTok)
7. Build the content using the relevant reference files
8. Map every text element to the typography scale in Section 2
9. Apply spacing from Section 9
10. Add hover + active states from Section 10 — button hover uses `#5221CF`
11. Handle all data states: loading, empty, error, demo, AI-pending (see `references/data-display.md`)
12. **Verify:** All buttons are pill-shaped (`border-radius: 9999px`), all text is Outfit, primary color is `#7033F5`

---

## 13. Page Catalog (Figma Verified)

| Page | Canvas | Components to use |
|---|---|---|
| Ads Manager / Performance Overview | Node 1 | Platform tabs, KPI cards, AI Analysis Panel, Campaign Table, SmartOptimizationConsole |
| Ads Manager / Campaign Table (Meta/Google/TikTok) | Node 1 | Platform tabs, Campaign Table expanded, Adset rows, pagination |
| Smart Optimization Console | Node 1 | Control Hub card (337×483, blue gradient), Mode toggles, Budget Allocation |
| Optimization Details Drawer | Node 1 | Full-screen overlay (1440×901), action items by type |
| Optimize Rules | Node 1 | Modal/basic (572×489–622), Rule list, Empty state |
| Brand Performance Goal | Node 1 | Business Goal dialog (447×400), vertical-form-item/select |
| Edit Budget | Node 1 | Dialog (450×387), radius 20px, shadow 0 1px 8px |
| Onboarding Guide (新手引导 1–4) | Node 1 | Step indicators, choice cards, primary + ghost buttons |
| AI Pending / Countdown | Node 1 | Countdown timer, timeline steps, purple container |
| Ads Regeneration / Recommended Publish | Node 2 | Campaign cards (radius 20px), audience cards (16px), hierarchy tree |
| Brand Center / Brand Info | Node 3 | Brand form, sidebar container (320×712, radius 20px), section cards |
| Brand Center / Products | Node 3 | Product listing table, Add product dialog (497×568–750×695) |
| Optimization Strategy | Node 3 | Section cards (radius 20px, stroke #F0F0F0), tree dropdown, form inputs |
| Feedback Dialog | Node 1 | 3 sizes (512×403/521/717), radius 14px, dual shadow |
| Delete Confirmation | Node 2 | Small dialog (400×204), radius 12px, button-group gap 8px |
