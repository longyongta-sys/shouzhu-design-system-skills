---
name: shouzhu-admin-ui-design
description: Shouzhu admin UI design-system skill for Vue 3 + Element Plus pages. Use when building, modifying, or reviewing Shouzhu/守筑后台管理页面、设计规范预览页、菜单、表单、表格、树、详情、标签、按钮、图标、弹窗表单、确认/告警/反馈对话框、分页器、颜色字体布局和后台壳布局 so output stays consistent with the approved design draft.
---

# Shouzhu Admin UI Design

## Purpose

Use this skill to make AI-generated Vue 3 + Element Plus admin pages match the approved Shouzhu design system. Treat the referenced files as implementation constraints unless the user explicitly overrides them.

## Required Reading

Always read:

- [references/tokens.md](references/tokens.md) for colors, typography, radius, sizing, Element Plus theme variables, and icon assets.
- [references/layout.md](references/layout.md) for the required admin shell, topbar, workspace, secondary menu, and scroll ownership.
- `../shouzhu-primary-menu-style/SKILL.md` for the fixed Shouzhu left primary menu, brand block, menu items, selected/hover states, and bottom actions.
- [references/components.md](references/components.md) for the component routing index, locked layout/menu rules, and list of approved component skills.
- [references/checklist.md](references/checklist.md) before final handoff.
- [references/spec-audit.md](references/spec-audit.md) when auditing, organizing, handing off, or checking coverage of the design-system skill.

Read when the task touches UI components, page content, or review. This is mandatory for any visible page or component work:

- Use the component style skills below instead of loading one large component file:
  - `../shouzhu-el-button-style/SKILL.md` for buttons, primary actions, secondary actions, danger actions, loading states, and icon buttons.
  - `../shouzhu-primary-menu-style/SKILL.md` for the fixed left primary menu and sidebar actions.
  - `../shouzhu-icon-style/SKILL.md` for icon assets, menu icons, table row icon actions, and icon-only buttons.
  - `../shouzhu-el-input-style/SKILL.md` for text inputs, search inputs, clearable inputs, placeholder, hover, focus/inputting, disabled, and error states.
  - `../shouzhu-el-select-style/SKILL.md` for dropdown selects, opened state, selected options, hover options, disabled options, and dropdown panels.
  - `../shouzhu-el-form-style/SKILL.md` for forms, inputs, selects, upload, search, textarea, labels, and validation states.
  - `../shouzhu-el-upload-style/SKILL.md` for image upload, video upload, media upload cards, upload progress, upload failure states, preview, delete, and re-upload.
  - `../shouzhu-el-attachment-upload-style/SKILL.md` for contracts, certificates, attachments, documents, compressed packages, and mixed image/video/file uploads.
  - `../shouzhu-el-date-picker-style/SKILL.md` for date pickers, date range pickers, datetime pickers, month pickers, year pickers, trigger inputs, and calendar panels.
  - `../shouzhu-el-checkbox-style/SKILL.md` for checkboxes, multi-select groups, checked states, disabled checked states, indeterminate states, and table selection checkboxes.
  - `../shouzhu-el-radio-style/SKILL.md` for radios, radio groups, single-choice fields, checked states, disabled states, and compact filter radio groups.
  - `../shouzhu-el-switch-style/SKILL.md` for switches, enable/disable controls, status toggles, loading switches, table switches, and switch confirmation behavior.
  - `../shouzhu-el-tag-style/SKILL.md` for status, type, result, and classification tags.
  - `../shouzhu-el-table-style/SKILL.md` for data tables, columns, row actions, empty states, table width, and table layout.
  - `../shouzhu-el-pagination-style/SKILL.md` for pagination below tables and lists.
  - `../shouzhu-el-tree-style/SKILL.md` for tree, organization tree, permission tree, menu tree, and category tree patterns.
  - `../shouzhu-detail-style/SKILL.md` for read-only key-value detail display.
  - `../shouzhu-approval-flow-style/SKILL.md` for approval flow timelines, audit records, approval histories, and review process sections inside the right detail panel.
  - `../shouzhu-el-dialog-style/SKILL.md` for form dialogs, add/edit dialogs, approval dialogs, and dialog footers.
  - `../shouzhu-el-message-box-style/SKILL.md` for confirmation, destructive confirmation, alert, and feedback dialogs.

Only read the component style skills that match the visible components in the task. Most page-building tasks need `tokens.md`, `layout.md`, the relevant component style skills, and `checklist.md`.

## Workflow

1. Identify whether the task is build, modification, or review.
2. Load the required references above.
3. Start from the shell layout and fixed primary menu, then apply tokens, then component rules.
4. Prefer Element Plus components; do not replace standard inputs/tables/forms with custom div controls unless Element Plus cannot express the behavior.
5. Apply the concrete structure, sizing, state, and Element Plus override rules from the relevant component style skills; do not rely on Element Plus defaults when Shouzhu specifies an override.
6. If a needed Element Plus component has no Shouzhu-specific style skill yet, use the Element Plus default component style and behavior. Do not invent custom Shouzhu styling for that undefined component.
7. Use the iconfont mappings in `../shouzhu-icon-style/SKILL.md` before drawing, importing, or inventing a new same-meaning icon.
8. Verify selected, hover, disabled, required, status, pagination, and responsive states.
9. Ensure the browser page itself does not scroll; long content must scroll inside the appropriate panel, table, dialog body, or content region.
10. Run available type/build checks for implementation tasks.
11. Perform a visual self-audit after the page is complete: inspect whether spacing, colors, typography, alignment, component states, scrolling, and responsive behavior are abnormal or inconsistent with the references.
12. If the self-audit finds any mismatch or visual anomaly, modify the page yourself and repeat the audit before final response.
13. Use the checklist before final response.

## Non-Negotiables

- Use Vue 3 + Element Plus patterns by default.
- Use the approved token values exactly unless the user changes the design system.
- The admin shell layout is locked: fixed `200px` left primary menu, fixed `64px` topbar, `16px` app-main padding, white `16px` radius workspace, and internal scrolling only.
- The left primary menu style is locked: do not change its width, brand block, spacing, selected state, hover state, bottom system management action, or return-home action unless the design system itself is explicitly being updated.
- Do not create marketing or landing-page layouts for admin pages.
- Do not use a dark sidebar.
- Do not omit the Shouzhu logo in the left primary menu.
- Do not place cards inside cards.
- Do not wrap page sections in decorative floating cards.
- Do not put filter controls into the table component spec; page filters call form controls.
- Tables must fill the available content width unless the user explicitly asks for a compact table.
- Dialog padding must override Element Plus defaults and match the dialog reference exactly.
- Component output must implement the required structure and CSS override points from the relevant Shouzhu component style skill, not only approximate the colors.
- Components without Shouzhu-specific rules use Element Plus default styling and behavior, while still obeying Shouzhu layout, menu, token, spacing, and scroll rules.
- Use tags for status-like, type-like, result-like, or classification-like fields.
- Do not allow text or UI elements to overlap.
- Do not hand off a page with known style anomalies or deviations from this design system; fix them first.
