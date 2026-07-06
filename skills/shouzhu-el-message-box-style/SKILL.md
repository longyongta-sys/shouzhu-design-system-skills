---
name: shouzhu-el-message-box-style
description: Shouzhu Element Plus message box and lightweight dialog style skill. Use when creating, modifying, reviewing, or prototyping confirmation dialogs, delete confirmations, alert dialogs, feedback dialogs, one-button result dialogs, or el-message-box-like interactions in Shouzhu Vue 3 + Element Plus admin pages.
---

# Shouzhu El Message Box Style

Use this skill for lightweight dialogs without form fields.

## Required Reading

Read `../shouzhu-admin-ui-design/references/tokens.md` and `../shouzhu-el-button-style/SKILL.md` before applying message box styles.

## Types

- Regular confirm: title + body + gray-fill cancel button + primary confirm button.
- Destructive confirm: title + body + gray-fill cancel button + danger confirm button.
- Feedback: title + body + one acknowledgement button.
- No icon is used by default.

## Implementation

- Use Element Plus `ElMessageBox` when the interaction can be expressed with it.
- Use `el-dialog` to simulate the same style only when custom content or custom button layout is required.
- Do not use the form dialog style for lightweight confirmation content.

## Layout

- Width: `500px`.
- Width adapts to viewport: `width: min(calc(100vw - 32px), 500px)`.
- Surface background: white.
- Radius: `12px`.
- Padding: `32px`.
- Shadow: none unless Element Plus requires an unavoidable base layer; visually it should read as no shadow.
- Overlay follows the dialog overlay rule: black at 50% opacity, `rgb(0 0 0 / 50%)`.
- Title centered, `18px`, weight `700`, color `var(--sz-text-title)`.
- Body centered, `14px`, color `var(--sz-text-secondary)`, line-height `1.5`.
- Title-to-body gap: `16px`.
- Body-to-button group gap: `24px`.
- Actions centered.
- Two-button action gap: `16px`.
- Single-button feedback dialog keeps one centered button.
- Destructive confirm action uses danger color, `var(--sz-color-danger)`.

## Buttons

- Cancel button uses the secondary gray-fill button style: `#F4F6F6` background and secondary text.
- Regular confirm button uses the primary regular button style.
- Destructive confirm button uses the danger/alert button style.
- Buttons use large button sizing unless a supplied design explicitly changes the size.

## CSS Contract

```css
.sz-message-box.el-message-box,
.sz-message-box.el-dialog {
  width: min(calc(100vw - 32px), 500px);
  padding: 32px;
  border-radius: 12px;
  background: var(--sz-color-white);
  box-shadow: none;
}

.sz-message-box .el-message-box__header,
.sz-message-box .el-dialog__header {
  padding: 0;
  margin: 0;
  text-align: center;
}

.sz-message-box .el-message-box__title,
.sz-message-box .el-dialog__title {
  color: var(--sz-text-title);
  font-size: 18px;
  font-weight: var(--sz-font-weight-bold);
  line-height: var(--sz-line-height-base);
}

.sz-message-box .el-message-box__content,
.sz-message-box .el-dialog__body {
  padding: 16px 0 0;
  color: var(--sz-text-secondary);
  font-size: var(--sz-font-size-body);
  line-height: var(--sz-line-height-base);
  text-align: center;
}

.sz-message-box .el-message-box__btns,
.sz-message-box .el-dialog__footer {
  display: flex;
  justify-content: center;
  gap: 16px;
  padding: 24px 0 0;
}

.sz-message-box .el-message-box__status {
  display: none;
}
```

## Forbidden

- Do not use this component for forms.
- Do not left-align title, body, or actions.
- Do not add a footer divider.
- Do not use primary blue for destructive confirmation.
- Do not add success/warning/error icons by default.
