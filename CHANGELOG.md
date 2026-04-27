# 变更日志

## 2026-04-27

- 新增双主题切换功能：暖色工程风（默认）和深色科技风，导航栏可一键切换。
- 原因：两种视觉风格各有优势——暖色偏专业稳重适合猎头和 employer，深色偏科技感适合同行和技术社区——用户希望同时保留。
- 范围：
  - 重构 `_sass/pages/modern-home.sass`，将所有硬编码颜色替换为 CSS 自定义属性（`--mh-*` 前缀），在 `:root` 和 `[data-theme="dark"]` 中分别定义两套主题色。
  - 在 `_layouts/modern-home.html` 中添加：`<head>` 内防闪烁同步脚本、导航栏主题切换按钮、`<body>` 底部切换逻辑 JS。
  - 在 `_data/home.yml` 中添加切换按钮双语文案（`theme_toggle_dark` / `theme_toggle_light`）和 Hero 渐变文字标记（`title_highlight`）。
- 深色主题特有效果：渐变标题文字、卡片发光边框、背景辐射光晕。
- 主题选择通过 localStorage 持久化，刷新和跨页面保持一致。
- 升级项目卡片：新增 tech-tags 技术标签展示、hover 上浮和发光效果。
- 所有改动仅影响 modern-home 相关文件，旧页面（blog、about 等）不受影响。

## 2026-04-26

- 重写 `README.md`，将原模板说明替换为当前个人网站的中文维护文档。
- 原因：旧 README 仍是 Indigo 模板介绍，已经无法反映当前双语首页、GoatCounter 统计和 GitHub Pages 发布流程。
- 范围：补充网站定位、技术栈、目录结构、内容维护方式、访问统计、发布流程和维护原则。

## 2026-04-25

- 确认使用 GoatCounter 作为网站访问统计方案，并在 `_config.yml` 中启用 `https://lzhangbq.goatcounter.com/count`。
- 原因：GoatCounter 可以直接配合 GitHub Pages 使用，不需要接入 Cloudflare DNS、不需要后端服务，也不会增加本地依赖。
- 将根路径首页改为新版中文首页，使 `https://lzhangbq.github.io/` 直接展示新版个人网站。
- 原因：公开访问入口应该直接进入新版作品集页面，同时方便用 `curl` 检查 GoatCounter 脚本是否已经部署。
- 提交前清理本地依赖缓存目录 `vendor/` 和 `.bundle/`，避免占用本地空间或误提交生成文件。

## 2026-04-24

- 开始个人网站重新设计与中英文双语改版。
- 原因：原站点基于极简博客模板，新方向需要更清晰地展示 AI / 大模型开发工程师背景。
- 范围：先建立变更记录，再调整布局、内容结构和样式。
- 新增双语首页数据、新版首页布局，以及 `/zh/` 和 `/en/` 两个入口页面。
- 原因：先做一个低风险预览版本，不删除现有文章、项目页或旧内容。
- 优化双语首页细节：站内导航锚点保留在当前语言页面，项目卡片链接文案支持中英文。
- 调整新版首页 Sass 写法，避免旧版 GitHub Pages Sass 管线解析 `min()` 与 `calc()` 组合时出现兼容问题。
- 决定继续保留 Jekyll，不迁移到其他框架。
- 原因：Jekyll 能延续现有 GitHub Pages 工作流，并尽量减少本地依赖和存储占用。
- 清理 Ruby gem 安装失败后留下的本地依赖缓存；这些文件是生成文件，不属于网站源码。
- 将原计划的 Cloudflare Web Analytics 方案替换为 GoatCounter。
- 原因：GoatCounter 更适合当前 GitHub Pages 场景，不需要 Cloudflare DNS、后端服务、付费托管或本地依赖。
- 启用计划中的 `lzhangbq.goatcounter.com` 统计端点，使部署后的 GitHub Pages 页面会包含统计脚本。
- 将根首页从跳转页改为新版中文首页。
- 原因：访问者和命令行检查 `https://lzhangbq.github.io/` 时应直接拿到新版页面和 GoatCounter 脚本。
- 将 GoatCounter 脚本 include 移到页面 body 结束前，更贴近推荐的脚本放置方式。
- 简化首页项目筛选逻辑，使用 Liquid 的 `where` 和 `limit` 过滤器提升 Jekyll 构建兼容性。
