---
name: shouzhu-el-radio-style
description: Shouzhu Element Plus radio style skill. Use when creating, modifying, reviewing, or prototyping el-radio, el-radio-group, single-choice fields, radio options in forms, radio hover/checked/disabled states, or compact filter radio groups in Shouzhu Vue 3 + Element Plus admin pages.
---

# Shouzhu El Radio Style

Use Element Plus `el-radio` and `el-radio-group`. Do not use button-style radio groups or segmented radio buttons unless the design system explicitly adds that component later.

## Required Reading

Read `../shouzhu-admin-ui-design/references/tokens.md` and `../shouzhu-el-form-style/SKILL.md` before applying radio styles inside forms.

## Structure

```vue
<el-radio-group v-model="form.type" class="sz-radio-group">
  <el-radio class="sz-radio" label="normal">未选</el-radio>
  <el-radio class="sz-radio" label="selected">已选</el-radio>
</el-radio-group>
```

Compact filter usage:

```vue
<el-radio-group v-model="filter.status" class="sz-radio-group is-compact">
  <el-radio class="sz-radio" label="all">全部</el-radio>
  <el-radio class="sz-radio" label="enabled">启用</el-radio>
  <el-radio class="sz-radio" label="disabled">禁用</el-radio>
</el-radio-group>
```

## Overall

- Use Element Plus `el-radio`.
- Button-style radio is not allowed.
- Radio must have visible label text.
- Radio and label gap: `8px`.
- Horizontal radio group gap: `24px`.
- Vertical radio group gap: `24px`.
- Radio options may wrap when there are many options.
- Radio is not used inside tables by default.
- Compact spacing is allowed in filter/search areas.

## Unchecked State

- Outer circle size: `16px * 16px`.
- Outer border width: `1px`.
- Outer border color: default line color, `var(--sz-border-default)`.
- Background: white.
- Text color: body text, `var(--sz-text-body)`.
- Text size: `14px`.
- Text weight: `400`.

## Checked State

- Outer circle size does not change: `16px * 16px`.
- Outer border color: primary color, `var(--sz-color-primary)`.
- Outer background: white.
- Inner dot size: `8px * 8px`.
- Inner dot color: primary color, `var(--sz-color-primary)`.
- Text color: body text, `var(--sz-text-body)`.
- Text is not bold.

## Hover State

- Hover outer border color: primary color, `var(--sz-color-primary)`.
- Hover text color does not change.
- Hover does not add a background.

## Disabled State

Disabled unchecked:

- Outer border color: default line color, `var(--sz-border-default)`.
- Outer background: `#EEEEEE`.
- Text color: secondary text, `var(--sz-text-secondary)`.

Disabled checked:

- Outer border color: default line color, `var(--sz-border-default)`.
- Outer background: `#EEEEEE`.
- Inner dot color: weak hint text, `var(--sz-text-placeholder)`.
- Text color: secondary text, `var(--sz-text-secondary)`.

## Error State

- Radio does not define a special error state in the current standard.
- Form validation error text belongs to `el-form-item`, not to the radio circle itself.

## Forbidden

- Do not use `el-radio-button`.
- Do not make selected radio text bold.
- Do not use radio controls inside normal data tables unless the user explicitly designs a table single-select interaction.
- Do not replace radio with checkbox or segmented buttons.
- Do not remove visible label text.

## CSS Contract

```css
.sz-radio-group.el-radio-group {
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  gap: 24px;
}

.sz-radio-group.is-vertical {
  flex-direction: column;
  align-items: flex-start;
  gap: 24px;
}

.sz-radio-group.is-compact {
  gap: 16px;
}

.sz-radio.el-radio {
  display: inline-flex;
  align-items: center;
  height: auto;
  margin-right: 0;
  color: var(--sz-text-body);
  font-size: var(--sz-font-size-body);
  font-weight: var(--sz-font-weight-regular);
}

.sz-radio .el-radio__input {
  display: inline-flex;
  align-items: center;
  justify-content: center;
}

.sz-radio .el-radio__inner {
  width: 16px;
  height: 16px;
  border-width: 1px;
  border-color: var(--sz-border-default);
  background: #FFFFFF;
}

.sz-radio .el-radio__input:hover .el-radio__inner {
  border-color: var(--sz-color-primary);
}

.sz-radio .el-radio__input.is-checked .el-radio__inner {
  border-color: var(--sz-color-primary);
  background: #FFFFFF;
}

.sz-radio .el-radio__input.is-checked .el-radio__inner::after {
  width: 8px;
  height: 8px;
  background: var(--sz-color-primary);
  transform: translate(-50%, -50%) scale(1);
}

.sz-radio .el-radio__label {
  padding-left: 8px;
  color: var(--sz-text-body);
  font-size: var(--sz-font-size-body);
  font-weight: var(--sz-font-weight-regular);
  line-height: var(--sz-line-height-base);
}

.sz-radio .el-radio__input.is-checked + .el-radio__label {
  color: var(--sz-text-body);
  font-weight: var(--sz-font-weight-regular);
}

.sz-radio.is-disabled,
.sz-radio.is-disabled .el-radio__label {
  color: var(--sz-text-secondary);
}

.sz-radio .el-radio__input.is-disabled .el-radio__inner {
  border-color: var(--sz-border-default);
  background: #EEEEEE;
}

.sz-radio .el-radio__input.is-disabled.is-checked .el-radio__inner {
  border-color: var(--sz-border-default);
  background: #EEEEEE;
}

.sz-radio .el-radio__input.is-disabled.is-checked .el-radio__inner::after {
  background: var(--sz-text-placeholder);
}
```
