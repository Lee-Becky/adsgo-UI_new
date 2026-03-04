# AdsGo AI Components Reference (2026)

These components are unique to AdsGo's AI-powered ad optimization features. Read this file when building the AI analysis panel, optimization console, budget controls, or any AI-driven UI.

## Table of Contents

- [AI Analysis Insights Panel](#ai-analysis-insights-panel) — Brief metrics, insight cards (highlight / optimize / risk), timestamp
- [Smart Optimization Console](#smart-optimization-console) — Mode selection, daily analysis toggles, budget allocation
- [Optimization Details Drawer](#optimization-details-drawer-1) — Action sections by type, apply/delete per item
- [Optimization Rules Modal](#optimization-rules-modal) — Rule list, example hint, add-rule input
- [AI Pending State](#ai-pending-state) — Lock icon, countdown, timeline steps
- [Brand Performance Goal](#brand-performance-goal) — Goal form with select, detail items

---

## AI Analysis Insights Panel

Displays AI-generated insights: highlights, risks, and recommendations.

```html
<div class="ai-panel">
  <div class="ai-panel-header">
    <div class="ai-panel-title">
      <svg class="sparkle-icon"><!-- sparkle/star svg --></svg>
      AI Analysis Insights
    </div>
    <span class="ai-panel-period">Last 14 days</span>
  </div>

  <!-- AI Summary Brief -->
  <div class="ai-brief">
    <div class="ai-brief-title">Meta Ads Insights Brief</div>
    <div class="ai-brief-metrics">
      <div class="ai-metric">
        <svg><!-- trend-down icon --></svg>
        <span class="ai-metric-label">Spend</span>
        <span class="ai-metric-value">$5,860</span>
        <span class="ai-metric-trend ai-metric-trend--down">↓ 1.72%</span>
      </div>
      <div class="ai-metric">
        <svg><!-- trend-up icon --></svg>
        <span class="ai-metric-label">Purchase</span>
        <span class="ai-metric-value">270</span>
        <span class="ai-metric-trend ai-metric-trend--up">↑ 10.23%</span>
      </div>
      <div class="ai-metric">
        <span class="ai-metric-label">CPA</span>
        <span class="ai-metric-value">$22.8</span>
        <span class="ai-metric-trend ai-metric-trend--up">↑ 4.62%</span>
      </div>
    </div>
  </div>

  <!-- Insight Cards -->
  <div class="ai-insights">

    <!-- Key Highlight -->
    <div class="ai-insight ai-insight--highlight">
      <svg class="ai-insight-icon check-icon"><!-- check icon --></svg>
      <div>
        <div class="ai-insight-type">Key Highlight</div>
        <div class="ai-insight-text">Overall brand performance is performing well.</div>
      </div>
    </div>

    <div class="ai-insight ai-insight--highlight">
      <svg class="ai-insight-icon check-icon"><!-- check icon --></svg>
      <div>
        <div class="ai-insight-text">AI channel achieved a ROAS of 4.50x, indicating stable and healthy performance.</div>
      </div>
    </div>

    <!-- Budget Optimization -->
    <div class="ai-insight ai-insight--optimize">
      <svg class="ai-insight-icon optimize-icon"><!-- target icon --></svg>
      <div>
        <div class="ai-insight-type">Budget Optimization</div>
        <div class="ai-insight-text">Based on the current CVR performance, the system recommends a gradual budget increase of 15%–25% for the top 20% highest-performing campaigns.</div>
      </div>
    </div>

    <!-- Potential Risk -->
    <div class="ai-insight ai-insight--risk">
      <svg class="ai-insight-icon risk-icon"><!-- alert icon --></svg>
      <div>
        <div class="ai-insight-type">Potential Risk</div>
        <div class="ai-insight-text">Increase budget gradually on high-ROAS campaigns to capture additional demand while maintaining efficiency.</div>
      </div>
    </div>

  </div>

  <!-- Timestamp -->
  <div class="ai-timestamp">
    <svg><!-- clock icon --></svg>
    Jan 18, 2026 · 13:52
  </div>
</div>
```

```css
.ai-panel {
  background: var(--color-bg);
  border: 1px solid var(--color-border);
  border-radius: 12px;
  overflow: hidden;
}
.ai-panel-header {
  display: flex; align-items: center; justify-content: space-between;
  padding: 16px 20px;
  border-bottom: 1px solid var(--color-border);
  background: linear-gradient(135deg, #FAFAFA 0%, #F5F1FF 100%);
}
.ai-panel-title {
  display: flex; align-items: center; gap: 8px;
  font-size: 15px; font-weight: 600; color: var(--color-text-dark);
}
.sparkle-icon { width: 18px; height: 18px; color: var(--color-primary); }
.ai-panel-period { font-size: 12px; color: var(--color-text-placeholder); }

/* Brief metrics row */
.ai-brief {
  padding: 14px 20px;
  border-bottom: 1px solid var(--color-border);
}
.ai-brief-title { font-size: 13px; font-weight: 600; color: var(--color-text-dark); margin-bottom: 10px; }
.ai-brief-metrics { display: flex; gap: 16px; flex-wrap: wrap; }
.ai-metric { display: flex; align-items: center; gap: 4px; }
.ai-metric-label { font-size: 12px; color: var(--color-text-muted); }
.ai-metric-value { font-size: 13px; font-weight: 600; color: var(--color-text-dark); }
.ai-metric-trend {
  font-size: 11px; font-weight: 500;
  padding: 1px 5px; border-radius: 9999px;
}
.ai-metric-trend--up   { background: var(--color-success-bg); color: var(--color-success); }
.ai-metric-trend--down { background: #FEF2F2; color: var(--color-danger); }

/* Insight items */
.ai-insights { padding: 12px 20px; display: flex; flex-direction: column; gap: 10px; }
.ai-insight {
  display: flex; align-items: flex-start; gap: 10px;
  padding: 12px 14px;
  border-radius: 10px;
  border-left: 3px solid transparent;
}
.ai-insight--highlight {
  background: #F0FDF4;
  border-left-color: var(--color-success);
}
.ai-insight--optimize {
  background: var(--color-primary-bg);
  border-left-color: var(--color-primary);
}
.ai-insight--risk {
  background: var(--color-warning-bg);
  border-left-color: var(--color-warning);
}
.ai-insight-icon { width: 16px; height: 16px; flex-shrink: 0; margin-top: 2px; }
.check-icon    { color: var(--color-success); }
.optimize-icon { color: var(--color-primary); }
.risk-icon     { color: var(--color-warning); }
.ai-insight-type { font-size: 11px; font-weight: 600; text-transform: uppercase; letter-spacing: 0.6px; color: var(--color-text-muted); margin-bottom: 3px; }
.ai-insight-text { font-size: 13px; font-weight: 400; color: var(--color-text-body); line-height: 18px; }

/* Timestamp */
.ai-timestamp {
  display: flex; align-items: center; gap: 6px;
  padding: 10px 20px;
  border-top: 1px solid var(--color-border);
  font-size: 12px; color: var(--color-text-placeholder);
}
```

---

## Smart Optimization Console

Control hub for AI automation mode settings.

```html
<div class="opt-console">
  <div class="opt-console-header">
    <div class="opt-console-title">
      <svg class="sparkle-icon"><!-- sparkle --></svg>
      Optimize Control Hub
    </div>
    <span class="opt-console-roas">ROAS 4.62x</span>
  </div>
  <p class="opt-console-sub">Summarizes the current status of your live campaigns and provides performance-based budget allocation suggestions.</p>

  <!-- Mode selection -->
  <div class="opt-modes">
    <div class="opt-mode opt-mode--active">
      <div class="opt-mode-icon">
        <svg><!-- recommendations icon --></svg>
      </div>
      <div>
        <div class="opt-mode-title">Recommendations</div>
        <div class="opt-mode-sub">AI suggests only. You choose whether to apply.</div>
      </div>
      <label class="toggle ml-auto">
        <input type="checkbox" />
        <span class="toggle-track"></span>
      </label>
    </div>

    <div class="opt-mode opt-mode--active">
      <div class="opt-mode-icon opt-mode-icon--purple">
        <svg><!-- infinity/auto icon --></svg>
      </div>
      <div>
        <div class="opt-mode-title">Auto-apply</div>
        <div class="opt-mode-sub">AI suggests and executes automatically.</div>
      </div>
      <label class="toggle ml-auto">
        <input type="checkbox" checked />
        <span class="toggle-track"></span>
      </label>
    </div>
  </div>

  <div class="opt-divider"></div>

  <!-- Daily Analysis settings -->
  <div class="opt-settings">
    <div class="opt-setting-row">
      <div class="opt-setting-info">
        <svg><!-- calendar icon --></svg>
        <div>
          <div class="opt-setting-title">Daily Auto Analysis</div>
          <span class="tag-active">Active</span>
        </div>
      </div>
      <label class="toggle">
        <input type="checkbox" checked />
        <span class="toggle-track"></span>
      </label>
    </div>

    <div class="opt-setting-row">
      <div class="opt-setting-info">
        <svg><!-- infinity icon --></svg>
        <div>
          <div class="opt-setting-title">24/7 AI Optimization</div>
          <span class="tag-inactive">Inactive</span>
        </div>
      </div>
      <label class="toggle">
        <input type="checkbox" />
        <span class="toggle-track"></span>
      </label>
    </div>
  </div>

  <div class="opt-divider"></div>

  <!-- Budget Allocation -->
  <div class="budget-allocation">
    <div class="budget-alloc-title">Budget Allocation</div>
    <div class="budget-compare">
      <div class="budget-item">
        <div class="budget-item-label">Current</div>
        <div class="budget-item-value">$900</div>
      </div>
      <svg class="budget-arrow"><!-- arrow-down icon --></svg>
      <div class="budget-item">
        <div class="budget-item-label">Recommend</div>
        <div class="budget-item-value budget-item-value--recommend">$800</div>
      </div>
    </div>
  </div>
</div>
```

```css
/* Figma: 337×483px, gradient bg #F1F7FF→#FFFFFF (blue tint!),
   border 1px #F5F5F5, radius 12px, shadow -2px 2px 15px rgba(14,0,45,0.06) */
.opt-console {
  background: linear-gradient(180deg, #F1F7FF 0%, #FFFFFF 100%);
  border: 1px solid #F5F5F5;
  border-radius: 12px;
  padding: 20px;
  box-shadow: -2px 2px 15px rgba(14, 0, 45, 0.06);
  width: 337px;
}
.opt-console-header {
  display: flex; align-items: center; justify-content: space-between;
  margin-bottom: 6px;
}
.opt-console-title {
  display: flex; align-items: center; gap: 8px;
  font-size: 15px; font-weight: 600; color: var(--color-text-dark);
}
.opt-console-roas {
  font-size: 14px; font-weight: 600; color: var(--color-primary);
  background: var(--color-primary-bg);
  padding: 3px 10px; border-radius: 9999px;
}
.opt-console-sub {
  font-size: 13px; color: var(--color-text-muted);
  line-height: 18px; margin-bottom: 16px;
}

/* Mode cards */
.opt-modes { display: flex; flex-direction: column; gap: 10px; }
.opt-mode {
  display: flex; align-items: center; gap: 12px;
  padding: 12px 14px;
  border-radius: 10px;
  border: 1px solid var(--color-border);
  cursor: pointer;
  transition: border-color 0.15s;
}
/* Figma: inactive mode cards use #F2F8FF (blue tint), 148×103px, radius 12px
   Active mode cards use gradient #3080E3→#285388, stroke #E7F0FF */
.opt-mode--inactive { background: #F2F8FF; border-color: transparent; }
.opt-mode--active {
  background: linear-gradient(180deg, #3080E3 0%, #285388 100%);
  border-color: #E7F0FF;
  color: #FFFFFF;
}
.opt-mode-icon {
  width: 36px; height: 36px;
  border-radius: 10px;
  background: var(--color-bg-soft);
  display: flex; align-items: center; justify-content: center;
  flex-shrink: 0;
}
.opt-mode-icon--purple { background: var(--color-primary-bg); }
.opt-mode-icon svg { width: 18px; height: 18px; color: var(--color-primary); }
.opt-mode-title { font-size: 14px; font-weight: 500; color: var(--color-text-dark); }
.opt-mode-sub   { font-size: 12px; color: var(--color-text-muted); margin-top: 2px; }
.ml-auto { margin-left: auto; }

.opt-divider { height: 1px; background: var(--color-border); margin: 16px 0; }

/* Settings rows */
.opt-settings { display: flex; flex-direction: column; gap: 12px; }
.opt-setting-row {
  display: flex; align-items: center; justify-content: space-between; gap: 12px;
}
.opt-setting-info {
  display: flex; align-items: center; gap: 10px;
}
.opt-setting-info svg { width: 18px; height: 18px; color: var(--color-text-muted); flex-shrink: 0; }
.opt-setting-title { font-size: 14px; font-weight: 500; color: var(--color-text-dark); margin-bottom: 3px; }

/* Budget allocation */
.budget-allocation {}
.budget-alloc-title { font-size: 13px; font-weight: 600; color: var(--color-text-dark); margin-bottom: 12px; }
.budget-compare {
  display: flex; align-items: center; gap: 12px;
}
.budget-item { flex: 1; }
.budget-item-label { font-size: 11px; font-weight: 500; color: var(--color-text-muted); text-transform: uppercase; letter-spacing: 0.5px; margin-bottom: 4px; }
.budget-item-value { font-size: 20px; font-weight: 700; color: var(--color-text-dark); }
.budget-item-value--recommend { color: var(--color-primary); }
.budget-arrow { width: 20px; height: 20px; color: var(--color-primary); }
```

---

## Optimization Details Drawer

Full detail view of AI optimization actions.

```html
<div class="drawer-overlay">
  <div class="drawer">
    <div class="drawer-header">
      <div class="drawer-title">Optimization Details</div>
      <button class="btn-icon">✕</button>
    </div>

    <!-- Action type sections -->
    <div class="drawer-body">

      <!-- Scale Up section -->
      <div class="opt-section">
        <div class="opt-section-header">
          <div class="opt-section-badge opt-section-badge--scale-up">↑ Scale Up</div>
          <span class="opt-section-count">8</span>
        </div>
        <div class="opt-action-list">
          <div class="opt-action">
            <svg><!-- target icon --></svg>
            <div class="opt-action-text">
              Gradually scale budget on high-performing campaigns during the learning phase.
            </div>
            <div class="opt-action-btns">
              <button class="btn-primary btn-sm">Apply</button>
              <button class="btn-icon">🗑</button>
            </div>
          </div>
        </div>
      </div>

      <!-- Scale Down section -->
      <div class="opt-section">
        <div class="opt-section-header">
          <div class="opt-section-badge opt-section-badge--scale-down">↓ Scale Down</div>
          <span class="opt-section-count">3</span>
        </div>
      </div>

      <!-- Pause section -->
      <div class="opt-section">
        <div class="opt-section-header">
          <div class="opt-section-badge opt-section-badge--pause">⏸ Pause</div>
          <span class="opt-section-count">4</span>
        </div>
        <div class="opt-action-list">
          <div class="opt-action">
            <svg><!-- alert icon --></svg>
            <div class="opt-action-text">
              Pause campaigns if CPA spikes by more than 30% compared to the 7-day average.
            </div>
            <div class="opt-action-btns">
              <button class="btn-primary btn-sm">Apply</button>
              <button class="btn-icon">🗑</button>
            </div>
          </div>
        </div>
      </div>

      <!-- Maintain section -->
      <div class="opt-section">
        <div class="opt-section-header">
          <div class="opt-section-badge opt-section-badge--maintain">● Maintain</div>
          <span class="opt-section-count">2</span>
        </div>
      </div>

    </div>

    <!-- Drawer footer -->
    <div class="drawer-footer">
      <div class="opt-rule-count">Added: 8/10</div>
      <a href="#" class="auto-apply-link">Auto-apply settings →</a>
    </div>
  </div>
</div>
```

```css
.drawer-body { flex: 1; overflow-y: auto; padding: 20px 24px; }

/* Action type sections */
.opt-section { margin-bottom: 20px; }
.opt-section-header {
  display: flex; align-items: center; gap: 8px; margin-bottom: 10px;
}
.opt-section-badge {
  display: inline-flex; align-items: center; gap: 4px;
  font-size: 12px; font-weight: 600;
  padding: 3px 10px; border-radius: 9999px;
}
.opt-section-badge--scale-up   { background: var(--color-success-bg); color: #065F46; }
.opt-section-badge--scale-down { background: #FEF2F2; color: #991B1B; }
.opt-section-badge--pause      { background: var(--color-warning-bg); color: #92400E; }
.opt-section-badge--maintain   { background: var(--color-bg-soft); color: var(--color-text-muted); }
.opt-section-count {
  font-size: 14px; font-weight: 700; color: var(--color-text-dark);
}

/* Action items */
.opt-action-list { display: flex; flex-direction: column; gap: 8px; }
.opt-action {
  display: flex; align-items: flex-start; gap: 10px;
  padding: 12px 14px;
  background: var(--color-bg-soft);
  border: 1px solid var(--color-border);
  border-radius: 10px;
}
.opt-action > svg { width: 16px; height: 16px; color: var(--color-text-muted); flex-shrink: 0; margin-top: 2px; }
.opt-action-text { flex: 1; font-size: 13px; color: var(--color-text-body); line-height: 18px; }
.opt-action-btns { display: flex; align-items: center; gap: 6px; flex-shrink: 0; }

/* Footer */
.drawer-footer {
  padding: 16px 24px;
  border-top: 1px solid var(--color-border);
  display: flex; align-items: center; justify-content: space-between;
}
.opt-rule-count { font-size: 13px; color: var(--color-text-muted); }
.auto-apply-link { font-size: 13px; font-weight: 500; color: var(--color-primary); text-decoration: none; }
.auto-apply-link:hover { text-decoration: underline; }
```

---

## Optimization Rules Modal

```html
<div class="modal">
  <div class="modal-header">
    <span class="modal-title">Optimize Rules</span>
    <button class="btn-icon">✕</button>
  </div>
  <div class="modal-divider"></div>
  <div class="modal-body">

    <!-- Active rules list -->
    <div class="rules-list">
      <div class="rule-item">
        <svg><!-- rule icon --></svg>
        <div class="rule-text">Gradually scale budget on high-performing campaigns during the learning phase.</div>
        <button class="btn-icon rule-delete">🗑</button>
      </div>
      <div class="rules-divider"></div>
      <div class="rule-item">
        <svg><!-- rule icon --></svg>
        <div class="rule-text">Expand budget only after performance stabilizes for at least 72 hours.</div>
        <button class="btn-icon rule-delete">🗑</button>
      </div>
    </div>

    <!-- Example hint -->
    <div class="rule-example">
      <span>Example:</span>
      <span class="rule-example-text">Pause when the campaign's 7-day ROAS is less than 2x</span>
      <svg><!-- arrow-right icon --></svg>
    </div>

    <!-- Add new rule input -->
    <div class="rule-add-wrap">
      <input type="text" class="input" placeholder="Add new optimization rules that you want..." />
    </div>

  </div>
  <div class="modal-divider"></div>
  <div class="modal-footer">
    <span class="rule-counter">Added: 8/10</span>
    <div class="modal-footer-btns">
      <button class="btn-ghost">Cancel</button>
      <button class="btn-primary">Save Rules</button>
    </div>
  </div>
</div>
```

```css
.rules-list { display: flex; flex-direction: column; gap: 0; margin-bottom: 16px; }
.rule-item {
  display: flex; align-items: flex-start; gap: 10px;
  padding: 12px 0;
}
.rule-item > svg { width: 16px; height: 16px; color: var(--color-primary); flex-shrink: 0; margin-top: 2px; }
.rule-text { flex: 1; font-size: 13px; color: var(--color-text-body); line-height: 18px; }
.rules-divider { height: 1px; background: var(--color-border); }

.rule-example {
  display: flex; align-items: center; gap: 6px;
  font-size: 13px; color: var(--color-text-muted);
  background: var(--color-bg-soft); border-radius: 8px;
  padding: 10px 12px; margin-bottom: 12px;
}
.rule-example-text { color: var(--color-text-dark); font-weight: 500; }

.rule-counter { font-size: 13px; color: var(--color-text-muted); }
.modal-footer { justify-content: space-between; }
.modal-footer-btns { display: flex; gap: 8px; }
```

---

## AI Pending State

Shown when campaign was recently launched and AI analysis is not ready yet.

```html
<div class="ai-pending">
  <div class="ai-pending-icon">
    <svg><!-- lock icon --></svg>
  </div>
  <div class="ai-pending-content">
    <div class="ai-pending-title">AI Analysis Pending</div>
    <div class="ai-pending-countdown">06h 06m remaining</div>
    <div class="ai-pending-sub">Your campaign was launched today. The first AI analysis will run at 24:00 (UTC+8). Insights will be available tomorrow morning.</div>
    <div class="ai-pending-timeline">
      <div class="ai-timeline-item ai-timeline-item--done">
        <svg><!-- check circle --></svg>
        Campaign launched
      </div>
      <div class="ai-timeline-item">
        <svg><!-- clock --></svg>
        Daily data collection
      </div>
      <div class="ai-timeline-item">
        <svg><!-- sparkle --></svg>
        AI analysis scheduled
        <span class="ai-timeline-time">Today 24:00</span>
      </div>
    </div>
  </div>
</div>
```

```css
.ai-pending {
  display: flex; align-items: flex-start; gap: 20px;
  padding: 24px;
  background: var(--color-bg-soft);
  border: 1px solid var(--color-border);
  border-radius: 12px;
}
.ai-pending-icon {
  width: 48px; height: 48px; flex-shrink: 0;
  background: var(--color-primary-bg);
  border-radius: 12px;
  display: flex; align-items: center; justify-content: center;
}
.ai-pending-icon svg { width: 24px; height: 24px; color: var(--color-primary); }
.ai-pending-title { font-size: 16px; font-weight: 600; color: var(--color-text-dark); margin-bottom: 4px; }
.ai-pending-countdown { font-size: 24px; font-weight: 700; color: var(--color-primary); margin-bottom: 8px; }
.ai-pending-sub { font-size: 13px; color: var(--color-text-muted); line-height: 18px; margin-bottom: 16px; max-width: 420px; }
.ai-pending-timeline { display: flex; flex-direction: column; gap: 10px; }
.ai-timeline-item {
  display: flex; align-items: center; gap: 8px;
  font-size: 13px; color: var(--color-text-body);
}
.ai-timeline-item svg { width: 16px; height: 16px; color: var(--color-text-placeholder); }
.ai-timeline-item--done svg { color: var(--color-success); }
.ai-timeline-time { margin-left: auto; font-size: 12px; color: var(--color-primary); font-weight: 500; }
```

---

## Brand Performance Goal

Goal configuration form panel.

```html
<div class="goal-panel card">
  <div class="goal-header">
    <svg class="sparkle-icon"><!-- target icon --></svg>
    Brand Performance Goal
  </div>
  <div class="goal-form">
    <div class="form-item">
      <label class="form-label">Brand</label>
      <select class="select"><option>Adsgo.ai</option></select>
    </div>
    <div class="form-item">
      <label class="form-label">Bid Promotion Type</label>
      <select class="select"><option>Purchase - Maximize Conversions</option></select>
    </div>
    <div class="goal-details">
      <div class="detail-item">
        <span class="detail-label">Locations</span>
        <span class="detail-value">US, UK</span>
      </div>
      <div class="detail-item">
        <span class="detail-label">Daily Budget</span>
        <span class="detail-value">$5,000</span>
      </div>
      <div class="detail-item">
        <span class="detail-label">Target ROAS</span>
        <span class="detail-value">≥ 4.5x</span>
      </div>
    </div>
  </div>
</div>
```

```css
.goal-panel { padding: 20px; }
.goal-header {
  display: flex; align-items: center; gap: 8px;
  font-size: 15px; font-weight: 600; color: var(--color-text-dark);
  margin-bottom: 16px;
}
.goal-form { display: flex; flex-direction: column; gap: 14px; }
.goal-details { display: flex; flex-direction: column; gap: 10px; padding: 14px; background: var(--color-bg-soft); border-radius: 10px; }
.detail-item { display: flex; justify-content: space-between; align-items: center; }
.detail-label { font-size: 13px; color: var(--color-text-muted); }
.detail-value { font-size: 13px; font-weight: 500; color: var(--color-text-dark); }
```
