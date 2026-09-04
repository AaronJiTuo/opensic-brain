# OpenSiC Brain

`opensic-brain` 是 OpenSiC 项目的数字大脑仓库，用于沉淀愿景、约束、设计决策与执行文档。  
它不是代码仓库，而是 OpenSiC 相关工作的文档中枢与协作上下文中心。

## 项目定位

- **服务对象**：项目负责人与 AI agent 协同工作。
- **核心目标**：把零散思路持续收敛成可执行文档，降低交接与多 agent 并行协作成本。
- **规范性事实**：`Releases/` 说明项目“应该是什么”，默认可照着执行。
- **当前状态**：`.records/CURRENT.md` 说明项目“实际上进行到哪里”，按需链接历史 Record。

如果你是新接手的 agent，请先阅读 `AGENTS.md`，再阅读 `Releases/00_项目总览.md` 和 `.records/CURRENT.md`。

## 目录结构

```text
opensic-brain/
├── README.md
├── AGENTS.md
├── .brain-template.json # 模板协议版本与托管文件清单
├── .skills/             # 项目内流程技能，按需由 AGENTS.md 显式触发
├── .records/            # 当前状态入口与重要历史事件
├── Releases/            # 规范性事实：定稿文档
├── Drafts/              # 当前工作台：草稿、成果与上下文素材
└── Archive/             # 低频历史归档
```

- `Drafts/00_灵感索引.md` 是从历史 Draft 摘出的轻量灵感入口。
- `Drafts/` 根目录只作临时收件箱；同主题达到 3 个文件时归组，程序从第 1 个文件起使用独立目录。
- `.records/events/` 保存追加式历史证据，只按任务需要检索，不全文扫描。

## 工作流

1. 纯探索讨论默认留在对话中；用户明确要求不记录时，不写 Draft、Record 或 CURRENT。
2. 已形成、若不落盘就会丢失的实质成果，按 `.skills/checkpoint-recorder/SKILL.md` 判断并保存到 `Drafts/`。
3. 在 `Drafts/` 中创建、续写、移动或整理文件时，按 `.skills/draft-organizer/SKILL.md` 选择路径并归组。
4. 从 AI 聊天页面或分享链接完整抓取对话时，依次执行 `.skills/chat-capture/SKILL.md` 与 `.skills/draft-organizer/SKILL.md`。
5. 重要决策、成果、发现、里程碑或状态变化形成后，创建结果级 Record 并更新 `.records/CURRENT.md`。
6. 草稿成熟到可执行后升级为 `Releases/`；从 Draft 或 Record 生成 Release 时，按 `.skills/release-organizer/SKILL.md` 处理来源、证据、灵感索引与 Draft 去留。
7. 被替代、完成使命或过时的内容迁移到 `Archive/`；历史 Record 不移动、不删除、不回写。

> 协议 2.1.0 在留痕与成果保全之外，增加正常任务结束时的静默版本检查：没有新版或检查失败时不提示，只有发现新版才询问用户，并在用户明确同意后升级。检查和升级都不会自动执行 `git add`、`commit`、`pull`、`push`，也不会对关联代码仓库执行任何 Git 写操作。

## 模板协议

本 brain 已接入 `brain-template` 协议，当前版本见 `.brain-template.json`。未来如果需要同步模板机制，请按 `.skills/template-upgrader/SKILL.md` 执行；升级只能补齐流程协议，不能覆盖 OpenSiC 项目事实与定稿文档。

## 半自动协议更新

升级到 2.1.0 后，agent 会在每次正常项目任务完成并验收后，对固定权威来源 `github.com/AaronJiTuo/brain-template` 做一次轻量只读检查：

- 本地已是最新版：不提示。
- 网络不可用、超时或无法可靠判断：不提示，不影响原任务。
- 发现更高版本：在原任务结果末尾说明当前版本、最新版本和更新摘要，询问是否升级。
- 用户忽略或没有明确同意：不升级、不写入忽略状态。
- 用户明确同意：下一轮按 `.skills/template-upgrader/SKILL.md` 从同一个远端 commit 快照执行非破坏升级。

版本检查本身不创建 Record、不修改 `.records/CURRENT.md`、不执行 Git 写操作。

## 命名与品牌约定（简版）

- 项目名称：`OpenSiC`（源于“碳化硅”，化学式 SiC）。
- 主要域名：`opensic.ai`，`opensic.cn` 作为中国区预留。
- 标识倾向：钻石语义，文本场景可用 `💎` 作为轻量识别符号。

## 模板协议

本 brain 已接入 `brain-template` 协议，当前版本见 `.brain-template.json`（稳定版 `2.4.0`，来源 Release `v2.4.0` / `133b6c781efe39f1d3bba5ec8af6f16d6d5b2543`）。  
需要同步模板机制时，按 `.skills/template-upgrader/SKILL.md` 执行；升级只补齐流程协议，不覆盖 OpenSiC 项目事实与定稿文档。

正常任务结束后，agent 会对权威来源 `github.com/AaronJiTuo/brain-template` 的正式稳定 Release 做轻量只读检查；无新版或检查失败时不提示，发现更高版本时询问是否升级。用户明确同意后直接完成标准稳定升级，不再二次确认。

## 如何让 agent 开始

若这是尚未初始化、`Releases/` 还没有项目内容的新 brain：

```text
请先读 AGENTS.md。若这是尚未初始化的新 brain，请按 .skills/brain-initializer/SKILL.md 开始；先通过对话了解项目，等我确认后再落盘。
```

让新 agent 接手已有 brain（本仓库已有 `Releases/00_项目总览.md`）：

```text
请先读 AGENTS.md，并按 .skills/brain-handoff/SKILL.md 接手当前项目。如果我同时给出了具体任务且不存在会实质改变执行结果的歧义，请在简要报告理解后直接继续，不要等待重复确认。
```

即使工具会自动读取 `AGENTS.md`，显式要求先读它，仍有助于不同工具从同一套规则开始。
