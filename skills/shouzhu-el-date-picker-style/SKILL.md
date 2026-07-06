---
name: shouzhu-el-date-picker-style
description: Shouzhu Element Plus date picker style skill. Use when creating, modifying, reviewing, or prototyping el-date-picker, date input, date range picker, datetime picker, month picker, year picker, date panel, month panel, year panel, calendar cells, date range states, or date-picker poppers in Shouzhu Vue 3 + Element Plus admin pages.
---

# Shouzhu El Date Picker Style

Use Element Plus `el-date-picker`. The trigger input must follow the existing Shouzhu input style; the popper panel must follow the panel and cell rules below.

## Required Reading

Read `../shouzhu-admin-ui-design/references/tokens.md`, `../shouzhu-el-input-style/SKILL.md`, `../shouzhu-el-form-style/SKILL.md`, and `../shouzhu-icon-style/SKILL.md` before applying date picker styles.

## Supported Types

- Date picker: `type="date"`.
- Date range picker: `type="daterange"`.
- Date time picker: `type="datetime"`.
- Month picker: `type="month"`.
- Year picker: `type="year"`.
- Clearable is allowed.
- Shortcut options are not enabled by default. Add shortcuts only when the page has a clear business need.

## Structure

`popper-class="sz-date-picker-popper"` is mandatory for every Shouzhu date picker. The date panel override CSS must be written in a global stylesheet, not only inside a Vue `<style scoped>` block, because Element Plus date picker poppers are allowed to teleport to `body`.

```vue
<el-date-picker
  v-model="form.date"
  class="sz-date-picker"
  popper-class="sz-date-picker-popper"
  type="date"
  clearable
  editable
  format="YYYY-MM-DD"
  value-format="YYYY-MM-DD"
  placeholder="请选择日期"
/>
```

Date range:

```vue
<el-date-picker
  v-model="form.dateRange"
  class="sz-date-picker"
  popper-class="sz-date-picker-popper"
  type="daterange"
  clearable
  editable
  range-separator="-"
  start-placeholder="开始日期"
  end-placeholder="结束日期"
  format="YYYY-MM-DD"
  value-format="YYYY-MM-DD"
/>
```

Date time:

```vue
<el-date-picker
  v-model="form.datetime"
  class="sz-date-picker"
  popper-class="sz-date-picker-popper"
  type="datetime"
  clearable
  editable
  format="YYYY-MM-DD HH:mm:ss"
  value-format="YYYY-MM-DD HH:mm:ss"
  placeholder="请选择日期"
/>
```

Dialog form usage:

```vue
<el-date-picker
  v-model="form.date"
  class="sz-date-picker"
  popper-class="sz-date-picker-popper sz-date-picker-popper-dialog"
  type="date"
  placement="bottom-start"
  :teleported="true"
  clearable
  editable
  format="YYYY-MM-DD"
  value-format="YYYY-MM-DD"
  placeholder="璇烽€夋嫨鏃ユ湡"
/>
```

## Trigger Input

- Input height: follows `../shouzhu-el-input-style/SKILL.md`, currently `40px`.
- Input radius: follows existing input style, currently `6px`.
- Input border color: follows existing input style, `var(--sz-border-default)`.
- Hover/focus border color: follows existing input style, `var(--sz-color-primary)`.
- Placeholder color: follows existing input style, `var(--sz-text-placeholder)`.
- Icon size: `20px * 20px`.
- Icon color: weak hint text, `var(--sz-text-placeholder)`.
- Text size: `14px`.
- Text color: weak hint text, `var(--sz-text-placeholder)`, until a value is selected or typed.
- Selected/inputted value text color should use body text, `var(--sz-text-body)`.
- Form usage width: `100%`.
- Filter/search area does not use compact height by default.
- Manual input is allowed.
- Always set `format` and `value-format`.
- Default placeholder: `请选择日期`.

## Panel

