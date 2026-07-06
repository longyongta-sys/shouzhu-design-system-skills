# Checklist

Use this checklist before final handoff for build, modification, and review tasks.

## Self-Audit Rule

- After completing a page, inspect the final UI yourself before handoff.
- Check whether the page has visual anomalies: misalignment, uneven spacing, inconsistent button sizes, incorrect colors, text overflow, component overlap, unexpected scrollbars, broken responsive layout, or Element Plus default styling that bypasses this design system.
- Check whether every visible component strictly follows `tokens.md`, `layout.md`, and the relevant Shouzhu component style skill.
- If any anomaly or mismatch is found, fix it yourself, then repeat the self-audit.
- Do not final-handoff while known style issues remain.

## Global

- Shell follows the required left sidebar + topbar + workspace structure.
- Primary color is `#0068FF`.
- Safe color is `#309B58`.
- Assist color is `#DE8723`.
- Font family starts with Noto Sans SC / Source Han Sans SC.
- Title/body/muted/weak text colors match tokens.
- Body/page does not scroll.
- Internal scroll belongs to table, form dialog body, tree/list, or content area.
- Text does not overlap.
- Text does not overflow buttons, cards, table cells, dialogs, or menu items.
- Default gaps, margins, and paddings follow the 8px spacing grid unless a specific component or supplied design explicitly overrides them.

## Layout

- Layout and primary menu are hard rules and have not been changed during ordinary page/component work.
- App shell uses fixed `200px` left menu, fixed `64px` topbar, and `#F2F2F2` page background.
- Workspace has `16px` radius and white background.
- Workspace fills available height under the topbar.
- Topbar is fixed `64px` high, with system title on the left and help/user actions on the right.
- Topbar system title is `18px`, bold, and title color.
- Topbar user dropdown clears Element Plus default popper border, shadow, and arrow, then uses only `var(--sz-shadow-panel)`.
- Topbar user dropdown panel uses white background, `8px` radius, and opens with `8px` gap below the user area.
- Left primary menu follows `../../shouzhu-primary-menu-style/SKILL.md`.
- Left primary menu includes `assets/brand/shouzhu-logo.png`.
- Menu width defaults to `200px`; first-level and second-level menu item height defaults to `44px`.
- Menu brand area includes logo, welcome text, city, and location icon.
- Menu bottom actions keep system management and return home separate from normal navigation.
- Menu selected state uses fixed menu blue `#0068FF` with white text; hover state uses light blue background and `#0068FF` text/icon.
- Menu text does not wrap; long labels ellipsis.
- Secondary menu is used only when there are real grouped child pages.
- Right content area does not add an unnecessary decorative outer card.
- Normal admin pages do not use page-level `max-width`, `fit-content`, centered narrow wrappers, or fixed-width containers.
- Data-list and table pages fill the available `.system-content` width.
- Responsive layout does not introduce horizontal scrolling.

## Development Structure

- Functional modules are split by feature and responsibility instead of being placed into one large file.
- A page does not contain all business logic, API calls, reusable UI, constants, dialogs, tables, and forms in a single `.vue`, `.ts`, or `.js` file.
- Complex pages split search/filter areas, tables/lists, dialogs, detail panels, approval flows, upload areas, and complex action groups into local components or module files when appropriate.
- API calls, constants, option lists, mapping dictionaries, status definitions, and utility functions are separated when they are reused or make the page hard to scan.
- File organization follows existing project conventions, or uses a feature-module structure such as `views/<feature>/index.vue`, `components/`, `api/`, `constants/`, `types/`, and `utils/`.

## Components

