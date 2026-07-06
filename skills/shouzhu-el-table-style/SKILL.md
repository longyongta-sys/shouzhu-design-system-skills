---
name: shouzhu-el-table-style
description: Shouzhu Element Plus table style skill. Use when creating, modifying, reviewing, or prototyping el-table, data lists, table columns, table row actions, status columns, selection columns, index columns, fixed operation columns, empty table states, or table layout in Shouzhu Vue 3 + Element Plus admin pages.
---

# Shouzhu El Table Style

Use Element Plus `el-table`. A Shouzhu data table is a full-width data region, not a content-width card.

## Required Reading

Read `../shouzhu-admin-ui-design/references/tokens.md`, `../shouzhu-el-checkbox-style/SKILL.md`, `../shouzhu-el-tag-style/SKILL.md`, `../shouzhu-icon-style/SKILL.md`, and `../shouzhu-el-pagination-style/SKILL.md` when the table uses selection columns, status tags, row actions, empty states, or pagination.

## Structure

```vue
<section class="table-region">
  <el-table class="sz-table" :data="rows" width="100%" height="100%">
    <el-table-column type="selection" width="80" />
    <el-table-column type="index" label="序号" width="80" />
    <el-table-column prop="name" label="标题" min-width="180" show-overflow-tooltip />
    <el-table-column label="状态" width="110">
      <template #default="{ row }">
        <el-tag class="sz-tag tag-success">{{ row.status || '--' }}</el-tag>
      </template>
    </el-table-column>
    <el-table-column prop="createdAt" label="日期时间" width="180" />
    <el-table-column label="操作" width="156" fixed="right">
      <template #default="{ row }">
        <div class="sz-table-actions">
          <el-tooltip content="查看">
            <button class="sz-table-icon-action" aria-label="查看">
              <el-icon><View /></el-icon>
            </button>
          </el-tooltip>
        </div>
      </template>
    </el-table-column>
  </el-table>

  <div v-if="!rows.length" class="sz-table-empty">
    <img src="/assets/empty/table-empty.png" alt="" />
    <p>暂无数据</p>
  </div>
</section>
```

## Overall Table

- The table must fill the available content width: `width: 100%`, `min-width: 0`.
- The table region uses `8px` radius.
- Do not show an outer table border.
- Do not show vertical inner borders.
- Show horizontal row dividers.
- Do not use zebra striping.
- Do not add a special table background color; inherit the content surface, usually white.
- If visible columns are few, the table still occupies the full region.
- Horizontal scroll belongs inside the table only.

## Header

- Header height: `56px`.
- Header background: `#FAFAFA`.
- Header text color: title text, `var(--sz-text-title)`.
- Header font size: `16px`.
- Header font weight: `700`.
- Header cell horizontal padding: `24px`.
- Header does not need a separate bottom divider beyond the table row divider system.
- Header radius appears only on the first header cell and last header cell: `8px`.

## Rows And Cells

- Normal row height: `48px`.
- Two-line row height: `72px`. Use this when any cell in the row displays two stacked lines, such as name/phone, certificate/effective date, title/description, or main text/helper text.
- Two-line rows must apply to the whole table row, not only the specific cell, so dividers and hover backgrounds align across columns.
- Mark two-line rows with an explicit row class such as `.sz-table-row-two-line` through Element Plus `row-class-name`, or use a clear table data flag that maps to that class.
- Two-line cell content uses a vertical stack: main line on top, secondary line below, with `4px` gap.
- Two-line main text uses `14px` body text; secondary text uses `12px` secondary text.
- Normal row background: none / transparent.
- Normal row text color: body text, `var(--sz-text-body)`.
- Normal row font size: `14px`.
- Normal row font weight: `400`.
- Cell horizontal padding: `24px`.
- Cell vertical padding is controlled by the fixed `48px` row height.
- Row bottom divider color: default border color, `var(--sz-border-default)`.
- The last visible table row must not show a bottom divider.
- Row hover background: `#FAFAFA`.
- Selected row background: primary 10%, `var(--sz-color-primary-light)`.
- Empty cell value displays as `--`.
- Long text must use ellipsis and show the full content in a hover tooltip.
- Icon + text content uses `8px` gap.
- Do not use D-DIN-PRO for table numbers by default; table data keeps the normal interface font unless a metric card or KPI explicitly needs numeric emphasis.

## Column Types

- Selection column: required when batch actions or multi-select are needed; width `80px`, centered, and follows `../shouzhu-el-checkbox-style/SKILL.md`.
- Index column: width `80px`.
- Status fields must use `el-tag` and follow `../shouzhu-el-tag-style/SKILL.md`.
- Date/time columns must be wide enough to display the complete date and time, normally `160-180px`.
- Operation column width: `100-200px`, based on the number of actions.
- Operation column must be fixed on the right.
- Normal business text columns use `min-width` and expand with remaining width.
- Do not make row actions wrap into two lines.

## Row Actions

- Row actions use icon-only buttons, not text buttons, unless the required icon asset is missing.
- Icon size: `24px * 24px`.
- Icon button size: `24px * 24px`.
- Shape: circular.
- Normal background: `#F4F6F6`.
- Hover background: primary 10%, `var(--sz-color-primary-light)`.
- Normal icon color: secondary text color, `var(--sz-text-secondary)`.
- Hover icon color: primary color, `var(--sz-color-primary)`.
- Destructive or warning operation icon color: alert/danger color, `var(--sz-color-danger)`.
- Multiple actions use `12px` gap.
- Icon-only buttons must have `aria-label`.
- Use tooltip text for compact or unclear actions.

