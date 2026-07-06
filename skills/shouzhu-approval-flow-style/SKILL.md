---
name: shouzhu-approval-flow-style
description: Shouzhu approval flow style skill. Use when creating, modifying, reviewing, or prototyping approval timelines, audit records, review flows, approval status histories, or approval process sections inside the right 500px detail panel of Shouzhu Vue 3 + Element Plus admin detail pages.
---

# Shouzhu Approval Flow Style

Use this style for the approval flow shown inside a detail page.

## Required Reading

Read `../shouzhu-admin-ui-design/references/tokens.md`, `../shouzhu-detail-style/SKILL.md`, `../shouzhu-el-attachment-upload-style/SKILL.md`, and `../shouzhu-el-upload-style/SKILL.md` before applying this style.

## Usage Scope

- Use only inside detail pages.
- Use only in the right detail panel with fixed `500px` width.
- The approval flow width follows the parent container: `width: 100%`.
- Do not use this component in list pages, table rows, dialogs, or the left adaptive detail area unless the design system is explicitly updated.
- Long approval flows scroll with the right `500px` detail column. Do not create an internal scroll container for the approval flow itself, and do not make the whole two-column detail body scroll as one block.

## Section Title

- The section title text is fixed: `审核流程`.
- Use the same title style as detail section titles:
  - Font-size: `16px`.
  - Font-weight: `700`.
  - Text color: `var(--sz-text-title)`.
  - Leading mark: `3px` wide, `16px` high.
  - Leading mark color: `var(--sz-color-primary)`.
  - Gap between mark and title: `8px`.

## Status Types

Only these approval node statuses are supported:

- Start / 发起审核: primary color, `var(--sz-color-primary)`.
- Pending / 审核中: warning color, `var(--sz-color-warning)`.
- Passed / 审核通过: success color, `var(--sz-color-success)`.
- Failed / 审核未通过: danger color, `var(--sz-color-danger)`.
- Void / 审核作废: weak hint color, `var(--sz-text-placeholder)`.

Do not invent extra statuses such as withdrawn, transferred, timeout, add-sign, or countersign unless the design system is explicitly updated.

## Required Assets

Use the official PNG assets. Do not replace them with iconfont or SVG.

- Start / 发起审核: `../shouzhu-admin-ui-design/assets/approval-flow/approval-start.png`.
- Pending / 审核中: `../shouzhu-admin-ui-design/assets/approval-flow/approval-pending.png`.
- Passed / 审核通过: `../shouzhu-admin-ui-design/assets/approval-flow/approval-pass.png`.
- Failed / 审核未通过: `../shouzhu-admin-ui-design/assets/approval-flow/approval-fail.png`.
- Void / 审核作废: `../shouzhu-admin-ui-design/assets/approval-flow/approval-void.png`.

Icon rules:

- Icon size: `48px * 48px`.
- Icon switches automatically by node status.
- Icon is centered on the timeline vertical line.
- Icon must not be replaced by iconfont.

## Timeline Line

- Line color: `#CACACA`.
- Line width: `2px`.
- Line style: dashed.
- Dash spacing: about `4px`.
- The line runs through the whole approval flow between nodes.
- The last node does not show a line below it.
- The icon sits centered on the line.

## Node Layout

- Horizontal gap between icon column and content: `24px`.
- Node-to-node vertical gap: `0`.
- Icon top aligns with the node title top.
- Content card bottom to next node icon distance: `32px`.
- Each node uses a two-column header: title/status on the left, time on the right.
- Header and content card gap: `20px`.

Header:

- Title font-size: `14px`.
- Title font-weight: `700`.
- Title color: `var(--sz-text-title)`.
- Title is single-line ellipsis when too long.
- Status font-size: `14px`.
- Status font-weight: `700`.
- Status color follows the node status.
- Gap between title and status: `4px`.
- Time font-size: `14px`.
- Time font-weight: `400`.
- Time color: `var(--sz-text-secondary)`.
- Time is right-aligned.
- If a pending node has no time yet, hide the time rather than showing `--`.

## Content Card

- Show the content card only for nodes that already have content.
- Pending/waiting nodes without content show only title, status, and optional time.
- Card background: `#FAFAFA`.
- Card radius: `12px`.
- Card padding: `24px`.
- Field row gap: `12px`.
- Gap from field area to attachment card area: `20px`.
- Gap from field area to image area: `20px`.
- Hide rows that have no meaningful content, such as no opinion or no attachment.
- Empty values that must be displayed use `--`.
- Multi-line approval opinions wrap from the value text area.

