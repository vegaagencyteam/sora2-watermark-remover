# 🎬 Sora2 水印去除工具

**基于 AI 的视频水印去除工具**

[![Next.js](https://img.shields.io/badge/Next.js-15-black)](https://nextjs.org/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.7-blue)](https://www.typescriptlang.org/)
[![License](https://img.shields.io/badge/license-MIT-green)](LICENSE)
[![Website](https://img.shields.io/badge/website-sora2watermarkremover.net-orange)](https://sora2watermarkremover.net)

[🌐 在线演示](https://sora2watermarkremover.net) | [📖 文档](https://sora2watermarkremover.net/docs) 

[English](README.md) | 简体中文

</div>

---

## 📋 目录

- [项目简介](#-项目简介)
- [核心功能](#-核心功能)
- [技术栈](#-技术栈)
- [工作原理](#-工作原理)
- [快速开始](#-快速开始)
- [使用指南](#-使用指南)
- [技术实现](#-技术实现)
- [常见问题](#-常见问题)
- [贡献指南](#-贡献指南)
- [开源协议](#-开源协议)

---

## 🌟 项目简介

**Sora2 水印去除工具** 是一款基于先进深度学习技术和计算机视觉模型的 AI 驱动 Web 应用，专为无缝去除 Sora 生成视频中的水印而设计。提供专业级的水印去除效果和直观的用户界面。

### 为什么选择 Sora2 水印去除工具？

- 🎯 **精准去除**：AI 驱动的 "Made with Sora" 水印检测和去除
- 🖱️ **手动控制**：交互式蒙版编辑器，精确选择水印区域
- ⚡ **快速处理**：优化的 ComfyUI 工作流，高效视频处理
- 🎨 **无缝效果**：先进的修复算法确保自然的输出效果
- 🔒 **隐私优先**：所有处理过程安全可靠，数据受保护

---

## ✨ 核心功能

### 主要能力

- **🎭 AI 水印检测**：使用计算机视觉自动检测 Sora 水印
- **✏️ 手动蒙版编辑**：基于 React Konva 的交互式画布水印区域标记
- **🎬 视频处理**：支持 MP4、MOV 等常见视频格式
- **📊 队列管理**：智能任务队列系统处理多个视频
- **💾 云存储**：与 Cloudflare R2 无缝集成进行视频存储
- **🌍 多语言支持**：使用 next-intl 支持 21+ 种语言
- **📱 响应式设计**：完美适配桌面、平板和移动设备

### 高级功能

- **实时预览**：处理前实时蒙版预览
- **批量处理**：队列中处理多个视频
- **积分系统**：灵活的基于积分的定价模型
- **用户仪表板**：跟踪处理历史和管理视频
- **社交分享**：使用自定义 URL 分享处理后的视频
- **API 访问**：面向开发者的 RESTful API（即将推出）

---

## 🛠️ 技术栈

### 前端
- **框架**：[Next.js 15](https://nextjs.org/) with App Router
- **语言**：[TypeScript 5.7](https://www.typescriptlang.org/)
- **UI 组件**：[Radix UI](https://www.radix-ui.com/) + [Tailwind CSS](https://tailwindcss.com/)
- **画布编辑**：[React Konva](https://konvajs.org/docs/react/)
- **状态管理**：React Hooks + Context API
- **国际化**：[next-intl](https://next-intl-docs.vercel.app/)

### 后端
- **数据库**：[PostgreSQL](https://www.postgresql.org/) with [Drizzle ORM](https://orm.drizzle.team/)
- **认证**：[NextAuth.js](https://next-auth.js.org/)
- **支付**：[Stripe](https://stripe.com/) 集成
- **存储**：[Cloudflare R2](https://www.cloudflare.com/products/r2/)
- **AI 处理**：[ComfyUI API](https://github.com/comfyanonymous/ComfyUI)

### 基础设施
- **部署**：[Vercel](https://vercel.com/) / [Cloudflare Pages](https://pages.cloudflare.com/)
- **CDN**：Cloudflare
- **分析**：OpenPanel
- **监控**：内置日志和错误跟踪

---

## 🔬 工作原理

### 处理流程

```
视频上传 → 手动蒙版编辑 → 生成蒙版图像 → 上传到 R2 存储 
→ 提交到 ComfyUI → AI 修复 → 下载结果 → 存储到 R2 → 交付给用户
```

### 技术工作流

1. **视频上传**：用户上传 Sora 视频（支持拖放）
2. **蒙版创建**：交互式画布允许精确标记水印区域
3. **蒙版生成**：将标记区域转换为 PNG 蒙版图像
4. **云上传**：将原始视频和蒙版上传到 Cloudflare R2
5. **ComfyUI 处理**：
   - 将视频和蒙版加载到 ComfyUI 工作流
   - 使用 U-Net 架构应用 AI 修复
   - 逐帧处理，保持上下文一致性
6. **结果交付**：下载处理后的视频并存储到 R2
7. **用户访问**：提供下载链接和预览

---

## 🚀 快速开始

### 前置要求

- Node.js 18+ 和 pnpm
- PostgreSQL 数据库
- Cloudflare R2 账户
- ComfyUI 服务器（用于处理）

### 安装步骤

```bash
# 克隆仓库
git clone https://github.com/yourusername/sora2-watermark-remover.git
cd sora2-watermark-remover

# 安装依赖
pnpm install

# 设置环境变量
cp .env.example .env.development

# 配置环境变量
# - 数据库连接（PostgreSQL）
# - Cloudflare R2 凭证
# - ComfyUI API 端点
# - NextAuth 密钥
# - Stripe 密钥（可选）

# 运行数据库迁移
pnpm db:push

# 启动开发服务器
pnpm dev
```

访问 `http://localhost:3000` 查看应用。

---

## 📖 使用指南

### 终端用户

1. **访问网站**：前往 [sora2watermarkremover.net](https://sora2watermarkremover.net)
2. **上传视频**：点击"上传视频"或拖放您的 Sora 视频
3. **标记水印**：使用交互式编辑器标记水印区域
4. **处理**：点击"去除水印"开始 AI 处理
5. **下载**：几分钟内获取无水印视频

### 开发者

```typescript
// 示例：使用视频水印去除 Hook
import { useVideoWatermarkRemoval } from '@/hooks/useVideoWatermarkRemoval';

function MyComponent() {
  const { status, actions } = useVideoWatermarkRemoval();

  const handleUpload = (file: File) => {
    actions.selectFile(file);
  };

  const handleProcess = async () => {
    await actions.startProcessing();
  };

  return (
    <div>
      <input type="file" onChange={(e) => handleUpload(e.target.files[0])} />
      <button onClick={handleProcess}>去除水印</button>
      {status.state === 'completed' && (
        <video src={status.processedVideoUrl} controls />
      )}
    </div>
  );
}
```

---

## 🧪 技术实现

### ComfyUI 工作流

应用使用复杂的 ComfyUI 工作流：

- 支持横向和纵向视频方向
- 基于视频尺寸应用条件分支
- 使用先进的修复模型实现无缝水印去除
- 逐帧处理，保持时间一致性

### 性能优化

- **队列系统**：智能任务队列防止服务器过载
- **GPU 加速**：ComfyUI 利用 CUDA 进行快速处理
- **CDN 交付**：Cloudflare CDN 实现全球视频交付
- **懒加载**：优化资源加载以获得更好的用户体验
- **数据库索引**：优化查询以实现快速数据检索

---

## ❓ 常见问题

**问：使用这个工具合法吗？**  
答：此工具用于个人、教育和研究目的。商业使用应遵守 OpenAI 的服务条款。

**问：处理需要多长时间？**  
答：15 秒视频通常需要 3-5 分钟，具体取决于队列长度和视频复杂度。

**问：支持哪些视频格式？**  
答：MP4、MOV、MKV、WebM 和大多数常见视频格式。

**问：可以处理 4K 视频吗？**  
答：可以，但处理时间会更长。我们建议使用 1080p 以获得最佳平衡。

**问：我的视频数据安全吗？**  
答：是的，所有视频都经过加密并安全存储在 Cloudflare R2 中。我们不会分享您的数据。

---

## 📄 开源协议

本项目采用 MIT 协议 - 详见 [LICENSE](LICENSE) 文件。

---

## 🙏 致谢

- [ComfyUI](https://github.com/comfyanonymous/ComfyUI) 提供强大的 AI 处理引擎
- [Next.js](https://nextjs.org/) 团队提供出色的框架
- [Vercel](https://vercel.com/) 提供托管和部署
- 本项目的所有贡献者和用户

---

## 📞 联系与支持

- **网站**：[sora2watermarkremover.net](https://sora2watermarkremover.net)
- **邮箱**：support@sora2watermarkremover.net
- **GitHub Issues**：[报告问题](https://github.com/yourusername/sora2-watermark-remover/issues)

---

<div align="center">

**由 Sora2 水印去除工具团队用 ❤️ 制作**

[⬆ 返回顶部](#-sora2-水印去除工具)

</div>