## Empty State

- Use the supplied empty-state image: `../shouzhu-admin-ui-design/assets/empty/table-empty.png`.
- Empty image size: `160px * 160px`.
- Image and text gap: `0`.
- Empty text: `暂无数据`.
- Empty text color: secondary text, `var(--sz-text-secondary)`.
- Empty text size: `14px`.
- Empty state content starts `80px` from the top of the empty table area.
- Pagination still displays when the table is empty.

## Forbidden

- Do not render table filters inside the table component spec. Page filters call form controls.
- Do not leave a large blank area to the right of a narrow table.
- Do not make row actions ellipsis or wrap into two lines.
- Do not use text-only status when the field is status-like.
- Do not put normal data tables inside fixed-width, inline-block, fit-content, or centered wrappers.
- Do not use vertical cell borders.
- Do not use zebra stripes unless the user explicitly changes the table standard.

## CSS Contract

```css
.table-region {
  position: relative;
  width: 100%;
  min-width: 0;
  border-radius: 8px;
  overflow: hidden;
}

.sz-table.el-table {
  width: 100%;
  border-radius: 8px;
  overflow: hidden;
  --el-table-header-bg-color: #FAFAFA;
  --el-table-row-hover-bg-color: #FAFAFA;
  --el-table-current-row-bg-color: var(--sz-color-primary-light);
  --el-table-border-color: var(--sz-border-default);
  --el-table-text-color: var(--sz-text-body);
  --el-table-header-text-color: var(--sz-text-title);
  font-size: var(--sz-font-size-body);
  color: var(--sz-text-body);
}

.sz-table.el-table,
.sz-table .el-table__inner-wrapper,
.sz-table .el-table__border-left-patch {
  border: 0;
}

.sz-table.el-table::before,
.sz-table.el-table::after,
.sz-table .el-table__inner-wrapper::before {
  display: none;
}

.sz-table .el-table__header th.el-table__cell {
  height: 56px;
  padding: 0;
  background: #FAFAFA;
  color: var(--sz-text-title);
  font-size: var(--sz-font-size-title);
  font-weight: var(--sz-font-weight-bold);
  border-bottom: 0;
}

.sz-table .el-table__header th.el-table__cell:first-child {
  border-top-left-radius: 8px;
  border-bottom-left-radius: 8px;
}

.sz-table .el-table__header th.el-table__cell:last-child {
  border-top-right-radius: 8px;
  border-bottom-right-radius: 8px;
}

.sz-table .el-table__body td.el-table__cell {
  height: 48px;
  padding: 0;
  border-bottom: 1px solid var(--sz-border-default);
  color: var(--sz-text-body);
  font-size: var(--sz-font-size-body);
  font-weight: var(--sz-font-weight-regular);
}

.sz-table .el-table__body tr.sz-table-row-two-line td.el-table__cell {
  height: 72px;
}

.sz-table-cell-stack {
  display: flex;
  flex-direction: column;
  justify-content: center;
  gap: 4px;
  min-width: 0;
  height: 72px;
}

.sz-table-cell-main {
  min-width: 0;
  overflow: hidden;
  color: var(--sz-text-body);
  font-size: var(--sz-font-size-body);
  line-height: 20px;
  text-overflow: ellipsis;
  white-space: nowrap;
}

.sz-table-cell-sub {
  min-width: 0;
  overflow: hidden;
  color: var(--sz-text-secondary);
  font-size: var(--sz-font-size-helper);
  line-height: 18px;
  text-overflow: ellipsis;
  white-space: nowrap;
}

.sz-table .el-table__body tr:last-child td.el-table__cell {
  border-bottom: 0;
}

.sz-table .el-table__cell {
  border-right: 0;
}

.sz-table .cell {
  padding: 0 24px;
  line-height: var(--sz-line-height-base);
}

.sz-table .el-table__placeholder {
  display: inline-block;
  width: 100%;
  color: var(--sz-text-secondary);
}

.sz-table-actions {
  display: inline-flex;
  align-items: center;
  gap: 12px;
}

.sz-table-icon-action {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  width: 24px;
  height: 24px;
  padding: 0;
  border: 0;
  border-radius: 50%;
  background: #F4F6F6;
  color: var(--sz-text-secondary);
  cursor: pointer;
}

.sz-table-icon-action:hover {
  background: var(--sz-color-primary-light);
  color: var(--sz-color-primary);
}

.sz-table-icon-action svg,
.sz-table-icon-action img,
.sz-table-icon-action .sz-action-iconfont {
  width: 24px;
  height: 24px;
  font-size: 24px;
  line-height: 1;
}

.sz-table-icon-action.is-danger {
  color: var(--sz-color-danger);
}

.sz-table-empty {
  min-height: 240px;
  padding-top: 80px;
  text-align: center;
  color: var(--sz-text-secondary);
  font-size: var(--sz-font-size-body);
}

.sz-table-empty img {
  display: block;
  width: 160px;
  height: 160px;
  margin: 0 auto;
  object-fit: contain;
}

.sz-table-empty p {
  margin: 0;
}
```
