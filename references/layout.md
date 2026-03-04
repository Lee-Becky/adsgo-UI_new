# AdsGo Layout Reference (2026)

## Table of Contents

- [Full Page Shell (HTML)](#full-page-shell-html) — Complete HTML boilerplate with all CSS variables
- [Sidebar Internal Layout](#sidebar-internal-layout) — Logo, brand selector, nav, upgrade card
- [Header Internal Layout](#header-internal-layout) — Breadcrumbs, timezone pill, bell, user info
- [Content Layout Patterns](#content-layout-patterns) — Full-width card, two-column split, KPI row, stacked sections
- [Performance Overview Layout](#performance-overview-layout) — Platform tabs + KPI row + AI panel + Campaign table
- [Ads Manager Page with Drawer](#ads-manager-page-with-drawer)
- [Spacing System](#spacing-system)

---

## Full Page Shell (HTML)

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>AdsGo.ai</title>
  <link href="https://fonts.googleapis.com/css2?family=Outfit:wght@400;500;600;700&display=swap" rel="stylesheet" />
  <style>
    :root {
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
    * { box-sizing: border-box; margin: 0; padding: 0; }
    body { font-family: var(--font-main); background: #F9F9F9; }

    .app  { display: flex; min-height: 100vh; }
    .sidebar {
      width: 232px; flex-shrink: 0;
      background: var(--color-bg);
      border-right: 1px solid var(--color-border);
      position: fixed; top: 0; left: 0; height: 100vh;
      display: flex; flex-direction: column;
      z-index: 10;
    }
    .main   { margin-left: 232px; flex: 1; display: flex; flex-direction: column; min-height: 100vh; }
    .header {
      height: 64px;
      background: var(--color-bg);
      border-bottom: 1px solid var(--color-border);
      display: flex; align-items: center; justify-content: space-between;
      padding: 0 24px;
      position: sticky; top: 0; z-index: 9;
    }
    .content { padding: 24px; flex: 1; }
  </style>
</head>
<body>
  <div class="app">
    <aside class="sidebar">
      <!-- SIDEBAR CONTENT -->
    </aside>
    <div class="main">
      <header class="header">
        <!-- HEADER CONTENT -->
      </header>
      <main class="content">
        <!-- PAGE CONTENT -->
      </main>
    </div>
  </div>
</body>
</html>
```

---

## Sidebar Internal Layout

```
┌────────────────────────────────┐  ← 232px wide
│  Logo area          68px tall  │
│  [logo]       [collapse icon]  │
├────────────────────────────────┤
│  Brand selector     54px tall  │
│  [avatar] Nike      [chevron]  │
│            Growth Plan         │
├────────────────────────────────┤  ← top: 134px
│  Nav section                   │
│  padding: 8px 12px; gap: 4px   │
│  ┌─────────────────────────┐   │
│  │[bar][icon] Ads Manager  │   │  ← active
│  └─────────────────────────┘   │
│  [icon] AI Optimize  [chevron] │
│    └── Smart Rules             │  ← sub-item
│  [icon] Creative Hub [chevron] │
│  [icon] Analytics   [chevron]  │
│  [icon] Brand Center[chevron]  │
├────────────────────────────────┤  ← bottom
│  Upgrade card  208px wide      │
│  Help Center row               │
└────────────────────────────────┘
```

```css
.sidebar-logo {
  height: 68px;
  display: flex; align-items: center;
  padding: 0 16px;
  border-bottom: 1px solid var(--color-border);
}
.sidebar-brand {
  height: 54px;
  display: flex; align-items: center;
  padding: 0 12px; gap: 10px;
  margin: 8px 12px;
  border-radius: 14px;
  cursor: pointer;
}
.sidebar-brand:hover { background: var(--color-bg-soft); }
.sidebar-nav {
  flex: 1;
  padding: 8px 12px;
  display: flex; flex-direction: column; gap: 4px;
  overflow-y: auto;
}
.sidebar-bottom {
  padding: 12px;
  border-top: 1px solid var(--color-border);
}
```

---

## Header Internal Layout

```
[Ads Manager > Performance Overview]      [GMT-5] [🌐] [🔔🔴] | [John Doe / john@co.com] [avatar]
```

```css
.header-left {
  display: flex; align-items: center; gap: 8px;
}
.breadcrumb-parent {
  font-size: 14px; font-weight: 400; color: var(--color-text-muted);
}
.breadcrumb-sep {
  font-size: 14px; color: var(--color-text-placeholder);
}
.breadcrumb-current {
  font-size: 14px; font-weight: 500; color: #404040;
}

.header-right {
  display: flex; align-items: center; gap: 16px;
}
.timezone-pill {
  display: flex; align-items: center; gap: 6px;
  height: 30px; padding: 0 12px;
  border-radius: 9999px;
  border: 1px solid var(--color-border);
  background: var(--color-bg-soft);
  font-size: 12px; font-weight: 500; color: var(--color-text-muted);
}
.header-icon-btn {
  width: 32px; height: 32px;
  border-radius: 50%;
  display: flex; align-items: center; justify-content: center;
  background: transparent;
  border: none; cursor: pointer;
  color: var(--color-text-muted);
  position: relative;
}
.notif-dot {
  width: 8px; height: 8px;
  background: var(--color-danger);
  border-radius: 50%;
  border: 2px solid white;
  position: absolute; top: 2px; right: 2px;
}
.header-sep {
  width: 1px; height: 32px;
  background: var(--color-border-medium);
}
.user-info {
  display: flex; flex-direction: column; align-items: flex-end;
}
.user-name  { font-size: 14px; font-weight: 500; color: var(--color-text-main); }
.user-email { font-size: 12px; font-weight: 400; color: var(--color-text-placeholder); }
```

---

## Content Layout Patterns

### Full-width Card (single section)
```css
.content-card {
  background: var(--color-bg);
  border: 1px solid var(--color-border);
  border-radius: 16px;
  padding: 20px;
}
```

### Two-column Split (main + side panel)
```css
.content-split {
  display: grid;
  grid-template-columns: 1fr 420px;
  gap: 20px;
  align-items: start;
}
```

### Three-column KPI Row
```css
.kpi-row {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 16px;
  margin-bottom: 20px;
}
```

### Stacked Sections
```css
.page-stack {
  display: flex;
  flex-direction: column;
  gap: 20px;
}
```

---

## Performance Overview Layout

```
┌────────────────────────────────────────────────────────────┐
│  [Platform tabs: Meta | Google | TikTok]   [Date picker]  │
└────────────────────────────────────────────────────────────┘

┌──────────┐ ┌──────────┐ ┌──────────┐ ┌──────────┐
│  Spend   │ │ Purchase │ │   CPA    │ │   ROAS   │
│ $5,860   │ │   270    │ │  $22.8   │ │  4.62x   │
│ ↓ 1.72% │ │ ↑10.23% │ │ ↑ 4.62%  │ │ ↑12.68%  │
└──────────┘ └──────────┘ └──────────┘ └──────────┘

┌──────────────────────────────┐ ┌───────────────────────────┐
│  AI Analysis Insights         │ │  Smart Optimization       │
│  Key Highlight ✓              │ │  Console                  │
│  Potential Risk ⚠             │ │  Budget Allocation        │
│  Budget Optimization →        │ │  Daily Analysis toggles   │
└──────────────────────────────┘ └───────────────────────────┘

┌──────────────────────────────────────────────────────────────┐
│  Campaign Table                              [Search] [Filter]│
│  ┌─────────────────────────────────────────────────────────┐ │
│  │ # │ Campaign              │ Budget │ Spend │ CPA │ ROAS  │ │
│  │───│───────────────────────│────────│───────│─────│───── │ │
│  │ ✓ │ 🔵 Nike Retargeting   │ $500   │$237   │$22  │ 4.5x │ │
│  │   │   AI Generated        │        │       │     │      │ │
│  └─────────────────────────────────────────────────────────┘ │
└──────────────────────────────────────────────────────────────┘
```

---

## Ads Manager Page with Drawer

When drawer is open:
```css
/* Main content dims slightly */
.main.drawer-open .content { pointer-events: none; }
/* Drawer slides in from right over the content */
```

---

## Spacing System

| Use | Value |
|---|---|
| Page padding | `24px` |
| Between page sections | `20px` |
| Within a card | `16px` or `20px` |
| Between nav items | `4px` |
| Between table rows | border only (`1px solid #F1F5F9`) |
| Between KPI cards | `16px` |
| Between header items | `16px` or `24px` |
| Icon to label gap (nav) | `12px` |
| Icon to label gap (other) | `6px–8px` |
| Form items vertical gap | `16px` |
| Button group gap | `8px–12px` |
| Drawer padding | `24px` |
| Modal padding | `20px 24px` |
