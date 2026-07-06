---
name: shouzhu-el-switch-style
description: Shouzhu Element Plus switch style skill. Use when creating, modifying, reviewing, or prototyping el-switch, status switches, enable/disable controls, table switches, form switches, loading switches, disabled switches, or switch confirmation behavior in Shouzhu Vue 3 + Element Plus admin pages.
---

# Shouzhu El Switch Style

Use Element Plus `el-switch`. A switch is for direct state toggles such as enabled/disabled, visible/hidden, or on/off.

## Required Reading

Read `../shouzhu-admin-ui-design/references/tokens.md`, `../shouzhu-el-form-style/SKILL.md`, and `../shouzhu-el-message-box-style/SKILL.md` when the switch toggles important, destructive, or business-critical status.

## Structure

```vue
<el-switch
  v-model="enabled"
  class="sz-switch"
  :loading="saving"
  :before-change="confirmBeforeChange"
/>
```

Use in a table cell:

```vue
<el-table-column label="状态" width="100">
  <template #default="{ row }">
    <el-switch
      v-model="row.enabled"
      class="sz-switch"
      :before-change="() => confirmBeforeToggle(row)"
    />
  </template>
</el-table-column>
```

## Overall

- Use Element Plus `el-switch`.
- Switch may be used in forms.
- Switch may be used in tables.
- Loading state is allowed.
- Text inside or beside the switch is not allowed by default.
- Do not use inline active/inactive text.
- Switch can be used for dangerous state changes only with confirmation.
- State switching requires secondary confirmation when it affects business status, permission, visibility, deletion-like disablement, or other risky behavior.
- Table switch does not need forced center alignment by default. Follow the table column alignment unless a page design explicitly centers it.

## Size

- Minimum width: `40px`.
- Height: `24px`.
- Radius: `99px`.
- Knob size: `18px * 18px`.
- Knob inset from outer track: `3px`.

## Off State

- Track background: neutral gray, `var(--sz-color-neutral)`.
- Knob color: white.
- Border: none.

## On State

- Track background: success/safe color, `var(--sz-color-success)`.
- Knob color: white.
- Border: none.

## Hover State

- No separate hover color is defined in the current standard.
- Hover keeps the same track and knob colors as the current state.

## Disabled State

- Disabled off track background: neutral gray, `var(--sz-color-neutral)`.
- Disabled on track background: success/safe color, `var(--sz-color-success)`.
- Disabled knob color: white.
- Disabled opacity: `40%`.

## Loading State

- Loading is allowed.
- Loading must not change the switch dimensions.
- When loading, keep the current on/off track color and show Element Plus loading feedback inside the knob if available.
- Do not allow repeated clicks during loading.

## Forbidden

- Do not use switch text labels by default.
- Do not use switch as a replacement for radio, checkbox, or segmented controls.
- Do not use switch for destructive or risky status changes without confirmation.
- Do not change switch width according to text because switch text is not used.
- Do not let loading or disabled states resize the switch.

## CSS Contract

```css
.sz-switch.el-switch {
  --el-switch-on-color: var(--sz-color-success);
  --el-switch-off-color: var(--sz-color-neutral);
  --el-switch-border-color: transparent;
  min-width: 40px;
  height: 24px;
  line-height: 24px;
}

.sz-switch .el-switch__core {
  min-width: 40px;
  width: 40px;
  height: 24px;
  border: 0;
  border-radius: 99px;
  background: var(--sz-color-neutral);
}

.sz-switch .el-switch__core .el-switch__action {
  width: 18px;
  height: 18px;
  left: 3px;
  color: #FFFFFF;
  background: #FFFFFF;
}

.sz-switch.is-checked .el-switch__core {
  background: var(--sz-color-success);
}

.sz-switch.is-checked .el-switch__core .el-switch__action {
  left: calc(100% - 21px);
}

.sz-switch.is-disabled {
  opacity: 0.4;
}

.sz-switch.is-disabled .el-switch__core {
  background: var(--sz-color-neutral);
}

.sz-switch.is-disabled.is-checked .el-switch__core {
  background: var(--sz-color-success);
}

.sz-switch .el-switch__label {
  display: none;
}
```

## Confirmation Pattern

Use `before-change` for risky toggles and confirm before committing the value.

```ts
const confirmBeforeToggle = async (row) => {
  await ElMessageBox.confirm(
    `确认${row.enabled ? '关闭' : '开启'}该状态吗？`,
    '操作确认',
    { type: 'warning' }
  )
  return true
}
```
