---
name: shouzhu-el-checkbox-style
description: Shouzhu Element Plus checkbox style skill. Use when creating, modifying, reviewing, or prototyping el-checkbox, table selection checkboxes, multi-select groups, checked states, disabled checked states, unchecked states, indeterminate states, or checkbox labels in Shouzhu Vue 3 + Element Plus admin pages.
---

# Shouzhu El Checkbox Style

Use Element Plus `el-checkbox` and Element Plus table selection columns. Do not replace checkboxes with handmade div controls.

## Required Reading

Read `../shouzhu-admin-ui-design/references/tokens.md` before applying checkbox styles. Read `../shouzhu-el-table-style/SKILL.md` when styling table selection checkboxes.

## Structure

```vue
<el-checkbox v-model="checked" class="sz-checkbox">多选项</el-checkbox>

<el-checkbox
  v-model="checked"
  class="sz-checkbox"
  :indeterminate="isIndeterminate"
>
  多选项
</el-checkbox>
```

For tables, keep Element Plus selection columns and center the checkbox:

```vue
<el-table-column type="selection" width="80" align="center" header-align="center" />
```

## Size And Spacing

- Checkbox size: `16px * 16px`.
- Radius: `4px`.
- Checkbox and label gap: `8px`.
- Table selection checkbox must be horizontally centered in the selection column.

## States

- Unchecked border color: default line color, `var(--sz-border-default)`.
- Unchecked background: white.
- Hover border color: primary color, `var(--sz-color-primary)`.
- Checked background: primary color, `var(--sz-color-primary)`.
- Checked border color: primary color, `var(--sz-color-primary)`.
- Checked check icon: use `../shouzhu-admin-ui-design/assets/icons/common/checkbox-check.svg`.
- Checked check icon color: white, from the supplied SVG.
- Checked check icon must be visually centered in the `16px * 16px` checkbox. Use the supplied SVG at `16px * 16px` with `background-position: center`; do not redraw the checkmark with rotated CSS borders.
- Indeterminate state: primary blue background with a white horizontal bar.
- Disabled unchecked: light gray background, weak border, weak label text.
- Disabled checked: light gray background, weak border, gray check icon, weak label text.
- Disabled indeterminate: light gray background, weak border, gray horizontal bar, weak label text.

## Forbidden

- Do not use Element Plus default rounded checkbox corners if they differ from `4px`.
- Do not use a black, green, or other non-primary check color.
- Do not let table checkboxes align left inside the selection column.
- Do not use checkbox labels with less than `8px` gap.

## CSS Contract

```css
.sz-checkbox.el-checkbox {
  --el-checkbox-input-width: 16px;
  --el-checkbox-input-height: 16px;
  --el-checkbox-border-radius: 4px;
  --el-checkbox-input-border: 1px solid var(--sz-border-default);
  --el-checkbox-checked-bg-color: var(--sz-color-primary);
  --el-checkbox-checked-input-border-color: var(--sz-color-primary);
  --el-checkbox-checked-text-color: var(--sz-text-body);
  --el-checkbox-disabled-border-color: #ADB5C3;
  --el-checkbox-disabled-input-fill: #F4F6F6;
  --el-checkbox-disabled-checked-input-fill: #F4F6F6;
  --el-checkbox-disabled-checked-input-border-color: #ADB5C3;
  color: var(--sz-text-body);
  font-size: var(--sz-font-size-body);
}

.sz-checkbox .el-checkbox__input {
  display: inline-flex;
  align-items: center;
  justify-content: center;
}

.sz-checkbox .el-checkbox__inner {
  width: 16px;
  height: 16px;
  border-radius: 4px;
  border-color: var(--sz-border-default);
  background-color: #FFFFFF;
}

.sz-checkbox .el-checkbox__input:hover .el-checkbox__inner {
  border-color: var(--sz-color-primary);
}

.sz-checkbox .el-checkbox__input.is-checked .el-checkbox__inner {
  border-color: var(--sz-color-primary);
  background-color: var(--sz-color-primary);
  background-image: url("../shouzhu-admin-ui-design/assets/icons/common/checkbox-check.svg");
  background-repeat: no-repeat;
  background-position: center;
  background-size: 16px 16px;
}

.sz-checkbox .el-checkbox__inner::after {
  display: none;
}

.sz-checkbox .el-checkbox__label {
  padding-left: 8px;
  color: var(--sz-text-body);
  font-size: var(--sz-font-size-body);
  line-height: var(--sz-line-height-base);
}

.sz-checkbox .el-checkbox__input.is-indeterminate .el-checkbox__inner {
  border-color: var(--sz-color-primary);
  background-color: var(--sz-color-primary);
}

.sz-checkbox .el-checkbox__input.is-indeterminate .el-checkbox__inner::before {
  display: block;
  top: 7px;
  left: 3px;
  right: 3px;
  height: 2px;
  border-radius: 1px;
  background-color: #FFFFFF;
}

.sz-checkbox.is-disabled,
.sz-checkbox.is-disabled .el-checkbox__label {
  color: var(--sz-text-placeholder);
}

.sz-checkbox .el-checkbox__input.is-disabled .el-checkbox__inner {
  border-color: #ADB5C3;
  background-color: #F4F6F6;
}

.sz-checkbox .el-checkbox__input.is-disabled.is-checked .el-checkbox__inner {
  border-color: #ADB5C3;
  background-color: #F4F6F6;
  background-image: none;
}

.sz-checkbox .el-checkbox__input.is-disabled.is-checked .el-checkbox__inner::after {
  display: block;
  box-sizing: content-box;
  width: 4px;
  height: 8px;
  left: 5px;
  top: 1px;
  border: 2px solid #ADB5C3;
  border-left: 0;
  border-top: 0;
  transform: rotate(45deg) scaleY(1);
}

.sz-checkbox .el-checkbox__input.is-disabled.is-indeterminate .el-checkbox__inner::before {
  background-color: #ADB5C3;
}

.sz-table .el-table-column--selection .cell {
  display: flex;
  justify-content: center;
  padding: 0;
}
```