- Panel background: white.
- Panel radius: `8px`.
- Panel shadow: `0 4px 16px -6px rgb(0 0 0 / 10%)`, equivalent to X `0`, Y `4`, blur `16`, spread `-6`, color `#000000` at `10%`.
- Panel padding: `16px`.
- Do not use Element Plus default panel width if it conflicts with the design.
- Date picker panel width must be based on calendar content, not the trigger input width. Single-date panels must never be compressed to a narrow input width.
- Single-month date panel minimum width: `322px`, from `7 * 38px` date cells + `6 * 4px` gaps + `16px` left/right panel padding.
- Teleporting to body is allowed. When teleported, `popper-class="sz-date-picker-popper"` is required so Shouzhu panel styles still apply.
- Because teleported poppers render outside the component DOM, `.sz-date-picker-popper` CSS must be loaded globally. If a page uses scoped SFC styles, put the popper rules in a separate unscoped `<style>` block or a shared global CSS file.
- No bottom confirm/cancel button area by default.

## Dialog Form Behavior

- Date pickers inside `el-dialog` / `.sz-dialog-form` must use the same trigger and panel rules as normal forms.
- Dialog date pickers must keep `teleported` enabled, normally `:teleported="true"`, so the popper is not clipped by the dialog body scroll container.
- Dialog date pickers must set `placement="bottom-start"` unless the supplied design explicitly requires another direction.
- Dialog date picker poppers use `popper-class="sz-date-picker-popper sz-date-picker-popper-dialog"`.
- The date panel should open below the trigger field whenever there is room. Do not let the calendar panel casually flip upward and cover preceding form fields in normal dialog layouts.
- If a dialog field is too close to the viewport bottom, the dialog body should scroll to create room for the opened panel; do not solve it by allowing the panel to cover the form title, previous fields, or footer actions.
- Do not set `teleported=false` for dialog date pickers unless there is a specific clipping or stacking bug and the resulting panel is visually verified.

## Panel Header

- Header horizontal padding follows panel padding: `16px`.
- Header height: keep compact and aligned with the design reference.
- Previous/next buttons use `32px * 32px` hit area when possible.
- Header title text color: body text, `var(--sz-text-body)`.
- Header title font size: `14px`.
- Header title weight: `500`.

## Date Cells

- Date cell size: `38px * 38px`.
- Date cell gap: `4px` between adjacent date cells, including horizontal and vertical spacing. Do not squeeze cells into a narrower panel.
- Date panel content width should fit `7 * 38px + 6 * 4px = 290px`; with `16px` panel padding on both sides, the single-month panel minimum width is `322px`.
- Calendar content must stay inside the white panel. If any weekday or date number overflows beyond the panel edge, the implementation is wrong and the popper/content width must be corrected.
- Date text size: `14px`.
- Normal date text color: body text, `var(--sz-text-body)`.
- Hover date background: primary 10%, `var(--sz-color-primary-light)`.
- Hover date text color: primary color, `var(--sz-color-primary)`.
- Selected date background: primary color, `var(--sz-color-primary)`.
- Selected date text color: white.
- Today date style: primary color, `var(--sz-color-primary)`.
- Disabled date text color: weak hint text, `var(--sz-text-placeholder)`.
- Adjacent-month dates also use weak hint text.

## Month And Year Cells

- Month/year panel uses the same panel background, radius, shadow, and padding.
- Month/year cell height follows the visual reference and should keep `16px` spacing between cells.
- Normal month/year text: body text, `14px`.
- Hover month/year background: primary 10%, text primary.
- Selected month/year background: primary, text white.
- Year range header uses body text, `14px`, weight `500`.

## Range Picker

- Range middle background: primary 10%, `var(--sz-color-primary-light)`.
- Range start/end background: primary color, `var(--sz-color-primary)`.
- Range start/end text color: white.
- Range hover style follows normal date hover unless the date is range start/end.
- Separator between the two inputs: `-`.

## Footer Buttons

- Do not show bottom buttons by default.
- Confirm, cancel, and clear buttons are not part of the current date picker standard.
- Clear behavior uses the input clear icon when `clearable` is enabled.