Field rows:

- Render rows as `字段名：字段值`.
- Label color: `var(--sz-text-secondary)`.
- Value color: `var(--sz-text-body)`.
- Value font-weight: `700`.
- Label/value gap: `0`.
- Field font-size: `14px`.
- Field line-height: `1.5`.

## Node Content By Status

Start / 发起审核:

- Node title is business-specific, such as `XXX申请`.
- Status text: `发起审核`.
- Content card only shows applicant: `申请人：张安全`.
- Do not show application opinion, application files, or site images unless the design system is updated.

Passed / 审核通过 and Failed / 审核未通过:

- Node title is business-specific, such as `XXX审核`.
- Show reviewer: `审核人：何文珠`.
- Show approval opinion only when present.
- Show approval files only when present.
- Failed nodes may show site situation images when present.

Pending / 审核中:

- Node title is business-specific, such as `XXXX审核`.
- Status text: `审核中`.
- If no content exists, show only header/status and hide the content card.
- If no time exists, hide the time.

Void / 审核作废:

- Status text: `审核作废`.
- Use these fields when content exists:
  - `作废人：`
  - `作废原因：`
  - `作废文件：`
- The void time is shown only in the node header time position, not repeated inside the content card.

## Attachments

Use the attachment list visuals from `../shouzhu-el-attachment-upload-style/SKILL.md`, with approval-flow read-only behavior.

- Supports multiple attachments.
- Multiple attachments stack vertically.
- Use the official file type PNG assets from attachment upload rules.
- Approval flow attachment operations: view and download only.
- Do not show delete in approval history.
- View opens in the browser when the file can be viewed.
- Download triggers normal file download.

## Site Images

- Image size: `100px * 100px`.
- Image fit: `cover`.
- Image radius: use `8px` unless a supplied design explicitly changes it.
- Image gap: `8px`.
- Max images per row: `3`.
- More than 3 images wrap to the next row.
- Clicking an image opens preview.
- Hover shows a view overlay.

## Interaction

- Approval flow is fully expanded by default.
- Do not support collapsing individual nodes.
- Do not support "view more" truncation.
- Click attachment view to open the file in browser.
- Click attachment download to download the file.
- Click site image to preview the larger image.

## Structure

```vue
<section class="sz-approval-flow">
  <header class="sz-approval-title">
    <span class="title-mark"></span>
    <h2>审核流程</h2>
  </header>

  <div class="sz-approval-list">
    <article class="sz-approval-node is-pass">
      <div class="sz-approval-icon-wrap">
        <img class="sz-approval-icon" src="/assets/approval-flow/approval-pass.png" alt="审核通过" />
      </div>
      <div class="sz-approval-main">
        <header class="sz-approval-head">
          <div class="sz-approval-heading">
            <div class="sz-approval-node-title">XXX审核</div>
            <div class="sz-approval-status">审核通过</div>
          </div>
          <time class="sz-approval-time">2025-09-23 07:00:26</time>
        </header>
        <div class="sz-approval-card">
          <div class="sz-approval-fields">
            <div class="sz-approval-field">
              <span class="field-label">审核人：</span>
              <span class="field-value">何文珠</span>
            </div>
          </div>
        </div>
      </div>
    </article>
  </div>
</section>
```

## CSS Contract

