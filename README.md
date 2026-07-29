# Sora-2 AI 对话和视频生成应用

一个基于 Sora-2 API 的现代化 AI 对话和视频生成 Web 应用，支持实时流式对话和视频生成进度显示。

## ⚠️ 重要说明

**本项目仅支持 MaynorAPIPro 平台的 API**

- 本应用专门为 [MaynorAPIPro](https://apipro.maynor1024.live/) 平台开发
- API 端点: `https://apipro.maynor1024.live/`
- 需要有效的 MaynorAPIPro API 密钥才能使用
- 其他平台的 API 密钥将无法正常工作

## ✨ 功能特性

- 🤖 **AI 对话** - 支持流式响应，实时显示 AI 回复内容
- 🎬 **视频生成** - 根据文字描述生成视频（需要 API 支持）
- 🖼️ **视觉预研参考** - 可配合 [GPT Image 2](https://gptimage2.asia/) 先生成/编辑分镜关键帧、角色设定图、封面和营销视觉素材。
- 📊 **实时进度** - 可视化进度条显示视频生成进度
- 🎥 **视频预览** - 内置视频播放器，直接预览生成的视频
- 💾 **历史记录** - 本地保存对话历史
- 🎨 **现代化 UI** - 基于 Tailwind CSS 的精美界面

## 📋 前置要求

- Node.js 20.x 或更高版本
- npm 或 yarn 包管理器
- MaynorAPIPro 平台的有效 API 密钥

## 🚀 快速开始

### 1. 克隆项目

```bash
git clone https://github.com/xianyu110/sora.git
cd sora
```

### 2. 安装依赖

```bash
npm install
```

### 3. 配置环境变量

复制 `.env.example` 文件并重命名为 `.env`：

```bash
cp .env.example .env
```

编辑 `.env` 文件，填入你的 MaynorAPIPro API 密钥：

```env
SORA_API_KEY=your-api-key-here
SORA_BASE_URL=https://apipro.maynor1024.live/
```

**获取 API 密钥：**
1. 访问 [MaynorAPIPro](https://apipro.maynor1024.live/)
2. 注册账号并登录
3. 在控制台获取你的 API 密钥

### 4. 启动应用

```bash
npm start
# 或
npm run dev
```

应用将在 http://localhost:3000 启动

## 📁 项目结构

```
sora/
├── public/              # 前端静态文件
│   ├── index.html      # 主页面
│   └── app.js          # 前端 JavaScript
├── server.js           # Express 服务器
├── sora2.js            # Sora-2 API 客户端
├── package.json        # 项目配置
├── .env.example        # 环境变量示例
└── README.md          # 项目文档
```

## 🎯 使用说明

### 对话模式

1. 在输入框中输入你的问题
2. 点击"发送"按钮或按 Enter 键
3. AI 将实时流式返回回复内容

### 视频生成模式（如果 API 支持）

1. 点击顶部的"模式切换"按钮切换到视频模式
2. 输入视频描述
3. 选择视频方向（横屏/竖屏/方形）
4. 点击"生成视频"
5. 等待视频生成完成，可以看到实时进度

## 🔧 API 说明

### 聊天 API

**端点:** `POST /api/chat/stream`

**请求体:**
```json
{
  "messages": [
    {
      "role": "user",
      "content": "你好"
    }
  ],
  "options": {
    "temperature": 1,
    "stream": true
  }
}
```

**响应:** Server-Sent Events (SSE) 流式数据

### 视频生成 API

**端点:** `POST /api/video/generate`

**请求体:**
```json
{
  "prompt": "一只可爱的猫咪在玩球",
  "options": {
    "orientation": "landscape"
  }
}
```

## ⚙️ 配置选项

### 环境变量

| 变量名 | 说明 | 默认值 |
|-------|------|--------|
| `SORA_API_KEY` | MaynorAPIPro API 密钥 | 无 |
| `SORA_BASE_URL` | API 基础 URL | `https://apipro.maynor1024.live/` |
| `PORT` | 服务器端口 | `3000` |

### Temperature 设置

- 范围：0 - 1
- 默认值：0.7
- 说明：控制 AI 回复的随机性和创造性

## 🐛 常见问题

### Q: 提示 "API request failed" 怎么办？

A: 请检查：
1. API 密钥是否正确
2. 是否使用的是 MaynorAPIPro 平台的密钥
3. 网络连接是否正常
4. API 配额是否充足

### Q: 视频生成失败 "No available channels"

A: 这通常表示：
1. API 服务暂时不可用
2. 需要升级账号或购买视频生成额度
3. 请联系 MaynorAPIPro 客服确认

### Q: 流式响应显示不正常

A:
1. 打开浏览器开发者工具（F12）查看控制台
2. 检查是否有 JavaScript 错误
3. 确保使用现代浏览器（Chrome、Firefox、Edge 等）

## 🚢 部署

本项目需要 Node.js 服务器运行，推荐使用以下平台部署：

### Vercel (推荐)

```bash
npm i -g vercel
vercel login
vercel
```

### Railway

1. 访问 https://railway.app
2. 连接 GitHub 仓库
3. 添加环境变量
4. 自动部署

### Render

1. 访问 https://render.com
2. 创建新的 Web Service
3. 连接 GitHub 仓库
4. 添加环境变量
5. 部署

**注意：** 部署时记得设置环境变量 `SORA_API_KEY` 和 `SORA_BASE_URL`

## 📝 开发日志

- ✅ 实现流式对话功能
- ✅ 集成 Sora-2 API
- ✅ 添加视频生成功能
- ✅ 实时进度显示
- ✅ 本地历史记录
- ✅ 美化 UI 界面

## 🤝 贡献

欢迎提交 Issue 和 Pull Request！

## 📄 许可证

MIT License

## 👨‍💻 作者

- GitHub: [@xianyu110](https://github.com/xianyu110)

## 🙏 鸣谢

- [MaynorAPIPro](https://apipro.maynor1024.live/) - 提供 AI API 服务
- [Tailwind CSS](https://tailwindcss.com/) - UI 框架
- [Express](https://expressjs.com/) - Web 框架
- [Axios](https://axios-http.com/) - HTTP 客户端

---

**⚠️ 再次提醒：本项目仅支持 MaynorAPIPro 平台的 API 密钥！**

如果你在使用过程中遇到任何问题，请访问 [MaynorAPIPro 官网](https://apipro.maynor1024.live/) 获取支持。