## Forbidden

- Do not use Element Plus default panel spacing when it conflicts with the Shouzhu panel.
- Do not omit `format` and `value-format`.
- Do not add footer confirm/cancel buttons unless a page-specific interaction requires them.
- Do not use shortcut panels by default.
- Do not use compact trigger height unless the design system later adds a date-picker compact variant.
- Do not let date picker popper styles disappear when teleported to body; always use the Shouzhu popper class.
- Do not ship a date panel that still shows Element Plus default calendar styling, such as small circular selected dates, default popper arrow, default narrow cell spacing, or default panel padding.
- Do not ship a dialog date picker whose panel opens upward over normal form content when the field can reasonably scroll or be placed to open downward.
- Do not make a date picker panel match the trigger input width. This rule differs from select dropdowns: selects match the trigger width, date picker panels use their own calendar content width.
- Do not ship a date picker panel where weekday labels or date cells overflow outside the white panel.

## Implementation Checks

If the opened calendar panel still looks like Element Plus default, check these items before handoff:

- `el-date-picker` includes `popper-class="sz-date-picker-popper"`.
- The `.sz-date-picker-popper` CSS is global, not trapped in `<style scoped>`.
- The popper arrow is hidden.
- The selected date cell renders as a `38px * 38px` Shouzhu cell, not a small default circle.
- The panel uses `16px` padding, `8px` radius, and `var(--sz-shadow-panel)`.
- The panel width is at least `322px`, and all 7 weekday/date columns remain inside the white panel.
- In dialogs, the date picker uses `placement="bottom-start"` and `:teleported="true"`.
- In dialogs, the opened date panel does not cover the dialog title, previous fields, or footer actions during normal use.

## CSS Contract

