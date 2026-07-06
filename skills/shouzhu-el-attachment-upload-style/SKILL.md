---
name: shouzhu-el-attachment-upload-style
description: Shouzhu Element Plus attachment upload style skill. Use when creating, modifying, reviewing, or prototyping el-upload for contracts, certificates, attachments, documents, compressed files, and mixed image/video/file uploads in Shouzhu Vue 3 + Element Plus admin pages.
---

# Shouzhu El Attachment Upload Style

Use Element Plus `el-upload`. This skill defines the second upload style: attachment upload for mixed files. Do not use the image/video card upload style for contracts, certificates, documents, compressed packages, or mixed attachment fields.

## Required Reading

Read `../shouzhu-admin-ui-design/references/tokens.md`, `../shouzhu-el-form-style/SKILL.md`, `../shouzhu-el-button-style/SKILL.md`, and `../shouzhu-icon-style/SKILL.md` before applying attachment upload styles.

## When To Use

- Use this style for contracts, certificates, attachments, documents, compressed packages, and mixed uploads that may include files, videos, and images.
- Use `../shouzhu-el-upload-style/SKILL.md` only when the field accepts images and/or videos and should render as `120px` media cards.

## Supported Usage

- Use Element Plus `el-upload`.
- Drag upload: not supported.
- Multiple files: supported.
- Delete: supported.
- Download: supported when the business has uploaded file URLs.
- Preview: supported when the file type can be previewed.
- Re-upload: supported.
- Upload progress: supported.
- Upload failure state: required.
- Validation and upload failure feedback use `ElMessage`, not form inline error text.

## Upload Entry

- Entry style: button.
- Button text: `上传附件`.
- Button size: large button.
- Button type: secondary outline button from `../shouzhu-el-button-style/SKILL.md`.
- Upload icon: required, use `sz-common-iconfont icon-shangchuan`.
- Icon size: `16px * 16px`.
- Icon-to-text gap: `4px`.
- Show tip text below the button.
- Tip text example: `支持 PDF、Word、Excel、图片、视频，单个文件不超过 50MB`.
- Tip font-size: `12px`.
- Tip color: secondary text, `var(--sz-text-secondary)`.
- Tip top gap: `8px`.

## Attachment List

- List style: card list.
- Single attachment item height: `80px`.
- Radius: `8px`.
- Background: `#FAFAFA`.
- Border: none.
- Horizontal padding: `16px`.
- Vertical padding follows the fixed height and vertical centering.
- Gap between attachment items: `16px`.
- Item layout: file type icon on the left, content in the middle, delete operation on the right.
- File type icon size: `48px * 48px`.
- File name font-size: `14px`.
- File name color: body text, `var(--sz-text-body)`.
- File name long-text handling: single-line ellipsis. Show full name with tooltip on hover when available.
- File size is shown after successful upload.
- File size font-size: `12px`.
- File size color: secondary text, `var(--sz-text-secondary)`.
- File name and secondary line gap: `8px`.

## File Type Icons

Use the official file type PNG assets. Do not redraw these file icons with CSS.

- PDF: `../shouzhu-admin-ui-design/assets/icons/file-types/file-pdf.png`.
- Word/document: `../shouzhu-admin-ui-design/assets/icons/file-types/file-doc.png`.
- Excel/table: `../shouzhu-admin-ui-design/assets/icons/file-types/file-xls.png`.
- JPG image: `../shouzhu-admin-ui-design/assets/icons/file-types/file-jpg.png`.
- PNG image: `../shouzhu-admin-ui-design/assets/icons/file-types/file-png.png`.
- Video: `../shouzhu-admin-ui-design/assets/icons/file-types/file-video.png`.
- Unknown/default document: use `file-doc.png` until a separate default icon is provided.
- Render the icon at `48px * 48px`.
- The file type icon is a visual marker, not an action button.

## Upload States

Uploading:

- The item keeps `80px` height, `8px` radius, and `#FAFAFA` background.
- Do not show a separate `上传中` text line by default.
- Show a progress bar below the file name.
- Progress bar height: `6px`.
- Progress bar radius: `99px`.
- Progress track: `#E6E6E6`.
- Progress fill: primary, `var(--sz-color-primary)`.

Failed:

- The item keeps `80px` height, `8px` radius, and `#FAFAFA` background.
- Show failure text `上传失败` below the file name.
- Failure text color: danger/alert color, `var(--sz-color-danger)`.
- Failure text font-size: `12px`.
- Do not show a success indicator on successful uploads.

Success:

- Show file name and file size.
- Do not show a success icon by default.

## Operations

- Visible operation on each attachment item: delete only.
- Operation type: icon.
- Delete icon: common close icon, `sz-common-iconfont icon-guanbi`.
- Visual icon size: `20px * 20px`.
- Icon button touch area: `24px * 24px`.
- Default icon circle color: secondary text, `var(--sz-text-secondary)`.
- Close glyph color: white.
- Close glyph visual size: `14px`.
- Successful upload items keep the delete icon in the default gray style; do not use primary blue to mark upload success.
- Hover icon circle color: primary, `var(--sz-color-primary)`, unless the product explicitly wants a destructive hover state.
- Delete operation is right aligned and vertically centered.
- If preview/download actions are enabled by business logic, place them before delete and keep `12px` gap between operation icons, but the default visible style only shows delete.

