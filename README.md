# Paper Agent 📄🤖

一个基于 [CodeBuddy Agent SDK](https://www.codebuddy.cn) 构建的 **AI 论文助手**，专注于追踪 arXiv 上的前沿研究。

无需写代码，用自然语言提问，AI 自动搜索、整理、总结最新论文。

---

## ✨ 能做什么？

| 功能 | 说明 |
|------|------|
| 🔍 **自动搜索 arXiv** | 输入一句话，AI 自动在 arXiv 上搜索相关论文 |
| 📝 **中文摘要** | 英文论文自动生成中文核心贡献说明 |
| 🏷️ **开源检测** | 自动标注是否有开源代码（附 GitHub 链接） |
| 💬 **多轮对话** | 追问细节、让 AI 深入解释某篇论文 |
| 📚 **历史记录** | 对话自动保存，随时回来继续 |

**专注三大领域：**
- 🤖 **Agent** — LLM Agent、Multi-Agent、工具调用
- 🚗 **智驾** — 端到端自动驾驶、VLM/VLA、BEV 感知
- 🦾 **具身智能** — Embodied AI、机器人学习、操控与导航

---

## 🚀 一分钟快速启动（新手版）

### 第一步：安装 Node.js

> 如果你已经装过 Node.js，可以跳过这一步。

1. 访问 [https://nodejs.org/zh-cn](https://nodejs.org/zh-cn)
2. 下载 **LTS（长期支持版）**，例如 `v20.x` 或更高版本
3. 双击安装包，一路点「下一步」即可
4. 安装完成后，**重新打开** PowerShell 或 CMD，输入：
   ```powershell
   node -v
   npm -v
   ```
   如果显示版本号，说明安装成功 ✅

---

### 第二步：获取 CodeBuddy API Key

Paper Agent 需要调用 CodeBuddy 的 AI 能力，需要先获取 API Key。

1. 打开浏览器，访问 👉 [https://copilot.tencent.com/profile/](https://copilot.tencent.com/profile/)
   > 如果你用的是海外版 CodeBuddy，访问 [https://www.codebuddy.ai/profile/keys](https://www.codebuddy.ai/profile/keys)
2. 登录你的账号（没有账号先注册）
3. 找到 **「API 管理」** 或 **「API Key」** 入口
4. 点击 **「创建 API Key」**
5. **复制生成的 Key**（⚠️ 只显示一次，务必保存好）

---

### 第三步：下载本项目

**方式一：直接下载 ZIP**
1. 在 GitHub 页面点击绿色的 `Code` 按钮
2. 选择 `Download ZIP`
3. 解压到任意文件夹（建议路径不要包含中文）

**方式二：用 Git 克隆**（如果你会用 Git）
```powershell
git clone https://github.com/你的用户名/paper-agent-assistant.git
cd paper-agent-assistant
```

---

### 第四步：配置 API Key

1. 在 `paper-agent-assistant` 文件夹里，找到 `.env.example` 文件
2. **复制一份**，重命名为 `.env`（如果已有 `.env` 直接编辑即可）
3. 用记事本打开 `.env`，填入你的 API Key：

```bash
PORT=3000
CODEBUDDY_API_KEY=你刚才复制的API_Key
CODEBUDDY_INTERNET_ENVIRONMENT=internal
```

> ⚠️ **注意**：`CODEBUDDY_INTERNET_ENVIRONMENT` 必须填 `internal`（中国版）或 `external`（海外版），否则无法连接！

---

### 第五步：安装依赖

在 `paper-agent-assistant` 文件夹里，**按住 Shift 键 + 右键**，选择「在此处打开 PowerShell 窗口」或「在终端中打开」，然后输入：

```powershell
npm install
```

> 💡 **常见问题**：如果提示 `npm 不是内部或外部命令`，说明 Node.js 没装好或没重启终端，请回到第一步重新检查。

等待几分钟，看到类似下面的输出说明安装成功：
```
added 800+ packages in 2m
```

---

### 第六步：启动应用

在同样的终端窗口输入：

```powershell
npm run dev
```

看到以下输出说明启动成功 ✅：

```
  VITE v5.xx.x  ready in xxx ms

  ➜  Local:   http://localhost:5173/
```

同时还会看到后端启动的提示（两个服务都会运行）。

---

### 第七步：开始使用！

1. 打开浏览器，访问 👉 [http://localhost:5173](http://localhost:5173)
2. 在左下角 **选择模型**（推荐 `deepseek-v3-2-volc` 或 `glm-5.1`）
3. 在输入框输入你的问题，例如：
   > `帮我找最近关于 VLA 机器人端到端控制的 arXiv 论文`
4. 等待 AI 搜索并整理结果 🎉

---

## 💬 怎么提问？——示例问题

### 搜索 Agent 领域论文
```
帮我找最近三个月关于 LLM Agent 工具调用的最新论文，
优先看有开源代码的。
```

### 搜索智驾领域论文
```
端到端自动驾驶领域，最近有哪些值得关注的 arXiv 论文？
重点关注 BEV 感知和决策规划方向。
```

### 搜索具身智能论文
```
VLA（Vision-Language-Action）机器人方向有哪些新进展？
帮我整理一个列表，包含论文标题、核心创新和代码链接。
```

### 让 AI 深入解释某篇论文
```
刚才第 3 篇论文看起来很有意思，能详细解释一下
它的方法部分吗？最好用中文。
```

---

## ⚙️ 进阶配置

### 切换模型

在界面左下角可以切换不同模型：

| 模型 | 特点 | 推荐场景 |
|------|------|----------|
| `deepseek-v3-2-volc` | 推理能力强，中文好 | 通用推荐 ✅ |
| `glm-5.1` | 平衡速度和质量 | 日常使用 |
| `glm-5v-turbo` | 支持图片输入 | 需要看论文配图时 |
| `kimi-k2.6` | 超长上下文 | 分析长论文全文 |

### 修改最大对话轮次

默认设置为 50 轮（已足够大多数场景）。如果你需要更多轮次，编辑 `server/index.ts` 第 509 行：

```typescript
maxTurns: 50,  // 改成你想要的数字
```

---

## 🔧 常见问题排查

### ❌ 问题 1：`npm` 命令不识别

**原因**：Node.js 没有正确安装，或安装后没有重启终端。

**解决方法**：
1. 重新安装 Node.js（记得选「Add to PATH」）
2. **关闭并重新打开** PowerShell
3. 输入 `node -v` 验证

---

### ❌ 问题 2：启动后浏览器显示「无法访问此网站」

**原因**：前端服务没有成功启动。

**解决方法**：
1. 检查终端里有没有报错信息
2. 确认 `5173` 端口没有被其他程序占用：
   ```powershell
   netstat -ano | findstr :5173
   ```
3. 如果端口被占用，可以杀掉进程或换个端口（编辑 `vite.config.ts`）

---

### ❌ 问题 3：选了模型但发消息报错「未指定模型」

**原因**：你的账号没有该模型的访问权限。

**解决方法**：
1. 在界面左下角**重新选择一个你有账号权限的模型**
2. 推荐先试 `deepseek-v3-2-volc`，这个模型对大多数用户都可用

---

### ❌ 问题 4：AI 回复「超过最大对话轮次」

**原因**：搜索论文需要多次工具调用，默认 10 轮不够用。

**解决方法**：项目已预设为 50 轮。如果还不够，按上面「进阶配置」修改 `maxTurns` 数值，然后重启服务。

---

### ❌ 问题 5：后端启动报错 `address already in use :::3000`

**原因**：3000 端口被占用了（可能是之前没正常关闭）。

**解决方法**：
```powershell
# 找到占用 3000 端口的进程
netstat -ano | findstr :3000
# 记住最后一列的 PID 数字，然后：
taskkill /PID <数字> /F
```

---

## 📁 项目结构（了解即可，不用改）

```
paper-agent-assistant/
├── server/                # 后端：负责调用 AI、管理对话
│   └── index.ts          # 主服务文件（核心逻辑在这里）
├── src/                   # 前端：你在浏览器里看到的界面
│   ├── components/       # 界面组件（消息气泡、侧边栏等）
│   ├── hooks/            # 数据处理逻辑
│   └── App.tsx          # 主界面入口
├── .env                   # ⚠️ 你的 API Key 配置（不要分享给别人！）
├── package.json           # 项目依赖清单
└── README.md             # 你正在看的这个文件
```

> 💡 **普通用户不用修改任何代码文件**，开箱即用。如果你想深度定制（比如改系统提示词、加新功能），才需要碰 `server/index.ts`。

---

## 🛠️ 开发者命令

| 命令 | 说明 |
|------|------|
| `npm run dev` | 启动开发模式（前端 + 后端同时运行）|
| `npm run build` | 构建生产版本 |
| `npm start` | 运行生产版本 |

---

## 📄 开源协议

Apache License —— 自由使用、修改和分发，记得声明源码原文~ 🎉

---

## ❤️ 致谢

- [CodeBuddy](https://www.codebuddy.cn) — 提供 Agent SDK 和 AI 能力
- [TDesign](https://tdesign.tencent.com/) — UI 组件库
- [arXiv](https://arxiv.org/) — 开放学术论文平台

---

## 💡 还没有跑起来？

遇到问题别着急！你可以：
1. 查看上面「常见问题排查」章节
2. 在 GitHub 提 Issue，描述你的问题和报错信息
3. 联系作者获取帮助

**祝你论文调研顺利！** 🎓
