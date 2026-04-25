# Liangwei Zhang 个人网站

这是 Liangwei Zhang 的个人网站源码，部署在 GitHub Pages：

<p align="center">
  <a href="https://lzhangbq.github.io/"><strong>https://lzhangbq.github.io/</strong></a>
</p>

网站定位是一个面向 AI / 大模型开发方向的双语个人作品集。它用于集中展示个人背景、工程经历、精选项目、简历入口与联系方式，并保留后续持续更新文章和项目的能力。

## 网站定位

- **身份表达**：计算机科学硕士、前美国 TikTok 软件开发工程师、当前 AI / 大模型开发方向。
- **内容结构**：中文首页、英文首页、经历、项目、文章、联系方式。
- **技术取向**：保持静态网站架构，优先稳定、轻量、易维护，不引入不必要的前端框架或后端服务。
- **数据统计**：使用 GoatCounter 做轻量访问统计，不需要 Cloudflare DNS、数据库或自建服务。

## 线上入口

- 中文主入口：`https://lzhangbq.github.io/`
- 中文页面：`https://lzhangbq.github.io/zh/`
- 英文页面：`https://lzhangbq.github.io/en/`
- GoatCounter 后台：`https://lzhangbq.goatcounter.com/`

## 技术栈

- **Jekyll / GitHub Pages**：静态站点生成与托管。
- **Liquid**：模板和内容渲染。
- **Sass**：页面样式组织。
- **Markdown**：项目、文章和个人内容维护。
- **GoatCounter**：隐私友好的轻量访问统计。

## 目录说明

```text
.
├── _config.yml                         # 站点配置、个人信息、社交链接、统计配置
├── _data/home.yml                      # 中英文新版首页内容
├── _layouts/
│   ├── default.html                    # 旧页面/文章通用布局
│   ├── modern-home.html                # 新版双语首页布局
│   ├── page.html                       # 普通页面布局
│   └── post.html                       # 项目/文章布局
├── _includes/
│   ├── analytics-goatcounter.html      # GoatCounter 统计脚本
│   └── style.scss                      # Sass 汇总入口
├── _sass/
│   └── pages/modern-home.sass          # 新版首页样式
├── _posts/                             # 项目与文章内容
├── assets/                             # 简历、图片、图标等静态资源
├── en/index.html                       # 英文首页入口
├── zh/index.html                       # 中文首页入口
├── index.html                          # 根路径中文首页
└── CHANGELOG.md                        # 中文变更日志
```

## 日常维护

### 更新首页文案

首页主要内容集中在：

```text
_data/home.yml
```

其中：

- `zh`：中文首页内容。
- `en`：英文首页内容。
- `experience`：经历区块。
- `focus`：技术方向标签。
- `projects_intro`：精选项目区块介绍。
- `contact_body`：联系区块说明。

### 更新个人配置

站点级配置集中在：

```text
_config.yml
```

常用字段包括：

- `name`：姓名。
- `bio`：个人一句话简介。
- `picture`：头像路径。
- `resume-url`：简历文件路径。
- `github` / `linkedin` / `email`：社交与联系方式。
- `goatcounter_endpoint`：GoatCounter 统计地址。

### 新增项目或文章

在 `_posts/` 中新增 Markdown 文件，文件名格式建议为：

```text
YYYY-MM-DD-title.markdown
```

如果希望项目出现在新版首页精选项目中，需要在 front matter 中设置：

```yaml
projects: true
category: project
```

新版首页当前会展示最近的 4 个 `projects: true` 内容。

### 更新简历

替换下面文件即可：

```text
assets/LiangweiZhang_CV.pdf
```

如果文件名变化，需要同步更新 `_config.yml` 中的 `resume-url`。

## 访问统计

当前使用 GoatCounter：

```yaml
goatcounter_endpoint: https://lzhangbq.goatcounter.com/count
```

部署后可以检查线上页面是否包含统计脚本：

```bash
curl -s https://lzhangbq.github.io/ | grep goatcounter
```

如果看到 `data-goatcounter="https://lzhangbq.goatcounter.com/count"`，说明统计脚本已经上线。

## 发布流程

当前部署分支是：

```bash
gh-pages
```

推荐流程：

```bash
git status
git add <需要提交的文件>
git commit -m "说明本次改动"
git push origin gh-pages
```

GitHub Pages 部署完成后，访问：

```text
https://lzhangbq.github.io/
```

## 变更记录原则

所有代码、布局、内容结构或统计方案的变更，都需要同步记录在：

```text
CHANGELOG.md
```

记录内容应包括：

- 改了什么。
- 为什么改。
- 影响范围。
- 是否涉及部署或第三方服务。

## 维护原则

- 优先保持网站轻量、稳定、易部署。
- 不引入不必要的后端服务。
- 不提交本地依赖缓存，例如 `vendor/`、`.bundle/`、`node_modules/`。
- 不提交 IDE 本地配置，例如 `.idea/`。
- 重要内容改动先更新 `CHANGELOG.md`，再提交代码。

## 致谢

本站最初基于 Indigo Minimalist Jekyll Template 改造，后续已重构为面向个人 AI / 大模型工程背景的双语作品集网站。
