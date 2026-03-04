# AdsGo Data Display Reference (2026)

## Table of Contents

- [KPI Metric Card](#kpi-metric-card) — Individual metric with trend pill
- [Today's Stats Row](#todays-stats-row) — 4-metric horizontal bar
- [Campaign Table (Ads Manager)](#campaign-table-ads-manager) — Full table with toolbar, columns, expanded adset rows
- [Pagination](#pagination)
- [Status Display](#status-display) — Demo banner, Processing state, AI Pending state
- [Real-time Recommendations Row](#real-time-recommendations-row)
- [Delivery Issues Alert](#delivery-issues-alert)

---

## KPI Metric Card

Individual performance metric with trend indicator.

```html
<div class="kpi-card">
  <div class="kpi-header">
    <span class="kpi-label">SPEND</span>
    <div class="kpi-trend kpi-trend--down">
      <svg><!-- trending-down icon --></svg>
      1.72%
    </div>
  </div>
  <div class="kpi-value">$5,860</div>
</div>
```

```css
.kpi-card {
  background: var(--color-bg);
  border: 1px solid var(--color-border);
  border-radius: 12px;
  padding: 16px 20px;
  display: flex; flex-direction: column; gap: 6px;
}
.kpi-header {
  display: flex; align-items: center; justify-content: space-between;
}
.kpi-label {
  font-size: 11px; font-weight: 600;
  color: var(--color-text-placeholder);
  text-transform: uppercase;
  letter-spacing: 0.8px;
}
.kpi-value {
  font-size: 28px; font-weight: 700;
  color: var(--color-text-dark);
  line-height: 1.1;
}
.kpi-trend {
  display: inline-flex; align-items: center; gap: 3px;
  font-size: 12px; font-weight: 500;
  padding: 2px 8px;
  border-radius: 9999px;
}
/* Figma: success green #00941E on #E1FAE1, warning orange #FF8E2B on #FFF5E6 */
.kpi-trend--up   { background: var(--color-success-bg); color: var(--color-success); }
.kpi-trend--down { background: var(--color-danger-bg); color: var(--color-danger); }
.kpi-trend svg   { width: 12px; height: 12px; }
```

---

## Today's Stats Row

Quick snapshot of today's performance.

```html
<div class="stats-today">
  <div class="stat-item">
    <div class="stat-label">Today Spend</div>
    <div class="stat-value">$3,070</div>
  </div>
  <div class="stat-sep"></div>
  <div class="stat-item">
    <div class="stat-label">Today Revenue</div>
    <div class="stat-value">$6,800
      <span class="stat-badge stat-badge--up">+12.5%</span>
    </div>
  </div>
  <div class="stat-sep"></div>
  <div class="stat-item">
    <div class="stat-label">Avg. ROAS</div>
    <div class="stat-value">2.82x</div>
  </div>
  <div class="stat-sep"></div>
  <div class="stat-item">
    <div class="stat-label">Conversions</div>
    <div class="stat-value">186</div>
  </div>
</div>
```

```css
.stats-today {
  display: flex; align-items: center; gap: 0;
  background: var(--color-bg);
  border: 1px solid var(--color-border);
  border-radius: 12px;
  padding: 16px 20px;
}
.stat-item {
  flex: 1;
  display: flex; flex-direction: column; gap: 4px;
}
.stat-label {
  font-size: 11px; font-weight: 600;
  text-transform: uppercase; letter-spacing: 0.6px;
  color: var(--color-text-placeholder);
}
.stat-value {
  font-size: 20px; font-weight: 700;
  color: var(--color-text-dark);
  display: flex; align-items: center; gap: 8px;
}
.stat-badge {
  font-size: 12px; font-weight: 500;
  padding: 1px 6px; border-radius: 9999px;
}
.stat-badge--up   { background: var(--color-success-bg); color: var(--color-success); }
.stat-badge--down { background: var(--color-danger-bg); color: var(--color-danger); }
.stat-sep {
  width: 1px; height: 36px;
  background: var(--color-border-medium);
  margin: 0 20px; flex-shrink: 0;
}
```

---

## Campaign Table (Ads Manager)

Full-featured table with status, metrics, and expandable adsets.

```html
<div class="table-card">
  <!-- toolbar -->
  <div class="table-toolbar">
    <div class="table-title">
      <span class="campaign-count">5/6 Active</span>
    </div>
    <div class="table-actions">
      <div class="search-input-wrap">
        <input type="text" placeholder="Search Campaign..." class="input search-input" />
      </div>
      <button class="btn-ghost">Campaign Status ▾</button>
      <button class="btn-ghost">Platform ▾</button>
      <button class="date-picker-trigger">📅 Jan 1–Jan 31</button>
      <button class="btn-primary">+ New Campaign</button>
    </div>
  </div>

  <!-- table -->
  <table class="ads-table">
    <thead>
      <tr>
        <th class="col-switch">Switch</th>
        <th class="col-campaign">Campaign</th>
        <th>Daily Budget</th>
        <th>Spend</th>
        <th>CPA</th>
        <th>ROAS</th>
        <th>Actions</th>
      </tr>
    </thead>
    <tbody>
      <!-- Campaign row -->
      <tr class="campaign-row">
        <td class="col-switch">
          <label class="toggle"><input type="checkbox" checked /><span class="toggle-track"></span></label>
        </td>
        <td class="col-campaign">
          <div class="campaign-cell">
            <div class="platform-icon-wrap">
              <img src="google.svg" class="platform-icon-sm" />
            </div>
            <div class="campaign-info">
              <div class="tag-ai">✦ AI Generated</div>
              <div class="campaign-name">Nike Retargeting | Purchase</div>
              <div class="campaign-sub">15/10 Active</div>
            </div>
          </div>
        </td>
        <td>$500</td>
        <td>$237.00</td>
        <td>$22.8</td>
        <td>4.62x</td>
        <td class="actions-cell">
          <button class="btn-icon" title="Edit">✏</button>
          <button class="btn-icon" title="Send">↗</button>
          <button class="btn-icon" title="Delete">🗑</button>
        </td>
      </tr>
    </tbody>
  </table>
</div>
```

```css
.table-card {
  background: var(--color-bg);
  border: 1px solid var(--color-border);
  border-radius: 16px;
  overflow: hidden;
}

/* Toolbar */
.table-toolbar {
  display: flex; align-items: center; justify-content: space-between;
  padding: 12px 16px;
  border-bottom: 1px solid var(--color-border);
  gap: 12px;
}
.table-actions { display: flex; align-items: center; gap: 8px; }
.campaign-count {
  font-size: 14px; font-weight: 500; color: var(--color-text-body);
}

/* Table base */
.ads-table {
  width: 100%; border-collapse: collapse;
}
.ads-table thead th {
  background: var(--color-bg-soft);
  padding: 12px 12px;
  font-size: 12px; font-weight: 500; color: var(--color-text-body);
  text-transform: uppercase; letter-spacing: 0.5px;
  text-align: left;
  border-bottom: 1px solid var(--color-border);
  white-space: nowrap;
}
.ads-table tbody tr {
  border-bottom: 1px solid var(--color-border);
  transition: background 0.15s;
}
.ads-table tbody tr:hover { background: var(--color-bg-soft); }
.ads-table td {
  padding: 12px;
  font-size: 14px; color: var(--color-text-dark);
  vertical-align: middle;
}

/* Column sizes */
.col-switch   { width: 78px; }
.col-campaign { min-width: 242px; }

/* Campaign cell */
.campaign-cell {
  display: flex; align-items: flex-start; gap: 10px;
}
.platform-icon-wrap {
  width: 29px; height: 28px;
  border-radius: 6px;
  background: var(--color-bg-soft);
  display: flex; align-items: center; justify-content: center;
  flex-shrink: 0;
}
.platform-icon-sm { width: 18px; height: 18px; object-fit: contain; }
.campaign-info { display: flex; flex-direction: column; gap: 2px; }
.campaign-name { font-size: 14px; font-weight: 500; color: var(--color-text-dark); }
.campaign-sub  { font-size: 12px; color: var(--color-text-placeholder); }
.tag-ai {
  display: inline-flex; align-items: center; gap: 4px;
  font-size: 12px; font-weight: 500; color: var(--color-primary);
}

/* Actions */
.actions-cell { display: flex; gap: 4px; align-items: center; }

/* Analyzing state */
.analyzing-label {
  display: flex; align-items: center; gap: 6px;
  font-size: 12px; color: var(--color-text-placeholder);
}
@keyframes spin { to { transform: rotate(360deg); } }
.spinner { width: 14px; height: 14px; animation: spin 1s linear infinite; }
```

### Expanded Adset Row
```css
.adset-row {
  background: var(--color-bg-soft);
  border-bottom: 1px solid var(--color-border);
}
.adset-row td {
  padding: 10px 12px 10px 54px; /* indent */
  font-size: 13px; color: var(--color-text-body);
}
.adset-name { font-weight: 500; color: var(--color-text-dark); }
.adset-audience { font-size: 12px; color: var(--color-text-muted); }
```

---

## Pagination

```html
<div class="pagination">
  <span class="pag-total">Total 85 items</span>
  <div class="pag-pages">
    <button class="pag-btn">‹</button>
    <button class="pag-btn active">1</button>
    <button class="pag-btn">2</button>
    <span class="pag-ellipsis">…</span>
    <button class="pag-btn">10</button>
    <button class="pag-btn">›</button>
  </div>
  <select class="pag-size"><option>10 / page</option></select>
  <span class="pag-goto">Go to <input type="number" class="pag-input" /></span>
</div>
```

```css
.pagination {
  display: flex; align-items: center; gap: 8px;
  padding: 14px 16px;
  border-top: 1px solid var(--color-border);
  font-size: 14px;
}
.pag-total { color: var(--color-text-muted); margin-right: 4px; }
.pag-pages { display: flex; gap: 4px; }
.pag-btn {
  width: 32px; height: 32px;
  border-radius: 8px;
  border: 1px solid transparent;
  background: transparent;
  font-family: var(--font-main); font-size: 14px;
  color: var(--color-text-body);
  cursor: pointer; display: flex; align-items: center; justify-content: center;
  transition: all 0.15s;
}
.pag-btn:hover:not(.active) { background: var(--color-bg-soft); border-color: var(--color-border); }
.pag-btn.active { background: var(--color-primary); color: white; }
.pag-ellipsis { color: var(--color-text-placeholder); padding: 0 4px; line-height: 32px; }
.pag-size {
  border: 1px solid var(--color-border-medium); border-radius: 6px;
  height: 32px; padding: 0 8px;
  font-family: var(--font-main); font-size: 13px;
  color: var(--color-text-body);
}
.pag-goto { color: var(--color-text-muted); display: flex; align-items: center; gap: 6px; }
.pag-input {
  width: 48px; height: 32px;
  border: 1px solid var(--color-border-medium); border-radius: 6px;
  text-align: center; font-family: var(--font-main);
}
```

---

## Status Display

### Data State Banners

```html
<!-- Demo mode banner -->
<div class="demo-banner">
  <svg class="demo-icon"><!-- info icon --></svg>
  Demo data only. Link your ad account to unlock detailed performance insights.
  <button class="btn-primary btn-sm">Connect Account</button>
  <button class="btn-icon demo-close">✕</button>
</div>

<!-- Processing state -->
<div class="state-processing">
  <svg class="spinner"><!-- loop icon --></svg>
  <div>
    <div class="state-title">Data Processing in Progress...</div>
    <div class="state-sub">Retrieving and analyzing the latest data, please refresh the page later to view.</div>
  </div>
</div>

<!-- AI pending state -->
<div class="state-ai-pending">
  <svg class="lock-icon"><!-- lock icon --></svg>
  <div>
    <div class="state-title">AI Analysis Pending</div>
    <div class="state-countdown">06h 06m remaining</div>
    <div class="state-sub">Your campaign was launched today. The first AI analysis will run at 24:00.</div>
  </div>
</div>
```

```css
.demo-banner {
  display: flex; align-items: center; gap: 10px;
  padding: 12px 16px;
  background: #FFFBEB;
  border: 1px solid #FCD34D;
  border-radius: 10px;
  font-size: 13px; color: #92400E;
}
.state-processing, .state-ai-pending {
  display: flex; align-items: center; gap: 16px;
  padding: 24px;
  background: var(--color-bg-soft);
  border-radius: 12px;
  border: 1px dashed var(--color-border-medium);
}
.state-title { font-size: 15px; font-weight: 500; color: var(--color-text-dark); }
.state-countdown { font-size: 20px; font-weight: 700; color: var(--color-primary); margin: 4px 0; }
.state-sub { font-size: 13px; color: var(--color-text-muted); max-width: 380px; }
```

---

## Real-time Recommendations Row

Horizontal scrolling recommendation list above the campaign table.

```html
<div class="recommendations-row">
  <div class="rec-header">
    <span class="rec-title">Real-time Recommendations</span>
    <span class="rec-update">Updated: 2026-01-15 13:29</span>
  </div>
  <div class="rec-list">
    <div class="rec-item">
      <div class="rec-rank">TOP 1</div>
      <div class="rec-text">Increase budget gradually on high-ROAS campaigns...</div>
      <button class="btn-sm btn-primary">Apply</button>
    </div>
  </div>
</div>
```

```css
.recommendations-row {
  background: var(--color-bg);
  border: 1px solid var(--color-border);
  border-radius: 12px;
  padding: 16px;
}
.rec-header {
  display: flex; align-items: center; justify-content: space-between;
  margin-bottom: 12px;
}
.rec-title { font-size: 14px; font-weight: 600; color: var(--color-text-dark); }
.rec-update { font-size: 12px; color: var(--color-text-placeholder); }
.rec-list { display: flex; gap: 12px; overflow-x: auto; padding-bottom: 4px; }
.rec-item {
  flex-shrink: 0;
  width: 280px;
  background: var(--color-bg-soft);
  border: 1px solid var(--color-border);
  border-radius: 10px;
  padding: 14px;
  display: flex; flex-direction: column; gap: 8px;
}
.rec-rank {
  display: inline-block;
  background: var(--color-primary);
  color: white;
  font-size: 10px; font-weight: 600;
  padding: 2px 6px; border-radius: 4px;
  letter-spacing: 0.5px;
}
.rec-text { font-size: 13px; color: var(--color-text-body); line-height: 18px; }
```

---

## Delivery Issues Alert

```html
<div class="delivery-alert">
  <div class="delivery-alert-header">
    <svg class="alert-icon"><!-- warning icon --></svg>
    <span>Delivery Issues from Facebook (3)</span>
    <button class="btn-icon delivery-close">✕</button>
  </div>
  <div class="delivery-items">
    <div class="delivery-item">Your ad account has reached its spending limit.</div>
  </div>
  <button class="btn-outline btn-sm">Go to check</button>
</div>
```

```css
.delivery-alert {
  background: #FEF2F2;
  border: 1px solid #FECACA;
  border-radius: 12px;
  padding: 16px;
  display: flex; flex-direction: column; gap: 10px;
}
.delivery-alert-header {
  display: flex; align-items: center; gap: 8px;
  font-size: 14px; font-weight: 600; color: #991B1B;
}
.delivery-items { font-size: 13px; color: #7F1D1D; }
```
