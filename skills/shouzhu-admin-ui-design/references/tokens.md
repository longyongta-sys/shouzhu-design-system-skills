# Tokens

Use this file as the source of truth for Shouzhu colors, typography, radius, sizing, and Element Plus theme variables.

These V0 color values come from the current design standard. Keep `#0068FF` as the global primary color unless the design system explicitly changes.

## CSS Variables

```css
--font-family-base: "Source Han Sans SC", "Noto Sans SC", "Source Han Sans CN", "Source Han Sans", "PingFang SC", "Microsoft YaHei", sans-serif;
--font-family-number: "D-DIN-PRO", "D-DIN", "DIN Alternate", "Arial Narrow", Arial, sans-serif;

/* Brand and semantic colors */
--sz-color-primary: #0068FF;
--sz-color-primary-hover: #005CE6;
--sz-color-primary-active: #0052CC;
--sz-color-white: #FFFFFF;
--sz-color-primary-light: #EDF3FF;
--sz-color-neutral: #D9D9D9;
--sz-color-success: #309B58;
--sz-color-danger: #DD4620;
--sz-color-warning: #DE8723;
--sz-color-purple: #3120D1;

/* Surface, text, and border */
--sz-bg-subtle: #F2F2F2;
--sz-bg-content: #FFFFFF;
--sz-text-title: #333539;
--sz-text-body: #222531;
--sz-text-secondary: #626B86;
--sz-text-placeholder: #ADB5C3;
--sz-border-default: #D8E0ED;

/* Backward-compatible aliases used by existing Shouzhu rules */
--color-primary: var(--sz-color-primary);
--color-primary-light: var(--sz-color-primary-light);
--color-primary-soft: #D9E9FF;
--color-safe: var(--sz-color-success);
--color-assist: var(--sz-color-warning);
--color-alert: var(--sz-color-danger);
--color-alert-light: #FDEBE7;
--color-action-bg: #F4F6F6;
--text-title: var(--sz-text-title);
--text-body: var(--sz-text-body);
--text-muted: var(--sz-text-secondary);
--text-weak: var(--sz-text-placeholder);
--border: var(--sz-border-default);
--surface-subtle: var(--sz-bg-subtle);

/* Typography */
--sz-font-size-helper: 12px;
--sz-font-size-body: 14px;
--sz-font-size-title: 16px;
--sz-font-size-page-title: 18px;
--sz-font-weight-regular: 400;
--sz-font-weight-medium: 500;
--sz-font-weight-semibold: 600;
--sz-font-weight-bold: 700;
--sz-line-height-base: 1.5;

/* Radius and sizing */
--spacing-1: 8px;
--spacing-2: 16px;
--spacing-3: 24px;
--spacing-4: 32px;
--radius-control: 8px;
--radius-panel: 16px;
--control-height: 40px;
--control-height-small: 34px;
--tree-node-height: 48px;
--tree-indent: 24px;
--menu-width: 200px;
--menu-item-height: 44px;
--menu-side-padding: 16px;
--sz-shadow-panel: 0 4px 16px -6px rgb(0 0 0 / 10%);
```

## Color Groups

- Primary: `#0068FF`.
- Primary hover: `#005CE6`.
- Primary active: `#0052CC`.
- White: `#FFFFFF`.
- Primary 10% / light primary surface: `#EDF3FF`.
- Neutral gray: `#D9D9D9`.
- Semantic green / success: `#309B58`.
- Semantic red / danger: `#DD4620`.
- Semantic orange / warning: `#DE8723`.
- Semantic purple: `#3120D1`.
- Page background: `#F2F2F2`.
- Content background: `#FFFFFF`.
- Title text: `#333539`.
- Body text: `#222531`.
- Secondary text: `#626B86`.
- Placeholder / weak hint text: `#ADB5C3`.
- Default line / border: `#D8E0ED`.

## Typography

Use only the core font sizes `12px`, `14px`, `16px`, and `18px` unless a supplied design specifically requires another size.

