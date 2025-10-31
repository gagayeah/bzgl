# 博主追踪系统 - 分享网页

这是多项目博主管理系统的云端分享网页项目,用于部署到 Cloudflare Pages。

## 部署步骤

### 1. 准备 GitHub 仓库

1. 在 GitHub 创建一个新仓库(名称随意,比如 `blogger-share`)
2. 在本地执行:

```bash
cd /Users/gaga/Desktop/博主追踪系统/blogger-share-web
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/你的用户名/blogger-share.git
git push -u origin main
```

### 2. 部署到 Cloudflare Pages

1. 访问 [Cloudflare Pages](https://pages.cloudflare.com/)
2. 登录或注册 Cloudflare 账号
3. 点击 "Create a project"
4. 选择 "Connect to Git"
5. 授权并选择你的 GitHub 仓库 `blogger-share`
6. 配置构建设置:
   - **Project name**: `blogger-share` (或你喜欢的名字)
   - **Production branch**: `main`
   - **Build command**: (留空)
   - **Build output directory**: `/`
7. 点击 "Save and Deploy"

### 3. 获取部署 URL

部署完成后,你会得到一个 URL,类似:
```
https://blogger-share.pages.dev
```

或者你可以绑定自己的域名。

### 4. 修改应用生成分享链接

完成部署后,需要修改桌面应用,让它生成 Cloudflare Pages 的链接而不是 HTML 文件。

分享链接格式:
```
https://blogger-share.pages.dev/?id=abc123
```

## 工作原理

- 用户在桌面应用中点击"分享到云端"
- 数据上传到 Supabase 数据库,生成唯一的 shareId
- 应用生成分享链接(包含 shareId)
- 别人打开链接时,网页从 Supabase 实时读取数据
- 数据是动态的,修改后自动同步

## 技术栈

- **前端**: 纯 HTML + JavaScript
- **数据库**: Supabase (PostgreSQL)
- **部署**: Cloudflare Pages
- **特点**: 完全免费,全球CDN加速

