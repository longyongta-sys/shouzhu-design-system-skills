---
name: shouzhu-detail-style
description: Shouzhu detail display style skill. Use when creating, modifying, reviewing, or prototyping object detail pages, key-value details, profile details, field rows, status detail fields, or read-only information blocks in Shouzhu Vue 3 + Element Plus admin pages.
---

# Shouzhu Detail Style

Use this style when a page needs to display read-only details for an object.

## Detail Page Layout

Use this layout for full detail pages with a left detail area, right summary/detail area, and bottom actions.

```vue
<section class="sz-detail-page">
  <div class="sz-detail-head">
    <button class="sz-detail-back" type="button">
      <i class="sz-common-iconfont icon-zuo"></i>
      <span>返回上一级</span>
    </button>
  </div>

  <div class="sz-detail-body">
    <main class="sz-detail-left">
      <section class="sz-detail-panel">
        <header class="sz-detail-section-title">
          <span class="title-mark"></span>
          <h2>详情标题</h2>
        </header>
        <div class="detail-list">...</div>
      </section>

      <section class="sz-detail-panel">
        <header class="sz-detail-section-title">
          <span class="title-mark"></span>
          <h2>详情标题</h2>
        </header>
        <div class="detail-list">...</div>
      </section>
    </main>

    <aside class="sz-detail-right">
      <section class="sz-detail-panel">
        <header class="sz-detail-section-title">
          <span class="title-mark"></span>
          <h2>详情标题</h2>
        </header>
        <div class="detail-list">...</div>
      </section>
    </aside>
  </div>

  <footer class="sz-detail-footer">
    <el-button class="sz-btn sz-btn-outline sz-btn-large">按钮</el-button>
    <el-button class="sz-btn sz-btn-primary sz-btn-large">按钮</el-button>
  </footer>
</section>
```

Layout rules:

- Detail page fills the available `.system-content` area and must not make the browser page scroll.
- Full detail pages must use the `.sz-detail-page` structure. Do not replace it with a dashboard-like project overview, profile header, KPI strip, freeform card grid, or right-side link list unless the designer explicitly supplies that as a separate page pattern.
- Read-only information must be organized into `.sz-detail-panel` sections inside `.sz-detail-left` and `.sz-detail-right`; do not place unframed detail content directly on the page background.
- Detail pages are a special shell case: because they contain their own `40px` back row, the outer content wrapper must not add an extra `16px` top padding above the detail page.
- The detail page itself must not add an extra outer `16px` padding when it already sits inside the locked admin shell. Avoid stacking `app-main` spacing and detail-page spacing into a double `16px + 16px` gap.
- Detail page outer padding: `0`.
- Detail page background uses the subtle page background, `var(--sz-bg-subtle)`, so white detail panels remain visually separated.
- Back row sits at the top of the detail page.
- Back row fixed height: `40px`.
- The back row and the detail body have no extra vertical gap; the detail body starts immediately below the `40px` back row.
- If content exceeds the visible height, the left detail column and right detail column scroll independently below the fixed `40px` back row.
- `.sz-detail-body` only controls the two-column layout and must not be the scrolling container.
- The left/right content area keeps a fixed `16px` distance from the bottom action area when a bottom action area exists; this is created by `.sz-detail-body { margin-bottom: 16px; }`.
- If a detail page has no bottom action area, add `is-no-footer` to `.sz-detail-page`, omit `.sz-detail-footer`, and set `.sz-detail-body { margin-bottom: 0; }` so only the shell's bottom `16px` remains.
- The left/right content area height adapts to the available space between the back row and bottom action area.
- Detail body uses two columns.
- Left detail area width: adaptive, `minmax(0, 1fr)`.
- Right detail area width: fixed `500px`.
- The right detail area must remain a real detail column, not a narrow operation/menu/sidebar column. Its width is fixed at `500px` on desktop.
- Left/right column gap: `16px`.
- Left area panels stack vertically with `16px` gap.
- Left area panel height is content-adaptive by default.
- When the left area has remaining vertical space, the last left detail panel must expand to fill the remaining height.
- Right detail panel minimum height is `100%`, but it must grow with content when the right content exceeds the visible height.
- Do not force detail panels to a fixed `height: 100%` when content can exceed the panel.
- Detail panels use white background and `8px` radius.
- Detail panel padding: `24px`.
- Detail columns must reserve space for the fixed bottom action area when it exists so content is not covered.
- If the overall detail content exceeds the available browser height, scrolling belongs independently inside `.sz-detail-left` and `.sz-detail-right`.
- Detail left/right column scrollbars use a custom lightweight style: no top/bottom arrow buttons, `6px` thickness, thumb color `#CCCCCC`, transparent track.
- The bottom action area stays in the independent bottom row of `.sz-detail-page`; it must not overlay, cover, or obscure the scrollable detail content.
- The fixed `16px` bottom spacing must not stack. With a footer, `.sz-detail-body` uses `margin-bottom: 16px`; without a footer, `.sz-detail-body` uses `margin-bottom: 0` and the shell bottom spacing provides the only bottom `16px`.
- Do not add a vertical divider, page-level scrollbar, or body-level scroll between the left and right detail areas. Scrolling belongs only to `.sz-detail-left` and `.sz-detail-right`.

