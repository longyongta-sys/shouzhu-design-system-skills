---
name: shouzhu-el-input-style
description: Shouzhu Element Plus input style skill. Use when creating, modifying, reviewing, or prototyping el-input, text input fields, search inputs, clearable inputs, prefix/suffix icon inputs, placeholder states, hover states, focus/inputting states, disabled inputs, or error inputs in Shouzhu Vue 3 + Element Plus admin pages.
---

# Shouzhu El Input Style

Use Element Plus `el-input` for single-line text input. Do not rely on Element Plus default input radius, border, focus, disabled, or error styling.

## Required Reading

Read `../shouzhu-admin-ui-design/references/tokens.md` before applying input styles.

## Required Class

- Base input class: `.sz-input`
- Error state can use Element Plus validation state or `.is-error`.

## Size

- Fixed height: `40px`.
- Border radius: `6px`.
- Horizontal padding: `12px`.
- Text font-size: `14px`.
- Text line-height: `1.5`.
- Width: `100%` inside forms, filters, dialogs, and search areas unless the design explicitly gives a fixed width.

## Colors

- Default border: `var(--sz-border-default)`.
- Hover border: `var(--sz-color-primary)`.
- Focus / inputting border: `var(--sz-color-primary)`.
- Input text: `var(--sz-text-body)`.
- Placeholder text: `var(--sz-text-placeholder)`.
- Disabled text: `var(--sz-text-placeholder)`.
- Disabled background: `#F7F8FA`.
- Error border: `var(--sz-color-danger)`.
- Error text: `var(--sz-color-danger)` when the input content itself is shown as invalid text.

## States

### Default

- Height `40px`.
- Border `1px solid var(--sz-border-default)`.
- Radius `6px`.
- Placeholder uses weak hint color.

### Hover

- Border changes to `var(--sz-color-primary)`.
- Placeholder and entered text keep their normal colors.

### Focus / Inputting

- Border changes to `var(--sz-color-primary)`.
- Caret color uses `var(--sz-color-primary)`.
- Clear icon may appear on the right when the input is clearable.
- Text remains `var(--sz-text-body)`.

### Disabled

- Border keeps `var(--sz-border-default)`.
- Background uses `#F7F8FA`.
- Text and placeholder use `var(--sz-text-placeholder)`.
- Cursor is `not-allowed`.

### Error

- Border changes to `var(--sz-color-danger)`.
- Error text uses `var(--sz-color-danger)`.
- Background stays white unless the design explicitly defines an error fill.

## Icon And Clear Button

- Prefix/suffix icon size: `16px * 16px`.
- Icon color: `var(--sz-text-placeholder)` by default.
- Clear icon size: `16px * 16px`.
- Clear icon color: `var(--sz-text-placeholder)`.
- Gap between text and suffix icon: `12px`.

## Forbidden

- Do not use Element Plus default `4px` input radius.
- Do not use Element Plus default focus blue if it differs from `#0068FF`.
- Do not replace labels with placeholders.
- Do not change disabled text to a high-contrast body color.
- Do not use red border for hover or focus unless the field is actually in error state.

## CSS Contract

```css
.sz-input.el-input {
  width: 100%;
}

.sz-input .el-input__wrapper {
  min-height: 40px;
  height: 40px;
  padding: 0 12px;
  border-radius: 6px;
  background: var(--sz-color-white);
  box-shadow: 0 0 0 1px var(--sz-border-default) inset;
  transition: box-shadow 0.16s ease, background-color 0.16s ease;
}

.sz-input .el-input__inner {
  height: 40px;
  color: var(--sz-text-body);
  font-size: var(--sz-font-size-body);
  line-height: 1.5;
  caret-color: var(--sz-color-primary);
}

.sz-input .el-input__inner::placeholder {
  color: var(--sz-text-placeholder);
}

.sz-input:hover .el-input__wrapper,
.sz-input .el-input__wrapper.is-focus {
  box-shadow: 0 0 0 1px var(--sz-color-primary) inset;
}

.sz-input.is-disabled .el-input__wrapper,
.sz-input .el-input__wrapper.is-disabled {
  cursor: not-allowed;
  background: #F7F8FA;
  box-shadow: 0 0 0 1px var(--sz-border-default) inset;
}

.sz-input.is-disabled .el-input__inner,
.sz-input .el-input__wrapper.is-disabled .el-input__inner {
  color: var(--sz-text-placeholder);
  cursor: not-allowed;
}

.sz-input.is-error .el-input__wrapper,
.el-form-item.is-error .sz-input .el-input__wrapper {
  box-shadow: 0 0 0 1px var(--sz-color-danger) inset;
}

.sz-input.is-error .el-input__inner,
.el-form-item.is-error .sz-input .el-input__inner {
  color: var(--sz-color-danger);
}

.sz-input .el-input__prefix,
.sz-input .el-input__suffix {
  color: var(--sz-text-placeholder);
}

.sz-input .el-input__clear {
  color: var(--sz-text-placeholder);
}
```