- Components with approved Shouzhu style skills follow their specific skills.
- Components without approved Shouzhu style skills use Element Plus default styling and behavior, without custom invented styling.
- Buttons have large/small sizing, min-width, hover, and disabled states.
- Large buttons use `80px` minimum width.
- Button display types cover pure text, icon + text, and icon-only usage where needed.
- Button icons use supplied SVG files from `assets/icons/common` when matching icons exist.
- Button icons are `16px`, placed before text, and keep a `4px` gap.
- One operation area has only one primary action when possible.
- Form controls use top labels; placeholders do not replace labels.
- Required stars only appear on required form fields.
- Form controls inside columns use `width: 100%`.
- Select selected value shown in the trigger field uses body text color, not weak hint / placeholder color.
- Checkbox size is `16px * 16px`, radius is `4px`, and label gap is `8px`.
- Checkbox checked state uses primary blue with the supplied white check icon.
- Checkbox hover border uses primary blue.
- Checkbox disabled and indeterminate states are explicitly styled.
- Table selection checkboxes are centered.
- Radio uses Element Plus `el-radio`, not `el-radio-button`.
- Radio circle is `16px`, inner selected dot is `8px`, and label gap is `8px`.
- Radio group horizontal and vertical default gap is `24px`; filter/search compact radio group may use tighter spacing.
- Radio selected state uses primary blue but selected text remains normal body text and regular weight.
- Radio disabled states use `#EEEEEE` circle background and secondary text.
- Switch uses Element Plus `el-switch`.
- Switch minimum width is `40px`, height is `24px`, knob is `18px`, and knob inset is `3px`.
- Switch off state uses neutral gray track and white knob.
- Switch on state uses safe/success green track and white knob.
- Switch disabled state keeps current on/off color but opacity is `40%`.
- Switch does not show active/inactive text.
- Risky or destructive switch changes require confirmation before changing.
- Date picker uses Element Plus `el-date-picker`.
- Date picker trigger follows existing input height, radius, border, hover/focus, and placeholder rules.
- Date picker icon is `20px` and uses weak hint text color.
- Date picker panel is white, radius `8px`, padding `16px`, and uses the Shouzhu popper class when teleported.
- Date picker inside dialogs uses `placement="bottom-start"`, keeps `teleported` enabled, and must not open upward over normal form content during ordinary use.
- Date picker panel does not match the trigger input width; single-month panels keep at least `322px` width and all 7 weekday/date columns stay inside the white panel.
- Date cells are `38px`; hover uses primary 10%, selected uses primary with white text, today uses primary text.
- Date range middle uses primary 10%; range start/end use primary with white text.
- Date picker does not show footer confirm/cancel buttons by default.
- Date picker must set `format` and `value-format`.
- Image/video upload uses Element Plus `el-upload` and follows `shouzhu-el-upload-style`.
- Image/video upload card is `120px * 120px`, radius `8px`, background `#F8F9FA`, and solid border.
- Image/video upload hover uses primary border and primary 5% background.
- Image/video upload uses `sz-common-iconfont icon-tupianshipinshangchuan` for upload and `icon-guanbi` for delete.
- Successful image/video cards show `查看` hover preview overlay.
- Image/video upload supports multiple files, delete, preview, re-upload, progress, and failure states.
- Mixed attachment upload is not covered by the image/video upload style and must use a separate attachment style when defined.
- Upload limits for count, size, and format are shown below the upload area, and validation errors use Message.
- Attachment upload uses `shouzhu-el-attachment-upload-style` for contracts, certificates, documents, compressed packages, and mixed file/image/video uploads.
- Attachment upload entry is a large outline button with upload icon and `上传附件` text.
- Attachment cards are `80px` high, `#FAFAFA`, radius `8px`, no border, with `16px` inner horizontal padding.
- Attachment file type icons use official PNG assets from `assets/icons/file-types`, not CSS-drawn badges.
- Attachment file names are `14px` body text with ellipsis, and file size/error/progress appears on the second line.
- Attachment uploading state uses a `6px` primary progress bar; failed state uses `上传失败` in danger color.
- Attachment delete uses `sz-common-iconfont icon-guanbi`, with a `20px` secondary-color circle and `14px` white close glyph.
- Attachment successful items keep the delete icon gray, not primary blue.
- Dialog forms use `el-row :gutter="16"` and `el-col :span="12"` / `:span="24"` as specified.
- Checkbox/radio/select/date/pagination selected states use primary blue.
- Status-like fields in tables and details use tags.
- Tags use `24px` height, `12px` bold text, `8px` horizontal padding, `4px` radius, and no border.
- Tags with icons use `4px` icon-to-text gap.
- Table uses Element Plus `el-table`, not a handmade div table.
- Table fills the available content width.
- Table outer radius is `8px`.
- Table does not show an outer border or vertical inner lines.
- Table has no zebra striping.
- Table header background is `#FAFAFA`.
- Table header height is `56px`, header text is `16px` bold title color.
- Table row height is `48px`, body text is `14px` regular body color.
- Table rows containing two-line stacked information use `72px` row height across the whole row.
- Two-line table cells use main text plus secondary text with `4px` vertical gap; secondary text is `12px` and secondary text color.
- Table cell horizontal padding is `24px`.
- Table row bottom divider uses the default line color.
- Table last visible row does not show a bottom divider.
- Table hover row background is `#FAFAFA`; selected row background is primary 10%.
- Table operations do not ellipsize.
- Table wrapper fills the available content width; `el-table` uses `width="100%"`.
- Tables are not trapped in fixed-width, intrinsic-width, or `fit-content` containers.
- With few columns, the table still fills the content region instead of leaving unused blank space outside the table.
- Table selection and index columns are `80px`.
- Table operation column is `100-200px` and fixed on the right.
- Table normal business columns use `min-width`; only fixed-purpose columns use fixed `width`.
- Table status/type/result columns render tags.
- Empty table cells display `--`.
- Long table text uses ellipsis and hover tooltip.
- Table row operation icons are `24px`; default icon color is secondary text color.
- Table row operation buttons are `24px` circular icon buttons when matching icons exist.
- Tree uses Element Plus `el-tree` for hierarchical data.
- Tree node default height is `48px`.
- Tree visible node row gap is `4px`, including parent-child and same-level rows.
- Tree parent nodes are dark and bold; leaf nodes use auxiliary text color and normal weight.
- Tree indentation defaults to `24px`, and tree nodes do not use leading connector lines.
- Tree hover, selected/current, and disabled states are all explicitly styled.
- Tree expand/collapse arrow is `12px`.
- Tree hover state uses primary 10% background and primary text.
- Tree selected/current state uses primary 5% background with primary text, regular weight, and no extra left bar.
- Tree disabled nodes use weak text, no background, and no hover highlight.
- Tree supports search filtering, click selection, expand/collapse arrows, and checkbox multi-select when needed.
- Long tree content scrolls inside the tree panel, not the browser page.
- Existing icon assets are reused where possible.
- Monochrome UI icons use the namespaced iconfont classes from `shouzhu-icon-style`.
- Do not use the raw `iconfont` base class when multiple iconfont projects are loaded.

