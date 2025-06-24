# 更新日志
本项目所有显著的变更都将记录在此文件中。

格式基于 [Keep a Changelog](https://keepachangelog.com/zh-CN/1.0.0/)，
且本项目遵循 [语义化版本](https://semver.org/spec/v2.0.0.html)。

## [0.3.0] - YYYY-MM-DD

### 新增
- 在 `prompts/02_Utility_Prompts_And_Format_Definitions/Handover_Artifact_Format.md` 的 `Handover_File.md` 中为"最近的对话上下文和关键用户指令"新增了一个部分。

### 变更
- **内存系统稳健性 (高优先级):**
  - 更新 `prompts/01_Manager_Agent_Core_Guides/02_Memory_Bank_Guide.md`，强制要求所有目录/文件命名严格遵守 `Implementation_Plan.md`，并在创建前增加验证步骤。澄清了阶段和任务的命名约定。
  - 大幅修订 `prompts/02_Utility_Prompts_And_Format_Definitions/Memory_Bank_Log_Format.md`，强调简洁性，提供实现简洁的清晰原则，并增加了良好日志条目与过于冗长日志条目的具体示例。
  - 更新 `prompts/01_Manager_Agent_Core_Guides/03_Task_Assignment_Prompts_Guide.md`，指示经理代理明确提醒专门代理其在内存库结构和日志质量方面的义务（此早期更改与下面的新更改一起仍然有效）。
- **交接协议增强:**
  - 修改 `prompts/01_Manager_Agent_Core_Guides/05_Handover_Protocol_Guide.md`，为离任经理代理增加一个新的强制性步骤：回顾最近与用户的对话回合，并将未记录的关键指令或上下文变化的摘要整合到交接产物中。
- **实施计划和任务分配流程:**
  - 增强 `prompts/01_Manager_Agent_Core_Guides/01_Implementation_Plan_Guide.md` 以：
    - 强调并澄清每个任务明确分配代理的要求。
    - 强制在任务操作步骤中包含简短的"指导说明"（例如，关键方法、库、参数），以确保任务间的一致性并提供更清晰的方向。
  - 更新 `prompts/01_Manager_Agent_Core_Guides/03_Task_Assignment_Prompts_Guide.md`，确保经理代理在为实施代理创建详细的任务分配提示时，整合并扩展 `Implementation_Plan.md` 中的这些"指导说明"。
- **交接产物优化:**
  - 重构并澄清 `prompts/02_Utility_Prompts_And_Format_Definitions/Handover_Artifact_Format.md`，以提高可用性和理解。

### 移除
- 移除 `Complex_Task_Prompting_Best_Practices.md` 指南，以保持更通用的框架。
- 从 `prompts/02_Utility_Prompts_And_Format_Definitions/Imlementation_Agent_Onboarding.md` 中移除关于 Jupyter Notebook 单元生成的明确指南，以保持代理指导的通用性。

## [0.2.0] - 2025-05-14
### 新增
- 用于动态内存库设置的新经理代理指南 (`02_Memory_Bank_Guide.md`)。
- Cursor 规则系统，包含 3 个初始规则和 `rules/README.md`，用于在启动阶段提高 MA 的可靠性。
- 增强的 MA 启动流程，改进了资产验证、文件结构显示等。

### 变更
- 优化了经理代理启动流程 (`01_Initiation_Prompt.md`)，用于内存库、规划和代码库指导。
- 对关键文件（根 `README.md`, `Getting Started`, `Cursor Integration`, `Core Concepts`, `Troubleshooting`）进行全面文档更新，以反映所有 v0.2.0 的变更。
- 重新编号 `prompts/01_Manager_Agent_Core_Guides/` 中的核心 MA 指南，并更新了框架引用。


## [0.1.0] - 2025-05-12
### 新增
- 初始框架结构
- 定义了内存库日志格式和交接产物格式。
- 创建了核心文档：引言、工作流概述、入门指南、术语表、Cursor 集成指南、故障排除。
- 建立了基本的仓库文件：README、LICENSE、CONTRIBUTING、CHANGELOG、CODE OF CONDUCT。
- 为错误报告添加了初始的 GitHub issue 模板。


## [未发布]
### 新增
- 未来变更的占位符。

