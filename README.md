# 代理项目管理 (APM)

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) [![Version](https://img.shields.io/badge/version-v0.3.0-blue)](https://github.com/sdi2200262/agentic-project-management/releases/tag/v0.3.0)

*通过AI助手团队，平稳高效地管理复杂项目。*

## 什么是APM？

**代理项目管理 (APM)** 是一个将现实世界项目管理原则引入AI辅助工作流程的框架。它解决了LLM的一个基本挑战：上下文窗口限制。APM使用各种上下文保留技术，以结构化方式协调专门的AI代理团队，使您能够在面临模型幻觉和需要重新开始之前，保持更长时间的AI辅助工作。当上下文窗口确实填满时，APM确保平滑过渡到"新鲜"的聊天会话，而不会丢失重要上下文。

将其想象为拥有一个项目经理、开发人员和专家，都由AI驱动，在您的指导下协同工作。

<p align="center">
  <img src="assets/apm-graph.png" alt="apm-graph" width="full"/>
</p>

## 为什么选择APM？

在大型项目中使用AI可能会变得混乱。上下文丢失，代理忘记指令，感觉就像您无休止地重复自己，通常导致高令牌使用量和成本。APM通过以下方式解决这个问题：

*   **模拟真实团队：** 它使用明确的角色（经理、实施者）和经过验证的流程，使AI协作更加直观。
*   **智能代理管理：** APM包含**记忆库**（共享项目日志）、详细的**Markdown任务分配提示**以确保一致的代理行为，以及**专门代理**用于专注、范围明确的任务等技术。这提供了一个具有强大错误处理的复杂工作流程。
*   **高效且经济实惠：** APM旨在平衡。它被设计为精简且具有成本效益，帮助您在不"烧毁"令牌或API请求的情况下获得出色的结果。
*   **以用户为中心的控制：** 这个系统让您掌握方向盘。它强调在任何关键步骤中的用户指导和监督。如果代理遇到困难或达到上下文限制，APM提供清晰的解决方案，如**交接协议**（平滑切换到"新鲜"代理）并依赖**记忆库系统**保持整个工作流程的一致性。

## 开始使用：

以下是如何为您的项目启动和运行核心APM框架：

**访问APM资产：** 您有几个选项来获取APM提示、指南和协议定义：

1.  **使用APM模板（推荐用于自定义项目）：**
    *   点击[APM GitHub仓库](https://github.com/sdi2200262/agentic-project-management)上的"使用此模板"按钮。
    *   这会创建*您自己的仓库*，预填充整个APM结构。
    *   **理想设置：** 将*您的新仓库*克隆到项目工作空间的根目录。如果您确认完全资产可用性，这确保经理代理可以轻松引用所有APM指南。
2.  **克隆官方APM仓库（推荐用于直接使用和更新）：**
    *   直接将主[APM GitHub仓库](https://github.com/sdi2200262/agentic-project-management)克隆到您的项目工作空间，理想情况下在根目录。
    *   这给您直接访问最新版本和所有资产。
3.  **手动复制粘贴（基本使用）：**
    *   您可以根据需要从官方APM GitHub仓库直接复制粘贴提示内容（如`01_Initiation_Prompt.md`）到您的AI助手。
    *   虽然这有效，但需要您进行更多手动工作来在经理代理请求时提供指南内容。

**无论您选择哪种方式，关键是APM资产（特别是`prompts/`目录）要一致可访问，如果您打算让经理代理在完全文件感知的情况下运行，理想情况下从项目工作空间的根目录。**

**在您的项目中启动APM：**

1.  **启动您的经理代理：** 导航到`prompts/00_Initial_Manager_Setup/01_Initiation_Prompt.md`（在您克隆的APM仓库、基于模板的仓库或GitHub网站上）。
2.  **复制粘贴或添加上下文：** 复制其*全部内容*并粘贴到新的聊天会话（例如，在新的Cursor聊天标签中）或以您的IDE允许的任何方式作为上下文传递。
3.  **启动您的经理代理：** 将此内容作为第一条消息发送给您的AI助手。这个AI现在将成为您的第一个APM经理代理！
4.  **跟随引导：** 您的新经理代理，由这个启动提示指导，将询问您问题以了解您的项目并开始设置您的实施计划和记忆库系统。

**可选：使用Cursor规则增强APM（推荐给Cursor用户）**

*   如果您使用**Cursor IDE**，APM在`rules/`目录（或您项目工作空间的`.cursor/rules/`）中提供了一套预定义的[Cursor规则](https://docs.cursor.com/context/rules)，旨在以对上下文窗口使用的最小影响增强代理可靠性和工作流程效率。
*   这些规则针对APM工作流程中的特定点，为经理和实施代理提供上下文强化。
*   查看`rules/README.md`和[Cursor集成指南](docs/04_Cursor_Integration_Guide.md)获取简单的设置说明。
*   **其他IDE的概念：** 使用IDE特定的、持久的、范围明确的指令的原则可能适用于其他提供类似规则或自定义指令功能的AI集成IDE，如Windsurf、Roo等。如果您为另一个平台探索这个并找到可行的方法，请考虑通过在APM GitHub仓库上打开issue或Pull Request来分享您的见解！

## 深入了解

这个README为您提供了要点。要更深入地了解APM工作流程、高级功能、自定义以及每个组件背后的技术细节：

*   🚀 **[完整APM文档](docs/)** - 您的综合指南。
*   ⚙️ **[示例Cursor规则](rules/)** - 如果您使用Cursor IDE，可选的规则来增强APM。查看`rules/README.md`了解它们如何工作。
*   🖱️ **[Cursor集成指南](docs/04_Cursor_Integration_Guide.md)** - 在Cursor中优化使用APM的技巧，包括设置项目特定规则。

*（或者，您也可以直接从[这里](https://github.com/sdi2200262/agentic-project-management)浏览提示和文档）*

## 贡献

APM是一个开源项目，欢迎您的想法！无论是改进提示、增强文档、建议新功能，还是报告错误、流程缺陷或任何故障，请随时打开issue或提交pull request。

请阅读[CONTRIBUTING.md](CONTRIBUTING.md)了解行为准则和如何贡献的详细信息。

## 许可证

本项目采用MIT许可证 - 查看[LICENSE](LICENSE)文件了解详细信息。

<p align="center">
  <img src="assets/cobuter-man.png" alt="CobuterMan" width="150"/>
</p>

---

## 版本0.3.0的关键改进

版本0.3.0专注于增强健壮性、代理输出一致性、规划的清晰性以及交接期间上下文传输的可靠性。主要变化包括：

*   **增强的记忆系统：** 
    *   对记忆库结构（目录、日志文件）进行更严格的验证，对照`Implementation_Plan.md`以确保一致性并防止管理不善（参见`prompts/01_Manager_Agent_Core_Guides/02_Memory_Bank_Guide.md`）。
    *   改进了`prompts/02_Utility_Prompts_And_Format_Definitions/Memory_Bank_Log_Format.md`中的日志质量指南，强调简洁、信息丰富的条目，并提供清晰的示例。
*   **更详细和一致的实施规划和任务分配：**
    *   `prompts/01_Manager_Agent_Core_Guides/01_Implementation_Plan_Guide.md`现在要求：
        *   更强调为每个任务明确分配代理，以确保平衡的工作负载分配和清晰性。
        *   在每个任务的操作步骤中包含简短的"指导说明"（例如，关键方法、库、参数）。这在计划中提供关键方向，确保跨任务和代理的方法一致性。
    *   更新了`prompts/01_Manager_Agent_Core_Guides/03_Task_Assignment_Prompts_Guide.md`，确保经理代理在为实施代理创建详细、可操作的提示时，明确使用并扩展`Implementation_Plan.md`中的这些"指导说明"。
*   **更健壮的交接协议：**
    *   交接过程现在包括一个步骤，让离任代理明确捕获和传输最近的对话上下文和未记录的用户指令，确保新任代理拥有最新层次的用户意图（参见`prompts/01_Manager_Agent_Core_Guides/05_Handover_Protocol_Guide.md`）。
    *   `prompts/02_Utility_Prompts_And_Format_Definitions/Handover_Artifact_Format.md`已重新构建，以提高记录交接上下文的清晰性和可用性。
