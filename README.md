# OpenSiC Brain

`opensic-brain` 是 OpenSiC 项目的数字大脑仓库，用于沉淀愿景、约束、设计决策与执行文档。  
它不是代码仓库，而是 OpenSiC 相关工作的文档中枢与协作上下文中心。

## 项目定位

- **服务对象**：项目负责人与 AI agent 协同工作。
- **核心目标**：把零散思路持续收敛成可执行文档，降低交接与多 agent 并行协作成本。
- **规范性事实**：`Releases/` 说明项目“应该是什么”，默认可照着执行。
- **当前状态**：`.records/CURRENT.md` 说明项目“实际上进行到哪里”，按需链接历史 Record。

如果你是新接手的 agent，请先阅读 `AGENTS.md`，并按 `.skills/brain-handoff/SKILL.md` 建立项目上下文。

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

> 当前协议 2.4.1 使用正式稳定 Release 作为更新边界。普通具体任务在建立足够上下文后直接继续；正式接手按 `brain-handoff` 执行。版本提示优先使用可忽略的原生选项，用户明确同意后直接完成标准稳定升级。检查和升级不自动执行 Git 交付，也不对关联代码仓库执行 Git 写操作。

## 模板协议

本 brain 已接入 `brain-template` 稳定协议 `2.4.1`，来源为 Release `v2.4.1`，精确 SHA 为 `5e90be98803ab030745af620dd7a14e9baff0f44`；当前版本与托管文件清单见 `.brain-template.json`。需要同步模板机制时，按 `.skills/template-upgrader/SKILL.md` 执行；升级只补齐流程协议，不覆盖 OpenSiC 项目事实与定稿文档。

## 半自动协议更新

agent 会在每次正常项目任务完成并验收后，对固定权威来源 `github.com/AaronJiTuo/brain-template` 的正式稳定 Releases 做一次轻量只读检查；按 SemVer 选择最高版本，核验 tag、精确 SHA 和 manifest，`v2.3.1` 及以后还须是不可变 Release：

- 本地已是最新版：不提示。
- 网络不可用、超时或无法可靠判断：不提示，不影响原任务。
- 发现更高的有效稳定版本：先交付原任务结果，再优先用可忽略的原生选项说明当前版本、目标版本和更新收益；没有合适工具时保留简短文字入口。
- 用户忽略或没有明确同意：不升级、不写入忽略状态。
- 用户明确同意：按 `.skills/template-upgrader/SKILL.md` 从该 Release tag 的同一个精确 SHA 执行非破坏升级，先说明范围后直接完成，不重复请求同一升级的确认。
- `main` 上未正式发布的开发快照不参与稳定更新检查；最高候选核验失败时不回退到较低版本或开发分支。

版本检查本身不创建 Record、不修改 `.records/CURRENT.md`、不执行 Git 写操作。

## 命名与品牌约定（简版）

- 项目名称：`OpenSiC`（源于“碳化硅”，化学式 SiC）。
- 主要域名：`opensic.ai`，`opensic.cn` 作为中国区预留。
- 标识倾向：钻石语义，文本场景可用 `💎` 作为轻量识别符号。

## 如何让 agent 开始

若这是尚未初始化、`Releases/` 还没有项目内容的新 brain：

```text
请先读 AGENTS.md。若这是尚未初始化的新 brain，请按 .skills/brain-initializer/SKILL.md 开始；先通过对话了解项目，等我确认后再落盘。
```

让新 agent 接手已有 brain（本仓库已有 `Releases/00_项目总览.md`）：

```text
请先读 `AGENTS.md`，并按 `.skills/brain-handoff/SKILL.md` 接手当前项目。先读 `Releases/00_项目总览.md` 和 `.records/CURRENT.md`，只按需读取少量相关 Record，不要全文扫描历史。如果我同时给出了具体任务且不存在会实质改变执行结果的歧义，请简要报告理解后直接继续，不要等待重复确认。任务：<你的任务>
```

即使工具会自动读取 `AGENTS.md`，显式要求先读它，仍有助于不同工具从同一套规则开始。