- Default interface font: use open-source Source Han Sans SC. Keep `Noto Sans SC`, `PingFang SC`, and `Microsoft YaHei` as fallbacks.
- Data metric numbers: use D-DIN-PRO for numeric values in statistic cards, dashboards, KPIs, rankings, amounts, percentages, counters, and other data-indicator numbers.
- Use D-DIN-PRO only for the numeric value itself. Units, labels, descriptions, table headers, and helper text must keep the default interface font.
- Helper text: `12px`, line-height `1.5`. Use for hints, placeholders, compact metadata, secondary descriptions, and small tags.
- Body text: `14px`, line-height `1.5`. Use as the default text size for forms, tables, detail content, normal buttons, menus, and body copy.
- Section title: `16px`, line-height `1.5`. Use for dialog titles, section headers, module titles, and emphasized labels.
- Topbar system title: `18px`, weight `700`, line-height `1.5`.
- Page title: `18px`, line-height `1.5`. Use for page-level titles when a page has an explicit title area.
- Font weight is selected by hierarchy and state: use `400` for normal body text, `500` for labels and table headers, `600` for emphasized controls, and `700` for major titles or selected states.
- Do not use negative letter spacing.
- Do not introduce extra font sizes casually. If a page needs a different size, treat it as a design exception and document why.

## Font Assets

- D-DIN-PRO bold font file: `assets/fonts/D-DIN-PRO-700-BOLD.OTF`.
- In preview or generated apps, expose it with `@font-face` and use `font-family: var(--font-family-number)` on metric number elements.

```css
@font-face {
  font-family: "D-DIN-PRO";
  src: url("/fonts/D-DIN-PRO-700-BOLD.OTF") format("opentype");
  font-weight: 700;
  font-style: normal;
  font-display: swap;
}

.metric-number,
.statistic-value,
.kpi-value {
  font-family: var(--font-family-number);
  font-weight: 700;
}
```

## Radius And Size

- Default spacing follows an 8px grid. Use `8px`, `16px`, `24px`, `32px`, and other multiples of 8 for normal gaps, margins, paddings, and layout distances.
- A component-specific or page-specific spacing value may override the 8px grid only when this skill or a supplied design explicitly defines that value.
- Control radius: `8px`.
- Panel/workspace radius: `16px`.
- Normal control height: `40px`.
- Toolbar compact control height: `34px`.
- Tree node default height: `48px`.
- Tree default indentation: `24px`.
- Menu width: `200px`.
- Menu item default height: `44px`.
- Menu horizontal padding: `16px`.
- Checkbox radius: `4px`.
- Icon-only circular actions: `50%`.
- Floating panel shadow: `0 4px 16px -6px rgb(0 0 0 / 10%)`, equivalent to X `0`, Y `4`, blur `16`, spread `-6`, color `#000000` at `10%`.

## Brand Assets

- Shouzhu menu logo: `assets/brand/shouzhu-logo.png`.
- Use this logo in the left primary menu brand area.
- Do not redraw or replace the logo unless the user provides a new logo.

## Element Plus Theme Variables

Set Element Plus selected, focused, and semantic states to Shouzhu tokens.

```css
.app-shell {
  --el-color-primary: var(--sz-color-primary);
  --el-color-success: var(--sz-color-success);
  --el-color-warning: var(--sz-color-warning);
  --el-color-danger: var(--sz-color-danger);
  --el-color-info: var(--sz-text-secondary);

  --el-color-primary-light-9: var(--sz-color-primary-light);
  --el-input-focus-border-color: var(--sz-color-primary);
  --el-select-input-focus-border-color: var(--sz-color-primary);

  --el-text-color-primary: var(--sz-text-title);
  --el-text-color-regular: var(--sz-text-body);
  --el-text-color-secondary: var(--sz-text-secondary);
  --el-text-color-placeholder: var(--sz-text-placeholder);

  --el-border-color: var(--sz-border-default);
  --el-border-color-light: var(--sz-border-default);
  --el-bg-color-page: var(--sz-bg-subtle);

  --el-checkbox-checked-bg-color: var(--sz-color-primary);
  --el-checkbox-checked-border-color: var(--sz-color-primary);
  --el-checkbox-checked-text-color: var(--sz-color-primary);
  --el-radio-checked-text-color: var(--sz-color-primary);
  --el-radio-checked-input-border-color: var(--sz-color-primary);
  --el-radio-checked-icon-color: var(--sz-color-primary);
}
```

## Icon Assets

Use `assets/icons/iconfont` and `../shouzhu-icon-style/SKILL.md` before drawing or importing a new same-meaning icon.

- Action iconfont CSS: `assets/icons/iconfont/action-iconfont.css`.
- Menu iconfont CSS: `assets/icons/iconfont/menu-iconfont.css`.
- Common iconfont CSS: `assets/icons/iconfont/common-iconfont.css`.
- Use SVG/image files only for logos, empty-state illustrations, checkbox checkmark masks, special multicolor artwork, or fallback when iconfont has no matching glyph.

If a required icon is missing, use a text action first and add the missing icon to the design system assets later.
