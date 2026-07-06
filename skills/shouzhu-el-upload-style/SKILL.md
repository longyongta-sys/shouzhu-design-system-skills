---
name: shouzhu-el-upload-style
description: Shouzhu Element Plus upload style skill. Use when creating, modifying, reviewing, or prototyping el-upload, image upload, video upload, avatar upload, certificate photo upload, media upload cards, upload progress, upload failure states, preview, delete, or re-upload behavior in Shouzhu Vue 3 + Element Plus admin pages.
---

# Shouzhu El Upload Style

Use Element Plus `el-upload`. This skill defines the first upload style: image/video upload cards. Attachment upload for mixed files, images, videos, and documents is a separate style defined in `../shouzhu-el-attachment-upload-style/SKILL.md`.

## Required Reading

Read `../shouzhu-admin-ui-design/references/tokens.md`, `../shouzhu-el-form-style/SKILL.md`, `../shouzhu-icon-style/SKILL.md`, and `../shouzhu-el-message-box-style/SKILL.md` before applying upload styles.

## Supported Usage

- Use Element Plus `el-upload`.
- Upload type: image and video only.
- Common scenarios: avatar, certificate photo, and other image/video media fields.
- Drag upload: not supported for this style.
- Multiple files: supported.
- Delete: supported.
- Preview: supported.
- Re-upload: supported.
- Upload progress: supported.
- Upload failure state: required.
- File validation errors use `ElMessage`, not form inline error text.

## When To Use This Style

- Use this style when the form field only accepts images and/or videos.
- Do not use this style for attachment upload that accepts mixed file types such as files, videos, images, PDFs, Word documents, or compressed packages. Use `../shouzhu-el-attachment-upload-style/SKILL.md`.

## Structure

```vue
<el-upload
  class="sz-media-upload"
  list-type="picture-card"
  :drag="false"
  multiple
  accept="image/*,video/*"
  :limit="9"
  :before-upload="beforeMediaUpload"
  :on-preview="handlePreview"
  :on-remove="handleRemove"
  :on-progress="handleProgress"
  :on-error="handleError"
>
  <div class="sz-media-upload-trigger">
    <i class="sz-common-iconfont icon-tupianshipinshangchuan"></i>
    <span>点击上传</span>
  </div>
  <template #tip>
    <div class="sz-upload-tip">支持 JPG/PNG/MP4，单个文件不超过 10MB，最多上传 9 个</div>
  </template>
</el-upload>
```

## Upload Area

- Upload area size: `120px * 120px`.
- Radius: `8px`.
- Background: `#F8F9FA`.
- Border color: default line color, `var(--sz-border-default)`.
- Border style: `1px solid`.
- Hover border color: primary, `var(--sz-color-primary)`.
- Hover background: primary 5%, `rgb(0 104 255 / 5%)`.
- Upload icon size: `24px * 24px`.
- Upload icon color: weak hint text, `var(--sz-text-placeholder)`.
- Hover upload icon color: primary, `var(--sz-color-primary)`.
- Main prompt text: `点击上传`.
- Main prompt font-size: `12px`.
- Main prompt color: primary, `var(--sz-color-primary)`.
- No auxiliary text inside the card by default.

## Media Card

- Image/video card size: `120px * 120px`.
- Card radius: `8px`.
- Image/video fit: use `cover` by default. Use `contain` only when the full image must be visible.
- Success image/video cards do not show a full-card overlay by default.
- Hover on a success image/video card shows a preview overlay with view icon/text `查看`.
- Delete operation uses common close icon: `sz-common-iconfont icon-guanbi`.
- Operation icon button size: `24px * 24px`.
- Close icon is visually centered inside the 24px button.
- Operation icon color: white on dark or image backgrounds; secondary text color on light cards.
- Delete button sits at the top-right of the media card.
- Video success card shows a play marker centered over the thumbnail.

## Uploading State