Bottom action rules:

- Action area is fixed at the bottom by the `.sz-detail-page` grid layout.
- Do not use sticky/fixed overlay behavior that covers the independently scrollable left/right detail columns.
- The action area is optional. Only render `.sz-detail-footer` when the detail page has real page-level actions.
- Action area background: white.
- Action area sits in the independent bottom row of the detail page grid when present.
- Keep exactly `16px` visual distance between the bottom of the left/right scrollable content area and the action area.
- Action area padding: `16px 24px`.
- Action area radius: `8px`.
- Buttons align right.
- Button gap: `16px`.
- Buttons follow `../shouzhu-el-button-style/SKILL.md`.
- Do not let bottom actions cover detail content.

Failure examples that must be corrected before handoff:

- The page shows a custom project title/overview block above the detail panels instead of the fixed `40px` back row followed immediately by `.sz-detail-body`.
- The left detail content and right detail content share one central scrollbar or one page-level scrolling area.
- The right area is a list of navigation/action cards instead of a fixed `500px` detail panel.
- White panels disappear into a white page background because `.sz-detail-page` did not use the subtle background.
- Detail sections are loose text, KPI cards, or unframed rows instead of `.sz-detail-panel` sections with the approved title mark.

Responsive rule:

- On narrow viewports where `500px` right column cannot fit without horizontal scrolling, stack the right detail area below the left area and set it to `width: 100%`.

## Structure

```vue
<div class="detail-list">
  <div class="detail-row">
    <span class="detail-label">所属区域：</span>
    <span class="detail-value">西藏自治区 / 日喀则市 / 谢通门县</span>
  </div>
  <div class="detail-row">
    <span class="detail-label">当前状态：</span>
    <el-tag class="sz-tag tag-success">启用</el-tag>
  </div>
</div>
```

## Rules

- Do not use bordered description tables for this style.
- Render each row as `字段名：字段值`.
- Row font-size: `14px`.
- Row line-height: about `22px`.
- Row gap: about `18px`.
- Detail content padding: `24px`.
- Label color: `var(--sz-text-secondary)`.
- Value color: `var(--sz-text-body)`.
- Label and value weight: `400`.
- Long values wrap; no horizontal scroll.
- Empty values render as `-`.
- Normal fields display plain text.
- Status/type/result fields display tags.

## Section Title

- Section title font-size: `16px`.
- Section title font-weight: `700`.
- Section title color: `var(--sz-text-title)`.
- Section title line-height: `1.5`.
- Blue title mark height: `16px`.
- Blue title mark width: `3px`.
- Blue title mark color: primary, `var(--sz-color-primary)`.
- Gap between title mark and title text: `8px`.
- Title mark and title text align vertically centered.

