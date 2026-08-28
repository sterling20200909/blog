# 博客部署指南

## 快速部署（推荐）

由于 Cloudflare API 对 Pages 子域名有限制，建议使用以下方法：

### 方法一：Cloudflare Dashboard 手动上传（最快）

1. **打开 Cloudflare Dashboard**
   - 访问：https://dash.cloudflare.com/
   - 登录：Youngsterling314@gmail.com

2. **创建 Pages 项目**
   - 左侧菜单点击 **Pages**
   - 点击 **Create a project**
   - 选择 **Direct upload**

3. **上传文件**
   - 项目名：`sterling-blog`
   - 将整个目录拖拽上传：
     ```
     /Users/shuaiyuan/WorkBuddy/2026-08-27-18-21-02/astro-blog-deploy/
     ```
   - 点击 **Save and Deploy**

4. **绑定域名**
   - 进入项目设置 → **Domains**
   - 添加自定义域名：`sterling.cc.cd`
   - 添加自定义域名：`www.sterling.cc.cd`

5. **等待生效**
   - DNS 通常几分钟后生效
   - 部署后获得子域名：`https://sterling-blog.pages.dev`

### 方法二：GitHub 自动部署（推荐用于持续更新）

#### 步骤 1: 创建 GitHub 仓库

```bash
# 在项目目录初始化 Git
cd /Users/shuaiyuan/WorkBuddy/2026-08-27-18-21-02/astro-blog
git init
git add .
git commit -m "Initial commit"

# 在 GitHub 创建仓库（如 sterling/blog）
git remote add origin https://github.com/sterling/blog.git
git push -u origin main
```

#### 步骤 2: 连接 Cloudflare Pages

1. 访问 https://dash.cloudflare.com/
2. 进入 **Pages** → **Create a project** → **Connect to Git**
3. 选择 GitHub 仓库 `sterling/blog`
4. 配置构建设置：
   - Framework preset: **Astro**
   - Build command: `pnpm build`
   - Build output directory: `dist`
   - Root directory: `/Users/shuaiyuan/WorkBuddy/2026-08-27-18-21-02`
5. 点击 **Save and Deploy**

#### 步骤 3: 绑定域名

同方法一。

### 方法三：使用 Wrangler CLI（需要解决 API 限制）

```bash
# 安装 Wrangler
npm install -g wrangler

# 登录
npx wrangler login

# 部署
npx wrangler pages deploy /Users/shuaiyuan/WorkBuddy/2026-08-27-18-21-02/astro-blog-deploy \
  --project-name=sterling-blog \
  --branch=production
```

## 部署后配置

### Giscus 评论系统

1. 在 GitHub 创建仓库（如 `sterling/blog-comments`）
2. 启用 Discussions 功能：Settings → General → Features → Discussions
3. 安装 Giscus App：https://github.com/apps/giscus
4. 访问 https://giscus.app/ 获取配置：
   - Repository: 选择你的仓库
   - Category: Announcements
   - Language: Chinese (Simplified)
5. 更新 `src/components/GiscusComments.astro` 中的配置
6. 重新构建部署

### 添加新文章

1. 在 `src/content/posts/` 创建 `.md` 或 `.mdx` 文件
2. 添加 frontmatter：
   ```markdown
   ---
   title: "文章标题"
   author: "Sterling"
   pubDatetime: 2026-08-28T12:00:00Z
   slug: "article-slug"
   featured: false
   draft: false
   tags:
     - astro
     - blog
   description: "文章描述"
   ---

   文章内容...
   ```
3. 构建并部署

## 项目文件

| 文件/目录 | 说明 |
|-----------|------|
| `astro-blog/` | 博客源码 |
| `astro-blog/dist/` | 构建输出 |
| `astro-blog-deploy/` | 部署文件（与 dist 相同） |
| `deploy-blog.sh` | 部署脚本 |
| `deploy-blog-to-github.sh` | GitHub 部署脚本 |
| `DEPLOY-GUIDE.md` | 详细部署指南 |

## 常见问题

### Q: 部署后样式丢失
**A**: 确保上传了完整的 `dist` 目录，包括 `_astro` 文件夹。

### Q: 如何绑定自定义域名
**A**: 在 Pages 项目设置 → Domains → Add custom domain

### Q: 如何启用 HTTPS
**A**: Cloudflare Pages 自动启用 HTTPS，无需额外配置

### Q: 如何配置评论系统
**A**: 参考上方的 Giscus 配置步骤

## 博客信息

- **站点**: https://sterling.cc.cd
- **标题**: Sterling Blog
- **作者**: Sterling
- **语言**: 中文
- **文章数**: 17 篇（含示例文章）
- **搜索**: Pagefind 站内搜索已启用
- **RSS**: 已生成
- **Sitemap**: 已生成
