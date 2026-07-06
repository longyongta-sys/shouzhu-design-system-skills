---
name: shouzhu-primary-menu-style
description: Shouzhu primary left menu style skill. Use when creating, modifying, reviewing, or prototyping the fixed left sidebar, primary menu shell, Shouzhu logo brand block, city/location block, first-level menu items, second-level menu items, selected and hover states, system management action, return-home action, or sidebar bottom actions in Shouzhu Vue 3 + Element Plus admin pages.
---

# Shouzhu Primary Menu Style

Use this skill for the fixed left sidebar menu. This menu is a Shouzhu business navigation pattern, not a generic Element Plus `el-menu` default skin.

## Locked Rule

The primary menu is a hard system rule. Do not change the sidebar width, brand block, menu spacing, selected state, hover state, second-level menu style, system management action, or return-home action in normal page work. Change this skill only when the designer explicitly updates the design system.

## Required Reading

Read `../shouzhu-admin-ui-design/references/tokens.md` before applying menu styles.
Read `../shouzhu-icon-style/SKILL.md` when using menu icons or bottom action icons.

## Required Structure

```vue
<aside class="primary-menu-shell">
  <div class="menu-brand">
    <img class="menu-logo" src="/brand/shouzhu-logo.png" alt="shouzhu logo" />
    <div class="menu-welcome">Welcome to shouzhu</div>
    <div class="menu-city">
      <strong>拉萨市</strong>
      <span class="location-icon" aria-hidden="true"></span>
    </div>
  </div>

  <nav class="menu-list">
    <button class="menu-item is-active">
      <i class="sz-menu-iconfont icon-shouyexuanzhong menu-icon" aria-hidden="true"></i>
      <span class="menu-text">首页</span>
    </button>

    <button class="menu-item">
      <i class="sz-menu-iconfont icon-xiangmukuweixuanzhong menu-icon" aria-hidden="true"></i>
      <span class="menu-text">项目库</span>
      <span class="menu-arrow" aria-hidden="true"></span>
    </button>

    <button class="menu-child">
      <span class="child-mark" aria-hidden="true"></span>
      <span class="menu-text">二级菜单</span>
    </button>
  </nav>

  <div class="menu-footer">
    <button class="system-action">
      <span class="system-icon" aria-hidden="true">
        <i class="sz-common-iconfont icon-zhongzhi"></i>
      </span>
      <span>系统管理</span>
    </button>
    <button class="home-action">
      <span class="home-icon" aria-hidden="true">
        <i class="sz-common-iconfont icon-zuo"></i>
      </span>
      <span>返回首页</span>
    </button>
  </div>
</aside>
```

## Shell

- Sidebar width: `200px`.
- Height: `100vh`.
- Background: `var(--sz-color-white)`.
- Right border: `1px solid var(--sz-border-default)`.
- Outer padding: `52px 16px 16px`.
- The sidebar itself does not scroll the browser page. If menu content is long, only `.menu-list` scrolls.
- Layout direction is vertical: brand block at top, menu list in the middle, footer actions pinned at bottom.

## Menu Color

- Primary menu blue is the global primary color `#0068FF`.
- Use `--sz-menu-primary: var(--sz-color-primary)` for menu selected state, menu hover text/icon, and location icon.

## Brand Block

- Brand block horizontal padding: `4px`.
- Top area starts with the Shouzhu logo.
- Logo size: `32px * 32px`.
- Logo radius: `8px`.
- Gap from logo to welcome text: `8px`.
- Welcome text: `12px`, weight `400`, color `var(--sz-text-secondary)`, line-height `1.5`.
- Gap from welcome text to city: `8px`.
- City text: `16px`, weight `700`, color `var(--sz-text-title)`, line-height `1.5`.
- Location icon gap after city text: `4px`.
- Location icon color: `#0068FF`.
- Gap after city row before first menu item: `16px`.

## First-Level Menu Item

- Height: `44px`.
- Vertical padding inside item: `10px 0`.
- Left padding: `12px`.
- Right padding: `12px`.
- Icon size: `18px * 18px`.
- Menu icon source: use `sz-menu-iconfont` classes from `../shouzhu-icon-style/SKILL.md`.
- Gap between icon and text: `10px`.
- Text size: `14px`.
- Text weight: `400`.
- Text color: `var(--sz-text-body)`.
- Icon color: `#7C8BA6`.
- Arrow is right-aligned, size `16px`, color `var(--sz-text-body)`.
- Text must stay on one line and ellipsis when too long.

## Second-Level Menu Item

- Height: `44px`.
- Vertical padding inside item: `10px 0`.
- Left padding: `28px`.
- Right padding: `12px`.
- Diamond marker size: `6px * 6px`.
- Gap between marker and text: `12px`.
- Text size: `14px`.
- Text weight: `400`.
- Text color: `#8E98AD`.
- Marker color: `#D9D9D9`.
- Text must stay on one line and ellipsis when too long.

## Menu List Spacing

- Gap between menu rows: `16px`.
- Keep the menu list visually airy. Do not compress row spacing to Element Plus defaults.
- Do not use connector lines before children.
- Do not nest the second-level item inside a boxed panel.

## Selected State

- Active first-level item background: `#0068FF`.
- Active first-level item text and icon color: `var(--sz-color-white)`.
- Active item radius: `8px`.
- Active item shadow: subtle primary shadow allowed.
- Active state may show a `4px` vertical primary indicator on the far left of the sidebar when the selected item is visually offset.
- Active item keeps the same height and padding as normal items.

## Hover State

