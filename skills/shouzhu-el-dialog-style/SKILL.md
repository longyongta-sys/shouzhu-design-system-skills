---
name: shouzhu-el-dialog-style
description: Shouzhu Element Plus dialog form style skill. Use when creating, modifying, reviewing, or prototyping el-dialog form dialogs, add dialogs, edit dialogs, approval dialogs, drawer-like modal forms, dialog headers, dialog body scroll, or dialog footer actions in Shouzhu Vue 3 + Element Plus admin pages.
---

# Shouzhu El Dialog Style

Use this skill for add, edit, approval, and other modal dialogs that contain form controls.

## Required Reading

Read `../shouzhu-admin-ui-design/references/tokens.md`, `../shouzhu-el-form-style/SKILL.md`, `../shouzhu-el-button-style/SKILL.md`, and `../shouzhu-icon-style/SKILL.md` when the dialog contains form fields, action buttons, or a close icon.

## Structure

```vue
<el-dialog
  v-model="visible"
  class="sz-dialog-form is-single-column"
  width="550px"
  :close-on-click-modal="false"
  :close-on-press-escape="false"
  :append-to-body="true"
>
  <template #header>
    <div class="dialog-form-head">
      <h3>弹窗标题</h3>
    </div>
  </template>

  <div class="dialog-form-body">
    <el-form label-position="top" class="sz-form dialog-form-control">
      <el-row :gutter="16">
        <el-col :span="12">...</el-col>
        <el-col :span="12">...</el-col>
        <el-col :span="24">...</el-col>
      </el-row>
    </el-form>
  </div>

  <template #footer>
    <div class="dialog-form-footer">
      <el-button class="sz-btn sz-btn-outline sz-btn-large">取消</el-button>
      <el-button class="sz-btn sz-btn-primary sz-btn-large">确定</el-button>
    </div>
  </template>
</el-dialog>
```

## Usage

- Use Element Plus `el-dialog`.
- Use for add, edit, approval, and other form-driven modal workflows.
- Do not use this form dialog style for lightweight confirm/alert feedback. Use `../shouzhu-el-message-box-style/SKILL.md` for those.

## Dimensions And Surface

- Default/minimum width: `550px`.
- Max width: `650px`.
- One-column form dialog uses the minimum/default width: `550px`.
- Two-column form dialog uses the maximum width: `650px`.
- Width adapts to viewport: single-column `width: min(calc(100vw - 32px), 550px)`; two-column `width: min(calc(100vw - 32px), 650px)`.
- Use `class="sz-dialog-form is-single-column"` for one-column forms.
- Use `class="sz-dialog-form is-two-column"` for two-column forms.
- Surface background: white.
- Radius: `12px`.
- Shadow: none.
- Overlay: black at 50% opacity, `rgb(0 0 0 / 50%)`.
- Close by clicking overlay: disabled.
- Close by pressing ESC: disabled.
- Right-top close button: shown.

## Dialog Padding And Layout

- Dialog inner padding: `24px`.
- Header/body/footer must clear Element Plus default padding rather than stacking extra padding.
- Header padding: `0`.
- Header bottom gap: `24px`.
- Body padding: `0`.
- Body max-height: adaptive to content and viewport.
- Body overflow: only the body scrolls when content is taller than the available viewport.
- Footer padding: `0`.
- Footer top gap: `24px`.
- Footer is fixed/sticky at the bottom when the body scrolls.
- Footer has no top divider line.

## Header

- Title text is the actual dialog title.
- Title font-size: `16px`.
- Title weight: `700`.
- Title color: title color, `var(--sz-text-title)`.
- Close icon size: `20px * 20px`.
- Close icon color: title color, `var(--sz-text-title)`.
- Close hover style: no visible background or color change.

## Body Form

- Form labels use top position.
- Form can use one or two columns depending on content, but must not exceed two columns.
- If the form has only one column, use the minimum/default dialog width `550px`.
- If the form has two columns, use the maximum dialog width `650px`.
- Two-column fields use `el-row :gutter="16"` and `el-col :span="12"`.
- Full-width fields use `el-col :span="24"`.
- Form column gap: `16px`.
- Dialog form item vertical gap: `16px`.
- Content width adapts to available width and must not create horizontal scrolling.

## Footer Actions

- Footer buttons align right.
- Button gap: `16px`.
- Footer uses large button sizing.
- Cancel button uses the outline button style.
- Confirm button uses the primary regular button style.

## CSS Contract

```css
.sz-dialog-form.el-dialog {
  width: min(calc(100vw - 32px), 550px);
  max-width: 650px;
  padding: 24px;
  border-radius: 12px;
  box-shadow: none;
  background: var(--sz-color-white);
}

.sz-dialog-form.is-single-column.el-dialog {
  width: min(calc(100vw - 32px), 550px);
}

.sz-dialog-form.is-two-column.el-dialog {
  width: min(calc(100vw - 32px), 650px);
}

.sz-dialog-form .el-dialog__header {
  padding: 0;
  margin: 0 0 24px;
}

.sz-dialog-form .el-dialog__title,
.sz-dialog-form .dialog-form-head h3 {
  margin: 0;
  color: var(--sz-text-title);
  font-size: 16px;
  font-weight: var(--sz-font-weight-bold);
  line-height: var(--sz-line-height-base);
}

.sz-dialog-form .el-dialog__headerbtn {
  top: 24px;
  right: 24px;
  width: 20px;
  height: 20px;
  color: var(--sz-text-title);
}

.sz-dialog-form .el-dialog__headerbtn .el-dialog__close {
  color: var(--sz-text-title);
  font-size: 20px;
}

.sz-dialog-form .el-dialog__headerbtn:hover,
.sz-dialog-form .el-dialog__headerbtn:hover .el-dialog__close {
  color: var(--sz-text-title);
  background: transparent;
}

.sz-dialog-form .el-dialog__body {
  padding: 0;
  max-height: min(60vh, 560px);
  overflow-y: auto;
  overflow-x: hidden;
}

.sz-dialog-form .el-dialog__footer {
  position: sticky;
  bottom: 0;
  padding: 0;
  margin-top: 24px;
  background: var(--sz-color-white);
}

.sz-dialog-form .dialog-form-footer {
  display: flex;
  justify-content: flex-end;
  gap: 16px;
}

.sz-dialog-form .sz-form .el-form-item {
  margin-bottom: 16px;
}

.el-overlay {
  background-color: rgb(0 0 0 / 50%);
}
```

For a two-column form dialog, use the maximum width and class:

```vue
<el-dialog class="sz-dialog-form is-two-column" width="650px" ...>
```

## Forbidden

- Do not close form dialogs by clicking the overlay.
- Do not close form dialogs by pressing ESC.
- Do not add dialog surface shadow.
- Do not stack Element Plus default padding with Shouzhu dialog padding.
- Do not use more than two form columns.
- Do not add a footer divider.
- Do not center footer actions in form dialogs.
