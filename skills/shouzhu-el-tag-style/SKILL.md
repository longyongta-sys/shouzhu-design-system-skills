---
name: shouzhu-el-tag-style
description: Shouzhu Element Plus tag style skill. Use when creating, modifying, reviewing, or prototyping el-tag status labels, type labels, result labels, classification labels, table status fields, detail status fields, or semantic tag variants in Shouzhu Vue 3 + Element Plus admin pages.
---

# Shouzhu El Tag Style

Use tags whenever a field is status-like, type-like, result-like, or classification-like.

## Size And Structure

- Tag height: `24px`.
- Font size: `12px`.
- Font weight: `700`.
- Line-height: `1.5`.
- Horizontal padding: `8px`.
- Radius: `4px`.
- Border: none.
- Tags may include an icon when the icon communicates status or type.
- Icon size: `12px * 12px`.
- Icon and text gap: `4px`.

## Variants

- Default / primary: text `var(--sz-color-primary)`, background `var(--sz-color-primary-light)`.
- Success / enabled / passed: text `var(--sz-color-success)`, background `#EAF8F1`.
- Warning / pending / paused: text `var(--sz-color-warning)`, background `#FFF8ED`.
- Danger / abnormal / failed: text `var(--sz-color-danger)`, background `#FDEBE7`.
- Disabled / gray / neutral: text `var(--sz-text-secondary)`, background `#F2F3F5`.
- Purple / special category: text `var(--sz-color-purple)`, background `#F0EEFF`.

## Forbidden

- Do not use strong Element Plus default tag borders.
- Do not render status-like table or detail fields as plain text.
- Do not use normal body text weight for tags; tag text is bold.

## CSS Contract

```css
.sz-tag.el-tag {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  height: 24px;
  padding: 0 8px;
  border: 0;
  border-radius: 4px;
  font-size: var(--sz-font-size-helper);
  font-weight: var(--sz-font-weight-bold);
  line-height: 1;
}

.sz-tag .el-icon,
.sz-tag svg {
  width: 12px;
  height: 12px;
  margin-right: 4px;
}

.sz-tag.tag-primary {
  color: var(--sz-color-primary);
  background: var(--sz-color-primary-light);
}

.sz-tag.tag-success {
  color: var(--sz-color-success);
  background: #EAF8F1;
}

.sz-tag.tag-warning {
  color: var(--sz-color-warning);
  background: #FFF8ED;
}

.sz-tag.tag-danger {
  color: var(--sz-color-danger);
  background: #FDEBE7;
}

.sz-tag.tag-disabled,
.sz-tag.tag-neutral {
  color: var(--sz-text-secondary);
  background: #F2F3F5;
}

.sz-tag.tag-purple {
  color: var(--sz-color-purple);
  background: #F0EEFF;
}
```
