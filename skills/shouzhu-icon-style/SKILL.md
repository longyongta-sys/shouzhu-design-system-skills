---
name: shouzhu-icon-style
description: Shouzhu icon style skill. Use when creating, modifying, reviewing, or prototyping menu icons, action icons, common icons, upload/download icons, status icons, table row icon actions, icon-only buttons, or Shouzhu iconfont/SVG asset usage in Vue 3 + Element Plus admin pages.
---

# Shouzhu Icon Style

Use Shouzhu iconfont projects for normal monochrome UI icons. Use SVG/image files only for logos, empty-state illustrations, checkmark masks, special multicolor artwork, or fallback when iconfont has no matching glyph.

## Required Assets

Load the iconfont CSS that matches the icon category being used:

- Action icons: `../shouzhu-admin-ui-design/assets/icons/iconfont/action-iconfont.css`.
- Menu icons: `../shouzhu-admin-ui-design/assets/icons/iconfont/menu-iconfont.css`.
- Common icons: `../shouzhu-admin-ui-design/assets/icons/iconfont/common-iconfont.css`.

Online iconfont links are only for preview/debug. For company delivery, download the font package, publish the font files with the project, and update the CSS to local font paths.

## Namespace Rule

Do not use the raw `iconfont` base class when multiple iconfont projects are present. Each project must use its namespaced base class so the fonts do not override each other:

- Action icon usage: `<i class="sz-action-iconfont icon-view"></i>`.
- Menu icon usage: `<i class="sz-menu-iconfont icon-shouyeweixuanzhong"></i>`.
- Common icon usage: `<i class="sz-common-iconfont icon-sousuo"></i>`.

The icon class describes what the icon is. The component class controls how it looks.

Examples:

```html
<button class="sz-button sz-button-primary">
  <i class="sz-action-iconfont icon-add sz-button-icon"></i>
  新增
</button>

<button class="sz-table-icon-action" aria-label="查看">
  <i class="sz-action-iconfont icon-view"></i>
</button>

<button class="menu-item is-active">
  <i class="sz-menu-iconfont icon-shouyexuanzhong menu-icon"></i>
  <span class="menu-text">首页</span>
</button>
```

## General Rules

- Do not duplicate same-meaning icons.
- Do not rename icons to generic labels such as `type-xxx`; use the actual visible meaning.
- Do not call random iconfont classes directly in page code without checking the mappings below.
- Iconfont color must follow `currentColor`, so normal, hover, selected, disabled, and danger states are controlled by CSS tokens.
- Icons in text buttons use `16px * 16px` and follow the button text color.
- Menu icons use the size and color defined by `../shouzhu-primary-menu-style/SKILL.md`.
- Table and compact operation icons use `24px * 24px`.
- Operation icon default color is secondary text color, `var(--sz-text-secondary)`.
- Operation icon hover color is primary color, `var(--sz-color-primary)`.
- Destructive operation icon color is danger color, `var(--sz-color-danger)`.
- If iconfont class names change, update this mapping before generating or reviewing pages.

## Action Iconfont Project

Project id: `5202837`.

Debug CSS: `https://at.alicdn.com/t/c/font_5202837_5wa41wvj2w4.css?t=1783478338406`.

Use action icons for table row actions, toolbar actions, icon-only operation buttons, and operation buttons inside dialogs.

- Add / create: `sz-action-iconfont icon-add`.
- Delete / remove: `sz-action-iconfont icon-delete`.
- Download / export: `sz-action-iconfont icon-download`.
- Edit / modify: `sz-action-iconfont icon-edit`.
- Release / unbind /解除: `sz-action-iconfont icon-jiechu`.
- Record / log /记录: `sz-action-iconfont icon-jilu`.
- Reset password: `sz-action-iconfont icon-reset-password`.
- View / detail / preview: `sz-action-iconfont icon-view`.

Local SVG fallback paths:

- Add / create: `../shouzhu-admin-ui-design/assets/icons/actions/action-add.svg`.
- Delete / remove: `../shouzhu-admin-ui-design/assets/icons/actions/action-delete.svg`.
- Download / export: `../shouzhu-admin-ui-design/assets/icons/actions/action-download.svg`.
- Edit / modify: `../shouzhu-admin-ui-design/assets/icons/actions/action-edit.svg`.
- Reset password: `../shouzhu-admin-ui-design/assets/icons/actions/action-reset-password.svg`.
- View / detail / preview: `../shouzhu-admin-ui-design/assets/icons/actions/action-view.svg`.

## Menu Iconfont Project

Project id: `5202843`.

