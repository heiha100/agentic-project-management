# APM 内存库系统指南

## 1. 目的

本指南为经理代理 (MA) 提供了确定、提议和设置为给定项目最合适的内存库系统的说明。内存库对于记录实施代理的所有重要操作、决策和输出至关重要。

内存库系统（单个文件或多文件目录结构）的选择是与创建 `Implementation_Plan.md` 同时进行的。本指南定义了如何评估项目复杂性（源自 `Implementation_Plan.md`）以做出此选择，并指定了内存库文件的初始结构和标题。

本指南是对 `prompts/02_Utility_Prompts_And_Format_Definitions/Memory_Bank_Log_Format.md` 的补充，后者详细说明了这些文件中*单个日志条目*的格式。

## 2. 内存库系统设计的核心原则

在决定内存库系统时，应以以下为目标：

*   **可扩展性：** 系统应能有效处理项目当前和预期的复杂性以及日志条目的数量。
*   **组织性：** 日志必须易于用户和所有代理（当前或未来）定位、导航和理解。
*   **清晰性：** 结构应直观，并逻辑上反映 `Implementation_Plan.md` 中的项目分解。
*   **一致性：** 记录信息的位置和方式应采用统一的方法。
*   **对齐性：** 内存库结构应直接反映 `Implementation_Plan.md` 的组织结构（阶段、任务）。

## 3. 评估项目复杂性以进行系统选择

在生成完整的 `Implementation_Plan.md` 之前（但在概念化其结构并向用户总结之后），您（经理代理）必须评估其可能的复杂性，以确定合适的内存库系统。

**从您对即将到来的 `Implementation_Plan.md` 的理解中，考虑以下因素：**

*   **项目分期：**
    *   **高复杂性指标：** 计划被（或将被）划分为多个不同的 `## 阶段 X:` 部分。
    *   **较低复杂性指标：** 计划没有正式的阶段，或者基本上是单个阶段。
*   **任务的数量和性质：**
    *   **高复杂性指标：** 大量的 `### 任务 Y:` 条目，分配给多个不同代理的任务，或涵盖非常不同工作领域的任务。
    *   **较低复杂性指标：** 数量可管理的任务，主要由一个或两个密切协作的代理处理。
*   **任务粒度和细节：**
    *   **高复杂性指标：** 任务有许多详细的子组件和操作步骤，表明每个任务可能有大量的日志条目。
*   **项目持续时间和代理数量：**
    *   **高复杂性指标：** 预计项目持续时间较长或涉及许多专业实施代理，每个代理都可能生成许多日志。
    *   **较低复杂性指标：** 项目较短，代理较少。

**决策点：**

*   **如果存在多个高复杂性指标（例如，不同的阶段和许多复杂的任务），请选择多文件目录系统 (`Memory/`)。**
*   **如果主要存在较低复杂性指标，请选择单文件系统 (`Memory_Bank.md`)。**

运用您的判断来平衡这些因素。在中等复杂度的项目中，如果不确定，多文件系统可以提供更好的长期组织。

## 4. 内存库系统选项

### 4.1. 选项 1：单文件系统 (`Memory_Bank.md`)

*   **使用时机：** 建议用于直接的项目、范围较小的项目，或者当 `Implementation_Plan.md` 相对简单时（例如，任务少，没有不同的阶段，代理参与有限）。
*   **设置：**
    1.  您将在项目工作区的根目录创建一个名为 `Memory_Bank.md` 的单个文件。
    2.  用以下标题填充此文件：

    ```markdown
    # APM 项目内存库
    
    项目目标：[简要的项目目标，取自或总结自实施计划的介绍]
    启动日期：[内存库创建的 YYYY-MM-DD]
    经理代理会话 ID：[您当前的会话标识符，如果适用/可用]
    实施计划参考：`Implementation_Plan.md`
    
    ---
    
    ## 日志条目
    
    *（此文件中的所有后续日志条目都必须遵循 `prompts/02_Utility_Prompts_And_Format_Definitions/Memory_Bank_Log_Format.md` 中定义的格式）*
    ```

### 4.2. 选项 2：多文件目录系统 (`Memory/`)

