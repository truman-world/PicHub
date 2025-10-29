<table>
<tr>
<td width="50%" align="center" valign="middle">

<img src="https://github.com/truman-world/PicHub/raw/main/public/images/pichub-logo.png" alt="PicHub Logo" width="400">

# PicHub - 专业的图片托管与管理平台

[在线演示](https://pichub.app) · [问题反馈](https://github.com/truman-world/PicHub/issues)

</td>
<td width="50%" valign="top">

**后端技术**

[![Laravel](https://img.shields.io/badge/Laravel-12.x-FF2D20?logo=laravel&logoColor=white&style=for-the-badge)](https://laravel.com)
[![PHP](https://img.shields.io/badge/PHP-8.2+-777BB4?logo=php&logoColor=white&style=for-the-badge)](https://php.net)
[![MySQL](https://img.shields.io/badge/MySQL-8.0+-4479A1?logo=mysql&logoColor=white&style=for-the-badge)](https://mysql.com)
[![Filament](https://img.shields.io/badge/Filament-3.2-F59E0B?logo=laravel&logoColor=white&style=for-the-badge)](https://filamentphp.com)

**前端技术**

[![Tailwind CSS](https://img.shields.io/badge/Tailwind-3.x-06B6D4?logo=tailwindcss&logoColor=white&style=for-the-badge)](https://tailwindcss.com)
[![Alpine.js](https://img.shields.io/badge/Alpine.js-3.x-8BC0D0?logo=alpinedotjs&logoColor=white&style=for-the-badge)](https://alpinejs.dev)
[![Vite](https://img.shields.io/badge/Vite-6.x-646CFF?logo=vite&logoColor=white&style=for-the-badge)](https://vitejs.dev)
[![Blade](https://img.shields.io/badge/Blade-模板引擎-FF2D20?logo=laravel&logoColor=white&style=for-the-badge)](https://laravel.com/docs/blade)

**存储支持**

[![本地存储](https://img.shields.io/badge/本地存储-支持-10B981?style=for-the-badge)]()
[![阿里云 OSS](https://img.shields.io/badge/阿里云_OSS-支持-FF6A00?logo=alibabacloud&logoColor=white&style=for-the-badge)](https://aliyun.com/product/oss)
[![腾讯云 COS](https://img.shields.io/badge/腾讯云_COS-支持-006EFF?style=for-the-badge)](https://cloud.tencent.com/product/cos)
[![七牛云](https://img.shields.io/badge/七牛云-支持-00C1DE?style=for-the-badge)](https://qiniu.com)

**核心特性**

[![图片处理](https://img.shields.io/badge/图片处理-Intervention_Image-4F46E5?style=for-the-badge)]()
[![相册管理](https://img.shields.io/badge/相册管理-完整支持-10B981?style=for-the-badge)]()
[![多语言](https://img.shields.io/badge/多语言-中英法俄-F59E0B?style=for-the-badge)]()
[![API 接口](https://img.shields.io/badge/API-RESTful-06B6D4?style=for-the-badge)]()

</td>
</tr>
</table>

---

## 核心优势

<table>
<tr>
<td width="25%" align="center">

### 简单易用

直观的界面设计，拖拽上传，批量管理，零学习成本快速上手。

</td>
<td width="25%" align="center">

### 功能完善

相册管理、图片处理、多格式支持、API 接口，满足各类需求。

</td>
<td width="25%" align="center">

### 灵活存储

支持本地存储和多种云存储服务，自由选择最适合的方案。

</td>
<td width="25%" align="center">

### 多语言

内置中英法俄四种语言，支持深色模式，提供更好的用户体验。

</td>
</tr>
</table>

---

## 核心功能

### 图片管理

- ✅ **多格式支持** - JPEG、PNG、WebP、GIF、SVG 等主流图片格式
- ✅ **批量上传** - 支持拖拽上传、粘贴上传、批量上传
- ✅ **图片处理** - 自动压缩、格式转换、尺寸调整、水印添加
- ✅ **智能裁剪** - 按比例裁剪、智能识别主体
- ✅ **懒加载** - 提升页面加载速度

### 相册系统

- ✅ **相册管理** - 创建、编辑、删除相册，支持封面设置
- ✅ **分类整理** - 按标签、日期、相册分类管理图片
- ✅ **批量操作** - 批量移动、复制、删除图片
- ✅ **相册分享** - 生成分享链接，支持密码保护
- ✅ **权限控制** - 公开/私有/仅自己可见

### 存储方案

- ✅ **本地存储** - 适合小规模部署
- ✅ **阿里云 OSS** - 高可用、低成本
- ✅ **腾讯云 COS** - 稳定可靠
- ✅ **七牛云** - 快速便捷
- ✅ **AWS S3** - 全球部署
- ✅ **混合存储** - 支持多存储后端并存

### 用户系统

- ✅ **用户认证** - 注册、登录、找回密码、邮箱验证
- ✅ **权限管理** - 基于角色的访问控制（RBAC）
- ✅ **配额管理** - 灵活的存储空间和流量配额
- ✅ **使用统计** - 详细的上传、浏览、流量统计
- ✅ **API 密钥** - 安全的 API 访问凭证管理

### API 接口

- ✅ **RESTful API** - 完整的图片上传、管理、删除接口
- ✅ **API 文档** - 详细的 API 文档和示例代码
- ✅ **认证方式** - 支持 Token、OAuth 2.0
- ✅ **SDK 支持** - 提供多种语言的 SDK
- ✅ **Webhook** - 事件通知和回调

---

## 快速开始

### 环境要求

- PHP >= 8.2
- Composer
- Node.js >= 18.x
- MySQL >= 8.0 或 PostgreSQL >= 13
- Redis （可选，用于缓存和队列）

### 一键安装

```bash
# 1. 克隆项目
git clone https://github.com/truman-world/pichub.git
cd pichub

# 2. 安装依赖
composer install
npm install

# 3. 配置环境
cp .env.example .env
php artisan key:generate

# 4. 配置数据库（编辑 .env 文件）
# DB_CONNECTION=mysql
# DB_HOST=127.0.0.1
# DB_PORT=3306
# DB_DATABASE=pichub
# DB_USERNAME=root
# DB_PASSWORD=

# 5. 运行迁移
php artisan migrate --seed

# 6. 构建前端资源
npm run build

# 7. 启动服务
php artisan serve
```

访问 `http://localhost:8000` 开始使用！

### Docker 部署

```bash
# 使用 Docker Compose 一键部署
docker-compose up -d

# 运行数据库迁移
docker-compose exec app php artisan migrate --seed
```

访问 `http://localhost` 即可使用。

---

## 功能截图

<table>
<tr>
<td width="50%" align="center">

**响应式首页**

<img src="https://via.placeholder.com/500x300/4F46E5/FFFFFF?text=Homepage" alt="首页" width="100%">

</td>
<td width="50%" align="center">

**图片管理**

<img src="https://via.placeholder.com/500x300/10B981/FFFFFF?text=Gallery" alt="图片管理" width="100%">

</td>
</tr>
<tr>
<td width="50%" align="center">

**相册系统**

<img src="https://via.placeholder.com/500x300/F59E0B/FFFFFF?text=Albums" alt="相册系统" width="100%">

</td>
<td width="50%" align="center">

**暗色模式**

<img src="https://via.placeholder.com/500x300/1F2937/FFFFFF?text=Dark+Mode" alt="暗色模式" width="100%">

</td>
</tr>
</table>

---

## 技术架构

### 核心架构

```
┌─────────────┐
│   用户端    │ (浏览器/API 客户端)
└──────┬──────┘
       │
┌──────▼──────────────────────────────┐
│         Laravel 12 应用层           │
│  ┌──────────┬──────────┬─────────┐ │
│  │ 路由层   │ 控制器   │ 中间件  │ │
│  └──────────┴──────────┴─────────┘ │
│  ┌──────────┬──────────┬─────────┐ │
│  │ 业务逻辑 │ 模型层   │ 服务层  │ │
│  └──────────┴──────────┴─────────┘ │
└──────┬──────────────────────────────┘
       │
┌──────▼──────────────────────────────┐
│          数据存储层                  │
│  ┌──────────┬──────────┬─────────┐ │
│  │  MySQL   │ 本地存储 │ 云存储  │ │
│  │  数据库  │  /img    │ OSS/COS │ │
│  └──────────┴──────────┴─────────┘ │
└─────────────────────────────────────┘
```

### 核心模块

- **用户系统**: 注册登录、权限管理、配额控制
- **图片管理**: 上传处理、格式转换、缩略图生成
- **相册系统**: 相册创建、图片分类、批量操作
- **存储引擎**: 本地存储、阿里云 OSS、腾讯云 COS、七牛云
- **API 服务**: RESTful API、认证授权、接口文档
- **后台管理**: Filament 3.2 管理面板、数据统计、系统配置

---

## 使用文档

### 快速开始

- **安装部署** - 参考上方"快速开始"章节
- **基础使用** - 注册账号后即可开始上传图片
- **相册管理** - 创建相册、整理图片、设置权限
- **API 接口** - 访问 `/api/docs` 查看完整 API 文档

### 配置说明

- **存储配置** - 在后台管理面板配置本地或云存储
- **邮件配置** - 配置 SMTP 服务用于邮件通知
- **系统设置** - 自定义网站名称、Logo、SEO 信息

---

## 多语言支持

PicHub 支持以下语言：

- 🇨🇳 简体中文
- 🇺🇸 English
- 🇫🇷 Français
- 🇷🇺 Русский

更多语言正在添加中...

---

## 贡献指南

我们欢迎所有形式的贡献！

### 如何贡献

1. **Fork 本项目** - 点击右上角的 Fork 按钮
2. **创建特性分支** - `git checkout -b feature/AmazingFeature`
3. **提交更改** - `git commit -m 'Add some AmazingFeature'`
4. **推送到分支** - `git push origin feature/AmazingFeature`
5. **提交 Pull Request** - 打开 PR 并描述您的更改

### 开发规范

在提交代码前，请确保：

- ✅ 遵循 [PSR-12 编码规范](https://www.php-fig.org/psr/psr-12/)
- ✅ 添加必要的单元测试
- ✅ 更新相关文档
- ✅ 代码通过 PHPStan 和 Pint 检查
- ✅ 遵循 [CLAUDE.md](CLAUDE.md) 中的开发规范

### 报告问题

发现 Bug？请 [提交 Issue](https://github.com/truman-world/pichub/issues) 并包含：

- 问题描述
- 复现步骤
- 预期行为
- 实际行为
- 系统环境信息

---

## 项目统计

<p align="center">
  <img src="https://img.shields.io/github/stars/truman-world/pichub?style=social" alt="GitHub stars">
  <img src="https://img.shields.io/github/forks/truman-world/pichub?style=social" alt="GitHub forks">
  <img src="https://img.shields.io/github/watchers/truman-world/pichub?style=social" alt="GitHub watchers">
</p>

<p align="center">
  <img src="https://img.shields.io/github/license/truman-world/pichub" alt="License">
  <img src="https://img.shields.io/github/v/release/truman-world/pichub" alt="Release">
  <img src="https://img.shields.io/github/last-commit/truman-world/pichub" alt="Last Commit">
  <img src="https://img.shields.io/github/issues/truman-world/pichub" alt="Issues">
  <img src="https://img.shields.io/github/issues-pr/truman-world/pichub" alt="Pull Requests">
</p>

---

## 许可证

本项目采用 [MIT 许可证](LICENSE)。

这意味着您可以自由地：

- ✅ 商业使用
- ✅ 修改代码
- ✅ 分发代码
- ✅ 私有使用

---

## 联系我们

<div align="center">

### 官方网站

[https://pichub.app](https://pichub.app)

### 问题反馈

发现 Bug 或有功能建议？欢迎 [提交 Issue](https://github.com/truman-world/PicHub/issues)

### 商务合作

邮箱：contact@pichub.app

</div>

---

## 致谢

感谢以下开源项目和贡献者：

- [Laravel](https://laravel.com) - 优雅的 PHP Web 框架
- [Alpine.js](https://alpinejs.dev) - 轻量级 JavaScript 框架
- [Tailwind CSS](https://tailwindcss.com) - 实用优先的 CSS 框架
- [FilamentPHP](https://filamentphp.com) - 强大的 Laravel 后台面板
- 所有为 PicHub 做出贡献的开发者 ❤️

---

## Star History

[![Star History Chart](https://api.star-history.com/svg?repos=truman-world/pichub&type=Date)](https://star-history.com/#truman-world/pichub&Date)

---

<p align="center">
  <strong>Made with ❤️ by PicHub Team</strong><br>
  <sub>© 2025 PicHub. All rights reserved.</sub>
</p>

<p align="center">
  <a href="https://pichub.app">官网</a> •
  <a href="https://pichub.app/docs">文档</a> •
  <a href="https://demo.pichub.app">演示</a> •
  <a href="https://github.com/truman-world/pichub/issues">问题反馈</a> •
  <a href="https://twitter.com/pichubapp">Twitter</a>
</p>
