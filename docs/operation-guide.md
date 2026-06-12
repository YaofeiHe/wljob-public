# wljob 整体操作指南

目标类型：`project`

## 定位

`wljob` 是由 Nexus 管理或初始化的项目，应拥有可运行代码、git 基线、GitHub private 默认同步和整体操作指南。

## 项目意图说明

- 原始意图需求固定存放于 `docs/intent/original-requirement.md`。
- 完整规范化需求主文档固定存放于 `docs/intent/normalized-requirement.md`。
- 项目说明文档固定存放于 `docs/project-overview.md`。
- 整体操作指南固定存放于 `docs/operation-guide.md`。
- 机器可读索引固定存放于 `.nexus/project-intent.json`。

### 原始意图摘录

# wljob 原始意图需求

- 记录时间：`2026-06-08T17:44:42.404151+00:00`
- 来源 run：`<NEXUS_RUN_ID>`
- 外部意图来源：`<LOCAL_PATH_REDACTED>`

## 原始输入

从零新建一个名为 wljob 的项目。参考文件 <LOCAL_PATH_REDACTED> 已读取，当前需求以 wljob 为准而不是 wlzuu 脚手架复制。项目用于中文互联网求职、网申流程、岗位信息整理、自动化执行前的安全规划和项目记录管理。核心目标：构建可审计的本地 workflow/tool，由 Codex 或宿主模型负责意图理解、路线选择、计划生成和风险审查，本地代码负责受控执行、状态记录、artifact 输出、岗位信息整理和审批门禁。默认画像：后端工程、工程型算法、数据分析、AI 大模型工程化应用；关注智能体平台、开发者 AI、AI Infra、数据与评测、智能驾驶相关岗位；输出先中文摘要再结构化 JSON/表格/岗位卡片。必备能力：意图 intake、路线选择、受控搜索/来源规划、岗位卡片标准化、解释性评分排序、proposal/confirmation card、state/job_cards/proposals/approval_required/audit/interaction/blocked 等 artifact、可扩展 adapter。硬安全边界：不读 cookie/token/browser profile/SSH key/.env/密码文件，不绕过 CAPTCHA/403/WAF/登录墙/风控，不自动输入账号密码，不自动提交网申，不自动发送消息或联系招聘方；登录和身份校验只能用户手动完成；简历上传、附件上传、最终投递点击、发送沟通内容、外部写入、发布、安装依赖、真实浏览器访问、外部 LLM 调用等动作必须单独审批；遇到登录、验证码、风控、异常跳转、敏感页面或凭据请求必须停止并写 blocked/approval artifact。MVP 优先验证本地可审计 workflow 行为：解析求职请求、生成受控来源计划、整理已批准本地或只读来源数据为岗位卡片、生成下一步 proposal 和审批卡、记录状态审计交互 artifact、无真实 provider/无批准来源/请求不安全/触发风控时输出 blocked，不使用 mock 或编造结果。该项目作为 Nexus/Verix 端到端测试样例，需验证初始化意图理解、真实可复用调研、实现计划安全门禁、Verix 审计、以及飞书/GitHub/浏览器/外部检索/外部提交审批边界。

## 参考意图全文摘录

# wljob 项目意图与测试描述

本文档用于作为 `wljob` 初始化、Nexus 调研和 Verix 审计时的项目意图输入。`wlzuu` 是早期由 skhub 生成的需求脚手架和历史来源；当前测试应以 `wljob` 的具体目标、范围和安全边界为准。

## 背景关系

- `wlzuu`：早期需求探索项目，记录了“构建中文互联网求职辅助 agent”的原始想法和边界要求。
- `wljob`：承接 `wlzuu` 意图的受控实现目标，是当前更具体的 workflow/tool 设计依据，也是 Nexus/Verix 端到端测试的目标项目名。

## 项目目标

`wljob` 目标是构建一个实用、可审计、面向中文互联网求职和网申流程的本地 workflow/tool。Codex 或宿主模型负责意图理解、路线选择、计划生成和风险审查；本地

...（已截断，完整内容见对应意图文档）

### 规范化意图摘录

# wljob 规范化意图需求

- 记录时间：`2026-06-08T17:44:42.404151+00:00`
- 来源 run：`<NEXUS_RUN_ID>`
- 项目路径：`<PROJECT_ROOT>`
- GitHub private 默认同步：`enabled`
- GitHub private 仓库：`<PRIVATE_REPO>`
- GitHub public 仓库：`YaofeiHe/wljob-public`
- 飞书文档同步：`enabled`
- 参考意图来源：`<LOCAL_PATH_REDACTED>`

## 文档职责

