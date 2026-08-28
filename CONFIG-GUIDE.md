# Sterling Blog 配置指南

## 博客已配置完成

博客已使用 AstroPaper 主题搭建，配置信息如下：

- **站点 URL**: https://sterling.cc.cd
- **站点标题**: Sterling Blog
- **描述**: 个人技术博客，分享开发经验与技术思考
- **作者**: Sterling
- **语言**: 中文 (zh-CN)
- **时区**: Asia/Shanghai

## 博客已构建完成 ✅

博客已成功构建，构建输出位于：`/Users/shuaiyuan/WorkBuddy/2026-08-27-18-21-02/astro-blog/dist/`

### 构建状态
- ✅ 所有页面生成成功（17 篇文章 + 静态页面）
- ✅ 站内搜索索引已生成（Pagefind）
- ✅ RSS 订阅已生成
- ✅ Sitemap 已生成
- ✅ 响应式设计和暗色模式已启用

## 待完成配置

### 1. Giscus 评论系统配置

博客已集成 Giscus 评论功能。需要按以下步骤配置：

#### 步骤 1：创建 GitHub 仓库
- 创建一个新的 GitHub 仓库用于存储评论（可以是私有仓库）
- 仓库名称建议：`sterling-blog-comments` 或类似名称

#### 步骤 2：启用 GitHub Discussions
- 进入仓库 Settings → General
- 找到 "Features" 部分，启用 "Discussions"

#### 步骤 3：安装 Giscus App
- 访问 https://github.com/apps/giscus
- 安装到你的 GitHub 账户

#### 步骤 4：获取配置信息
- 访问 https://giscus.app/
- 按照向导配置：
  - Repository: 选择你的仓库
  - Category: 创建一个新的 Announcement 类型分类（如 "General"）
  - 语言: 选择 "Chinese (Simplified)"
  - 主题: 保持默认（preferred_color_scheme）
  
- 复制生成的 script 标签配置

#### 步骤 5：更新配置文件
- 编辑 `src/components/GiscusComments.astro`
- 替换以下占位符：
  - `repo`: "你的用户名/仓库名"（如 "sterling/blog-comments"）
  - `repoId`: 从 Giscus 配置中获取
  - `category`: "Announcement" 或你创建的分类名
  - `categoryId`: 从 Giscus 配置中获取

### 2. 部署到 Cloudflare Pages

#### 本地构建
```bash
cd /Users/shuaiyuan/WorkBuddy/2026-08-27-18-21-02/astro-blog
npm run build
```

#### 部署到 Cloudflare Pages
1. 登录 Cloudflare Dashboard
2. 进入 Pages → Create a project
3. 选择 "Direct upload" 或连接 GitHub 仓库
4. 上传 `dist` 目录内容
5. 绑定域名 `sterling.cc.cd`

或者使用 Wrangler CLI：
```bash
npx wrangler pages deploy dist --project-name=sterling-blog
```

## 示例文章

博客已包含示例文章，位于 `src/content/posts/` 目录：
- `adding-new-post.mdx` - 如何添加新文章
- `customizing-astropaper-theme-color-schemes.mdx` - 主题定制
- `dynamic-og-images.md` - 动态 Open Graph 图片
- `how-to-add-latex-equations-in-blog-posts.md` - LaTeX 公式支持
- `how-to-configure-astropaper-theme.mdx` - 主题配置指南
- `how-to-integrate-giscus-comments.md` - Giscus 评论集成指南

## 自定义博客内容

### 添加新文章
1. 在 `src/content/posts/` 目录创建新的 `.md` 或 `.mdx` 文件
2. 添加 frontmatter（元数据）：
```yaml
---
title: "文章标题"
pubDatetime: 2026-08-28T00:00:00Z
description: "文章描述"
author: "Sterling"
tags:
  - 标签1
  - 标签2
---
```
3. 编写文章内容

### 修改配置
编辑 `astro-paper.config.ts` 文件：
- 站点信息（标题、描述、作者等）
- 社交链接
- 功能开关

## 域名配置

博客使用域名 `sterling.cc.cd`，需要确保：
1. DNS 记录指向 Cloudflare Pages（或当前 Worker）
2. SSL 证书已配置
3. 已验证域名所有权

## 博客特性

✅ **免登录浏览** - 所有用户无需登录即可查看文章内容
✅ **评论功能** - 通过 Giscus 实现，GitHub 用户可登录评论
✅ **暗色模式** - 支持自动切换和手动切换
✅ **搜索功能** - 使用 Pagefind 实现站内搜索
✅ **响应式设计** - 适配桌面和移动设备
✅ **SEO 优化** - 自动生成 sitemap 和 RSS

## 文件位置

- **博客源码**: `/Users/shuaiyuan/WorkBuddy/2026-08-27-18-21-02/astro-blog/`
- **构建输出**: `/Users/shuaiyuan/WorkBuddy/2026-08-27-18-21-02/astro-blog/dist/`
- **配置文档**: `CONFIG-GUIDE.md`
- **部署指南**: `DEPLOY-GUIDE.md`

## 已完成的任务

1. ✅ 克隆 AstroPaper 博客主题
2. ✅ 配置站点信息（标题、描述、作者、语言）
3. ✅ 集成 Giscus 评论组件
4. ✅ 安装依赖并成功构建
5. ✅ 生成站内搜索索引
6. ✅ 创建配置和部署文档

## 待完成的任务

1. ⏳ 配置 Giscus 评论系统（获取 GitHub 仓库信息）
2. ⏳ 部署到 Cloudflare Pages
3. ⏳ 绑定域名 `sterling.cc.cd`
4. ⏳ 添加你的第一篇文章
