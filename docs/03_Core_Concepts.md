# APM 核心概念和术语词汇表

本文档为代理项目管理 (APM) 框架中使用的关键术语提供了简明的定义。请将其用作快速参考，并导航到链接的文档以获取更详细的解释、指南或格式规范。

---

**代理交接/交接协议**

在 AI 代理实例之间转移项目上下文和责任的已定义程序（例如，从经理到新经理，或在专门代理之间）。它利用 `Handover_File.md` 和 `Handover_Prompt.md` 来确保项目连续性，尤其是在处理 LLM 上下文限制时。
*   *查看程序：* `prompts/01_Manager_Agent_Core_Guides/05_Handover_Protocol_Guide.md`
*   *查看产物格式：* `prompts/02_Utility_Prompts_And_Format_Definitions/Handover_Artifact_Formats.md`
*   *查看实际步骤：* `docs/02_Getting_Started.md` (第 6 步)
*   *查看可视化概述：* `docs/01_Workflow_Overview.md` (交接协议流程)

**APM (代理项目管理)**

整个框架，包括提示、格式定义、协议和最佳实践，旨在利用多个协作的 AI 助手来结构化复杂项目的执行。
*   *查看概述：* `docs/00_Introduction.md`

**核心 APM 周期**

APM 项目中活动的主要迭代循环：经理准备提示 -> 用户交付 -> 执行者执行 -> 执行者报告 -> 用户确认日志 -> 执行者记录日志 -> 用户通知经理 -> 经理审查 -> 重复。
*   *查看可视化概述：* `docs/01_Workflow_Overview.md` (核心 APM 周期)
*   *查看实际步骤：* `docs/02_Getting_Started.md` (第 5 步)

**交接文件 (`Handover_File.md`)**

在交接协议期间创建的结构化 Markdown 文档。它作为一个全面的上下文转储，包含当前项目状态、计划状态、最近的日志、决策以及传入代理所需的其他关键信息。
*   *查看格式定义：* `prompts/02_Utility_Prompts_And_Format_Definitions/Handover_Artifact_Formats.md` (第 2 节)
*   *查看程序上下文：* `prompts/01_Manager_Agent_Core_Guides/05_Handover_Protocol_Guide.md` (第 3.1 节)

**交接提示 (`Handover_Prompt.md`)**

用于在交接期间初始化新代理实例的 Markdown 提示。它包括标准的 APM 入职信息（如果适用）、处理 `Handover_File.md` 的说明，并指定传入代理的直接后续步骤。
*   *查看格式定义：* `prompts/02_Utility_Prompts_And_Format_Definitions/Handover_Artifact_Formats.md` (第 3 节)
*   *查看程序上下文：* `prompts/01_Manager_Agent_Core_Guides/05_Handover_Protocol_Guide.md` (第 3.2 节)

**实施代理**

一个 AI 代理实例，负责根据 `Implementation_Plan.md` 和 `Task Assignment Prompt` 中提供的说明执行特定的、分配的任务。他们在用户确认后向用户报告状态并将其工作记录到 `Memory_Bank.md` 中。
*   *查看入职提示：* `prompts/02_Utility_Prompts_And_Format_Definitions/Implementation_Agent_Onboarding.md`
*   *查看在工作流程中的角色：* `docs/01_Workflow_Overview.md`

**实施计划 (`Implementation_Plan.md`)**

由经理代理创建的详细、结构化的 Markdown 文档（在用户批准结构后）。它将项目分解为阶段（可选）、任务和细分的子任务，并将责任分配给特定的实施代理。它作为项目执行的蓝图。
*   *查看格式指南：* `prompts/01_Manager_Agent_Core_Guides/01_Implementation_Plan_Guide.md`
*   *查看创建过程：* `docs/02_Getting_Started.md` (第 4 步)

**经理代理**

负责整个项目协调的中央 AI 代理实例。其职责包括理解需求、创建实施计划、协助用户处理任务分配提示、审查记录在内存库中的工作以及管理交接协议。
*   *查看启动提示：* `prompts/00_Initial_Manager_Setup/01_Initiation_Prompt.md`
*   *查看核心指南：* `prompts/01_Manager_Agent_Core_Guides/`
*   *查看在工作流程中的角色：* `docs/01_Workflow_Overview.md`

**内存库 (`Memory_Bank.md`)**

一个或多个指定的 Markdown 文件，作为项目的持久、按时间顺序的日志簿。实施和专门代理在用户确认后，以标准化格式在此处记录其操作、输出、结果和问题。它提供了共享的上下文和审计跟踪。
*   *查看系统设置指南：* `prompts/01_Manager_Agent_Core_Guides/02_Memory_Bank_Guide.md`
*   *查看日志条目格式定义：* `prompts/02_Utility_Prompts_And_Format_Definitions/Memory_Bank_Log_Format.md`
*   *查看概念概述：* `docs/01_Workflow_Overview.md` (内存库概念)
*   *查看实践中的设置：* `docs/02_Getting_Started.md` (第 4 步)

**专门代理**

一个 AI 代理实例，被分配执行超出标准实施范围的特定、专门的功能，例如调试代码（`调试器代理`）、解释概念（`导师代理`）或执行详细审查（`审查员代理`）。它们遵循与实施代理类似的交互模式（通过用户分配任务，记录到内存库）。
*   *查看入职提示（共享）：* `prompts/02_Utility_Prompts_And_Format_Definitions/Implementation_Agent_Onboarding.md`

**任务分配提示**

一个通常由经理代理起草并由用户交付的提示，用于将 `Implementation_Plan.md` 中的特定任务分配给实施代理或专门代理。它包括任务目标、详细步骤、必要的上下文、预期的输出和强制性的日志记录说明。
*   *查看制作指南：* `prompts/01_Manager_Agent_Core_Guides/03_Task_Assignment_Prompts_Guide.md`
*   *查看在工作流程中的使用：* `docs/02_Getting_Started.md` (第 5 步)

**用户**

人类项目负责人。用户定义项目目标，作为所有 AI 代理之间至关重要的沟通桥梁，做出关键决策（例如，计划批准、日志记录确认），审查进度并提供总体监督。
*   *查看在工作流程图中的角色：* `docs/01_Workflow_Overview.md` 