## CSS Contract

```css
.sz-detail-page {
  position: relative;
  display: grid;
  grid-template-rows: 40px minmax(0, 1fr) auto;
  gap: 0;
  width: 100%;
  height: 100%;
  min-width: 0;
  min-height: 0;
  padding: 0;
  background: var(--sz-bg-subtle);
  overflow: hidden;
}

.sz-detail-head {
  display: flex;
  align-items: center;
  justify-content: space-between;
  height: 40px;
  min-width: 0;
}

.sz-detail-back {
  display: inline-flex;
  align-items: center;
  gap: 4px;
  width: fit-content;
  padding: 0;
  border: 0;
  background: transparent;
  color: var(--sz-text-secondary);
  font-family: var(--font-family-base);
  font-size: var(--sz-font-size-helper);
  cursor: pointer;
}

.sz-detail-back .sz-common-iconfont {
  color: var(--sz-color-primary);
  font-size: 16px;
}

.sz-detail-body {
  display: grid;
  grid-template-columns: minmax(0, 1fr) 500px;
  gap: 16px;
  min-width: 0;
  min-height: 0;
  margin-bottom: 16px;
  overflow: hidden;
}

.sz-detail-page.is-no-footer .sz-detail-body {
  margin-bottom: 0;
}

.sz-detail-left {
  display: flex;
  flex-direction: column;
  gap: 16px;
  min-width: 0;
  min-height: 0;
  height: 100%;
  overflow: auto;
}

.sz-detail-left .sz-detail-panel {
  flex: 0 0 auto;
}

.sz-detail-left .sz-detail-panel:last-child {
  flex: 1 0 auto;
}

.sz-detail-right {
  display: flex;
  flex-direction: column;
  min-width: 0;
  min-height: 0;
  height: 100%;
  overflow: auto;
}

.sz-detail-right .sz-detail-panel {
  flex: 1 0 auto;
  height: auto;
  min-height: 100%;
}

.sz-detail-left,
.sz-detail-right {
  scrollbar-width: thin;
  scrollbar-color: #CCCCCC transparent;
}

.sz-detail-left::-webkit-scrollbar,
.sz-detail-right::-webkit-scrollbar {
  width: 6px;
  height: 6px;
}

.sz-detail-left::-webkit-scrollbar-button,
.sz-detail-right::-webkit-scrollbar-button {
  display: none;
  width: 0;
  height: 0;
}

.sz-detail-left::-webkit-scrollbar-track,
.sz-detail-right::-webkit-scrollbar-track {
  background: transparent;
}

.sz-detail-left::-webkit-scrollbar-thumb,
.sz-detail-right::-webkit-scrollbar-thumb {
  border-radius: 99px;
  background: #CCCCCC;
}

.sz-detail-panel {
  min-width: 0;
  min-height: max-content;
  padding: 24px;
  border-radius: 8px;
  background: var(--sz-color-white);
}

.sz-detail-section-title {
  display: flex;
  align-items: center;
  gap: 8px;
  margin: 0 0 24px;
}

.sz-detail-section-title .title-mark {
  width: 3px;
  height: 16px;
  flex: none;
  border-radius: 2px;
  background: var(--sz-color-primary);
}

.sz-detail-section-title h2 {
  margin: 0;
  color: var(--sz-text-title);
  font-size: var(--sz-font-size-title);
  font-weight: var(--sz-font-weight-bold);
  line-height: var(--sz-line-height-base);
}

.sz-detail-footer {
  position: relative;
  display: flex;
  justify-content: flex-end;
  gap: 16px;
  padding: 16px 24px;
  border-radius: 8px;
  background: var(--sz-color-white);
}

@media (max-width: 1100px) {
  .sz-detail-body {
    grid-template-columns: minmax(0, 1fr);
  }
}
```
