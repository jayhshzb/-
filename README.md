# Toonflow-app

**Toonflow** 是开源一站式 AI 短剧创作工具，将小说、剧本快速转化为动画短剧。

集成 AI 编剧、智能分镜、角色与视频生成，跨平台桌面端轻量部署，助力创作者低成本批量产出视觉内容。

---

## 📊 项目信息

- **Stars**: ⭐ 8,534
- **Forks**: 🔄 1,472
- **License**: Apache 2.0
- **官方网站**: https://toonflow.net
- **原始仓库**: https://github.com/HBAI-Ltd/Toonflow-app

---

## 🌟 主要功能

- ✅ **无限画布生产工作台** - 以类无限画布形式组织剧本、角���、分镜、素材与视频节点
- ✅ **三层 Agent 协作体系** - 决策层、执行层、监督层协同工作
- ✅ **持久化 Agent 记忆** - 基于本地 ONNX 向量检索的跨会话记忆系统
- ✅ **可编程供应商系统** - 支持在设置中心直接编写供应商 TypeScript 逻辑
- ✅ **章节事件图谱驱动改编** - 自动提取原著章节事件
- ✅ **Skill 文件化配置** - 核心提示词外化为 Markdown Skill 文件

---

## 🔧 技术栈

| 类别 | 技术 |
|------|------|
| 运行时 | Node.js 23.11.1+ |
| 语言 | TypeScript 5.x |
| 后端框架 | Express 5 |
| 数据库 | SQLite |
| AI 集成 | Vercel AI SDK |
| 桌面客户端 | Electron 40 |
| 容器化 | Docker |

---

## 🚀 快速开始

### 1. 安装依赖

```bash
yarn install
```

### 2. 启动开发环境

**启动后端服务：**
```bash
yarn dev
```

**启动 Electron 桌面客户端：**
```bash
yarn dev:gui
```

### 3. 项目构建

```bash
# 编译 TypeScript
yarn build

# 打包为 Windows 可执行文件
yarn dist:win

# 打包为 Mac 可执行文件
yarn dist:mac

# 打包为 Linux 可执行文件
yarn dist:linux
```

---

## 📂 项目结构

```
📂 src/
├─ 📂 agents/           # AI Agent 模块
├─ 📂 lib/              # 公共库
├─ 📂 middleware/       # 中间件
├─ 📂 routes/           # 路由模块
├─ 📂 socket/           # WebSocket 实时通信
├─ 📂 types/            # TypeScript 类型
└─ 📂 utils/            # 工具函数
📂 data/
├─ 📂 models/           # 本地推理模型（ONNX）
├─ 📂 oss/              # 对象存储
├─ 📂 skills/           # Agent 技能提示词
└─ 📂 web/              # 前端编译产物
📂 scripts/             # 构建与辅助脚本
```

---

## 🔑 默认登录凭证

- **账号**: `admin`
- **密码**: `admin123`

---

## 📝 许可证

Toonflow 基于 Apache-2.0 协议开源发布，并附有补充商业协议。

详见 [LICENSE](./LICENSE) 文件。

---

## 🤝 贡献指南

⚠️ **PR 提交规范**
- ❌ `master` 分支**不接受**任何 PR
- ✅ 请将 PR 提交到 `develop` 分支

---

## 💬 社区

- 📧 邮箱: ltlctools@outlook.com
- 🎮 Discord: https://discord.gg/HEjKmpNpAZ
- 📱 微信交流群: 扫描二维码加入

---

## 📺 学习资源

- **Bilibili 视频教程**: https://www.bilibili.com/video/BV1oXD7BqEqJ
- **官方文档**: 详见原始仓库

---

**本仓库用于学习和个人使用。如有任何问题，请参考原始仓库。**
