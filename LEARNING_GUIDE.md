# Toonflow 学习指南

欢迎使用 Toonflow！本指南将帮助您快速上手这个 AI 短剧创作工具。

---

## 📚 目录

1. [项目概述](#项目概述)
2. [安装与启动](#安装与启动)
3. [核心概念](#核心概念)
4. [代码结构分析](#代码结构分析)
5. [学习路线](#学习路线)
6. [常见问题](#常见问题)

---

## 项目概述

### 什么是 Toonflow？

Toonflow 是一款开源的 AI 短剧创作工具，可以：

- 📖 将小说/剧本转化为结构化的剧本内容
- 🎨 生成符合风格要求的角色和场景
- 🎬 生成视频内容
- 📝 提供智能分镜功能
- 🤖 使用 AI Agent 进行内容创作

### 应用场景

- 短视频内容创作
- 小说影视化实验
- AI 文学改编工具
- 剧本开发与快速原型
- 视频素材生成

---

## 安装与启动

### 环境要求

- **Node.js**: 23.11.1 或更高
- **Yarn**: 推荐作为包管理器
- **操作系统**: Windows、macOS 或 Linux

### 安装步骤

1. **克隆或下载项目**
   ```bash
   git clone https://github.com/jayhshzb/-.git
   cd -
   ```

2. **安装依赖**
   ```bash
   yarn install
   ```

3. **启动开发环境**

   **方式一：仅启动后端服务**
   ```bash
   yarn dev
   # 访问：http://localhost:10588
   ```

   **方式二：启动完整桌面应用**
   ```bash
   yarn dev:gui
   # 自动打开 Electron 窗口
   ```

4. **首次登录**
   - 账号：`admin`
   - 密码：`admin123`

---

## 核心概念

### 1. 三层 Agent 体系

Toonflow 采用协作式的 AI Agent 设计：

| 层级 | 名称 | 职责 |
|------|------|------|
| 策略层 | ScriptAgent | 剧本生成、故事框架、改编策略 |
| 执行层 | ProductionAgent | 分镜组织、素材管理、视频拼接 |
| 监督层 | QualityAgent | 内容审阅、质量把控、修订反馈 |

### 2. 无限画布工作台

- 类似 Figma 的节点编辑界面
- 自由组织剧本、角色、分镜、素材、视频
- 支持并行工作流，不受线性步骤限制
- 支持自由编排、回溯与并行生产

### 3. Agent 记忆系统

- **短期记忆**: 当前会话的消息
- **长期记忆**: 摘要和总结
- **语义检索**: 基于 ONNX 向量数据库
- **跨会话连续性**: 多轮创作保持上下文

### 4. 可编程供应商系统

- 在设置中心直接编写 TypeScript 逻辑
- 支持多个 AI 模型供应商
- 无需改源码或重启应用即时生效
- 便于私有化和多模型接入

### 5. Skill 文件化配置

- 核心提示词外化为 Markdown 文件
- ScriptAgent 和 ProductionAgent 可在线编辑
- 快速调优和实验不同的创作风格

---

## 代码结构分析

### 项目目录树

```
src/
├── agents/                 # AI Agent 实现
│   ├── scriptAgent/        # 剧本生成 Agent
│   └── productionAgent/    # 制作 Agent
├── routes/                 # API 路由
│   ├── script/             # 剧本相关接口
│   ├── production/         # 制作相关接口
│   ├── project/            # 项目管理
│   ├── setting/            # 系统设置
│   └── task/               # 任务管理
├── lib/                    # 核心库
│   ├── database.ts         # 数据库初始化
│   └── response.ts         # 统一响应格式
├── utils/                  # 工具函数
├── types/                  # TypeScript 类型定义
├── middleware/             # Express 中间件
├── socket/                 # WebSocket 实时通信
├── app.ts                  # 应用入口
├── core.ts                 # 核心初始化
├── env.ts                  # 环境变量处理
├── logger.ts               # 日志系统
└── router.ts               # 自动生成的路由配置

data/
├── skills/                 # Agent 技能提示词（Markdown）
│   ├── script_agent_skill.md
│   └── production_agent_skill.md
├── models/                 # 本地 ONNX 推理模型
├── oss/                    # 对象存储（角色、场景、素材）
├── web/                    # 前端编译产物
└── serve/                  # 生产环境入口
```

### 关键文件说明

| 文件 | 说明 |
|------|------|
| `src/app.ts` | Express 应用主文件，初始化服务器 |
| `src/router.ts` | 自动生成的路由配置（勿手动编辑） |
| `src/core.ts` | 核心初始化逻辑 |
| `src/env.ts` | 环境变量处理 |
| `src/logger.ts` | 日志输出系统 |
| `package.json` | 项目依赖和脚本配置 |
| `tsconfig.json` | TypeScript 编译配置 |
| `Dockerfile` | Docker 容器配置 |

---

## 学习路线

### 🟢 初级：快速上手（1-2 小时）

**目标**: 能够运行项目并创建第一个短剧

1. ✅ 成功安装和启动项目
2. ✅ 使用默认账号登录
3. ✅ 阅读 README.md 了解功能
4. ✅ 创建第一个项目
5. ✅ 生成简单的剧本
6. ✅ 体验分镜和素材生成

**推荐学习资源**:
- 官方 Bilibili 教程：https://www.bilibili.com/video/BV1oXD7BqEqJ
- README.md 的使用指南部分

---

### 🟡 中级：理解架构（3-5 小时）

**目标**: 理解项目的技术架构和核心概念

1. ✅ 阅读项目结构和代码注释
2. ✅ 理解 Agent 体系的三层设计
3. ✅ 学习前后端通信方式（REST API + WebSocket）
4. ✅ 了解数据存储结构（SQLite）
5. ✅ 探索 Skill 文件的作用和修改方法

**推荐操作**:
- 查看 `data/skills/` 目录下的 Markdown 文件
- 修改 ScriptAgent 的提示词并观察结果变化
- 查看浏览器开发者工具（F12）的网络标签页，观察 API 调用

---

### 🔴 高级：二次开发（8+ 小时）

**目标**: 能够对项目进行定制开发

1. ✅ 修改 Agent 提示词（Skill 文件）
2. ✅ 添加新的 API 路由
3. ✅ 集成新的 AI 模型供应商
4. ✅ 自定义前端界面
5. ✅ 部署到生产环境

**推荐学习资源**:
- Express.js 官方文档：https://expressjs.com/
- Vercel AI SDK 文档：https://ai-sdk.dev/
- TypeScript 官方文档：https://www.typescriptlang.org/

---

## 常见问题

### Q1: 启动时出现端口占用错误

**A**: 更改环境变量 PORT 或清除占用该端口的进程：

```bash
# Linux/Mac
lsof -i :10588
kill -9 <PID>

# Windows
netstat -ano | findstr :10588
taskkill /PID <PID> /F
```

### Q2: 如何配置 AI 模型供应商？

**A**: 
1. 启动应用后登录
2. 进入 **设置** → **模型配置**
3. 选择供应商（OpenAI、Anthropic 等）
4. 填入 API 密钥
5. 测试连接后保存

### Q3: 如何修改 Agent 行为？

**A**: Agent 的行为由 `data/skills/` 目录下的 Markdown 文件定义：
- `script_agent_skill.md` - 剧本 Agent 的提示词
- `production_agent_skill.md` - 制作 Agent 的提示词

编辑这些文件后无需重启即可生效。

### Q4: 数据存储在哪里？

**A**:
- **数据库**: `data/db.sqlite`
- **用户生成内容**: `data/oss/` 目录
- **本地模型**: `data/models/`

### Q5: 如何部署到生产环境？

**A**:

```bash
# 构建项目
yarn build

# 方式一：使用 PM2
pm2 start data/serve/app.js --name toonflow

# 方式二：使用 Docker
docker build -t toonflow .
docker run -d -p 10588:10588 -v /data/toonflow:/app/data toonflow

# 方式三：打包为桌面应用
yarn dist:win    # Windows
yarn dist:mac    # macOS
yarn dist:linux  # Linux
```

---

## 📞 获取帮助

- 📧 **邮箱**: ltlctools@outlook.com
- 🎮 **Discord**: https://discord.gg/HEjKmpNpAZ
- 🐛 **Bug 报告**: https://github.com/HBAI-Ltd/Toonflow-app/issues

---

**祝您学习愉快！如有任何问题欢迎反馈。** 🚀