*   **使用时机：** 建议用于复杂的项目，特别是那些具有多个阶段、大量不同任务、多个不同工作流或预计持续时间较长的项目，如 `Implementation_Plan.md` 的结构所示。
*   **设置：**
    1.  您将在项目根目录创建一个名为 `Memory/` 的根目录。
    2.  **在 `Memory/` 目录中，创建一个 `README.md` 文件**以解释其结构。`Memory/README.md` 的示例内容：
        ```markdown
        # APM 项目内存库目录
        
        此目录存放 [项目名称] 项目的详细日志文件。
        
        ## 结构：
        
        （描述所选的结构，例如：
        - 日志被组织到与 `Implementation_Plan.md` 中每个阶段相对应的子目录中。
        - 在每个阶段目录中，单个 `.md` 文件捕获特定任务的日志。
        或者
        - `Implementation_Plan.md` 中每个主要任务的日志都作为单个 `.md` 文件直接存储在此目录中。）
        
        这些文件中的所有日志条目都遵守 `prompts/02_Utility_Prompts_And_Format_Definitions/Memory_Bank_Log_Format.md` 中定义的格式。
        ```
    3.  **根据 `Implementation_Plan.md` 确定子目录和文件命名策略：**
        *   **A. 如果 `Implementation_Plan.md` 有阶段（例如，`## 阶段 1：后端设置`）：**
            *   对于每个阶段，在 `Memory/` 中创建一个相应的子目录。使用从计划中派生的清晰、文件系统友好的名称（例如，`Memory/Phase_1_Backend_Setup/`、`Memory/Phase_2_Frontend_Dev/`）。
            *   在每个阶段子目录中，为属于该阶段的日志任务创建单独的 Markdown 文件。
            *   **日志文件命名约定：** `Task_[任务标识符]_Log.md`（例如，`Task_A_User_Auth_Log.md`、`Task_B_Activity_API_Log.md`）。`任务标识符`应简洁，并清楚地映射到 `Implementation_Plan.md` 中的任务。
            *   **示例路径：** `Memory/Phase_1_Backend_Setup/Task_A_User_Auth_Log.md`
        *   **B. 如果 `Implementation_Plan.md` 没有阶段但很复杂（许多不同的任务）：**
            *   直接在 `Memory/` 目录下创建单独的 Markdown 日志文件。
            *   **日志文件命名约定：** `Task_[任务标识符]_Log.md`（例如，`Task_Data_Processing_Log.md`）。
            *   **示例路径：** `Memory/Task_Data_Processing_Log.md`
    4.  **用以下标题填充每个单独的日志文件 (`Task_..._Log.md`)：**

        ```markdown
        # APM 任务日志：[来自 Implementation_Plan.md 的完整任务标题]
        
        项目目标：[来自实施计划的简要项目目标]
        阶段：[来自 Implementation_Plan.md 的阶段名称，如果适用，否则为"N/A"]
        计划中的任务参考：[来自 Implementation_Plan.md 的完整任务标题，例如，"### 任务 A - 代理 A：用户身份验证模块"]
        计划中分配的代理：[在 Implementation_Plan.md 中为任务列出的代理]
        日志文件创建日期：[YYYY-MM-DD]
        
        ---
        
        ## 日志条目
        
        *（此文件中的所有后续日志条目都必须遵循 `prompts/02_Utility_Prompts_And_Format_Definitions/Memory_Bank_Log_Format.md` 中定义的格式）*
        ```
    5.  作为 MA，您负责创建 `Memory/` 目录、其 `README.md`，以及与 `Implementation_Plan.md` 中的初始任务相对应的初始阶段子目录（如果有）和带有其标题的任务日志文件。

## 5. 向用户提议和创建内存库系统

此过程与您启动的"综合提案和创建"步骤一致，在该步骤中您还介绍了 `Implementation_Plan.md` 摘要。

1.  **分析：** 根据您（MA）对项目范围和 `Implementation_Plan.md` 的计划结构的理解，使用第 3 节中的标准在单文件或多文件内存库系统之间做出决定。
2.  **制定提案：** 为用户准备一份简短的声明，其中包括：
    *   所选的内存库系统（例如，"单个 `Memory_Bank.md` 文件"或"`Memory/` 目录中的多文件系统，每个阶段都有子目录"）。
    *   与（即将到来的）`Implementation_Plan.md` 中反映的项目复杂性相关的简明理由（例如，"……由于项目性质直接，"或"……为了有效管理多个阶段和复杂任务的日志"）。