- Hover first-level item background: `#EDF3FF`.
- Hover first-level item text and icon color: `#0068FF`.
- Hover radius: `8px`.
- Hover item keeps the same height and padding as normal items.
- Active item hover does not change away from the active style.

## Footer Actions

- Footer is pinned to the bottom when the menu list is short.
- Footer horizontal padding: `4px`.
- Gap between system action and return-home card: `24px`.
- Footer bottom padding: `16px`.

### System Management

- Height: `44px`.
- Padding: `8px 12px`.
- Icon size: `28px * 28px`.
- Icon background: `#EEF3FF`.
- Icon color: `#98A9FF`.
- Icon radius: `10px`.
- Text size: `14px`.
- Text weight: `400`.
- Text color: `var(--sz-text-body)`.
- Icon/text gap: `10px`.
- Background is transparent unless hover/active is specified by the page.

### Return Home

- Height: `56px`.
- Padding: `10px 12px`.
- Background: `#FFF7E6`.
- Radius: `8px`.
- Icon size: `32px * 32px`.
- Icon background: `#FFC126`.
- Icon color: `var(--sz-color-white)`.
- Icon radius: `8px`.
- Text size: `14px`.
- Text weight: `700`.
- Text color: `var(--sz-text-body)`.
- Icon/text gap: `12px`.

## Forbidden

- Do not use a dark sidebar.
- Do not omit the Shouzhu logo.
- Do not replace the brand block with plain text.
- Do not use Element Plus default `el-menu` spacing, selected state, or nested submenu visuals.
- Do not use connector lines for second-level menus.
- Do not let menu text wrap to multiple lines.
- Do not merge system management or return home into the normal menu list.
- Do not allow the browser page to scroll because of menu height.

## CSS Contract

```css
.primary-menu-shell {
  --sz-menu-primary: var(--sz-color-primary);
  width: 200px;
  height: 100vh;
  padding: 52px 16px 16px;
  display: flex;
  flex-direction: column;
  background: var(--sz-color-white);
  border-right: 1px solid var(--sz-border-default);
  overflow: hidden;
}

.menu-brand {
  padding: 0 4px;
}

.menu-logo {
  width: 32px;
  height: 32px;
  border-radius: 8px;
  object-fit: contain;
}

.menu-welcome {
  margin-top: 8px;
  font-size: 12px;
  line-height: 1.5;
  color: var(--sz-text-secondary);
}

.menu-city {
  display: flex;
  align-items: center;
  gap: 4px;
  margin-top: 8px;
  font-size: 16px;
  line-height: 1.5;
  color: var(--sz-text-title);
}

.menu-city strong {
  font-weight: 700;
}

.menu-list {
  flex: 1;
  min-height: 0;
  margin-top: 16px;
  display: flex;
  flex-direction: column;
  gap: 16px;
  overflow-y: auto;
  overflow-x: hidden;
}

.menu-item,
.menu-child,
.system-action,
.home-action {
  border: 0;
  font-family: var(--font-family-base);
  cursor: pointer;
}

.menu-item {
  height: 44px;
  padding: 10px 12px;
  display: flex;
  align-items: center;
  gap: 10px;
  color: var(--sz-text-body);
  background: transparent;
  border-radius: 8px;
  font-size: 14px;
  line-height: 1.5;
}

.menu-icon {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  width: 18px;
  height: 18px;
  flex: none;
  font-size: 18px;
  line-height: 1;
  color: #7C8BA6;
}

.menu-text {
  min-width: 0;
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}

.menu-arrow {
  width: 16px;
  height: 16px;
  margin-left: auto;
  flex: none;
}

.menu-item:hover {
  color: var(--sz-menu-primary);
  background: #EDF3FF;
}

.menu-item:hover .menu-icon {
  color: var(--sz-menu-primary);
}

.menu-item.is-active {
  color: var(--sz-color-white);
  background: var(--sz-menu-primary);
}

.menu-item.is-active .menu-icon {
  color: var(--sz-color-white);
}

.menu-child {
  height: 44px;
  padding: 10px 12px 10px 28px;
  display: flex;
  align-items: center;
  gap: 12px;
  color: #8E98AD;
  background: transparent;
  font-size: 14px;
  line-height: 1.5;
}

.child-mark {
  width: 6px;
  height: 6px;
  flex: none;
  transform: rotate(45deg);
  background: #D9D9D9;
}

.menu-footer {
  flex: none;
  padding: 0 4px 16px;
}

.system-action {
  width: 100%;
  height: 44px;
  padding: 8px 12px;
  display: flex;
  align-items: center;
  gap: 10px;
  color: var(--sz-text-body);
  background: transparent;
  font-size: 14px;
}

.system-icon {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  width: 28px;
  height: 28px;
  flex: none;
  border-radius: 10px;
  color: #98A9FF;
  background: #EEF3FF;
}

.system-icon .sz-common-iconfont {
  font-size: 18px;
  line-height: 1;
}

.home-action {
  width: 100%;
  height: 56px;
  margin-top: 24px;
  padding: 10px 12px;
  display: flex;
  align-items: center;
  gap: 12px;
  color: var(--sz-text-body);
  background: #FFF7E6;
  border-radius: 8px;
  font-size: 14px;
  font-weight: 700;
}

.home-icon {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  width: 32px;
  height: 32px;
  flex: none;
  border-radius: 8px;
  color: var(--sz-color-white);
  background: #FFC126;
}

.home-icon .sz-common-iconfont {
  font-size: 18px;
  line-height: 1;
}
```