- Card keeps `120px * 120px`, radius `8px`, background `#F8F9FA`, border `1px solid var(--sz-border-default)`.
- Show a small progress/loading indicator centered above the text.
- Progress text format: `上传中 40%`.
- Progress text font-size: `12px`.
- Progress text color: secondary text, `var(--sz-text-secondary)`.
- Delete/cancel icon can be shown at the top-right while uploading.

## Failed State

- Card keeps `120px * 120px`, radius `8px`, background `#F8F9FA`, border `1px solid var(--sz-border-default)`.
- Show a small error indicator centered above the text.
- Error indicator color uses danger color, `var(--sz-color-danger)`.
- Error text: `上传失败`.
- Error text font-size: `12px`.
- Error text color: secondary text, `var(--sz-text-secondary)`.
- Delete icon can be shown at the top-right.

## Tips And Limits

- Show file count limit when a limit exists.
- Show file size limit.
- Show allowed file format.
- Tip position: below the upload area.
- Tip font-size: `12px`.
- Tip color: secondary text, `var(--sz-text-secondary)`.
- Validation and upload failure feedback uses `ElMessage`.

## CSS Contract

```css
.sz-media-upload {
  --sz-upload-size: 120px;
}

.sz-media-upload .el-upload--picture-card,
.sz-media-upload .el-upload-list__item {
  width: var(--sz-upload-size);
  height: var(--sz-upload-size);
  border-radius: 8px;
}

.sz-media-upload .el-upload--picture-card {
  border: 1px solid var(--sz-border-default);
  background: #F8F9FA;
}

.sz-media-upload .el-upload--picture-card:hover {
  border-color: var(--sz-color-primary);
  background: rgb(0 104 255 / 5%);
}

.sz-media-upload-trigger {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 8px;
  width: 100%;
  height: 100%;
  color: var(--sz-color-primary);
  font-size: var(--sz-font-size-helper);
}

.sz-media-upload-trigger .sz-common-iconfont {
  color: var(--sz-text-placeholder);
  font-size: 24px;
}

.sz-media-upload .el-upload--picture-card:hover .sz-media-upload-trigger .sz-common-iconfont {
  color: var(--sz-color-primary);
}

.sz-media-upload .el-upload-list__item {
  overflow: hidden;
  border: 1px solid var(--sz-border-default);
  background: #F8F9FA;
}

.sz-media-upload .el-upload-list__item-thumbnail,
.sz-media-upload .sz-media-thumbnail {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.sz-media-upload .sz-media-remove {
  position: absolute;
  top: 8px;
  right: 8px;
  z-index: 2;
  display: inline-grid;
  place-items: center;
  width: 24px;
  height: 24px;
  border: 0;
  border-radius: 50%;
  background: rgb(34 37 49 / 45%);
  color: #FFFFFF;
  font-size: 16px;
  line-height: 1;
}

.sz-media-upload .sz-media-preview-mask {
  position: absolute;
  inset: 0;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 8px;
  opacity: 0;
  background: rgb(0 0 0 / 50%);
  color: #FFFFFF;
  font-size: 16px;
  transition: opacity 0.16s ease;
}

.sz-media-upload .el-upload-list__item:hover .sz-media-preview-mask {
  opacity: 1;
}

.sz-media-upload .sz-media-preview-mask .sz-common-iconfont {
  font-size: 24px;
}

.sz-upload-tip {
  margin-top: 8px;
  color: var(--sz-text-secondary);
  font-size: var(--sz-font-size-helper);
  line-height: var(--sz-line-height-base);
}
```

## Forbidden

- Do not enable drag upload for this image/video style.
- Do not use this style for mixed attachment upload.
- Do not use dashed borders for this style.
- Do not show a full-card overlay on successful image/video cards by default; only show the `查看` preview overlay on hover.
- Do not use the old upload delete glyph `icon-shangchuan-shanchu`; upload delete/remove must use `icon-guanbi`.
