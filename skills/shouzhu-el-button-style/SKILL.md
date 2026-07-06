---
name: shouzhu-el-button-style
description: Shouzhu Element Plus button style skill. Use when creating, modifying, reviewing, or prototyping buttons, button groups, icon buttons, primary actions, secondary actions, danger actions, loading buttons, or disabled button states in Shouzhu Vue 3 + Element Plus admin pages.
---

# Shouzhu El Button Style

Use Element Plus `el-button`. Do not rely on Element Plus default button styling.

## Required Reading

Read `../shouzhu-admin-ui-design/references/tokens.md` before applying button styles.

## Classes

- Base: `.sz-btn`
- Primary: `.sz-btn-primary`
- Secondary fill: `.sz-btn-secondary`
- Secondary outline: `.sz-btn-outline`
- Assist: `.sz-btn-assist`
- Danger: `.sz-btn-danger`
- Large: `.sz-btn-large`
- Small: `.sz-btn-small`
- Icon-only: `.sz-icon-btn`

## Size

- Large button: min-width `80px`, fixed height `40px`, horizontal padding `24px`, font-size `14px`, font-weight `400`, radius `8px`.
- Small button: min-width `72px`, fixed height `32px`, horizontal padding `16px`, font-size `12px`, font-weight `700`, radius `6px`.
- Icon + text gap: `4px`.
- Icon size in text buttons: `16px * 16px`.
- Icon-only action size: `24px * 24px` in table rows, circular.

## Types

- Primary: white text, background and border `var(--sz-color-primary)`.
- Secondary fill: text `var(--sz-text-secondary)`, background and border `#F4F6F6`.
- Secondary outline: text `var(--sz-text-body)`, white background, border `var(--sz-border-default)`.
- Assist: text `var(--sz-color-primary)`, background `var(--sz-color-primary-light)`, border `var(--sz-color-primary-light)`.
- Danger: white text, background and border `var(--sz-color-danger)`.

## States

- Define default, hover, active, disabled, and loading states for every button type used.
- Primary hover: background and border `var(--sz-color-primary-hover)`. Primary active: background and border `var(--sz-color-primary-active)`.
- Secondary fill hover: text `var(--sz-text-body)`, background and border `#EAEEF3`. Secondary fill active: background and border `#DDE3EA`.
- Secondary outline hover: text `var(--sz-color-primary)`, background `var(--sz-color-primary-light)`, border `var(--sz-border-default)`. Secondary outline active: background `var(--sz-color-primary-light)`, border `var(--sz-color-primary)`.
- Assist hover: background and border `var(--sz-color-primary-light)`. Assist active: background and border `#D9E9FF`.
- Danger hover: background and border `#C83A1B`. Danger active: background and border `#A92F16`.
- Disabled primary and danger buttons: white text, background and border `#C8CED8`.
- Disabled secondary, outline, and assist buttons: text `var(--sz-text-placeholder)`, background `#F5F7FA`, border `var(--sz-border-default)`.
- Loading state keeps the same visual type as the original button, shows the loading indicator before text, disables repeat clicking, and keeps text from shifting horizontally.
- Keep one primary button per operation area whenever possible.

## Forbidden

- Do not use Element Plus default radius or default primary blue.
- Do not let button text wrap or overflow.
- Do not create custom div buttons when `el-button` can express the action.
- Do not place multiple primary buttons in one operation area unless the design explicitly requires it.

## CSS Contract

