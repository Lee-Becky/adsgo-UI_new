# AdsGo Component Reference (2026)

## Table of Contents

- [CSS Variables](#css-variables)
- [Button Variants](#button-variants) — Primary, Outline, Ghost, Icon, Small
- [Tag / Badge Variants](#tag--badge-variants) — Status tags, Rank, AI Generated, Plan, Coming Soon
- [Toggle Switch](#toggle-switch)
- [Input & Form Elements](#input--form-elements) — Text input, Search, Date picker, Select, Vertical form item
- [Tooltip](#tooltip)
- [Dropdown Menu](#dropdown-menu)
- [Modal](#modal)
- [Alert Components](#alert-components) — Inline banner, Toast notification
- [Platform Tab Bar](#platform-tab-bar)
- [Avatar](#avatar)
- [Sidebar Nav Item](#sidebar-nav-item) — Main nav, Sub-menu
- [Card Container](#card-container)
- [Empty State](#empty-state)
- [Optimization Details Drawer](#optimization-details-drawer)
- [Upgrade Card](#upgrade-card)

---

## CSS Variables (always include)

```css
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
```

---

## Button Variants

### Primary Button (Pill)
```css
.btn-primary {
  background: var(--color-primary);
  color: #FFFFFF;
  border: none;
  border-radius: 9999px;
  padding: 0 20px;
  height: 36px;
  font-family: var(--font-main);
  font-size: 14px;
  font-weight: 500;
  cursor: pointer;
  display: inline-flex;
  align-items: center;
  gap: 6px;
  transition: background 0.2s;
}
.btn-primary:hover { background: var(--color-primary-dark); }
```

### Secondary / Outline Button
```css
.btn-outline {
  background: transparent;
  color: var(--color-primary-text-dark);
  border: 1px solid #6424EF;
  border-radius: 9999px;
  padding: 0 16px;
  height: 36px;
  font-size: 14px;
  font-weight: 500;
  display: inline-flex;
  align-items: center;
  gap: 6px;
  cursor: pointer;
  transition: background 0.2s;
}
.btn-outline:hover { background: var(--color-primary-bg); }
```

### Ghost / Text Button
```css
.btn-ghost {
  background: transparent;
  color: var(--color-text-muted);
  border: 1px solid var(--color-border-medium);
  border-radius: 9999px;
  padding: 0 16px;
  height: 36px;
  font-size: 14px;
  font-weight: 400;
  cursor: pointer;
  display: inline-flex;
  align-items: center;
  gap: 6px;
}
.btn-ghost:hover { border-color: var(--color-primary); color: var(--color-primary); }
```

### Icon Button (Table Actions)
```css
.btn-icon {
  width: 32px; height: 32px;
  border-radius: 8px;
  border: none;
  background: transparent;
  color: var(--color-text-placeholder);
  display: flex; align-items: center; justify-content: center;
  cursor: pointer;
  transition: all 0.15s;
}
.btn-icon:hover { color: var(--color-primary); background: var(--color-primary-bg); }
```

### Small Action Button (inline)
```css
.btn-sm {
  height: 28px;
  padding: 0 12px;
  border-radius: 9999px;
  font-size: 12px;
  font-weight: 500;
}
```

---

## Tag / Badge Variants

### Status Tags
```css
/* Active / Running — Figma: #E1FAE1 bg, 25px radius, 1px 8px padding */
.tag-active {
  display: inline-flex; align-items: center;
  background: var(--color-success-bg);
  color: var(--color-success);
  font-size: 12px; font-weight: 500;
  padding: 1px 8px;
  border-radius: 25px;
}

/* Warning / Paused — Figma: #FFF5E6 bg */
.tag-paused {
  background: var(--color-warning-bg);
  color: var(--color-warning);
  font-size: 12px; font-weight: 500;
  padding: 1px 8px;
  border-radius: 25px;
}

/* Inactive / Default — Figma: #F5F5F5 bg, 20px radius */
.tag-inactive {
  background: #F5F5F5;
  color: var(--color-text-muted);
  font-size: 12px; font-weight: 500;
  padding: 1px 8px;
  border-radius: 20px;
}

/* Pending */
.tag-pending {
  background: var(--color-primary-bg);
  color: var(--color-primary-text);
  font-size: 12px; font-weight: 500;
  padding: 1px 8px;
  border-radius: 25px;
}

/* AI Generated */
.tag-ai {
  display: inline-flex; align-items: center; gap: 4px;
  color: var(--color-primary);
  font-size: 12px; font-weight: 500;
}

/* E-commerce tag */
.tag-ec {
  background: #EFF6FF;
  color: #1D4ED8;
  font-size: 12px; font-weight: 500;
  padding: 2px 10px;
  border-radius: 9999px;
}
```

### Rank Badge
```css
.rank-badge {
  background: var(--color-primary);
  color: white;
  font-size: 10px; font-weight: 600;
  padding: 2px 6px;
  border-radius: 4px;
  letter-spacing: 0.5px;
}
```

### Plan Badge
```css
.badge-plan {
  font-size: 12px; font-weight: 400;
  color: var(--color-text-placeholder);
}
```

### Coming Soon Badge
```css
.badge-coming-soon {
  background: var(--color-bg-soft);
  color: var(--color-text-muted);
  font-size: 10px; font-weight: 500;
  padding: 2px 8px;
  border-radius: 9999px;
  border: 1px solid var(--color-border);
}
```

---

## Toggle Switch

```html
<label class="toggle">
  <input type="checkbox" />
  <span class="toggle-track"></span>
</label>
```

```css
.toggle { position: relative; display: inline-block; width: 36px; height: 20px; flex-shrink: 0; }
.toggle input { opacity: 0; width: 0; height: 0; }
.toggle-track {
  position: absolute; inset: 0;
  background: #CBD5E1;
  border-radius: 9999px;
  transition: background 0.2s;
  cursor: pointer;
}
.toggle-track::after {
  content: '';
  position: absolute;
  width: 16px; height: 16px;
  border-radius: 50%;
  background: white;
  top: 2px; left: 2px;
  transition: transform 0.2s;
  box-shadow: 0 1px 3px rgba(0,0,0,0.2);
}
.toggle input:checked + .toggle-track { background: var(--color-primary); }
.toggle input:checked + .toggle-track::after { transform: translateX(16px); }
```

---

## Input & Form Elements

### Text Input
```css
.input {
  height: 36px;
  border: 1px solid var(--color-border-medium);
  border-radius: 8px;
  padding: 0 12px;
  font-family: var(--font-main);
  font-size: 14px;
  color: var(--color-text-dark);
  background: var(--color-bg);
  outline: none;
  transition: border-color 0.2s, box-shadow 0.2s;
  width: 100%;
}
.input::placeholder { color: var(--color-text-placeholder); }
.input:focus {
  border-color: var(--color-primary);
  box-shadow: 0 0 0 3px rgba(112, 51, 245, 0.1);
}
```

### Search Input
```html
<div class="search-input-wrap">
  <svg class="search-icon"><!-- 12×12 search svg --></svg>
  <input type="text" class="input search-input" placeholder="Search Campaign..." />
</div>
```
```css
.search-input-wrap { position: relative; }
.search-icon { position: absolute; left: 10px; top: 50%; transform: translateY(-50%); width: 12px; height: 12px; color: var(--color-text-muted); pointer-events: none; }
.search-input { padding-left: 30px; }
```

### Date Picker Trigger
```css
.date-picker-trigger {
  display: inline-flex; align-items: center; gap: 6px;
  height: 32px;
  padding: 0 12px;
  border-radius: 9999px;
  border: 1px solid var(--color-border);
  background: var(--color-bg-soft);
  font-size: 12px; font-weight: 500; color: var(--color-text-muted);
  cursor: pointer;
}
```

### Select Dropdown
```css
.select {
  height: 36px;
  border: 1px solid var(--color-border-medium);
  border-radius: 8px;
  padding: 0 32px 0 12px;
  font-family: var(--font-main);
  font-size: 14px;
  color: var(--color-text-dark);
  background: var(--color-bg) url("data:image/svg+xml,...") no-repeat right 10px center;
  appearance: none;
  outline: none;
}
```

### Vertical Form Item
```html
<div class="form-item">
  <label class="form-label">Brand</label>
  <select class="select">...</select>
</div>
```
```css
.form-item { display: flex; flex-direction: column; gap: 6px; }
.form-label { font-size: 13px; font-weight: 500; color: var(--color-text-body); }
```

---

## Tooltip

```html
<div class="tooltip-wrap">
  <button>Hover me</button>
  <div class="tooltip">
    Run AI analysis instantly
    <div class="tooltip-beak"></div>
  </div>
</div>
```

```css
.tooltip-wrap { position: relative; display: inline-block; }
/* Figma: dark tooltip uses rgba(0,0,0,0.65) bg, radius 24px, pad 6px 16px
   Also has a light variant with white bg + shadow 0 2px 8px rgba(0,0,0,0.15) */
.tooltip {
  position: absolute;
  bottom: calc(100% + 8px);
  left: 50%; transform: translateX(-50%);
  background: rgba(0, 0, 0, 0.65);
  color: #FFFFFF;
  font-size: 12px; font-weight: 400;
  padding: 6px 16px;
  border-radius: 24px;
  white-space: nowrap;
  max-width: 240px;
  pointer-events: none;
  z-index: 30;
}
/* Light tooltip variant */
.tooltip-light {
  background: var(--color-bg);
  color: var(--color-text-body);
  box-shadow: 0 2px 8px rgba(0,0,0,0.15);
  border-radius: 8px;
  padding: 8px 12px;
}
.tooltip-beak {
  position: absolute;
  top: 100%; left: 50%; transform: translateX(-50%);
  border: 5px solid transparent;
  border-top-color: #1D293D;
}
```

---

## Dropdown Menu

```html
<div class="dropdown-menu">
  <div class="dropdown-item">
    <svg class="dropdown-icon">...</svg>
    <span>Edit</span>
  </div>
  <div class="dropdown-divider"></div>
  <div class="dropdown-item danger">
    <svg class="dropdown-icon">...</svg>
    <span>Delete</span>
  </div>
</div>
```

```css
.dropdown-menu {
  background: var(--color-bg);
  border: 1px solid var(--color-border);
  border-radius: 12px;
  box-shadow: 0 8px 24px rgba(0,0,0,0.1);
  padding: 6px;
  min-width: 160px;
  z-index: 20;
}
.dropdown-item {
  display: flex; align-items: center; gap: 10px;
  height: 40px; padding: 0 12px;
  border-radius: 8px;
  font-size: 14px; font-weight: 400; color: var(--color-text-dark);
  cursor: pointer;
  transition: background 0.15s;
}
.dropdown-item:hover { background: var(--color-primary-bg); }
.dropdown-item.danger { color: var(--color-danger); }
.dropdown-item.danger:hover { background: #FEF2F2; }
.dropdown-icon { width: 16px; height: 16px; color: var(--color-text-muted); }
.dropdown-divider { height: 1px; background: var(--color-border); margin: 4px 0; }
```

---

## Modal

```html
<div class="modal-overlay">
  <div class="modal">
    <div class="modal-header">
      <span class="modal-title">Optimize Rules</span>
      <button class="btn-icon modal-close">✕</button>
    </div>
    <div class="modal-divider"></div>
    <div class="modal-body">
      <!-- content -->
    </div>
    <div class="modal-divider"></div>
    <div class="modal-footer">
      <button class="btn-ghost">Cancel</button>
      <button class="btn-primary">Confirm</button>
    </div>
  </div>
</div>
```

```css
/* Figma: overlay rgba(0,0,0,0.50), modal radius 20px, shadow 0 6px 20px */
.modal-overlay {
  position: fixed; inset: 0;
  background: rgba(0, 0, 0, 0.50);
  display: flex; align-items: center; justify-content: center;
  z-index: 40;
}
.modal {
  background: var(--color-bg);
  border-radius: 20px;
  width: 560px;
  max-height: 80vh;
  display: flex; flex-direction: column;
  box-shadow: 0 6px 20px rgba(0,0,0,0.15);
  animation: modal-in 0.2s ease;
}
@keyframes modal-in {
  from { opacity: 0; transform: translateY(10px) scale(0.98); }
  to   { opacity: 1; transform: translateY(0) scale(1); }
}
/* Figma: header 68px, border-bottom #EAEAEA, body pad 20/24, footer pad ?/24 gap 12 */
.modal-header {
  display: flex; align-items: center; justify-content: space-between;
  padding: 20px 24px;
  height: 68px;
}
.modal-title { font-size: 16px; font-weight: 600; color: var(--color-text-dark); }
.modal-divider { height: 1px; background: #EAEAEA; }
.modal-body { padding: 20px 24px; overflow-y: auto; flex: 1; }
.modal-footer {
  padding: 16px 24px;
  display: flex; justify-content: flex-end; gap: 12px;
}
```

---

## Alert Components

### Inline Alert Banner
```css
.alert {
  display: flex; align-items: flex-start; gap: 12px;
  padding: 14px 16px;
  border-radius: 12px;
  font-size: 14px;
  line-height: 20px;
}
.alert-error   { background: #FEF2F2; border: 1px solid #FECACA; color: #991B1B; }
.alert-warning { background: var(--color-warning-bg); border: 1px solid #FCD34D; color: #92400E; }
.alert-info    { background: #EFF6FF; border: 1px solid #BFDBFE; color: #1E40AF; }
.alert-icon    { width: 18px; height: 18px; flex-shrink: 0; margin-top: 1px; }
```

### Toast Notification
```css
.toast {
  position: fixed; top: 20px; right: 20px;
  background: var(--color-bg);
  border-radius: 12px;
  border-left: 4px solid var(--color-primary);
  box-shadow: 0 4px 24px rgba(0,0,0,0.12);
  width: 360px;
  padding: 16px;
  display: flex; align-items: flex-start; gap: 12px;
  z-index: 50;
  animation: toast-in 0.25s ease;
}
@keyframes toast-in {
  from { opacity: 0; transform: translateX(20px); }
  to   { opacity: 1; transform: translateX(0); }
}
.toast-title   { font-size: 14px; font-weight: 600; color: var(--color-text-dark); }
.toast-body    { font-size: 13px; color: var(--color-text-body); margin-top: 2px; }
.toast-close   { margin-left: auto; color: var(--color-text-placeholder); cursor: pointer; }
```

---

## Platform Tab Bar

```html
<div class="platform-tabs">
  <button class="platform-tab active">
    <img src="meta.svg" class="tab-icon" /> Meta
  </button>
  <button class="platform-tab">
    <img src="google.svg" class="tab-icon" /> Google
  </button>
  <button class="platform-tab">
    <img src="tiktok.svg" class="tab-icon" /> TikTok
  </button>
</div>
```

```css
.platform-tabs { display: flex; gap: 8px; }
.platform-tab {
  display: inline-flex; align-items: center; gap: 8px;
  height: 36px; padding: 0 16px;
  border-radius: 9999px;
  border: 1px solid transparent;
  font-family: var(--font-main);
  font-size: 14px; font-weight: 500;
  color: var(--color-text-muted);
  background: transparent;
  cursor: pointer;
  transition: all 0.15s;
}
.platform-tab.active {
  background: var(--color-primary-bg-mid);
  border-color: #D4C5FA;
  color: #5221CF;
}
.platform-tab:hover:not(.active) { background: var(--color-bg-soft); }
.tab-icon { width: 16px; height: 16px; object-fit: contain; }
```

---

## Avatar

```css
.avatar {
  width: 40px; height: 40px;
  border-radius: 50%;
  border: 1.25px solid #FFFFFF;
  filter: drop-shadow(0px 1px 7.2px rgba(0,0,0,0.21));
  object-fit: cover;
}
.avatar-brand {
  width: 32px; height: 32px;
  border-radius: 50%;
  box-shadow: 0 0 0 2px var(--color-border);
  display: flex; align-items: center; justify-content: center;
  font-size: 12px; font-weight: 600; color: white;
}
```

---

## Sidebar Nav Item

```html
<div class="nav-item active">
  <div class="nav-accent"></div>
  <svg class="nav-icon"><!-- 18×18 icon --></svg>
  <span class="nav-label">Ads Manager</span>
</div>
```

```css
.nav-item {
  display: flex; align-items: center;
  width: 100%; height: 48px;
  border-radius: 10px;
  padding: 0 12px;
  gap: 12px;
  cursor: pointer;
  position: relative;
  transition: background 0.15s;
}
.nav-accent {
  display: none;
  width: 4px; height: 32px;
  background: var(--color-primary);
  border-radius: 0 9999px 9999px 0;
  position: absolute; left: 0;
}
.nav-item.active { background: var(--color-primary-bg); }
.nav-item.active .nav-accent { display: block; }
.nav-item.active .nav-label { color: var(--color-primary-text); font-weight: 500; }
.nav-item.active .nav-icon { color: var(--color-primary); }
.nav-label { font-size: 14px; font-weight: 500; color: var(--color-text-body); }
.nav-icon { width: 18px; height: 18px; color: var(--color-text-placeholder); flex-shrink: 0; }
.nav-item:hover:not(.active) { background: var(--color-bg-soft); }
```

### Sub-menu item
```css
.nav-sub-item {
  display: flex; align-items: center;
  height: 40px; padding: 0 12px 0 42px;
  border-radius: 10px;
  font-size: 13px; font-weight: 400; color: var(--color-text-body);
  cursor: pointer;
  transition: background 0.15s;
}
.nav-sub-item.active {
  background: var(--color-primary-bg);
  color: var(--color-primary-text);
  font-weight: 500;
}
```

---

## Card Container

```css
.card {
  background: var(--color-bg);
  border: 1px solid var(--color-border);
  border-radius: 12px;
  padding: 16px;
}
.card-lg { border-radius: 16px; padding: 20px; }
```

---

## Empty State

```html
<div class="empty-state">
  <img src="empty-simple.svg" class="empty-img" />
  <div class="empty-title">No customize rules yet</div>
  <div class="empty-sub">Add new optimization rules that you want...</div>
  <button class="btn-primary">+ Add Rule</button>
</div>
```

```css
.empty-state {
  display: flex; flex-direction: column; align-items: center;
  padding: 48px 24px; gap: 12px; text-align: center;
}
.empty-img { width: 120px; height: 90px; opacity: 0.7; }
.empty-title { font-size: 16px; font-weight: 500; color: var(--color-text-dark); }
.empty-sub   { font-size: 14px; color: var(--color-text-placeholder); max-width: 280px; }
```

---

## Optimization Details Drawer

```html
<div class="drawer-overlay">
  <div class="drawer">
    <div class="drawer-header">
      <span class="drawer-title">Optimization Details</span>
      <button class="btn-icon">✕</button>
    </div>
    <!-- sections -->
  </div>
</div>
```

```css
.drawer-overlay {
  position: fixed; inset: 0;
  background: rgba(0,0,0,0.3);
  z-index: 40;
  display: flex; justify-content: flex-end;
}
.drawer {
  width: 480px; height: 100vh;
  background: var(--color-bg);
  border-radius: 16px 0 0 16px;
  display: flex; flex-direction: column;
  box-shadow: -4px 0 24px rgba(0,0,0,0.08);
  animation: drawer-in 0.25s ease;
}
@keyframes drawer-in {
  from { transform: translateX(100%); }
  to   { transform: translateX(0); }
}
.drawer-header {
  display: flex; align-items: center; justify-content: space-between;
  padding: 20px 24px;
  border-bottom: 1px solid var(--color-border);
}
.drawer-title { font-size: 16px; font-weight: 600; color: var(--color-text-dark); }
```

---

## Upgrade Card (bottom of sidebar)

```css
.upgrade-card {
  width: 208px;
  background: var(--color-primary-bg-soft);
  border-radius: 10px;
  padding: 16px;
  position: relative;
  overflow: hidden;
}
.upgrade-card-title {
  font-size: 14px; font-weight: 500; color: #5B5E6F;
  line-height: 20px;
}
.upgrade-card-body {
  font-size: 12px; color: #595959;
  opacity: 0.8; margin: 8px 0;
}
```