Debug CSS: `https://at.alicdn.com/t/c/font_5202843_y4ohbnk8ib.css?t=1782813660064`.

Use menu icons only in the left primary menu and menu-like navigation.

- Home selected: `sz-menu-iconfont icon-shouyexuanzhong`.
- Home normal: `sz-menu-iconfont icon-shouyeweixuanzhong`.
- Project library selected: `sz-menu-iconfont icon-xiangmukuxuanzhong`.
- Project library normal: `sz-menu-iconfont icon-xiangmukuweixuanzhong`.
- Enterprise library selected: `sz-menu-iconfont icon-qiyekuxuanzhong`.
- Enterprise library normal: `sz-menu-iconfont icon-qiyekuweixuanzhong`.
- Personnel library selected: `sz-menu-iconfont icon-renyuankuxuanzhong`.
- Personnel library normal: `sz-menu-iconfont icon-renyuankuweixuanzhong`.
- Machinery library selected: `sz-menu-iconfont icon-jixiekuxuanzhong`.
- Machinery library normal: `sz-menu-iconfont icon-jixiekuweixuanzhong`.
- Equipment/instrument library selected: `sz-menu-iconfont icon-shebeiyiqikuxuanzhong`.
- Equipment/instrument library normal: `sz-menu-iconfont icon-shebeiyiqikuweixuanzhong`.

## Common Iconfont Project

Project id: `5202849`.

Debug CSS: `https://at.alicdn.com/t/c/font_5202849.css` is only for iconfont debugging. Use the downloaded local CSS in delivery.

Use common icons for form controls, topbar, hints, upload/download in non-table contexts, media, date/time, arrows, and general UI controls.

- Image/video upload: `sz-common-iconfont icon-tupianshipinshangchuan`.
- Upload delete/remove: `sz-common-iconfont icon-guanbi`.
- Clear: `sz-common-iconfont icon-qingkong`.
- Fingerprint: `sz-common-iconfont icon-zhiwen`.
- Download: `sz-common-iconfont icon-xiazai`.
- Up arrow: `sz-common-iconfont icon-shang`.
- Enterprise: `sz-common-iconfont icon-qiye`.
- Down arrow: `sz-common-iconfont icon-xia`.
- Hint/info: `sz-common-iconfont icon-tishi`.
- User: `sz-common-iconfont icon-yonghu`.
- Safety officer: `sz-common-iconfont icon-anquanyuan`.
- Map/location: `sz-common-iconfont icon-ditu`.
- Shield: `sz-common-iconfont icon-dunpai`.
- Add: `sz-common-iconfont icon-tianjia`.
- Right arrow: `sz-common-iconfont icon-you`.
- Phone: `sz-common-iconfont icon-shouji`.
- Search: `sz-common-iconfont icon-sousuo`.
- Refresh/reset: `sz-common-iconfont icon-shuaxin`.
- Left arrow: `sz-common-iconfont icon-zuo`.
- Time: `sz-common-iconfont icon-shijian`.
- Draft: `sz-common-iconfont icon-caogao`.
- Reset: `sz-common-iconfont icon-zhongzhi`.
- Close: `sz-common-iconfont icon-guanbi`.
- View: `sz-common-iconfont icon-chakan`.
- Date: `sz-common-iconfont icon-riqi`.
- Print: `sz-common-iconfont icon-dayin`.
- Approval: `sz-common-iconfont icon-shenpi`.
- Edit: `sz-common-iconfont icon-bianji`.
- Camera: `sz-common-iconfont icon-xiangji`.
- Play: `sz-common-iconfont icon-bofang`.
- Upload: `sz-common-iconfont icon-shangchuan`.
- ID card: `sz-common-iconfont icon-shenfenzheng`.
- Video recording: `sz-common-iconfont icon-luxiang`.
- Delete: `sz-common-iconfont icon-shanchu`.
- Lock: `sz-common-iconfont icon-suo`.

## Table Row Icon Action

- Icon size: `24px * 24px`.
- Icon button size: `24px * 24px`.
- Shape: circular.
- Background: `#F4F6F6`.
- Normal icon color: `var(--sz-text-secondary)`.
- Hover background: `var(--sz-color-primary-light)`.
- Hover border: `#D9E9FF`.
- Hover icon color: `var(--sz-color-primary)`.
- Destructive or warning actions: icon `var(--sz-color-danger)`, background `#F4F6F6`.
- Destructive or warning hover: icon `var(--sz-color-danger)`, background `#FDEBE7`, border `#FDEBE7`.

## Required Accessibility

- Icon-only buttons must have `aria-label`.
- Use a tooltip for compact or unclear icon actions.
