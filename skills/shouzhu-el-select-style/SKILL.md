---
name: shouzhu-el-select-style
description: Shouzhu Element Plus select style skill. Use when creating, modifying, reviewing, or prototyping el-select, dropdown selects, single-select fields, select placeholders, opened select states, selected options, option hover states, disabled options, clearable selects, or select dropdown panels in Shouzhu Vue 3 + Element Plus admin pages.
---

# Shouzhu El Select Style

Use Element Plus `el-select` for dropdown selection. Do not rely on Element Plus default select radius, focus color, option spacing, selected option, hover option, or disabled option styling.

## Required Reading

Read `../shouzhu-admin-ui-design/references/tokens.md` and `../shouzhu-el-input-style/SKILL.md` before applying select styles.

## Required Class

- Base select class: `.sz-select`.
- Dropdown popper class: `.sz-select-popper`.
- Use `popper-class="sz-select-popper"` on `el-select`.

## Trigger Field

- Fixed height: `40px`.
- Border radius: `6px`.
- Horizontal padding follows input style.
- Text font-size: `14px`.
- Placeholder color: `var(--sz-text-placeholder)`.
- Selected value text color in the trigger field: `var(--sz-text-body)`.
- Default border: `var(--sz-border-default)`.
- Hover border: `var(--sz-color-primary)`.
- Opened/focused border: `var(--sz-color-primary)`.
- Arrow icon color: `#7C8BA6`.
- Disabled trigger follows disabled input style.

## Dropdown Panel

- Panel background: `var(--sz-color-white)`.
- Panel radius: `6px`.
- Panel padding: `8px`.
- Option vertical gap follows the 8px spacing grid.
- Panel shadow uses the global floating panel shadow: `var(--sz-shadow-panel)`, currently `0 4px 16px -6px rgb(0 0 0 / 10%)`.
- Clear Element Plus default popper border, default popper shadow, and popper arrow so the panel uses only the Shouzhu shadow.
- Panel width must match the trigger select width by default.
- Do not let long option text stretch the dropdown wider than the trigger.
- Do not let short option text shrink the dropdown narrower than the trigger.
- Only use a different dropdown width when the supplied design explicitly specifies it.

## Option Item

- Option height: `32px`.
- Option horizontal padding: `8px`.
- Option radius: `6px`.
- Option text size: `14px`.
- Default option text: `var(--sz-text-body)`.
- Selected option: background `var(--sz-color-primary-light)`, text `var(--sz-color-primary)`, weight `400`.
- Hover option: background `#FAFAFA`, text `var(--sz-text-body)`.
- Disabled option: text `var(--sz-text-placeholder)`, background transparent, cursor `not-allowed`.

## States

### Placeholder

- Empty select displays placeholder in weak hint color.
- Do not apply placeholder color to the selected value. In Element Plus, single-select selected text may render through `.el-select__placeholder` without `.is-transparent`; that state must use body text color.

### Selected Value In Trigger

- When an option has been selected, the text shown inside the select trigger must use body text color, `var(--sz-text-body)`.
- Selected trigger text must not use weak hint / placeholder color.

### Hover

- Trigger border changes to `var(--sz-color-primary)`.

### Opened / Focused

- Trigger border changes to `var(--sz-color-primary)`.
- Arrow can rotate upward.
- Dropdown panel is shown below the trigger with `8px` gap when space allows.
- Dropdown panel keeps the same width as the trigger.

### Selected Option

- Use light primary background and primary text.
- Do not add checkmarks unless the design explicitly requires them.

### Disabled Option

- Use weak hint color.
- Do not apply hover highlight.

## Forbidden

- Do not use Element Plus default `4px` radius.
- Do not use Element Plus default selected option color if it differs from `#0068FF`.
- Do not make option rows taller or shorter unless a supplied design specifies it.
- Do not place option text on multiple lines.
- Do not use a dark dropdown panel.
- Do not allow the dropdown panel to become wider or narrower than the select trigger by default.

## CSS Contract

```css
.sz-select.el-select {
  width: 100%;
}

.sz-select .el-select__wrapper {
  min-height: 40px;
  height: 40px;
  border-radius: 6px;
  background: var(--sz-color-white);
  box-shadow: 0 0 0 1px var(--sz-border-default) inset;
  transition: box-shadow 0.16s ease, background-color 0.16s ease;
}

.sz-select:hover .el-select__wrapper,
.sz-select .el-select__wrapper.is-focused {
  box-shadow: 0 0 0 1px var(--sz-color-primary) inset;
}

.sz-select .el-select__placeholder {
  color: var(--sz-text-body);
  font-size: var(--sz-font-size-body);
}

.sz-select .el-select__placeholder.is-transparent {
  color: var(--sz-text-placeholder);
}

.sz-select .el-select__selected-item,
.sz-select .el-select__selected-item .el-select__tags-text {
  color: var(--sz-text-body);
  font-size: var(--sz-font-size-body);
}

.sz-select .el-select__caret {
  color: #7C8BA6;
}

.sz-select.is-disabled .el-select__wrapper,
.sz-select .el-select__wrapper.is-disabled {
  cursor: not-allowed;
  background: #F7F8FA;
  box-shadow: 0 0 0 1px var(--sz-border-default) inset;
}

.sz-select-popper.el-popper {
  border: 0;
  border-radius: 6px;
  box-shadow: var(--sz-shadow-panel);
}

.sz-select-popper.el-popper,
.sz-select-popper .el-popper__popper {
  box-shadow: var(--sz-shadow-panel);
}

.sz-select-popper .el-popper__arrow {
  display: none;
}

.sz-select-popper .el-select-dropdown {
  border: 0;
  border-radius: 6px;
  box-shadow: none;
}

.sz-select-popper .el-select-dropdown__list {
  padding: 8px;
}

.sz-select-popper .el-select-dropdown__item {
  height: 32px;
  margin: 0 0 8px;
  padding: 0 8px;
  border-radius: 6px;
  color: var(--sz-text-body);
  font-size: var(--sz-font-size-body);
  line-height: 32px;
}

.sz-select-popper .el-select-dropdown__item:last-child {
  margin-bottom: 0;
}

.sz-select-popper .el-select-dropdown__item.hover,
.sz-select-popper .el-select-dropdown__item:hover {
  color: var(--sz-text-body);
  background: #FAFAFA;
}

.sz-select-popper .el-select-dropdown__item.selected {
  color: var(--sz-color-primary);
  background: var(--sz-color-primary-light);
  font-weight: var(--sz-font-weight-regular);
}

.sz-select-popper .el-select-dropdown__item.is-disabled {
  color: var(--sz-text-placeholder);
  background: transparent;
  cursor: not-allowed;
}
```
