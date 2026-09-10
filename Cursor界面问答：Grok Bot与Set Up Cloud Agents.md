# Cursor 界面问答：这两个按键是干什么的

对话时间：2026-09-09  
对话标题：Nuwa skill 部署  
模型：Cursor Grok 4.6 High Fast  
界面：cursor.com/agents 网页里的 Cloud Agent 对话

---

## 问题（原文）

这两个按键是干什么的  
什么是 grokbot 什么是 set up cloud agents。  
我不是已经在 nuwaskill 里面有了 agent 了吗。

截图里红框标出的两个按键：

1. 左下角：**Try Grok Bot**
2. 输入框上方：**Set Up Cloud Agents**  
   悬停后弹出卡片标题是 **Give Agents a Computer**，说明文字是：Cloud agents ship better code and run faster when you set up their development environment.

---

## 答复（摘要）

这两个按键都不是“再给你开一个 NuwaSkill 的 agent”。

- **Try Grok Bot**：去试用另一个产品 **Grok Bot**（独立桌面/手机 App 里的长期 AI 同事）。
- **Set Up Cloud Agents**：给 Cloud Agent 配置开发环境（依赖、启动命令、快照），不是创建 agent。
- 你现在这条 **Nuwa skill 部署** 对话，本身就已经是 Cloud Agent。仓库里的 Nuwa skill 是给 agent 用的技能包，不是 agent 本体。

当前这次运行还没有绑定可复用的 Cloud Agent 环境（没有 `.cursor/environment.json`，也没有预构建 Build），所以页面会一直推环境配置。不点也可以继续用。

---

## 1. 左下角「Try Grok Bot」是干什么的

这是一个试用/跳转按钮，把你带到 Cursor 的另一个产品：**Grok Bot**。

点它不会：

- 换掉你现在这条 Cloud Agent 对话
- 改变右下角已经选中的模型「Cursor Grok 4.6 High Fast」
- 在 NuwaSkill-Yao 仓库里再装一个 skill

它只是邀请你去用 Grok Bot 那个独立 App。

### 什么是 Grok Bot

Grok Bot 是 Cursor 做的「长期 AI 同事」产品，不是 x.com / grok.com 网页聊天，也不是 Telegram/Discord 机器人。

官方定义的要点：

- 你给 Bot 起名字、定岗位，像给同事派活一样发消息
- 每个账号有一台**长期存在**的云电脑（浏览器、文件系统、终端）
- 你的多个 Bot **共用这一台电脑**，登录态、文件会留下来
- 工作在云端跑，合上笔记本也不会停
- 入口是 **macOS / Windows 桌面 App** 和 **iPhone App**，没有 Linux 桌面版
- 用**同一个 Cursor 账号**登录；付费个人计划、Cursor Teams，或关联 SuperGrok，都可以用

典型用途更像：查 CRM、写邮件草稿、报销、跨网站调研、按日程跑例行工作。  
不是「克隆这个 GitHub 仓库、改代码、开 PR」——那是你现在用的 Cloud Agent。

官方说明：<https://cursor.com/docs/grok-bot>

### 和右下角「Cursor Grok 4.6 High Fast」不是一回事

| 名字 | 实际是什么 |
| --- | --- |
| **Cursor Grok 4.6 High Fast** | 驱动**这条 Cloud Agent 对话**的模型 |
| **Grok Bot** | 另一个产品：独立 App 里的长期 Bot |
| **Grok（grok.com / x.com）** | xAI 自己的聊天产品，不是这个按钮 |

名字里都有 Grok，所以容易混。你现在已经在用 Grok **模型**，不等于已经在用 Grok **Bot**。

---

## 2. 「Set Up Cloud Agents」是干什么的

这是 **Cloud Agent 开发环境配置** 的入口，不是「你还没有 agent，点一下才有」。

悬停卡片标题 **Give Agents a Computer**，对应官方文档里这句话：

> Not setting up a development environment for your cloud agents is like not giving your engineers a computer.

翻译过来：agent 已经有一台远程电脑了；如果你不把依赖、测试、启动命令配好，这台电脑就像一台空机，写得出代码但跑不了项目。

官方说明：<https://cursor.com/docs/cloud-agent/setup>

### 它实际会配置什么

点进去（或点卡片上的 Get started）通常会去 Cloud Agents 的环境设置，用来准备：

- 克隆哪些仓库
- `install`：装依赖、生成代码等可提前做好的事
- `start` / `terminals`：每次开机要起来的服务
- 密钥、网络策略
- **Builds / 快照**：后台先装好，下次 agent 启动更快

配置可以写在仓库的 `.cursor/environment.json`，也可以存在 Cursor 仪表盘里的个人/团队环境。

### 和「已经有一个 agent」的关系