```css
/* Trigger styles may live beside the component. Popper styles below must be global. */
.sz-date-picker.el-date-editor {
  width: 100%;
}

.sz-date-picker.el-input,
.sz-date-picker.el-date-editor.el-input,
.sz-date-picker.el-date-editor.el-input__wrapper {
  height: 40px;
}

.sz-date-picker .el-input__wrapper,
.sz-date-picker.el-date-editor .el-input__wrapper {
  height: 40px;
  min-height: 40px;
  border-radius: 6px;
  box-shadow: 0 0 0 1px var(--sz-border-default) inset;
}

.sz-date-picker .el-input__wrapper:hover,
.sz-date-picker.el-date-editor .el-input__wrapper:hover {
  box-shadow: 0 0 0 1px var(--sz-color-primary) inset;
}

.sz-date-picker .el-input__wrapper.is-focus,
.sz-date-picker.el-date-editor .el-input__wrapper.is-focus {
  box-shadow: 0 0 0 1px var(--sz-color-primary) inset;
}

.sz-date-picker .el-input__inner {
  color: var(--sz-text-body);
  font-size: var(--sz-font-size-body);
}

.sz-date-picker .el-input__inner::placeholder {
  color: var(--sz-text-placeholder);
}

.sz-date-picker .el-input__prefix,
.sz-date-picker .el-input__suffix,
.sz-date-picker .el-range__icon,
.sz-date-picker .el-range__close-icon {
  color: var(--sz-text-placeholder);
  font-size: 20px;
}

.sz-date-picker-popper.el-popper,
.sz-date-picker-popper.el-picker__popper {
  width: max-content !important;
  min-width: 322px;
  max-width: calc(100vw - 32px);
  border: 0;
  border-radius: 8px;
  box-shadow: var(--sz-shadow-panel);
  overflow: visible;
}

.sz-date-picker-popper-dialog.el-popper,
.sz-date-picker-popper-dialog.el-picker__popper {
  z-index: 3000;
}

.sz-date-picker-popper .el-popper__arrow {
  display: none;
}

.sz-date-picker-popper .el-picker-panel {
  width: max-content;
  min-width: 322px;
  border: 0;
  border-radius: 8px;
  background: #FFFFFF;
  box-shadow: none;
  color: var(--sz-text-body);
  box-sizing: border-box;
}

.sz-date-picker-popper .el-picker-panel__body,
.sz-date-picker-popper .el-picker-panel__body-wrapper {
  padding: 16px;
  box-sizing: border-box;
}

.sz-date-picker-popper .el-picker-panel__body-wrapper {
  width: max-content;
  min-width: 322px;
}

.sz-date-picker-popper .el-picker-panel__content {
  width: 290px;
  margin: 0;
}

.sz-date-picker-popper .el-picker-panel__footer {
  display: none;
}

.sz-date-picker-popper .el-date-picker__header {
  height: 32px;
  margin: 0 0 16px;
  padding: 0;
  color: var(--sz-text-body);
}

.sz-date-picker-popper .el-date-picker__header-label {
  color: var(--sz-text-body);
  font-size: var(--sz-font-size-body);
  font-weight: var(--sz-font-weight-medium);
}

.sz-date-picker-popper .el-picker-panel__icon-btn {
  width: 32px;
  height: 32px;
  margin: 0;
  color: var(--sz-text-body);
  font-size: 16px;
  line-height: 32px;
}

.sz-date-picker-popper .el-date-table th {
  padding: 0 0 8px;
  color: var(--sz-text-secondary);
  font-size: var(--sz-font-size-body);
  font-weight: var(--sz-font-weight-regular);
  text-align: center;
  border-bottom: 0;
}

.sz-date-picker-popper .el-date-table td {
  width: 38px;
  height: 38px;
  padding: 0;
}

.sz-date-picker-popper .el-date-table {
  width: 290px !important;
  border-collapse: separate;
  border-spacing: 4px;
  table-layout: fixed;
}

.sz-date-picker-popper .el-date-table td .el-date-table-cell {
  width: 38px;
  height: 38px;
  padding: 0;
}

.sz-date-picker-popper .el-date-table td .el-date-table-cell__text {
  width: 38px;
  height: 38px;
  line-height: 38px;
  border-radius: 8px !important;
  color: var(--sz-text-body);
  font-size: var(--sz-font-size-body);
}

.sz-date-picker-popper .el-date-table td.available:hover .el-date-table-cell__text {
  color: var(--sz-color-primary);
  background: var(--sz-color-primary-light);
}

.sz-date-picker-popper .el-date-table td.today .el-date-table-cell__text {
  color: var(--sz-color-primary);
  font-weight: var(--sz-font-weight-regular);
}

.sz-date-picker-popper .el-date-table td.current:not(.disabled) .el-date-table-cell__text,
.sz-date-picker-popper .el-date-table td.start-date .el-date-table-cell__text,
.sz-date-picker-popper .el-date-table td.end-date .el-date-table-cell__text {
  color: #FFFFFF;
  background: var(--sz-color-primary);
  border-radius: 8px !important;
}

.sz-date-picker-popper .el-date-table td.in-range .el-date-table-cell {
  background: var(--sz-color-primary-light);
}

.sz-date-picker-popper .el-date-table td.disabled .el-date-table-cell__text,
.sz-date-picker-popper .el-date-table td.prev-month .el-date-table-cell__text,
.sz-date-picker-popper .el-date-table td.next-month .el-date-table-cell__text {
  color: var(--sz-text-placeholder);
}

.sz-date-picker-popper .el-year-table td .cell,
.sz-date-picker-popper .el-month-table td .cell {
  height: 38px;
  line-height: 38px;
  border-radius: 8px;
  color: var(--sz-text-body);
  font-size: var(--sz-font-size-body);
}

.sz-date-picker-popper .el-year-table td .cell:hover,
.sz-date-picker-popper .el-month-table td .cell:hover {
  color: var(--sz-color-primary);
  background: var(--sz-color-primary-light);
}

.sz-date-picker-popper .el-year-table td.current:not(.disabled) .cell,
.sz-date-picker-popper .el-month-table td.current:not(.disabled) .cell {
  color: #FFFFFF;
  background: var(--sz-color-primary);
}
```
