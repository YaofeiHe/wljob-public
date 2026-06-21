# wljob System Architecture

wljob 系统架构展示：基于项目意图、长期文档和 repo scan 生成，覆盖领域 workflow、schema/index、审批门禁、审计 artifact 与同步边界。

## Nodes
- `intent_source` 意图与需求源: 沉淀 wljob 的原始需求、规范化需求和历史参考边界。
  - details: 读取 docs/intent 与项目概览，明确 wljob 是通用中文互联网求职/网申 workflow kernel，而不是单次求职脚本。
- `intake` 求职意图 Intake: 解析用户的求职方向、公司/岗位/链接输入、地点和偏好约束。
  - details: 输出可审计的 intent artifact，作为后续路线选择和岗位整理的输入。
- `source_planning` 岗位来源规划: 在官网招聘、官方 ATS、招聘平台、用户链接和本地数据之间选择受控路线。
  - details: 只生成来源计划和只读检索边界；没有真实来源或审批时不得编造岗位 URL。
- `job_cards` 岗位卡片与索引: 把已批准来源整理为岗位卡片、状态索引和可比较表格。
  - details: 字段包括公司、岗位、地点、薪资、技能、链接、申请状态、风险提示、证据来源和更新时间。
- `scoring` 解释性评分排序: 结合默认画像与用户偏好，对岗位匹配度做可解释排序。
  - details: 面向后端、工程型算法、数据分析、AI 工程化、AI Infra、数据评测和智能驾驶等方向。
- `proposal_gate` Proposal 与审批门禁: 在真实浏览器、外部写入、附件上传、投递或沟通前生成审批卡。
  - details: 敏感动作必须等待显式确认；审批卡和 decision artifact 进入审计链路。
- `execution_guard` 安全执行边界: 遇到登录、验证码、风控、凭据请求或敏感页面时停止并写 blocked artifact。
  - details: 不读取 cookie/token/browser profile/SSH key/.env/密码，不绕过 CAPTCHA/403/WAF，不自动提交网申或发送消息。
- `artifacts` 状态与审计 Artifacts: 统一记录 state、interaction、proposal、approval、audit 和 blocked 结果。
  - details: 用于恢复回绑、Verix 审计、人工复核和后续前端展示。
- `records_sync` 项目记录与同步: 维护项目说明、操作指南、飞书记录、GitHub private/public 同步边界和记录板。
  - details: 默认 GitHub private 与飞书长期文档同步；public 发布必须先做 secret/private metadata scan 并显式确认。
- `operation_surface` 操作入口与前端展示: 为 wljob 提供 CLI/Codex workflow 入口，并为后续前端实现暴露稳定结构。
  - details: architecture.json、architecture.mmd 和 modules.yaml 可作为系统架构展示、文档同步和前端渲染输入。

## Edges
- `intent_source` -> `intake`: scope
- `intake` -> `source_planning`: route selection
- `source_planning` -> `job_cards`: approved readonly sources
- `job_cards` -> `scoring`: normalize + compare
- `scoring` -> `proposal_gate`: next action proposal
- `proposal_gate` -> `execution_guard`: sensitive action check
- `execution_guard` -> `artifacts`: write audit trail
- `execution_guard` -> `records_sync`: document result
- `artifacts` -> `operation_surface`: renderable state
- `records_sync` -> `operation_surface`: docs + board

## Safety Boundaries
- 不读取 cookie、token、浏览器 profile、SSH key、.env、密码文件或其他凭据。
- 不绕过登录、CAPTCHA、403、WAF、平台风控或反爬系统。
- 外部写入、发布、安装依赖、真实浏览器访问和外部 LLM 调用必须显式审批。
- GitHub public 发布必须先完成 secret/private metadata scan，并需要显式确认。
- 不自动输入账号密码，不自动提交网申，不自动发送消息或联系招聘方。
- 简历上传、附件上传、最终投递点击和发送沟通内容必须单独审批。
- 飞书同步必须使用真实 Open Platform 配置；缺配置或权限时输出 blocked。

## Evidence Sources
- `docs/intent/normalized-requirement.md`
- `docs/intent/original-requirement.md`
- `docs/project-overview.md`
- `docs/operation-guide.md`
- `docs/feishu-records.md`
- `.nexus/project-intent.json`
- `.nexus/board.md`
- `README.md`
- `docs/github-sync-guide.md`
- `.github/nexus-sync.json`
- `docs/system/architecture.md`
- `docs/system/architecture.mmd`
- `docs/system/architecture.json`
- `docs/system/modules.yaml`
