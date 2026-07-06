# Shouzhu Design System Spec Audit

Last updated: 2026-07-01.

This file summarizes the current approved Shouzhu UI skill set. It is a handoff and review aid, not a replacement for the detailed component skills.

## Hard Rules

- Admin shell layout is locked and follows `layout.md`.
- Left primary menu is locked and follows `../../shouzhu-primary-menu-style/SKILL.md`.
- Primary menu width is fixed at `200px`.
- Topbar height is fixed at `64px`.
- Page background is `#F2F2F2`.
- Workspace is white, fills the available area, and uses `16px` radius.
- Browser page must not scroll; overflow belongs inside content panels, tables, trees, dialogs, or upload lists.
- Default layout spacing follows the 8px grid unless a component rule explicitly defines another value.

## Approved Foundations

- Tokens: `tokens.md`.
- Layout: `layout.md`.
- Component routing index: `components.md`.
- Final checklist: `checklist.md`.
- Icon source and mapping: `../../shouzhu-icon-style/SKILL.md`.
- Primary menu: `../../shouzhu-primary-menu-style/SKILL.md`.

## Approved Components

- Button: `../../shouzhu-el-button-style/SKILL.md`.
- Form: `../../shouzhu-el-form-style/SKILL.md`.
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
- Detail display: `../../shouzhu-detail-style/SKILL.md`.
- Dialog form: `../../shouzhu-el-dialog-style/SKILL.md`.
- MessageBox / confirmation dialog: `../../shouzhu-el-message-box-style/SKILL.md`.

## Current Asset Inventory

- Brand logo: `../assets/brand/shouzhu-logo.png`.
- Empty table illustration: `../assets/empty/table-empty.png`.
- D-DIN-PRO font: `../assets/fonts/D-DIN-PRO-700-BOLD.OTF`.
- Iconfont packages: `../assets/icons/iconfont`.
- Action SVG fallback icons: `../assets/icons/actions`.
- Common SVG fallback icons: `../assets/icons/common`.
- Attachment file type PNG icons: `../assets/icons/file-types`.

## Known Undefined Components

Use Element Plus default styling and behavior for these components unless the designer asks to define a Shouzhu-specific rule:

- Tabs.
- Drawer.
- Cascader / tree-select.
- Tooltip / popover / popconfirm.
- Alert / message / notification.
- Breadcrumb / page header.
- Steps / progress.
- Descriptions using Element Plus bordered layouts.
- Skeleton / loading overlays beyond local component loading states.

## Cleanup Performed

- `components.md` has been converted from an outdated rule dump into a routing index.
- Layout and primary menu are now marked as locked rules in the main skill, layout reference, menu skill, and component routing index.
- Attachment upload now uses official file type PNG assets instead of CSS-drawn file badges.
- Image/video upload delete uses close icon `icon-guanbi`, not the old upload-delete glyph.

## Installation Status

The working source lives under:

`C:/Users/lazyr/Documents/shouzhu design system/skills`

The installed Codex skill directory has been synchronized from the working source:

`C:/Users/lazyr/.codex/skills`

The old installed `shouzhu-admin-design` entry is deprecated and points users to `shouzhu-admin-ui-design`.