```css
.sz-approval-flow {
  width: 100%;
  min-width: 0;
}

.sz-approval-title {
  display: flex;
  align-items: center;
  gap: 8px;
  margin: 0 0 24px;
}

.sz-approval-title .title-mark {
  width: 3px;
  height: 16px;
  flex: none;
  border-radius: 2px;
  background: var(--sz-color-primary);
}

.sz-approval-title h2 {
  margin: 0;
  color: var(--sz-text-title);
  font-size: var(--sz-font-size-title);
  font-weight: var(--sz-font-weight-bold);
  line-height: var(--sz-line-height-base);
}

.sz-approval-list {
  display: grid;
}

.sz-approval-node {
  position: relative;
  display: grid;
  grid-template-columns: 48px minmax(0, 1fr);
  column-gap: 24px;
  min-width: 0;
  padding-bottom: 32px;
}

.sz-approval-node:last-child {
  padding-bottom: 0;
}

.sz-approval-node::before {
  content: "";
  position: absolute;
  top: 48px;
  bottom: 0;
  left: 23px;
  width: 2px;
  background-image: repeating-linear-gradient(
    to bottom,
    #CACACA 0,
    #CACACA 4px,
    transparent 4px,
    transparent 8px
  );
}

.sz-approval-node:last-child::before {
  display: none;
}

.sz-approval-icon-wrap {
  position: relative;
  z-index: 1;
  width: 48px;
  height: 48px;
}

.sz-approval-icon {
  display: block;
  width: 48px;
  height: 48px;
  object-fit: contain;
}

.sz-approval-main {
  min-width: 0;
}

.sz-approval-head {
  display: grid;
  grid-template-columns: minmax(0, 1fr) auto;
  gap: 16px;
  align-items: start;
}

.sz-approval-heading {
  min-width: 0;
  display: grid;
  gap: 4px;
}

.sz-approval-node-title {
  overflow: hidden;
  color: var(--sz-text-title);
  font-size: var(--sz-font-size-body);
  font-weight: var(--sz-font-weight-bold);
  line-height: var(--sz-line-height-base);
  text-overflow: ellipsis;
  white-space: nowrap;
}

.sz-approval-status {
  font-size: var(--sz-font-size-body);
  font-weight: var(--sz-font-weight-bold);
  line-height: var(--sz-line-height-base);
}

.sz-approval-node.is-start .sz-approval-status {
  color: var(--sz-color-primary);
}

.sz-approval-node.is-pending .sz-approval-status {
  color: var(--sz-color-warning);
}

.sz-approval-node.is-pass .sz-approval-status {
  color: var(--sz-color-success);
}

.sz-approval-node.is-fail .sz-approval-status {
  color: var(--sz-color-danger);
}

.sz-approval-node.is-void .sz-approval-status {
  color: var(--sz-text-placeholder);
}

.sz-approval-time {
  color: var(--sz-text-secondary);
  font-size: var(--sz-font-size-body);
  font-weight: var(--sz-font-weight-regular);
  line-height: var(--sz-line-height-base);
  white-space: nowrap;
}

.sz-approval-card {
  margin-top: 20px;
  padding: 24px;
  border-radius: 12px;
  background: #FAFAFA;
}

.sz-approval-fields {
  display: grid;
  gap: 12px;
}

.sz-approval-field {
  display: flex;
  align-items: flex-start;
  min-width: 0;
  color: var(--sz-text-body);
  font-size: var(--sz-font-size-body);
  line-height: var(--sz-line-height-base);
}

.sz-approval-field .field-label {
  flex: none;
  color: var(--sz-text-secondary);
}

.sz-approval-field .field-value {
  min-width: 0;
  color: var(--sz-text-body);
  font-weight: var(--sz-font-weight-bold);
  overflow-wrap: anywhere;
}

.sz-approval-attachments,
.sz-approval-images {
  margin-top: 20px;
}

.sz-approval-images {
  display: grid;
  grid-template-columns: repeat(3, 100px);
  gap: 8px;
}

.sz-approval-image {
  position: relative;
  width: 100px;
  height: 100px;
  overflow: hidden;
  border: 0;
  border-radius: 8px;
  background: transparent;
  cursor: pointer;
}

.sz-approval-image img {
  display: block;
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.sz-approval-image::after {
  content: "查看";
  position: absolute;
  inset: 0;
  display: grid;
  place-items: center;
  opacity: 0;
  color: #FFFFFF;
  font-size: var(--sz-font-size-body);
  font-weight: var(--sz-font-weight-bold);
  background: rgb(0 0 0 / 50%);
  transition: opacity 0.16s ease;
}

.sz-approval-image:hover::after {
  opacity: 1;
}
```

## Forbidden

- Do not use this component outside the right `500px` detail panel.
- Do not replace approval status PNG icons with iconfont.
- Do not add unsupported statuses.
- Do not show empty opinion or empty attachment rows.
- Do not show a content card for pending nodes when no content exists.
- Do not add collapse, expand, or "view more" interactions.
- Do not create an internal scroll area for the approval flow.
- Do not show delete actions in approval history attachments.