| | 你现在这条对话 | Set Up Cloud Agents |
| --- | --- | --- |
| 是什么 | 一次已经在跑的 Cloud Agent | 给这类 agent 用的**环境配方** |
| 有没有电脑 | 有。一次运行一台隔离的 Ubuntu 云主机 | 把这台主机变成「能装依赖、能跑测试」的开发机 |
| 绑仓库 | 已经绑了 `NuwaSkill-Yao` | 给这个仓库（或一组仓库）存一份可复用环境 |
| 必点吗 | 已经在用了 | 不必。想让以后启动更快、测试更稳再配 |

本次运行查到的状态：

- 仓库：`github.com/36613453226Wallen/NuwaSkill-Yao`
- 已链接环境：无
- 预构建 Build：无

也就是说：agent 已经在一台临时云主机上干活；只是还没有给这个仓库保存一份可复用的环境。横幅因此会反复出现。

---

## 3. 「我不是已经在 NuwaSkill 里面有了 agent 了吗」

对，你已经有了。需要把三个「agent」拆开：

### A. 这条网页对话 = Cloud Agent（你已经在用）

打开的是 [cursor.com/agents](https://cursor.com/agents) 上的 **Nuwa skill 部署**。  
这就是 Cloud Agent：远程虚拟机、克隆仓库、改文件、提交、开 PR。  
对话地址：<https://cursor.com/agents/bc-f87eb191-b34a-4674-bf38-23bd5cf02cd3>

### B. 仓库里的 Nuwa skill ≠ agent 本体

`skills/` 下的女娲 / 姚勇 perspective，是**技能说明书**（怎么调研、怎么蒸馏、边界是什么）。  
Cloud Agent 读这些文件来按你的方法干活。  
Skill 不会自己变成左下角那个 Grok Bot，也不会替代环境配置。

### C. Grok Bot 里的 Bot = 另一种 agent

那是长期存在的「同事」：自己的电脑、插件、日程、记忆。  
和这次 NuwaSkill 代码任务不是同一个东西。Grok Bot 有时可以把写代码的活转交给 Cloud Agent，那是可选委派，不是你现在这条对话。

一句话：

> 你已经有 Cloud Agent。仓库里有 skill。页面还在推销两件别的事：另一个产品（Grok Bot），以及给这台云主机配开发环境（Set Up Cloud Agents）。

---

## 4. 现在要不要点这两个键

**做 NuwaSkill 仓库这件事：两个都不必点。**

- **Try Grok Bot**：只有当你想用独立 App 养一个长期 Bot（邮件、CRM、例行网页操作）时才需要。
- **Set Up Cloud Agents**：只有当你发现 agent 装不了依赖、跑不了测试、启动太慢，或希望以后每次开机都自带工具链时才需要。这份仓库目前主要是文档和 skill，不是必须本地编译的大应用，不配环境也可以继续收录文章、改目录、提交 PR。

如果以后要配环境，从这里进比误点对话里的广告更清楚：

<https://cursor.com/dashboard/cloud-agents>

在 agent 页面把鼠标放到顶部的仓库名上，可以看到这一次用了哪套环境 / Build。

---

## 5. 对照表

| | 这条 Cloud Agent 对话 | Grok Bot | Set Up Cloud Agents |
| --- | --- | --- | --- |
| 产品 | Cursor Cloud Agents | Cursor Grok Bot | Cloud Agent 的环境配置 |
| 入口 | cursor.com/agents、桌面 Cloud、Slack、GitHub `@cursor` | macOS/Windows/iOS App | 仪表盘 Environments，或 `.cursor/environment.json` |
| 电脑 | 每次运行一台隔离 Ubuntu 机，用完随运行结束 | 每个用户一台长期云电脑，Bot 共用 | 给 Cloud Agent 那台机预装工具和依赖 |
| 典型工作 | 改 NuwaSkill-Yao、OCR、写文档、开 PR | 跨 App 办事、例行任务、登录网站操作 | `pnpm install`、起服务、密钥、快照 |
| 和 Grok 4.6 的关系 | 这是当前选用的**模型** | 另一个产品 | 无关 |
| 当前任务需要吗 | 已经在用 | 不需要 | 不需要 |

---

## 6. 参考链接

- Cloud Agents：<https://cursor.com/docs/cloud-agent>
- 环境配置（Give Agents a Computer 对应的说明）：<https://cursor.com/docs/cloud-agent/setup>
- Grok Bot：<https://cursor.com/docs/grok-bot>
- Grok Bot 入门：<https://cursor.com/docs/grok-bot/get-started>
- 模型 Grok 4.6：<https://cursor.com/docs/models/grok-4-6>
- 当前这次 Cloud Agent：<https://cursor.com/agents/bc-f87eb191-b34a-4674-bf38-23bd5cf02cd3>
