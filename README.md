# OpenSiC Brain

`opensic-brain` 是 OpenSiC 项目的数字大脑仓库，用于沉淀愿景、约束、设计决策与执行文档。  
它不是代码仓库，而是 OpenSiC 相关工作的文档中枢与协作上下文中心。

## 项目定位

- **服务对象**：项目负责人与 AI agent 协同工作。
- **核心目标**：把零散思路持续收敛成可执行文档，降低交接与多 agent 并行协作成本。
- **事实来源**：`Releases/` 为唯一事实来源（Single Source of Truth）。

如果你是新接手的 agent，请先阅读 `AGENTS.md`，再阅读 `Releases/00_项目总览.md`。

## 目录结构

```
opensic-brain/
├── README.md
├── AGENTS.md
├── .brain-template.json # 模板协议版本与托管文件清单
├── .skills/           # 项目内流程技能，按需由 AGENTS.md 显式触发
├── Releases/          # 定稿文档（唯一事实来源）
├── Drafts/            # 草稿与上下文素材，含 00_灵感索引.md
└── Archive/           # 历史归档
```

## 工作流

1. 新想法与对话先进入 `Drafts/`。
2. 从 AI 聊天页面或分享链接完整抓取对话时，按 `.skills/chat-capture/SKILL.md` 保存为 Draft。
3. 草稿反复打磨到可执行后，迁移到 `Releases/`；从 Draft 生成 Release 时，按 `.skills/release-organizer/SKILL.md` 处理来源、灵感索引与 Draft 去留。
4. 被替代、完成使命或过时内容迁移到 `Archive/`。

## 模板协议

本 brain 已接入 `brain-template` 协议，当前版本见 `.brain-template.json`。未来如果需要同步模板机制，请按 `.skills/template-upgrader/SKILL.md` 执行；升级只能补齐流程协议，不能覆盖 OpenSiC 项目事实与定稿文档。

## 命名与品牌约定（简版）

- 项目名称：`OpenSiC`（源于“碳化硅”，化学式 SiC）。
- 主要域名：`opensic.ai`，`opensic.cn` 作为中国区预留。
- 标识倾向：钻石语义，文本场景可用 `💎` 作为轻量识别符号。

## agent 启动提示词

可直接使用下面这句作为新任务前置：

```
请先读 `AGENTS.md`，再读 `Releases/`（尤其「当前状态」一节）。读完后，请用几句话复述你对项目的理解，等我确认无误后再开始：<你的任务>
```