- `docs/intent/original-requirement.md`：原始输入归档，只保留用户原文和引用来源。
- `docs/intent/normalized-requirement.md`：完整规范化需求主文档，需求更新时优先更新这里。
- `docs/project-overview.md`：项目说明文档，随代码结构和模块演进更新。
- `docs/operation-guide.md`：操作指南，随 workflow 入口和实际操作方式更新。
- `docs/feishu-records.md`：飞书同步记录流，不承担长期说明职责。

## 规范化目标

`wljob` 应作为一个由 Nexus 初始化和维护的真实项目，服务于中文互联网求职、网申流程、岗位信息整理、自动化执行前的安全规划和项目记录管理。

## 项目命名说明

- 项目当前使用名称 `wljob`，因为用户在初始化输入中已明确指定该项目名。
- 名称校验：用户显式指定的项目 slug，已通过路径安全校验；不适用真实五字母英文词规则。

## 项目范围

- 支持自然语言求职意图 intake、岗位来源规划、岗位信息整理和结构化输出。
- 在任何敏感动作前产出 proposal、审批卡和审计 artifact。
- 将项目文档、项目说明、操作指南和飞书同步记录纳入统一维护。
- 作为 Nexus/Verix 的端到端测试样例，验证真实 provider、审批边界、artifact 和同步链路。

## 默认能力边界

- 保留中文互联网求职、网申和岗位整理场景，不把项目收缩成单一平台脚本。
- 将 GitHub private 默认同步、Feishu 文档同步和记录管理视为基础配套能力。
- 项目说明文档与操作指南应根据代码结构和 workflow 入口持续刷新，不允许长期漂移。

## 硬安全边界

- 不读取 cookie、token、浏览器 profile、SSH key、`.env`、密码文件或其他凭据。
- 不绕过登录、CAPTCHA、403、WAF、平台风控或反爬系统。
- 不自动输入账号密码、不自动提交网申、不自动发送消息给招聘方。
- 简历上传、附件上传、最终投递点击、外部写入、真实浏览器访问和外部 LLM 调用等动作都必须单独审批。
- 遇到登录、验证码、风控或敏感页面时必须 blocked 并输出审计 artifact。

## 默认更新约束

- 需求变更时必须更新 `docs/intent/normalized-requirement.md`，必要时同步修订原始需求引用和文档职责。
- 代码结构、模块职责或 artifact 变化时必须刷新 `docs/project-overview.md`。
- workflow 入口、同步方式或运维步骤变化时必须刷新 `docs/operation-gui

...（已截断，完整内容见对应意图文档）

### 项目说明摘录

# wljob 项目说明

- 更新时间：`2026-06-08T17:44:42.404151+00:00`
- 项目路径：`<PROJECT_ROOT>`
- GitHub private：`<PRIVATE_REPO>` (enabled)
- GitHub public：`YaofeiHe/wljob-public`
- Feishu 长期文档同步：`enabled`

## 项目定位

`wljob` 是由 Nexus 管理的项目，要求同时维护完整需求主文档、项目说明文档、操作指南、飞书记录和受控同步能力。

## 项目命名说明

- 项目当前使用名称 `wljob`，因为用户在初始化输入中已明确指定该项目名。
- 名称校验：用户显式指定的项目 slug，已通过路径安全校验；不适用真实五字母英文词规则。

## 文档体系

- `docs/intent/original-requirement.md`：原始需求归档。
- `docs/intent/normalized-requirement.md`：完整规范化需求主文档。
- `docs/project-overview.md`：项目说明文档。
- `docs/operation-guide.md`：操作指南。
- `docs/feishu-records.md`：飞书同步记录。

## 当前目录结构摘要

- `docs/`
- `.nexus/`
- `.github/`

## 关键运行与同步约束

- 长期文档默认同步到飞书，并复用已有线上文档绑定。
- GitHub private 是默认同步能力；GitHub public 仍需要显式确认。
- 任何超出安全边界的自动化动作都必须先审批。

## Skill 入口

```text
$nexus-workflow 为项目 <PROJECT_ROOT> 生成整体操作指南
$nexus-workflow 同步项目 <PROJECT_ROOT> 的整体操作指南到飞书
$nexus-workflow 将项目 <PROJECT_ROOT> 同步到 GitHub public，确认 public 发布
```

## 初始化与日常更新

- 新项目初始化应创建真实项目目录，并在默认情况下初始化 git。
- GitHub private 同步是默认能力；只有指令显式写“不同步 GitHub”、“跳过 GitHub 同步”、`no-github-sync`，或 CLI 使用 `--no-github-sync` 时才跳过。
- Feishu 是操作指南、说明文档和初始化/更新记录的发布通道；初始化项目时默认写入 `docs/feishu-records.md` 并同步到飞书，只有指令显式写“不同步飞书”、“跳过飞书”、`no-feishu-sync`，或 CLI 使用 `--no-feishu-sync` 时才跳过。
- 激活 `$nexus-workflow` 后，每次对项目内容产生更新，都应默认触发飞书自动同步：优先更新已有线上文档，没有对应绑定时才新建，不能把同一份说明拆成多份重复文件。
- 如果飞书配置不可用，应 blocked 到 setup/doctor，不应假装写入成功；本地记录和本地指南仍需保留为 artifact。
- GitHub public 发布永远需要显式确认，不能跟随 private 自动发布。

## GitHub 同步

private 仓库：`<PRIVATE_REPO>`

public 仓库：`YaofeiHe/wljob-public`

GitHub CLI 未认证或 token 失效时，workflow 使用原生 GitHub CLI 浏览器登录：

```bash
gh auth login --web --clipboard --skip-ssh-key --git-protocol https --hostname github.com
```

用户手动完成邮箱、密码、2FA、CAPTCHA 和授权确认。workflow 不读取本地邮箱、密码、token、cookie、浏览器 profile、SSH key、`.env` 或 2FA/CAPTCHA 内容。

### GitHub 登录与同步经验

- 如果 `gh auth login --web` 在 `https://github.com/login/device/code` 阶段返回 EOF，不要立即让用户重复登录；workflow 应先复查 `gh auth status --hostname github.com`，因为设备授权可能已经成功写入 GitHub CLI 状态。
- 如果登录启动失败包含代理、`127.0.0.1`、`operation not permitted`、`dial tcp` 或 EOF，优先复用 recovery playbook 的 `retry_without_proxy_and_debug_api` 方向：绕开代理并开启 `GH_DEBUG=api` 后再次发起 GitHub CLI 官方 web/device 登录。
- 如果 GitHub 仓库创建失败，先检查是否为同名 private/public 仓库已存在；若 `gh repo view` 可访问，应复用现有仓库、补齐 remote，并重试原 bootstrap/sync，不要默认更换仓库名。
- 如果 `git push` 看似卡住或失败，先收口检查本地 commit、remote、GitHub 仓库可访问性和 `gh auth setup-git --hostname github.com`；确认凭证桥接可用后再重试原 private/public sync。
- GitHub 登录、建仓、凭证桥接、push、public staging/secret scan 任一环节失败时，应先查项目 `.nexus/recovery-playbook.json` 和内置经验；命中经验先按对应方向尝试或发起提权，仍失败才调用高精度恢复模块。
- 如果没有精确命中的经验，高精度恢复模块应读取相关经验库条款和历史操作结果作为参考证据，先判断经验是否与当前情景有关、是否仍有效、是否值得尝试；经验无关时应直接丢弃并自主规划新路线，不能被经验库限制住。

