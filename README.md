# green-apple2026 —— 个人概念学习仓库

「大数据与人工智能」课程作业 1：用 AI 构建个人概念学习资料生成 Skill。

本仓库包含一个可复用的项目级 Skill（concept-tutor）和由它生成、经本人核查的三份概念学习资料，后续课程学习中可持续添加新概念的学习资料。

## 📁 仓库结构

```
green-apple2026/
├── .workbuddy/
│   └── skills/
│       └── concept-tutor/
│           └── SKILL.md              ← 项目级 Skill：概念学习资料生成器
├── learning-materials/
│   ├── agent.html                    ← 概念一：Agent（智能体）
│   ├── llm-context.html              ← 概念二：大模型的上下文
│   ├── skill.html                    ← 概念三：Skill（技能）
│   └── concept-relationship.html     ← 三者关系说明（含关系图与 Mermaid）
├── README.md                         ← 本文件
└── .gitignore
```

## 🧰 Skill 说明

**存放路径：** `.workbuddy/skills/concept-tutor/SKILL.md`（项目级 Skill，随仓库版本管理）

**它能做什么：** 输入任意一个技术概念，按固定结构生成一份单文件 HTML 学习资料，包含九个小节——学习目标、核心问题、个人化解释（比喻重述）、核心机制、应用场景、概念辨析、自测问题、可核查的参考来源、人工核查记录。它对任何新概念通用，不是只服务本次三个概念的一次性提示词。

**在 WorkBuddy 中调用方式：**

1. 在 WorkBuddy 中打开本仓库（作为工作区）
2. 在对话框输入，例如：

   > 请使用项目级 Skill `concept-tutor`，学习概念「RAG」。

3. WorkBuddy 会自动加载该 Skill 并按其流程生成 `learning-materials/rag.html`
4. 打开生成的 HTML 逐节核查，填写文末"人工核查记录"，确认无误后提交

**设计要点：** 参考来源只允许真实可访问链接（官方文档优先），解释必须个人化重述而非照搬 AI 回答，生成后附自检清单——这些都写进了 SKILL.md 的约束里。

## 📚 已生成的学习资料

| 文件 | 概念 | 一句话概括 |
|---|---|---|
| `learning-materials/agent.html` | Agent | 在循环中根据反馈自主使用工具的 LLM 系统，与预定义流程的 Workflow 相对 |
| `learning-materials/llm-context.html` | 大模型的上下文 | 模型每次回答能"看见"的全部信息，是边际收益递减的有限资源 |
| `learning-materials/skill.html` | Skill | 指令+脚本+资源组成的文件夹，把做事经验沉淀为按需加载的可复用资产 |
| `learning-materials/concept-relationship.html` | 三者关系 | Agent 是"人"，上下文是"工作记忆"，Skill 是"经验手册" |

所有 HTML 均为单文件、零外部依赖（图示为内联 SVG），双击即可在浏览器打开。

## ✍️ 人工核查与修改说明（AI 使用规范）

学习资料由 concept-tutor Skill（AI）生成初稿，以下为本人完成的人工工作：

1. **来源核查**：生成过程中逐个访问了全部参考链接，确认真实存在且内容确实支撑文中论断。其中 OpenAI 文档站因网络原因无法核实，已从参考来源中移除，替换为可验证的 Anthropic 官方来源与 WorkBuddy 官方文档。
2. **内容修改**：三份资料的"个人理解"部分基于我自己的理解重新组织（实习生/工作台/培训手册的比喻是我选定并核对的）；结合本课程作业的真实经历（建仓、克隆、推送）改写了应用场景，使其来自亲身体验而非虚构。
3. **概念关系**：concept-relationship.html 第五节"总结判断"为个人观点，文中已明确标注。
4. **自测题**：均未附带答案，留待复习时自检。

## 🛡️ 安全说明

- 仓库不含任何 API Key、密码、Token 或个人隐私信息
- `.gitignore` 排除了常见敏感文件与环境目录（`.env*`、`*.pem`、`.venv/` 等）
- Skill 未引入任何第三方可执行脚本，全部内容为本人在 WorkBuddy 中协作编写

## 🧗 遇到的问题与解决记录

**问题：** `git push` 到 GitHub 时多次报错 `Failed to connect to github.com port 443`（连接超时/重置），本地提交无法推送。

**诊断：** `git ls-remote` 与 `curl` 测试确认是本机到 github.com（443 端口）的网络连接持续不可达，属于网络层面问题，与凭据或仓库配置无关。

**解决：** 排查中发现 api.github.com（GitHub REST API 通道）始终可访问，于是改用"Fine-grained 个人访问令牌 + REST API（create tree / create commit / update ref）"的方式，把本地提交的文件内容按同样结构提交到远程 main 分支，绕过了被阻断的 github.com 443 通道，推送成功。本地提交历史完整，无数据丢失。

## 📮 提交信息

- 姓名：（在学习通提交框中填写）
- GitHub 仓库：https://github.com/star-mqp/green-apple2026