3.  **与计划摘要一起交付提案：** 在您交付 `Implementation_Plan.md` 的高级摘要的*同时*向用户展示此内存库提案。
    *   **示例用户通信（多文件）：**
        > "根据此项目预期的分阶段结构和多个复杂任务（将在 `Implementation_Plan.md` 中详细说明），我建议采用多文件内存库系统。这将涉及一个 `Memory/` 目录，可能每个阶段都有子目录（例如，`Memory/Phase_1_Design/`），以及关键任务的单独日志文件（例如，`Task_Alpha_User_Research_Log.md`）。这将使我们的项目日志井然有序且可追溯。
        >
        > 我现在将继续创建初始的 `Implementation_Plan.md` 文件和此内存库结构。请在创建后审查两者。"
    *   **示例用户通信（单文件）：**
        > "鉴于项目的重点范围（将在 `Implementation_Plan.md` 中详细说明），单个 `Memory_Bank.md` 文件应该足以满足我们的日志记录需求。这将为所有任务更新提供一个集中的位置。
        >
        > 我现在将继续创建初始的 `Implementation_Plan.md` 文件和此 `Memory_Bank.md` 文件。请在创建后审查两者。"
4.  **创建文件：** 提交后，并假设用户对高级计划摘要和内存库概念没有立即提出异议，则继续创建：
    *   完整的 `Implementation_Plan.md`（根据 `01_Implementation_Plan_Guide.md`）。
    *   所选的内存库文件/目录结构，带有正确的标题，如*本*指南第 4 节所述。
5.  **邀请审查：** 创建后，明确邀请用户审查新创建的 `Implementation_Plan.md` 的*内容*以及 `Memory_Bank.md` 文件或 `Memory/` 目录及其初始文件的结构/标题。

## 6. 持续日志记录

*   本指南涵盖内存库系统的*设置*。
*   实施代理（在用户确认后）在这些文件中进行的所有*实际日志条目***必须**严格遵守 `prompts/02_Utility_Prompts_And_Format_Definitions/Memory_Bank_Log_Format.md` 中定义的格式化规则。
*   随着在不断演变的 `Implementation_Plan.md` 中定义新任务或启动新阶段，您（MA）可能需要指导在已建立的多文件系统中创建新的日志文件，并保持相同的命名约定和标题格式。

通过遵循本指南，您将建立一个组织良好、可扩展且能有效支持 APM 工作流程的内存库系统。

## 严格遵守实施计划

内存库的完整性取决于其忠实地反映 `Implementation_Plan.md` 中定义的项目计划结构和进度。

*   **权威来源：** 所有内存库目录和文件名都必须精确地反映*当前、权威的* `Implementation_Plan.md` 中的阶段和任务标识符及描述。
*   **验证义务：** 在创建任何目录或文件之前，负责的代理（无论是经理代理还是专业代理）都必须根据 `Implementation_Plan.md` 验证提议的名称和位置。
*   **阶段目录命名：** 阶段目录名称必须遵循确切的命名约定：`Memory/Phase_X_Title_From_Plan/`。
    *   `X` 是阶段编号（例如，1、2、3）。
    *   `Title_From_Plan` 是 `Implementation_Plan.md` 中用于该阶段的确切标题字符串。计划中阶段标题中的空格应在目录名称中替换为下划线。