## Pagination

- Pagination is fixed at the bottom of the page content area for table pages.
- Pagination still displays when the table is empty.
- Total text format is `共 50 条数据`.
- Default page size is `10`.
- Page size options are `[10, 20, 30, 40, 50, 100]`.
- Current page button is `32px * 32px` and uses primary blue.
- Normal page number text uses secondary text color.
- Jump input is `32px * 32px`.
- Page-size selector width is adaptive.

## Details

- Detail page layout follows `shouzhu-detail-style`.
- Full detail pages use `.sz-detail-page`; they are not replaced by dashboard-like overview pages, KPI strips, freeform card grids, or right-side link lists unless the designer explicitly defines that as a separate pattern.
- Detail page background uses `var(--sz-bg-subtle)` so white detail panels remain visible.
- Detail read-only content is organized inside `.sz-detail-panel` sections, not placed loose on the page background.
- Detail page does not stack double outer spacing such as `16px + 16px` inside the locked shell.
- Detail page removes the outer content wrapper's extra top `16px` because the `40px` back row already acts as the page's top control area.
- Detail back row is fixed at `40px` high.
- Detail back row has no extra vertical gap before the detail body.
- Detail overflow scroll starts independently inside the left detail column and right detail column below the fixed `40px` back row.
- Detail left/right column scrollbars have no top/bottom arrows, use `6px` thickness, thumb color `#CCCCCC`, and transparent track.
- Detail page has left adaptive detail area and right fixed `500px` detail area on desktop.
- Detail right area remains a fixed `500px` detail panel, not a narrow navigation, action, or link sidebar.
- Detail left/right column gap is `16px`; left detail panels stack with `16px` gap.
- Detail left panels are content-adaptive; the last left panel fills remaining height when content is not enough.
- Detail right panel has `min-height: 100%` and grows with content; detail text must stay inside the white panel.
- When detail content exceeds the available height, the left and right detail columns scroll independently and the bottom action area stays fixed in its own bottom row.
- Detail bottom action area must not overlay or cover the final rows of the scrollable detail content.
- Detail bottom action area is optional and appears only when the page has real actions.
- Left/right content areas keep a fixed `16px` visual distance above the bottom action area when actions exist.
- If no bottom action area exists, `.sz-detail-page` uses `is-no-footer`, `.sz-detail-body` has no extra bottom margin, and only one `16px` bottom distance remains.
- Detail panels use white background, `8px` radius, and `24px` padding.
- Detail section title uses `16px` bold title text.
- Detail section title has a primary blue mark, `3px` wide and `16px` high, with `8px` gap before the title text.
- Detail page bottom action area is fixed at the bottom by the detail page grid layout.
- Detail bottom action area radius is `8px`.
- Detail bottom actions align right with `16px` button gap and do not cover content.
- Detail pages do not show a shared central scrollbar, body-level scrollbar, or vertical divider between left and right content; left and right columns own their own scroll.
- Detail rows use `字段名：字段值`.
- Detail text is `14px`.
- Normal fields render plain text.
- Status/type/result fields render tags.
- Long values wrap without horizontal scrolling.

