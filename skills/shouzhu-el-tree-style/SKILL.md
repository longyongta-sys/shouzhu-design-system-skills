---
name: shouzhu-el-tree-style
description: Shouzhu Element Plus tree style skill. Use when creating, modifying, reviewing, or prototyping el-tree, hierarchical data, permission trees, menu trees, organization trees, category trees, current nodes, disabled tree nodes, or large tree panels in Shouzhu Vue 3 + Element Plus admin pages.
---

# Shouzhu El Tree Style

Use Element Plus `el-tree` for organization trees, permission trees, and category trees when expansion, selection, filtering, checking, or updating may be needed.

## Required Reading

Read `../shouzhu-admin-ui-design/references/tokens.md`, `../shouzhu-el-input-style/SKILL.md`, and `../shouzhu-el-checkbox-style/SKILL.md` before applying tree styles.

## Supported Usage

- Use Element Plus `el-tree`.
- Organization tree, permission tree, and category tree are supported.
- Search/filter is supported and should use `el-input` with the Shouzhu input style.
- Default expand all is allowed and is the default behavior for current Shouzhu tree previews.
- Node checkbox multi-select is allowed.
- Click-to-select/current-node is allowed.
- Do not show connector lines.
- Show expand/collapse arrows.
- Use Element Plus default expand/collapse arrow icons, styled by CSS.

## Structure

```vue
<el-input
  v-model="filterText"
  class="sz-input sz-tree-filter"
  clearable
  placeholder="请输入关键词"
/>

<el-tree
  class="sz-tree"
  :data="treeRows"
  :props="{ children: 'children', label: 'label', disabled: 'disabled' }"
  node-key="id"
  default-expand-all
  highlight-current
  show-checkbox
  :filter-node-method="filterNode"
  :indent="24"
/>
```

## Container

- Tree outer background: white.
- Tree outer radius: `8px`.
- Tree outer padding: `16px`.
- Tree outer border is optional. Do not add a border unless the surrounding page needs clear separation.
- Tree content must scroll inside the tree panel when taller than the available area.
- Do not let the browser page scroll because of a long tree.

## Rules

- Use `el-tree` rather than hand-built nested lists when interaction, expansion, selection, or filtering may be needed.
- Always set `node-key` when nodes may be selected, checked, expanded, or updated.
- Parent/level-one node text uses title color and `700` weight.
- Child/leaf node text uses secondary text color and normal weight.
- Node font-size: `14px`.
- Node line-height: `1.5`.
- Node row height: `48px`.
- Visible tree node vertical gap: `4px` between adjacent node rows, including parent-child and same-level rows.
- Node horizontal padding: `8px`.
- Indentation: `24px`.
- Expand arrow and text gap: `4px`.
- Checkbox and text gap follows checkbox skill, currently `8px`.
- Node leading business icon is not used by default.
- Expand/collapse icon size: `12px`.
- Expand/collapse default color: title color.
- Do not use leading connector lines.
- Long labels must ellipsis and show the full value on hover with a tooltip.
- Search input sits above the tree with a normal `16px` bottom gap unless a page-specific design changes it.

## States

- Hover background: `var(--sz-color-primary-light)`.
- Hover text: `var(--sz-color-primary)`.
- Selected/current background: primary 5%, `rgb(0 104 255 / 5%)`.
- Selected/current text: primary color, `var(--sz-color-primary)`.
- Selected/current weight: regular. Do not make selected tree text bold by default.
- Selected/current icon color: primary color, `var(--sz-color-primary)`.
- Current node does not show a left bar or extra marker.
- Disabled text: `var(--sz-text-placeholder)`.
- Disabled background: none.
- Disabled icon color: `var(--sz-text-placeholder)`.
- Disabled cursor: `not-allowed`.
- Disabled nodes have no hover highlight.

## Checkbox

- Tree checkbox uses the Shouzhu checkbox style from `../shouzhu-el-checkbox-style/SKILL.md`.
- Checkbox size is `16px * 16px`.
- Checkbox radius is `4px`.
- Checked state uses primary blue with the supplied white checkmark.
- Checked checkmark must stay visually centered and use the checkbox SVG from the Shouzhu checkbox skill.
- Indeterminate state follows checkbox style.
- Checkbox and node text stay vertically centered in the `48px` node row.

## Forbidden

- Do not use connector lines.
- Do not add node leading business icons by default.
- Do not show an extra selected left bar.
- Do not use selected/current state as solid primary blue.
- Do not use white text for selected/current tree nodes.
- Do not hand-build a custom nested list when Element Plus `el-tree` can express the behavior.

## CSS Contract

```css
.sz-tree-panel {
  min-height: 0;
  padding: 16px;
  border-radius: 8px;
  background: var(--sz-color-white);
  overflow: hidden;
}

.sz-tree-scroll {
  min-height: 0;
  overflow: auto;
}

.sz-tree-filter {
  margin-bottom: 16px;
}

.sz-tree.el-tree {
  --el-tree-node-hover-bg-color: var(--sz-color-primary-light);
  color: var(--sz-text-secondary);
  background: transparent;
}

.sz-tree .el-tree-node__content {
  height: 48px;
  margin-bottom: 4px;
  padding-right: 8px;
  border-radius: 8px;
  color: var(--sz-text-secondary);
  font-size: var(--sz-font-size-body);
  line-height: var(--sz-line-height-base);
}

.sz-tree .el-tree-node__expand-icon {
  width: 12px;
  height: 12px;
  margin-right: 4px;
  color: var(--sz-text-title);
  font-size: 12px;
}

.sz-tree .el-tree-node__label {
  min-width: 0;
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}

.sz-tree .el-tree-node.is-expanded > .el-tree-node__content .el-tree-node__label,
.sz-tree .el-tree-node:has(.el-tree-node__children) > .el-tree-node__content .el-tree-node__label {
  color: var(--sz-text-title);
  font-weight: var(--sz-font-weight-bold);
}

.sz-tree .el-tree-node__content:hover {
  color: var(--sz-color-primary);
  background: var(--sz-color-primary-light);
}

.sz-tree .el-tree-node__content:hover .el-tree-node__label,
.sz-tree .el-tree-node__content:hover .el-tree-node__expand-icon {
  color: var(--sz-color-primary);
}

.sz-tree .el-tree-node.is-current > .el-tree-node__content {
  color: var(--sz-color-primary);
  background: rgb(0 104 255 / 5%);
}

.sz-tree .el-tree-node.is-current > .el-tree-node__content .el-tree-node__label,
.sz-tree .el-tree-node.is-current > .el-tree-node__content .el-tree-node__expand-icon {
  color: var(--sz-color-primary);
  font-weight: var(--sz-font-weight-regular);
}

.sz-tree .el-tree-node.is-disabled > .el-tree-node__content,
.sz-tree .el-tree-node.is-disabled > .el-tree-node__content .el-tree-node__label,
.sz-tree .el-tree-node.is-disabled > .el-tree-node__content .el-tree-node__expand-icon {
  color: var(--sz-text-placeholder);
  cursor: not-allowed;
  background: transparent;
}
```
