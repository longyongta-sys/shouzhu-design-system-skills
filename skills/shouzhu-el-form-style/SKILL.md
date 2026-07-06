---
name: shouzhu-el-form-style
description: Shouzhu Element Plus form and form-control style skill. Use when creating, modifying, reviewing, or prototyping el-form, el-input, el-select, checkbox, radio, switch, date picker, time picker, upload, search input, textarea, validation, required labels, or dialog forms in Shouzhu Vue 3 + Element Plus admin pages.
---

# Shouzhu El Form Style

Use Element Plus form controls for data entry, filters, search, and dialog forms. Do not invent separate table filters or custom div controls when Element Plus has a matching control.

## Required Reading

Read `../shouzhu-admin-ui-design/references/tokens.md` before applying form styles. Read `../shouzhu-el-input-style/SKILL.md` whenever the form uses text inputs, search inputs, clearable inputs, disabled inputs, or error inputs. Read `../shouzhu-el-select-style/SKILL.md` whenever the form uses dropdown selects. Read `../shouzhu-el-date-picker-style/SKILL.md` whenever the form uses date, date range, datetime, month, or year pickers. Read `../shouzhu-el-checkbox-style/SKILL.md` whenever the form uses checkboxes or multi-select checkbox groups. Read `../shouzhu-el-radio-style/SKILL.md` whenever the form uses radios or single-choice radio groups. Read `../shouzhu-el-switch-style/SKILL.md` whenever the form uses switches, status toggles, or enable/disable controls. Read `../shouzhu-el-upload-style/SKILL.md` whenever the form uses image upload, video upload, media upload cards, upload progress, upload failure states, preview, delete, or re-upload. Read `../shouzhu-el-attachment-upload-style/SKILL.md` whenever the form uses contracts, certificates, attachments, documents, compressed packages, or mixed file/image/video uploads.

## Structure

```vue
<el-form label-position="top" class="sz-form">
  <el-row :gutter="16">
    <el-col :span="12">
      <el-form-item>
        <template #label>
          <span class="is-required">字段名称</span>
        </template>
        <el-input v-model="form.name" clearable placeholder="请输入" />
      </el-form-item>
    </el-col>
  </el-row>
</el-form>
```

## Layout

- Labels are always above controls. Do not replace labels with placeholders.
- Required `*` appears only after labels of fields configured as required.
- Label color: `var(--sz-text-title)`.
- Label font-size: `14px`.
- Label font-weight: `500`.
- Label bottom gap: `8px`.
- Normal form item bottom gap: `18px`.
- Dialog form item bottom gap: `24px`.
- Normal control height: `40px`.
- Toolbar/search/filter compact control height: `34px`.
- Control radius follows the relevant component skill. Text inputs and selects use `6px` from their component style skills.
- All controls inside a form column use `width: 100%`.
- Two-column form layout uses `el-row :gutter="16"` and `el-col :span="12"`.
- Full-width fields use `el-col :span="24"`.

## States

- Input border, focus, placeholder, disabled, and error states must follow `shouzhu-el-input-style`.
- Checkbox size, checked, disabled, indeterminate, label spacing, and table alignment must follow `shouzhu-el-checkbox-style`.
- Radio size, checked, disabled, label spacing, group wrapping, and compact filter spacing must follow `shouzhu-el-radio-style`.
- Switch size, on/off color, disabled opacity, loading, and confirmation behavior must follow `shouzhu-el-switch-style`.
- Select trigger, dropdown panel, selected option, hover option, and disabled option states must follow `shouzhu-el-select-style`.
- Date picker trigger, panel, cell, range, month, and year states must follow `shouzhu-el-date-picker-style`.
- Image/video upload cards, upload progress, upload failure, preview, delete, and re-upload must follow `shouzhu-el-upload-style`.

## Upload

- Image/video-only upload fields use `../shouzhu-el-upload-style/SKILL.md`.
- Image/video upload card size is `120px * 120px`.
- Mixed attachment upload that accepts files/videos/images together is a separate style and must not reuse the image/video-only card rules until that second style is defined.
- Attachment upload fields use `../shouzhu-el-attachment-upload-style/SKILL.md`.
- Attachment upload uses an outline large button entry and an `80px` high attachment card list.

## Forbidden

- Do not use placeholder as the only field label.
- Do not show required stars by default.
- Do not create horizontal scroll in narrow layouts.
- Do not leave Element Plus default focus colors when Shouzhu tokens are available.

## CSS Contract

```css
.sz-form .el-input,
.sz-form .el-select,
.sz-form .el-date-editor,
.sz-form .el-textarea {
  width: 100%;
}
```