## Approval Flow

- Approval flow follows `shouzhu-approval-flow-style`.
- Approval flow appears only inside the right `500px` detail panel.
- Approval flow width follows the parent container at `100%`.
- Approval flow title is fixed as `审核流程` and uses the detail title mark style.
- Approval statuses are limited to `发起审核`, `审核中`, `审核通过`, `审核未通过`, and `审核作废`.
- Approval status text uses the approved token colors: primary, warning, success, danger, and weak hint.
- Approval node icons use the official PNG assets from `assets/approval-flow`; do not replace them with iconfont.
- Approval icons are `48px * 48px`.
- Approval timeline line is `#CACACA`, `2px`, dashed, and does not continue below the last node.
- Approval node content cards use `#FAFAFA`, `12px` radius, and `24px` padding.
- Pending nodes without content show no content card.
- Empty approval opinion, attachment, or image rows are hidden.
- Approval attachments reuse attachment upload visuals but are read-only and show only view/download actions.
- Approval site images are `100px * 100px`, `cover`, `8px` radius, with max three per row and preview on click.
- Approval flow is fully expanded by default and does not support collapse or view-more truncation.
- Approval flow does not create its own internal scroll area; long content scrolls with the right `500px` detail column.

## Dialogs

- Dialog form default/minimum width is `550px`, max width is `650px`, and it adapts to viewport width.
- Dialog form uses `550px` for one-column forms and `650px` for two-column forms.
- Dialog form uses `is-single-column` for one-column forms and `is-two-column` for two-column forms.
- Dialog form radius is `12px`, surface is white, and it has no shadow.
- Dialog overlay is black at `50%` opacity.
- Dialog form cannot close by overlay click or ESC.
- Dialog form content adapts to width and has no horizontal scroll.
- Dialog form overrides Element Plus default header/body/footer padding rather than stacking extra padding on top.
- Dialog form inner padding is `24px`; header/body/footer padding is cleared to `0`.
- Dialog form title is `16px` bold title color, and close icon is `20px` title color with no visible hover style.
- Dialog form body scrolls internally when content overflows.
- Dialog form footer is fixed/sticky at the bottom when the body scrolls.
- Dialog form footer buttons align right with `16px` gap.
- Dialog form footer has no top divider line.
- Message dialogs have the correct type: regular confirm, alert, or feedback.
- Message dialog width is `500px`, radius is `12px`, and padding is `32px`.
- Message dialog title/body/actions are centered.
- Message dialog title-to-body gap is `16px`.
- Message dialog body-to-actions gap is `24px`.
- Message dialog double-button gap is `16px`.
- Message dialog cancel button uses the secondary gray-fill button style.
- Message dialogs do not show icons by default.
- Destructive message dialog confirm action uses danger color `#DD4620`.
