# Shouzhu Design System Skills

这是首筑后台管理系统的 AI agent 设计规范 skill 交付包，适用于 Vue 3 + Element Plus 项目。

这套 skill 的目标是让产品、UI、开发在生成原型或页面时，优先遵循首筑后台的布局、菜单、组件样式、交互状态和业务展示规则，从而减少 AI 自由发挥导致的样式偏差。

## 使用方式

使用时优先调用：

```text
@shouzhu
```

`shouzhu` 是快捷入口，会引导 AI 使用完整的首住后台设计系统规则。

如果当前工具不识别快捷入口，也可以直接调用：

```text
@shouzhu-admin-ui-design
```

## 依赖关系

这套规范不是替代 Element Plus，而是在 Element Plus 的基础上做首筑后台样式约束。

交付和使用时需要同时具备：

- Element Plus 组件 skill：用于保证组件能力完整。
- Shouzhu 设计规范 skill：用于约束首住后台的布局、颜色、间距、组件状态和业务样式。

当某个组件在 Shouzhu skill 中已经定义规则时，必须优先使用 Shouzhu 规则。

当某个组件暂时没有定义 Shouzhu 规则时，默认使用 Element Plus 原始组件规则，不允许自行创造新的视觉风格。

## 硬性规则

以下规则属于首筑后台基础框架规则，不应在具体页面中随意更改：

- 左侧主菜单固定宽度为 200px。
- 顶部栏固定高度为 64px。
- 系统页面背景色使用 `#F2F2F2`。
- 主内容区域默认内边距为 16px。
- 页面布局和左侧菜单样式为固定规则。
- 全局主色为 `#0068FF`。
- 默认元素间距遵循 8px 倍数，例如 8、16、24。

## 已覆盖内容

当前交付包已包含以下规则：

- 全局设计入口：`shouzhu`
- 后台页面总规范：`shouzhu-admin-ui-design`
- 左侧菜单：`shouzhu-primary-menu-style`
- 详情页布局：`shouzhu-detail-style`
- 审批流程：`shouzhu-approval-flow-style`
- 图标资源：`shouzhu-icon-style`
- 图片查看：`shouzhu-image-preview-style`
- Button 按钮
- Form / Input / Select / DatePicker
- Checkbox / Radio / Switch
- Table / Pagination / Tag / Tree
- Dialog / MessageBox
- Upload 图片视频上传
- Attachment Upload 附件上传

## 推荐安装位置

将本仓库中的 `skills` 文件夹内所有目录复制到 Codex skills 目录中。

Windows 默认位置通常是：

```text
C:\Users\<你的用户名>\.codex\skills
```

复制后建议重启 Codex，确保新的 skill 可以被识别。

## 推荐协作方式

UI 维护这套 skill 时，建议按组件拆分维护：

- 基础框架和总规则放在 `shouzhu-admin-ui-design`
- 每个组件样式单独放在对应的 `shouzhu-el-xxx-style`
- 业务模块样式单独放在对应的业务 skill，例如详情页、审批流程

这样可以避免一个 skill 过于臃肿，也方便后续增量更新。

## 交付建议

交付给产品或开发时，建议同时说明：

1. 生成首筑后台页面时，优先 `@shouzhu`。
2. 页面必须遵循固定左侧菜单和系统布局。
3. 已定义的组件样式必须按 Shouzhu 规则执行。
4. 未定义的组件样式回退到 Element Plus 默认规则。
5. 如生成结果与规范不一致，应优先补充或修正对应 skill，而不是只在单个页面里临时修。

