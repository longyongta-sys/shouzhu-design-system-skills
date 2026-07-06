---
name: shouzhu-image-preview-style
description: Shouzhu image preview style skill. Use when creating, modifying, reviewing, or prototyping Element Plus el-image preview overlays, single-image viewers, image preview dialogs, upload image previews, attachment image previews, approval-flow site image previews, detail-page image previews, or image viewing interactions in Shouzhu Vue 3 + Element Plus admin pages.
---

# Shouzhu Image Preview Style

Use Element Plus `el-image` preview for image viewing. This skill defines the single-image preview overlay used from upload components, attachment image entries, approval flow images, and detail page images.

## Required Reading

Read `../shouzhu-admin-ui-design/references/tokens.md`, `../shouzhu-icon-style/SKILL.md`, and the source component skill that opens the preview, such as `../shouzhu-el-upload-style/SKILL.md`, `../shouzhu-el-attachment-upload-style/SKILL.md`, `../shouzhu-approval-flow-style/SKILL.md`, or `../shouzhu-detail-style/SKILL.md`.

## Usage

- Use Element Plus `el-image` preview.
- Use for image viewing from image/video upload cards, attachment images, approval flow site images, and detail page images.
- Single image preview only.
- Do not support multi-image browsing for the current standard.
- Do not show previous/next controls, progress count, thumbnail strips, zoom controls, rotate controls, download actions, or a bottom toolbar.
- Keep Element Plus default loading and failed states.

## Structure

```vue
<el-image
  class="sz-image-preview-trigger"
  :src="image.url"
  :preview-src-list="[image.url]"
  :initial-index="0"
  :hide-on-click-modal="true"
  :close-on-press-escape="true"
  :preview-teleported="true"
  :infinite="false"
  :z-index="4000"
  fit="cover"
  @show="previewName = image.name"
  @close="previewName = ''"
/>

<teleport to="body">
  <div v-if="previewName" class="sz-image-preview-name">{{ previewName }}</div>
</teleport>
```

The thumbnail/entry size follows the component that owns it. For example, media upload cards use `120px * 120px`; approval site images use `100px * 100px`.

## Overlay

- Preview overlay is fullscreen.
- Overlay background: `rgb(0 0 0 / 40%)`.
- Preview z-index must be higher than normal dialogs. Use `z-index: 4000`.
- Click overlay closes preview.
- Pressing `ESC` closes preview.
- Right-top close button is shown.
- Close button size: `20px * 20px`.
- Close button color: secondary text, `var(--sz-text-secondary)`.
- Close hover style: no visible background or color change.

## Image Display

- Preview image maximum width: `600px`.
- Preview image maximum height: `600px`.
- Fit: `contain`, so the whole image is visible without cropping or stretching.
- Background behind the image: none.
- Image radius: `8px`.
- Do not allow image dragging/panning.
- Do not enable zoom, rotate, reset, download, or original-image actions.
- The image must stay fully visible in the viewport. On smaller screens, clamp to `calc(100vw - 128px)` and `calc(100vh - 168px)`.

## Image Name

- Show image name below the preview image.
- Image name position: centered below image.
- Gap between image and name: `16px`.
- Text color: white.
- Text size: `14px`.
- Line-height: `1.5`.
- Long names use single-line ellipsis.
- Do not show sequence numbers or descriptions.

## CSS Contract

Element Plus image viewer is teleported to body, so the viewer override CSS must be global.

```css
.el-image-viewer__wrapper {
  z-index: 4000;
}

.el-image-viewer__mask {
  background: rgb(0 0 0 / 40%);
  opacity: 1;
}

.el-image-viewer__close {
  top: 32px;
  right: 32px;
  width: 20px;
  height: 20px;
  color: var(--sz-text-secondary);
  background: transparent;
}

.el-image-viewer__close:hover {
  color: var(--sz-text-secondary);
  background: transparent;
}

.el-image-viewer__close .el-icon {
  width: 20px;
  height: 20px;
  font-size: 20px;
}

.el-image-viewer__actions,
.el-image-viewer__prev,
.el-image-viewer__next,
.el-image-viewer__progress {
  display: none;
}

.el-image-viewer__canvas {
  padding: 64px;
}

.el-image-viewer__img {
  max-width: min(600px, calc(100vw - 128px));
  max-height: min(600px, calc(100vh - 168px));
  border-radius: 8px;
  object-fit: contain;
  cursor: default;
}

.sz-image-preview-name {
  position: fixed;
  left: 50%;
  bottom: calc(50vh - min(300px, calc((100vh - 168px) / 2)) - 40px);
  z-index: 4001;
  max-width: min(600px, calc(100vw - 128px));
  transform: translateX(-50%);
  overflow: hidden;
  color: #FFFFFF;
  font-size: var(--sz-font-size-body);
  line-height: var(--sz-line-height-base);
  text-align: center;
  text-overflow: ellipsis;
  white-space: nowrap;
  pointer-events: none;
}
```

If the exact image height is dynamic and the caption cannot align correctly with pure CSS, render a small custom caption layer together with the preview open state. The caption must still use the same visual rules.

## Interaction Rules

- Click thumbnail or image entry to open preview.
- Click overlay closes preview.
- Press `ESC` closes preview.
- Do not support mouse wheel zoom.
- Do not support double-click zoom.
- Do not support drag/pan after zoom.
- Do not support keyboard left/right switching.
- Do not support image download from this viewer.

## Forbidden

- Do not use a form dialog or MessageBox for image viewing.
- Do not use multi-image navigation, thumbnail strips, page counters, or previous/next buttons.
- Do not show Element Plus default image viewer toolbar.
- Do not crop the preview image; use `contain`.
- Do not exceed `600px * 600px` for normal desktop preview.
- Do not use a dialog-style white panel behind the image.