```css
.sz-btn.el-button {
  border-radius: var(--radius-control);
  font-family: var(--font-family-base);
  display: inline-flex;
  align-items: center;
  justify-content: center;
  gap: 4px;
  white-space: nowrap;
}

.sz-btn-large.el-button {
  min-width: 80px;
  height: 40px;
  min-height: 40px;
  padding: 0 24px;
  font-size: var(--sz-font-size-body);
  font-weight: var(--sz-font-weight-regular);
  border-radius: 8px;
}

.sz-btn-small.el-button {
  min-width: 72px;
  height: 32px;
  min-height: 32px;
  padding: 0 16px;
  font-size: var(--sz-font-size-helper);
  font-weight: var(--sz-font-weight-bold);
  border-radius: 6px;
}

.sz-btn-primary.el-button {
  --el-button-bg-color: var(--sz-color-primary);
  --el-button-border-color: var(--sz-color-primary);
  --el-button-text-color: var(--sz-color-white);
  --el-button-hover-bg-color: var(--sz-color-primary-hover);
  --el-button-hover-border-color: var(--sz-color-primary-hover);
  --el-button-hover-text-color: var(--sz-color-white);
  --el-button-active-bg-color: var(--sz-color-primary-active);
  --el-button-active-border-color: var(--sz-color-primary-active);
  --el-button-active-text-color: var(--sz-color-white);
  --el-button-disabled-bg-color: #C8CED8;
  --el-button-disabled-border-color: #C8CED8;
  --el-button-disabled-text-color: var(--sz-color-white);
}

.sz-btn-secondary.el-button {
  --el-button-bg-color: #F4F6F6;
  --el-button-border-color: #F4F6F6;
  --el-button-text-color: var(--sz-text-secondary);
  --el-button-hover-bg-color: #EAEEF3;
  --el-button-hover-border-color: #EAEEF3;
  --el-button-hover-text-color: var(--sz-text-body);
  --el-button-active-bg-color: #DDE3EA;
  --el-button-active-border-color: #DDE3EA;
  --el-button-active-text-color: var(--sz-text-body);
  --el-button-disabled-bg-color: #F5F7FA;
  --el-button-disabled-border-color: var(--sz-border-default);
  --el-button-disabled-text-color: var(--sz-text-placeholder);
}

.sz-btn-outline.el-button {
  --el-button-bg-color: var(--sz-color-white);
  --el-button-border-color: var(--sz-border-default);
  --el-button-text-color: var(--sz-text-body);
  --el-button-hover-bg-color: var(--sz-color-primary-light);
  --el-button-hover-border-color: var(--sz-border-default);
  --el-button-hover-text-color: var(--sz-color-primary);
  --el-button-active-bg-color: var(--sz-color-primary-light);
  --el-button-active-border-color: var(--sz-color-primary);
  --el-button-active-text-color: var(--sz-color-primary);
  --el-button-disabled-bg-color: #F5F7FA;
  --el-button-disabled-border-color: var(--sz-border-default);
  --el-button-disabled-text-color: var(--sz-text-placeholder);
}

.sz-btn-assist.el-button {
  --el-button-bg-color: var(--sz-color-primary-light);
  --el-button-border-color: var(--sz-color-primary-light);
  --el-button-text-color: var(--sz-color-primary);
  --el-button-hover-bg-color: var(--sz-color-primary-light);
  --el-button-hover-border-color: var(--sz-color-primary-light);
  --el-button-hover-text-color: var(--sz-color-primary);
  --el-button-active-bg-color: #DCE7FF;
  --el-button-active-border-color: #DCE7FF;
  --el-button-active-text-color: var(--sz-color-primary);
  --el-button-disabled-bg-color: #F5F7FA;
  --el-button-disabled-border-color: var(--sz-border-default);
  --el-button-disabled-text-color: var(--sz-text-placeholder);
}

.sz-btn-danger.el-button {
  --el-button-bg-color: var(--sz-color-danger);
  --el-button-border-color: var(--sz-color-danger);
  --el-button-text-color: var(--sz-color-white);
  --el-button-hover-bg-color: #C83A1B;
  --el-button-hover-border-color: #C83A1B;
  --el-button-hover-text-color: var(--sz-color-white);
  --el-button-active-bg-color: #A92F16;
  --el-button-active-border-color: #A92F16;
  --el-button-active-text-color: var(--sz-color-white);
  --el-button-disabled-bg-color: #C8CED8;
  --el-button-disabled-border-color: #C8CED8;
  --el-button-disabled-text-color: var(--sz-color-white);
}

.sz-btn.el-button.is-loading {
  pointer-events: none;
}

.sz-btn.el-button.is-loading > span {
  display: inline-flex;
  align-items: center;
  gap: 4px;
}
```