public 发布必须先生成 staging，并通过 secret scan。`.env`、token、key、cookie、apikey、本地运行数据、`.data`、`.codex`、`.agents` 等不能进入 public。

## Feishu 同步

- 本指南的主文件是 `docs/operation-guide.md`。
- 同步到飞书时，应优先把本地 Markdown 文件上传并通过 Drive import task 导入为飞书云文档，以保留 Markdown 标题、列表、代码块等结构。
- Markdown 导入需要 folder_token 作为目标文件夹；仅配置 doc_token 时不能保真导入 `.md`。
- 飞书同步应维护 `.nexus/feishu-documents.json`，按本地 Markdown 路径绑定线上 docx；有效绑定存在时更新同一文档，不重复创建。
- 初始化和日常更新记录统一写入 `docs/feishu-records.md`，不应为每一次记录生成一份独立飞书文档。
- 如果绑定文档已删除、失效或资源不可访问，且 folder_token 可用，workflow 应在同一条同步指令内自动标记旧绑定为 stale、重新导入新文档并更新绑定。
- 只有缺凭证、缺 folder_token、缺 API 权限、缺资源权限或网络不可用等真实外部条件时才 blocked；blocked 的下一步提示必须指向真实缺口，并回到原同步指令重试。
- 缺少 `.nexus/feishu.json`、app_id/app_secret、folder_token、`docs:document.media:upload`/Drive 导入上传权限或文件夹资源权限时，应返回明确 blocked reason。
- Feishu 配置和权限问题由 `feishu setup` / `feishu doctor` 处理，不使用 mock 替代。

## 验收边界

- GitHub private/bootstrap/auth/secret scan 已作为基础能力验证；日常变更不重复跑完整 GitHub private E2E。
- Nexus 自身指南同步飞书可以作为本机真实 Feishu 自同步测试。
- Verix 飞书同步、Nexus 初始化新项目后的飞书同步、public 发布由后续 `$` 指令验收。

## 机器可读上下文

```json
{
  "schema": "nexus.operation_guide_context.v1",
  "project": "wljob",
  "target": "project",
  "private_repo": "<PRIVATE_REPO>",
  "public_repo": "YaofeiHe/wljob-public",
  "updated_at": "2026-06-12T08:15:17.203839+00:00"
}
```
