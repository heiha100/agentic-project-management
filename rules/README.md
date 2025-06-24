# APM 框架 - 可选的 Cursor IDE 规则

这个目录 `rules/`（如果用户选择使用此功能，则旨在镜像为用户项目中的 `.cursor/rules/`）包含可选的 [Cursor IDE 规则](https://docs.cursor.com/context/rules)。这些规则旨在在 Cursor IDE 中使用时，增强代理项目管理 (APM) 框架的稳健性和效率。

**它们的使用完全是可选的，主要惠及在 Cursor 中操作 APM 的用户。** 核心 APM 提示旨在在没有这些规则的情况下也能有效运行。

## 这些规则如何工作

Cursor 规则允许您向 AI 提供持久的、有范围的指令。在此背景下，经理代理在其核心协议的特定点（例如，在 `01_Initiation_Prompt.md` 或 `02_Codebase_Guidance.md` 中）被提示了有条件的“自注”。这些自注建议，*如果*用户启用了 Cursor 规则并且 MA 认为有帮助，它*可以考虑*按其名称请求相关规则（例如，`@rule_name`）。

这种方法确保：
1.  **可选性：** 如果不使用规则或在 Cursor 之外使用，APM 框架不会中断。
2.  **有针对性的帮助：** 规则仅在可能对工作流程的特定、脆弱部分有益时才被调用。
3.  **上下文相关性：** AI（经理代理）使用规则的描述及其当前的​​操作上下文来决定激活规则是否合适。

## 可用规则（支持经理代理）

### 常规启动和规划阶段

*   **`apm_discovery_synthesis_reminder.mdc`**
    *   **规则描述：** “当 MA 收集了大量信息（例如，通过 `codebase_search`、`read_file`）时，此规则会提示它综合发现，确定规划的后续步骤，并在深入生成 `Implementation_Plan.md` 之前明确咨询用户。有助于防止基于不完整综合的过早规划。”
    *   **目的：** 帮助经理代理从信息收集（发现）过渡到结构化规划，确保在提交详细计划之前与用户保持一致。

*   **`apm_plan_format_source.mdc`**
    *   **规则描述：** “提醒 MA `01_Implementation_Plan_Guide.md` 是格式化 `Implementation_Plan.md` 的权威来源。”
    *   **目的：** 确保 MA 在被要求生成或修改实施计划时使用正确的指南，以促进一致性。

*   **`apm_memory_system_format_source.mdc`**
    *   **规则描述：** “提醒 MA `02_Memory_Bank_Guide.md` 是内存库系统设置（单个与多个文件）和初始文件头的权威来源。”
    *   **目的：** 确保 MA 在提议和设置项目的内存库时使用正确的指南，以与项目复杂性保持一致。

### 实施计划完整性

*   **`apm_impl_plan_critical_elements_reminder.mdc`** (新增)
    *   **规则描述：** “实施计划提醒：确保为所有任务定义 1) 明确的代理分配（考虑分配）和 2) 关键操作步骤的'指导说明'。”
    *   **目的：** 强调为每个任务分配代理的必要性，并在 `Implementation_Plan.md` 中直接包含关键的"指导说明"以确保方法的一致性。有助于防止歧义，并确保为后续的代理分配明确定义任务。

### 内存系统完整性

*   **`apm_memory_naming_validation_reminder.mdc`** (新增)
    *   **规则描述：** “提醒：在创建之前，根据实施计划验证所有内存库文件/目录名称。遵守 02_Memory_Bank_Guide.md 中的约定。”
    *   **目的：** 促进严格遵守内存库命名约定，并在创建任何文件或目录*之前*根据 `Implementation_Plan.md` 进行验证。这对于防止内存库中的结构性错误至关重要。

### 任务分配一致性

*   **`apm_task_prompt_plan_guidance_incorporation_reminder.mdc`** (新增)
    *   **规则描述：** “任务分配提示提醒：明确地包含并扩展实施计划操作步骤中的任何'指导说明'。”
    *   **目的：** 确保当经理代理生成详细的`任务分配提示`时，它能正确使用并详细阐述 `Implementation_Plan.md` 中提供的"指导说明"。这在从高级计划到详细任务执行的指令链中保持了一致性。

## 在 Cursor 中使用这些规则

1.  如果您克隆 APM 框架，则此 `rules/` 目录已包含在内。
2.  要使这些规则在您的 Cursor 项目中生效，请将此 `rules/` 目录的内容复制到项目根目录下的 `.cursor/rules/` 目录中。
3.  确保在您的 Cursor 设置中启用了"项目规则"。
