---
name: shouzhu-el-pagination-style
description: Shouzhu Element Plus pagination style skill. Use when creating, modifying, reviewing, or prototyping el-pagination, table pagination rows, page-size selectors, pager selected states, page jump inputs, or data-list pagination in Shouzhu Vue 3 + Element Plus admin pages.
---

# Shouzhu El Pagination Style

Use Element Plus `el-pagination` under data tables and list regions.

## Placement

- Pagination is fixed at the bottom of the page content area for table pages.
- It should remain visible when the table area scrolls.
- Pagination still displays when the table is empty.
- The total count sits on the left; pager, page-size selector, and jump controls sit on the right or center-right according to the page width.
- Keep pagination inside the business content/workspace, not inside the global page shell.

## Configuration

- Total text format: `共 50 条数据`.
- Default page size: `10`.
- Page size options: `[10, 20, 30, 40, 50, 100]`.
- Layout should include total count, previous/next, pager, page-size selector, and page jump.
- Use `:teleported="false"` on dropdowns when needed to inherit local theme variables.
- Page-size selector width is adaptive to its content.

```vue
<div class="sz-pagination-bar">
  <span class="sz-pagination-total">共 {{ total }} 条数据</span>
  <el-pagination
    class="sz-pagination"
    v-model:current-page="page"
    v-model:page-size="pageSize"
    :page-sizes="[10, 20, 30, 40, 50, 100]"
    :total="total"
    layout="prev, pager, next, sizes, jumper"
    :teleported="false"
  />
</div>
```

## Size And States

- Current page button: `32px * 32px`.
- Current page background: primary color, `var(--sz-color-primary)`.
- Current page text: white.
- Normal page number text: secondary text, `var(--sz-text-secondary)`.
- Hover state uses primary color.
- Page jump input size: `32px * 32px`.
- Page-size selector width: adaptive.

## CSS Contract

```css
.sz-pagination-bar {
  display: flex;
  align-items: center;
  justify-content: space-between;
  width: 100%;
  min-height: 32px;
  gap: 24px;
}

.sz-pagination-total {
  flex: 0 0 auto;
  color: var(--sz-text-secondary);
  font-size: var(--sz-font-size-body);
}

.sz-pagination.el-pagination {
  --el-pagination-button-width: 32px;
  --el-pagination-button-height: 32px;
  --el-pagination-button-color: var(--sz-text-secondary);
  --el-pagination-hover-color: var(--sz-color-primary);
  --el-pagination-button-bg-color: transparent;
  --el-pagination-button-disabled-bg-color: transparent;
  justify-content: flex-end;
  color: var(--sz-text-secondary);
  font-size: var(--sz-font-size-body);
}

.sz-pagination .el-pager li {
  min-width: 32px;
  height: 32px;
  border-radius: 6px;
  color: var(--sz-text-secondary);
}

.sz-pagination .el-pager li.is-active {
  background: var(--sz-color-primary);
  color: #FFFFFF;
}

.sz-pagination .el-pagination__jump .el-input,
.sz-pagination .el-pagination__jump .el-input__wrapper {
  width: 32px;
  height: 32px;
}

.sz-pagination .el-pagination__sizes .el-select {
  width: auto;
}
```
