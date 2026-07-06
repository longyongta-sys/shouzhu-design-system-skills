# Component Routing Index

This file is only an index. Detailed component rules live in standalone sibling skills. Do not use this file as a substitute for the relevant component skill.

## Locked Page Rules

The admin shell layout and the fixed left primary menu are hard rules. They are not optional style suggestions.

- Page layout must follow `layout.md`.
- Left primary menu must follow `../../shouzhu-primary-menu-style/SKILL.md`.
- The primary menu width is fixed at `200px`.
- The topbar height is fixed at `64px`.
- The page background is `#F2F2F2`.
- The workspace background is white and uses `16px` radius.
- Do not change the layout, sidebar structure, menu spacing, menu selected state, menu hover state, or bottom menu actions unless the design system itself is explicitly being updated.

## Source Of Truth

Use these files as the source of truth:

- Global tokens: `tokens.md`.
- Shell, topbar, workspace, scroll ownership: `layout.md`.
- Left primary menu: `../../shouzhu-primary-menu-style/SKILL.md`.
- Icons and iconfont mappings: `../../shouzhu-icon-style/SKILL.md`.
- Final audit: `checklist.md`.

## Component Skills Already Defined

- Buttons: `../../shouzhu-el-button-style/SKILL.md`.
- Form layout and labels: `../../shouzhu-el-form-style/SKILL.md`.
- Input: `../../shouzhu-el-input-style/SKILL.md`.
- Select: `../../shouzhu-el-select-style/SKILL.md`.
- Checkbox: `../../shouzhu-el-checkbox-style/SKILL.md`.
- Radio: `../../shouzhu-el-radio-style/SKILL.md`.
- Switch: `../../shouzhu-el-switch-style/SKILL.md`.
- Date picker: `../../shouzhu-el-date-picker-style/SKILL.md`.
- Image/video upload: `../../shouzhu-el-upload-style/SKILL.md`.
- Attachment upload: `../../shouzhu-el-attachment-upload-style/SKILL.md`.
- Tag: `../../shouzhu-el-tag-style/SKILL.md`.
- Table: `../../shouzhu-el-table-style/SKILL.md`.
- Pagination: `../../shouzhu-el-pagination-style/SKILL.md`.
- Tree: `../../shouzhu-el-tree-style/SKILL.md`.
- Detail display and detail page layout: `../../shouzhu-detail-style/SKILL.md`.
- Approval flow in right detail panel: `../../shouzhu-approval-flow-style/SKILL.md`.
- Dialog form: `../../shouzhu-el-dialog-style/SKILL.md`.
- MessageBox / confirmation dialog: `../../shouzhu-el-message-box-style/SKILL.md`.

## Component Selection Rules

- Use Element Plus components by default.
- If a component has an approved Shouzhu component skill, follow that Shouzhu skill.
- If a component has no approved Shouzhu component skill yet, use the Element Plus default style and behavior for that component.
- Do not invent custom styling for undefined components just to make them look more Shouzhu-like.
- Even when using Element Plus default component styling, the locked page layout, primary menu, global tokens, spacing grid, and scroll ownership still apply.
- Use image/video upload only for fields that accept images and/or videos as media cards.
- Use attachment upload for contracts, certificates, documents, compressed packages, and mixed file/image/video uploads.
- Use tags for status-like, type-like, result-like, and classification-like fields.
- Page filters and search areas use form components; do not define filters inside the table spec.
- Table pages must fill the available content width.
- Do not create custom div controls when Element Plus can express the behavior.

## Still Undefined

These components have not been approved yet. If a task requires them, use Element Plus default styling and behavior unless the designer asks to define a Shouzhu-specific rule:

- Tabs.
- Drawer.
- Cascader / tree-select.
- Tooltip / popover / popconfirm.
- Alert / message / notification.
- Breadcrumb / page header.
- Steps / progress.
- Descriptions using Element Plus bordered layouts.
- Skeleton / loading overlays beyond local component loading states.

## Conflict Rule

If this index conflicts with a standalone component skill, the standalone component skill wins. If a component skill conflicts with `layout.md` or `shouzhu-primary-menu-style`, the layout or menu rule wins.