1.  **Analyze:** Based on your (MA's) understanding of the project's scope and the planned structure of `Implementation_Plan.md`, decide between the Single-File or Multi-File Memory Bank system using the criteria in Section 3.
2.  **Formulate Proposal:** Prepare a brief statement for the User that includes:
    *   The chosen Memory Bank system (e.g., "a single `Memory_Bank.md` file" or "a multi-file system within a `Memory/` directory, with subdirectories per phase").
    *   A concise justification linked to the project's complexity as reflected in the (upcoming) `Implementation_Plan.md` (e.g., "...due to the project's straightforward nature," or "...to effectively manage logs for the multiple phases and complex tasks outlined").
3.  **Deliver Proposal with Plan Summary:** Present this Memory Bank proposal to the User *at the same time* you deliver the high-level summary of the `Implementation_Plan.md`.
    *   **Example User Communication (Multi-File):**
        > "Based on the phased structure and multiple complex tasks anticipated for this project (which will be detailed in the `Implementation_Plan.md`), I propose a multi-file Memory Bank system. This will involve a `Memory/` directory, potentially with subdirectories for each phase (e.g., `Memory/Phase_1_Design/`) and individual log files for key tasks (e.g., `Task_Alpha_User_Research_Log.md`). This will keep our project logs organized and traceable.
        >
        > I will now proceed to create the initial `Implementation_Plan.md` file and this Memory Bank structure. Please review both once they are created."
    *   **Example User Communication (Single-File):**
        > "Given the focused scope of the project (which will be detailed in the `Implementation_Plan.md`), a single `Memory_Bank.md` file should be sufficient for our logging needs. This will provide a centralized location for all task updates.
        >
        > I will now proceed to create the initial `Implementation_Plan.md` file and this `Memory_Bank.md` file. Please review both once they are created."
4.  **Create Files:** After presenting, and assuming no immediate objections from the User to the high-level plan summary and Memory Bank concept, proceed to create:
    *   The full `Implementation_Plan.md` (as per `01_Implementation_Plan_Guide.md`).
    *   The chosen Memory Bank file(s)/directory structure with the correct headers, as detailed in Section 4 of *this* guide.
5.  **Invite Review:** After creation, explicitly invite the User to review the *content* of the newly created `Implementation_Plan.md` AND the structure/headers of the `Memory_Bank.md` file or `Memory/` directory and its initial files.

## 6. Ongoing Logging

*   This guide covers the *setup* of the Memory Bank system.
*   All *actual log entries* made by Implementation Agents (after User confirmation) into these files **must** strictly adhere to the formatting rules defined in `prompts/02_Utility_Prompts_And_Format_Definitions/Memory_Bank_Log_Format.md`.
*   As new tasks are defined or phases initiated in an evolving `Implementation_Plan.md`, you (the MA) may need to guide the creation of new log files within the established multi-file system, maintaining the same naming conventions and header formats.

By following this guide, you will establish a Memory Bank system that is well-organized, scalable, and effectively supports the APM workflow.

## Strict Adherence to Implementation Plan

The integrity of the Memory Bank relies on its faithful reflection of the project's planned structure and progress as defined in the `Implementation_Plan.md`.

*   **Authoritative Source:** All Memory Bank directory and file names MUST precisely mirror the Phase and Task identifiers and descriptions found in the *current, authoritative* `Implementation_Plan.md`.
*   **Verification Obligation:** Before creating any directory or file, the responsible agent (whether Manager Agent or a specialized agent) MUST verify the proposed name and location against the `Implementation_Plan.md`.
*   **Phase Directory Naming:** Phase directory names MUST follow the exact naming convention: `Memory/Phase_X_Title_From_Plan/`.
    *   `X` is the phase number (e.g., 1, 2, 3).
    *   `Title_From_Plan` is the exact title string used for that phase in the `Implementation_Plan.md`. Spaces in the plan's phase title should be replaced with underscores in the directory name.
    *   Example: If Phase 1 is titled "Project Setup & Data Exploration" in the plan, the directory will be `Memory/Phase_1_Project_Setup_Data_Exploration/`.
*   **Task Log File Naming:** Task log file names MUST follow the exact naming convention: `Task_[Phase.Task]_Short_Task_Description_Log.md`.
    *   `[Phase.Task]` is the precise identifier from the plan (e.g., 1.1, 2.3).
    *   `Short_Task_Description` is a concise, underscore_separated version of the task's title or primary objective from the `Implementation_Plan.md`.
    *   Example: If Task 1.1 is "Environment, Constants & Initial Notebook Setup", the log file could be `Task_1.1_Env_Init_Notebook_Setup_Log.md`. Strive for clarity and direct correlation with the plan.

## Validation Before Creation

To prevent errors arising from outdated information or misunderstandings:

*   **Clarification Protocol:** If an agent is tasked with creating a memory structure and finds that the `Implementation_Plan.md` is unclear regarding the specific naming, if the plan has recently undergone changes, or if a proposed name appears inconsistent with the current plan, the agent MUST seek clarification from the Manager Agent BEFORE proceeding with creation.
*   **Dynamic but Verified Creation:** The dynamic, incremental creation of memory structures is encouraged as it allows the Memory Bank to adapt to the project's evolution. However, this dynamism must always be rooted in the *actively confirmed and current* state of the `Implementation_Plan.md` at the moment of creation. Do not create structures based on anticipated or outdated plan versions. 