## Limits And Feedback

- Show format limits in the tip text.
- Show size limits in the tip text when a size limit exists.
- Show count limits in the tip text when a count limit exists.
- Error feedback uses `ElMessage`.
- Recommended message examples:
  - Format error: `仅支持 PDF、Word、Excel、图片、视频等格式`.
  - Size limit: `单个文件不能超过 50MB`.
  - Count limit: `最多上传 {limit} 个附件`.

## Structure

```vue
<el-upload
  class="sz-attachment-upload"
  :drag="false"
  multiple
  :show-file-list="false"
  :before-upload="beforeAttachmentUpload"
  :on-progress="handleAttachmentProgress"
  :on-error="handleAttachmentError"
  :on-remove="handleAttachmentRemove"
>
  <el-button class="sz-btn sz-btn-outline sz-btn-large">
    <i class="sz-common-iconfont icon-shangchuan"></i>
    <span>上传附件</span>
  </el-button>
  <template #tip>
    <div class="sz-attachment-tip">支持 PDF、Word、Excel、图片、视频，单个文件不超过 50MB</div>
  </template>
</el-upload>

<div class="sz-attachment-list">
  <div class="sz-attachment-item is-uploading">
    <img class="sz-file-icon" src="/assets/icons/file-types/file-pdf.png" alt="PDF" />
    <div class="sz-attachment-main">
      <div class="sz-attachment-name">建设项目安全生产巡查单建设项目安全生产巡查单.pdf</div>
      <div class="sz-attachment-progress"><span style="width: 40%"></span></div>
    </div>
    <button class="sz-attachment-remove" type="button" aria-label="删除附件">
      <i class="sz-common-iconfont icon-guanbi"></i>
    </button>
  </div>
</div>
```

## CSS Contract

```css
.sz-attachment-upload .sz-btn .sz-common-iconfont {
  font-size: 16px;
}

.sz-attachment-tip {
  margin-top: 8px;
  color: var(--sz-text-secondary);
  font-size: var(--sz-font-size-helper);
  line-height: var(--sz-line-height-base);
}

.sz-attachment-list {
  display: grid;
  gap: 16px;
  margin-top: 24px;
}

.sz-attachment-item {
  display: grid;
  grid-template-columns: 48px minmax(0, 1fr) 24px;
  align-items: center;
  gap: 16px;
  width: 100%;
  min-width: 0;
  height: 80px;
  padding: 0 16px;
  border: 0;
  border-radius: 8px;
  background: #FAFAFA;
}

.sz-file-icon {
  display: block;
  width: 48px;
  height: 48px;
  object-fit: contain;
}

.sz-attachment-main {
  min-width: 0;
}

.sz-attachment-name {
  overflow: hidden;
  color: var(--sz-text-body);
  font-size: var(--sz-font-size-body);
  line-height: var(--sz-line-height-base);
  text-overflow: ellipsis;
  white-space: nowrap;
}

.sz-attachment-meta,
.sz-attachment-error {
  margin-top: 8px;
  font-size: var(--sz-font-size-helper);
  line-height: 1;
}

.sz-attachment-meta {
  color: var(--sz-text-secondary);
}

.sz-attachment-error {
  color: var(--sz-color-danger);
}

.sz-attachment-progress {
  height: 6px;
  margin-top: 8px;
  overflow: hidden;
  border-radius: 99px;
  background: #E6E6E6;
}

.sz-attachment-progress > span {
  display: block;
  height: 100%;
  border-radius: inherit;
  background: var(--sz-color-primary);
}

.sz-attachment-remove {
  display: inline-grid;
  place-items: center;
  width: 24px;
  height: 24px;
  padding: 0;
  border: 0;
  border-radius: 50%;
  background: transparent;
  color: #FFFFFF;
  cursor: pointer;
}

.sz-attachment-remove .sz-common-iconfont {
  display: inline-grid;
  place-items: center;
  width: 20px;
  height: 20px;
  border-radius: 50%;
  background: var(--sz-text-secondary);
  font-size: 14px;
  line-height: 1;
}

.sz-attachment-remove:hover .sz-common-iconfont {
  background: var(--sz-color-primary);
}
```

## Forbidden

- Do not use the `120px * 120px` image/video card style for mixed attachments.
- Do not enable drag upload for this style.
- Do not redraw file type icons with CSS when the official PNG assets exist.
- Do not show a success check icon by default.
- Do not use primary blue on successful upload items just to indicate success; success keeps the normal gray delete icon and file-size text.
- Do not use inline form error text for upload validation; use `ElMessage`.
- Do not let long file names wrap and increase the attachment item height.
