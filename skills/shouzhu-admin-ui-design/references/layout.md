# Layout

Use this file for the admin shell, topbar, workspace, optional secondary menu, and scroll ownership. For the fixed left primary menu, read `../../shouzhu-primary-menu-style/SKILL.md`.

## Locked Rule

This page layout is a hard rule and must not be changed in normal page generation. Do not reinterpret, compress, restyle, or replace the fixed shell, topbar, workspace, or left primary menu. Change these values only when the designer explicitly says the design system layout itself is being updated.

## Required Shell

Use this structure for admin pages:

```vue
<el-config-provider>
  <el-container class="app-shell">
    <el-aside width="200px" class="primary-aside">fixed primary menu</el-aside>
    <el-container class="main-column">
      <el-header class="topbar">system title + help + user actions</el-header>
      <el-main class="app-main">
        <div class="system-workspace no-secondary-nav">
          <div class="system-content">business content</div>
        </div>
      </el-main>
    </el-container>
  </el-container>
</el-config-provider>
```

For grouped modules, use:

```vue
<div class="system-workspace with-secondary-nav">
  <aside class="system-nav-panel">secondary menu</aside>
  <div class="system-content">business content</div>
</div>
```

## Dimensions

- `.app-shell`: `height: 100vh; overflow: hidden; background: #F2F2F2`.
- Primary aside: fixed width `200px`. Use `../../shouzhu-primary-menu-style/SKILL.md` for all menu structure, spacing, brand, states, and bottom actions.
- Main column: `min-width: 0`, `min-height: 0`, `height: 100%`.
- Topbar: fixed height `64px`, padding `0 32px`, white background.
- App main: fills available height, padding `16px`, overflow hidden.
- Workspace: fills remaining height, white background, radius `16px`, overflow hidden.
- Workspace with secondary nav: `grid-template-columns: 180px minmax(0, 1fr)`.
- Workspace without secondary nav: `grid-template-columns: minmax(0, 1fr)`.
- Business content: padding `24px 16px 20px`, min-width/min-height `0`.
- Business content uses the full available workspace width. Do not add page-level `max-width`, `fit-content`, or centered narrow wrappers around normal admin pages.
- Data-list pages and table pages must be full-width inside `.system-content`; compact widths are allowed only for intentionally framed tools, dialog previews, or short forms.

## Spacing Rule

- Default spacing follows an 8px grid.
- Use multiples of 8 such as `8px`, `16px`, `24px`, and `32px` for normal gaps, margins, paddings, and layout distances.
- Explicit component rules or supplied design specs may override this default for a specific element. A specific exception does not change the global default.

## Topbar

- Required on every admin page.
- Left side: system title only.
- System title uses `18px`, `700`, title color.
- Right side reserves help, user avatar, user identity, organization, and account dropdown.
- Help area uses icon + `帮助` text.
- User area shows avatar, user name, organization name, and dropdown arrow.
- User account dropdown uses `popper-class="sz-user-dropdown-popper"` and clears Element Plus default popper border, shadow, and arrow.
- User account dropdown panel background is white, radius `8px`, shadow is `var(--sz-shadow-panel)`, and it opens below the user area with an `8px` gap.
- User account dropdown item height is `40px`, horizontal padding is `16px`, font size is `14px`, and logout uses danger color.
- Do not place topbar actions inside business content.

Topbar user dropdown CSS contract:

```css
.sz-user-dropdown-popper.el-popper {
  border: 0;
  border-radius: 8px;
  box-shadow: var(--sz-shadow-panel);
}

.sz-user-dropdown-popper .el-popper__arrow {
  display: none;
}

.sz-user-dropdown-popper .el-dropdown-menu {
  min-width: 128px;
  padding: 8px 0;
  border: 0;
  border-radius: 8px;
  box-shadow: none;
  background: var(--sz-color-white);
}

.sz-user-dropdown-popper .el-dropdown-menu__item {
  height: 40px;
  padding: 0 16px;
  color: var(--sz-color-danger);
  font-size: var(--sz-font-size-body);
}
```

## Primary Menu

The left primary menu is fixed and must follow `../../shouzhu-primary-menu-style/SKILL.md`.

Do not define or approximate primary menu spacing in this layout file. The menu style skill is the source of truth for the Shouzhu logo brand block, first-level menu, second-level menu, selected and hover states, system management action, and return-home action.

The primary menu is a locked system component. Do not change its width, brand block, menu item dimensions, row gaps, selected/hover states, or footer actions when building ordinary pages.

Secondary menu:

- Use only when the module has real grouped child pages.
- Do not create an empty or fake secondary menu.
- Item height `40px`.
- Item radius `8px`.
- Normal text uses body color.
- Active state uses background `var(--sz-color-primary-light)`, text `var(--sz-color-primary)`, font weight `700`.

## Scroll Ownership

- The browser page itself must not scroll.
- Long content scrolls inside the content area, table region, tree/list region, or dialog body.
- Use `min-height: 0` on flex/grid children that contain scrollable regions.
- Scrollbars should be hidden by default and appear only while scrolling.

## Responsive Behavior

- Around `1100px` and below, collapse left-right business grids to one column.
- Replace vertical dividers with horizontal dividers when stacked.
- Preserve internal scroll behavior.
- Do not let mobile/narrow layouts create horizontal scrolling.

## Failure Guards

Do not:

- Use a dark primary sidebar.
- Move the topbar into the business content area.
- Omit the system title or user actions from the topbar.
- Add secondary navigation when the module does not need it.
- Put page sections inside nested decorative cards.
- Make the entire browser page scroll.
- Use marketing or landing-page layout patterns.
