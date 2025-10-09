
在过去两周，我们已经逐期整理了 **吴恩达与 Anthropic 在线教育主管 Elie Schoppik** 的合作课程[《Claude Code: A Highly Agentic Coding Assistant》](https://www.deeplearning.ai/short-courses/claude-code-a-highly-agentic-coding-assistant)的全部内容，总共九期并收录在[《吴恩达 Claude Code 笔记合集》](https://mp.weixin.qq.com/mp/appmsgalbum?__biz=Mzg2OTg5NDg3Mg==&action=getalbum&album_id=4121229896725266445#wechat_redirect)：

- [01. 引言](https://mp.weixin.qq.com/s/wcAOpNHjngxyXdg2NV2kQg)
- [02. 揭秘 AI 编程助理的核心机制](https://mp.weixin.qq.com/s/WsgTjgruDgm9wNwx7stbww)
- [03. 深入代码库与 AI 记忆的构建](https://mp.weixin.qq.com/s/5LvwLn2d5kxqThfKElLX2g)
- [04. Prompt范式、深度思考、上下文工程与MCP](https://mp.weixin.qq.com/s/8xOjGUkXzCGSOvB74vnd8A)
- [05. 测试驱动开发（TDD）与并行Agent头脑风暴](https://mp.weixin.qq.com/s/g6RUtFldSjiYmDAW1LOknw)
- [06. CC + Git Worktree = 王炸](https://mp.weixin.qq.com/s/_4oPcqy-vcQWcsAOO4DKZA)
- [07. 集成 GitHub 与 Hooks 实现开发全流程自动化](https://mp.weixin.qq.com/s/al6c_mi6oi3caNmHvT2VnA)
- [08. Jupyter 数据分析与 Streamlit 可视化](https://mp.weixin.qq.com/s/LE4JZ-nzu914Q__vl9i3Hw)
- [09. 基于 Figma MCP 直出 App](https://mp.weixin.qq.com/s/lm4vYa0mzEc4Yc6w736OtA)

如果您也有类似高质量的教程、文章资源，欢迎留言区推荐，我们一起学习，一起进步~

今天是精华总结版特刊，旨在提供一个速览，并针对不同人群提供尽可能全面的学习路线指导。

![](https://mmbiz.qpic.cn/sz_mmbiz_png/2niaYkVLHpnGicMMr69cicWHgxWjt6LOVntpOdqYZRADdicticCQflMZSUFCF02BqW57hyVrZ0FeicjJYmIox9QTIs6A/640?wx_fmt=png&from=appmsg&tp=webp&wxfrom=5&wx_lazy=1)

### Key Insights

1.  **范式转变：从“指令式工具”到“智能体伙伴”**：核心在于思维模式的跃迁。**你需要将 Claude Code 视为一个能够自主规划、执行并进行反思的初级合伙人**，而非一个被动的代码生成器。
2.  **上下文工程：对话的本质是信息架构**：与 AI 的每一次交互，都是一次微型的信息架构设计。成功的关键在于**如何精准、高效地构建上下文**，这决定了其输出质量的上限。
3.  **持久化记忆：构建项目的“第二大脑”**：通过 `CLAUDE.md` 系统，我们将为 AI 构建一个可版本化、可共享的项目知识库，实现**跨会话、跨团队的知识沉淀与复用**。
4.  **工程化整合：将 AI 注入开发生命周期**：真正的价值在于**将 AI 无缝融入成熟的工程实践**中，例如测试驱动调试（TDD）、并行开发（Git Worktree）和持续集成/持续部署（CI/CD）。
5.  **元编程思维：从“使用 AI”到“编排 AI”**：通过 MCPs 和 Hooks 等高级功能，开发者将从 AI 的“使用者”转变为 **AI 工作流的“设计者与编排者”**，实现开发流程的深度自动化与定制。

---

## 最佳实践（一） 开发范式的重塑

在我们深入探讨具体实践之前，必须首先完成一次思维模式的转变。Claude Code 并非一个增强版的 Stack Overflow，而是一个 **智能体化系统 (Agentic System)**。

```ad-tip {TITLE: "智能体化系统 (Agentic System)"}

一个智能体化系统，指的是一个由 **模型 (Model)**、**工具集 (Tools)** 和 **执行环境 (Environment)** 协同工作的系统。它超越了被动的输入-输出模式，能够主动地 **规划 (Plan)**、**获取信息 (Perceive)** 并 **采取行动 (Act)** 来实现一个既定目标。Claude Code 正是这样一个系统，它能像人类开发者一样，在你的本地代码库这个“环境”中，利用文件读写、命令执行等“工具”，来完成复杂的编程任务。 [7]
```

![](https://poketto.oss-cn-hangzhou.aliyuncs.com/96cc546f5068dd3495c34074bd85e010.png?x-oss-process=image/quality,q_90/rotate,0)


这意味着，我们的交互方式应**从“提问”转向“委托”**，从“寻求代码片段”转向“分派一个完整的、有明确目标和约束的任务”。

## 最佳实践（二） 上下文工程

与 AI 协作的成败，直接取决于我们构建上下文的质量。资深开发者应将每一次 Prompt 视为一次精准的“任务描述”或“技术方案”的撰写。

![](https://poketto.oss-cn-hangzhou.aliyuncs.com/71ae63768b46f2fa7c7b263acfd91a6f.png?x-oss-process=image/quality,q_90/rotate,0)

### 结构化 Prompt：定义与 AI 的“交互契约”

一个专业级的 Prompt 应该像一份清晰的需求文档，它定义了你与 AI 之间的“交互契约”。

1.  **定义现状 (Context)**：`The current implementation in @module/service.py has a performance bottleneck under concurrent loads.`
2.  **定义目标 (Goal)**：`Refactor this module to use an asynchronous pattern with a connection pool to handle up to 500 concurrent requests.`
3.  **提供示例 (Example)**：`For instance, a call to process_data(items) should now return a Future object.`
4.  **施加约束 (Constraints)**：`Only use libraries present in requirements.txt. The solution must be compatible with Python 3.9+. Maintain the existing public API signature to avoid breaking changes.`
5.  **指定路径 (Methodology)**：`First, write a failing benchmark test that reproduces the bottleneck. Then, implement the async changes. Finally, ensure all existing unit tests and the new benchmark pass.



### 策略性思考与规划：引导而非命令

在面对复杂任务时，直接要求实现是低效的。更高级的策略是引导 AI 先进行深度思考。

- **扩展思考模式**：通过在 Prompt 中加入 `think`, `think hard`, `think harder`, `ultrathink` 等关键词，可以强制 AI 分配更多资源进行规划，这对于架构设计或复杂重构至关重要。
- **计划模式 (Plan Mode)**：通过 `Shift + Tab` 切换到计划模式，强制 AI 在动手前提交一份详细的行动计划。这提供了一个关键的架构评审节点，确保 AI 的执行路径符合你的预期，避免不必要的返工。

### 对话上下文管理：战略性的“记忆”取舍

长对话会消耗宝贵的上下文窗口。资深开发者需要像管理内存一样管理对话历史。

- `/clear`：当任务切换，上下文已完全无关时，果断清空历史，避免信息污染。
- `/compact`：当需要开启一个相关但更聚焦的新任务时，使用此命令。它会总结之前的对话，保留关键信息作为新会话的引子，实现上下文的平滑过渡。此命令甚至支持自定义指令，如 `/compact Focus on code samples and API usage`，以优化压缩效果并节约成本。

## 最佳实践（三） 驾驭`CLAUDE.md`

为了让 AI 在项目中拥有持久化、可共享的知识，我们必须善用 `CLAUDE.md` 这一核心机制。它本质上是为项目构建了一个可由 AI 读取和遵循的、版本化的“技术宪章”。

### 记忆的层级与加载机制

`CLAUDE.md` 的分层加载机制允许我们清晰地分离团队规范与个人偏好。加载顺序为：企业策略 -> 用户记忆 -> 项目记忆，更具体的配置会覆盖或补充上层配置。

![](https://poketto.oss-cn-hangzhou.aliyuncs.com/811666e841ff29112c9d13a5216dd0d5.png?x-oss-process=image/quality,q_90/rotate,0)


```ad-tip {TITLE: "CLAUDE.md 查找与导入机制"}

Claude Code 会从当前工作目录开始，向上递归查找 `CLAUDE.md` 文件，直到根目录。 [11] 此外，`CLAUDE.md` 支持 `@path/to/file.md` 语法导入其他文件，这已取代了现已废弃的 `CLAUDE.local.md`，特别是在使用 Git Worktrees 时能提供更好的支持。 [11]
```

### 构建高质量的项目记忆

- **初始化 (`/init`)**：在项目初期，使用 `/init` 命令让 AI 自动扫描代码库，生成一份包含项目架构、关键依赖和编码风格的基础 `CLAUDE.md`。
- **动态更新 (`#`)**：在日常协作中，当你发现 AI 存在知识盲点或反复犯错时（例如，使用了错误版本的库），应立即使用 `#` 快捷指令将其纠正并固化到项目记忆中。

## 最佳实践（四） 工程化整合

将 AI 能力与成熟的软件工程实践相结合，才能发挥其最大价值。

### 测试驱动调试 (Test-Driven Debugging)

这是从“作坊式”修复到“工程化”修复的思维飞跃。当遇到 Bug 时，最佳实践是委托 AI：**“为这个 Bug 编写一个能够稳定复现它的 `pytest` 测试用例。这个测试现在应该是失败的。然后，修改代码，让这个测试通过。”** 这种方法不仅修复了 Bug，还为系统增加了一道永久的回归测试防线。

> 手工川注：TDD 只是众多开发范式中的一种，还有以 [Kiro](https://kiro.dev/) 为代表的 Spec 驱动，以及最近比较火的 pilot驱动（去年就有一个gpt-pilot也火过一次），各有各的用处。参考：
>   - [AWS Kiro 发布：AI 赋能的 agentic IDE，开启“spec 驱动开发”新时代](https://www.hkn.today/p/aws-kiro-ai-agentic-idespec)
>   - [字节新出的「PromptPilot」太好用了！！](https://mp.weixin.qq.com/s/CEw1KHk_kDCTR3zOR1a9_Q)

### 并行智能体头脑风暴 (Subagent Brainstorming)

```ad-tip {TITLE: "子智能体 (Subagents)"}

子智能体是专为特定任务配置的 AI 助手，拥有独立的上下文窗口、系统提示和工具集。 [12] Claude Code 可以根据任务描述自动委托给合适的子智能体，或者由用户明确调用。你可以通过在 `.claude/agents/` (项目级) 或 `~/.claude/agents/` (用户级) 目录下创建 Markdown 文件来定义自己的子智能体。 [12]
```

对于开放性的架构设计，避免直接给出方案。利用子智能体能力让其进行方案探索：
`Refactor the authentication module. Use two parallel subagents to brainstorm possible plans, one based on JWT and another on session cookies. Compare their trade-offs in terms of security, scalability, and statelessness. Do not implement any code.`

这能让你在极短时间内获得多个备选方案及其深度分析，极大地提升了决策质量。

![教程截图：两个agent在并行地执行任务](https://poketto.oss-cn-hangzhou.aliyuncs.com/0429fbd210ff84e787fac6ba98739af2.png?x-oss-process/image/quality,q_90/rotate,0)

>手工川注：这个办法简单有效，特别适合搞抽象的vibe coder，建议背诵 `Use N parallel subagents to brainstorm possible plans`，或者抽象为 slash command。

### Git Worktree：无摩擦的并行开发

`Git Worktree` 允许你在同一代码库上创建多个物理隔离的工作目录，彻底解决了并行开发中因切换分支带来的上下文切换开销和潜在冲突。结合 Claude Code，你可以为每个功能分支或 Bug 修复创建一个 Worktree，并在其中运行独立的 AI 会话，实现真正的无干扰并行开发。

>手工川注：git worktree会强迫cc在非当前目录运行，导致 @的智能补全失效、merge维护成本变高等，更加适合团队开发使用，每个人独立开启worktree，互不干扰，然后组长决定是否合并。手工川一直维护的 [claude code 增强工具 ccm](https://github.com/MarkShawn2020/claude-code-manager) 最近也上线了 worktree 开发模式，欢迎大家体验与反馈。


### 云端协作：GitHub 上的虚拟工程师

通过 `/install-github-app` 将 Claude Code 集成到 GitHub，它就从你的个人助理升级为团队的共享资源。它可以 7x24 小时地执行自动化代码审查（PR Review），或通过在 Issue 中 `@claude` 来直接指派其修复 Bug，并将结果以 PR 的形式提交，无缝融入团队的 CI/CD 流程。

```ad-tip 手工川注：Github 集成 Claude Code 摘要  

**前置工作**
  
1. 确保 claude 账号 ok（国内确保梯子健康）  
2. 确保github pat token 权限 ok （建议直接勾选全部权限，否则中途可能会有各种乱七八糟的问题，目前测试至少需要 action、content、pr 等读写权限）  
   
**配置办法**  

1. 在 cc 中输入 /install-github-app  
2. 根据指示，勾选当前仓库或者所有仓库，勾选支持手动at与自动pr等功能，等待配置完成  
   
**如何使用**
  
1. 【在 github 上主动 at claude 干活】在github上的某个issue内，直接输入 @，就会有自动补全，勾选claude，然后输入内容即可（比如 please ultrathink and fix this issue） 
2. 【自动 pr】每当 pr 时，claude bot 会被自动触发进行代码 review

**原理**

cc创建了workflow，workflow里约定了一些特定场景（例如被at），触发后自动读取仓库并实现需求，参考：https://github.com/MarkShawn2020/claude-code-manager/blob/main/.github/workflows/claude.yml  

---  

参考：[吴恩达 Claude Code 笔记 07：集成 GitHub 与 Hooks 实现开发全流程自动化](https://mp.weixin.qq.com/s/al6c_mi6oi3caNmHvT2VnA)
```

## 最佳实践（五） 扩展能力

最高级的实践，是把 AI 本身当作一个可编程的平台，深度定制其行为。

### MCP (模型上下文协议)：扩展 AI 的感知与行动

MCP 是 AI 的“驱动程序”标准，允许它与外部世界（如 Figma、数据库、甚至是物理设备）进行标准化的双向通信。通过 `/mcp` 管理连接，我们可以赋予 AI 超越代码的“视觉”（读取设计稿）和“触觉”（操作浏览器），使其能完成从设计到实现的端到端任务。

### Hooks：为 AI 的行为注入“中间件”

```ad-tip {TITLE: "Claude Code Hooks"}

Hooks 是在 Claude Code 生命周期特定事件点（如 `PreToolUse`, `PostToolUse`, `UserPromptSubmit` 等）执行的、用户定义的 Shell 命令。 [6] 它们提供了对 AI 行为的确定性控制，能将团队的非功能性需求（如安全、合规、质量）强制注入到 AI 的每一次操作中，实现从“建议”到“规则”的转变。 [5]
```

**应用场景**：

- **PreToolUse Hook**：在 `git commit` 前，强制运行 linting 和静态分析。
- **PostToolUse Hook**：在 `Write` 或 `Edit` 工具使用后，自动运行 `prettier` 对 TypeScript 文件进行格式化。
- **安全**：使用 `PreToolUse` Hook 阻止对 `.env` 或 `package-lock.json` 等敏感文件的修改。

>手工川注：ccm 有使用 post-tool hook 以支持实时数据分析。

---

## Learning Roadmap

根据不同的技术角色，我们建议以下学习路径来最大化 Claude Code 的价值：

### 开发者 (所有级别) - 聚焦个人生产力

1.  **快速上手**：从 [Quickstart](https://docs.anthropic.com/en/docs/claude-code/quickstart) 开始，熟悉基本的交互模式。
2.  **掌握上下文工程**：精通 `@` 文件引用、结构化 Prompt 和 `#` 记忆添加，这是提升日常效率的核心。
3.  **融入工程实践**：将测试驱动调试（TDD）和 `claude commit` 等功能融入日常开发流程。
4.  **效率自动化**：学习创建个人自定义斜杠命令 (`~/.claude/commands/`)，将高频操作封装起来。

### 高级开发者 / 团队负责人 - 聚焦团队协作与代码质量

1.  **构建团队知识库**：精通 `CLAUDE.md` 的项目级配置，将团队的最佳实践、架构决策和代码规范沉淀下来。
2.  **优化团队流程**：全面采用 `Git Worktree` 进行并行开发，并集成 GitHub Actions 实现自动化代码审查和问题修复。
3.  **设计高级工作流**：创建项目级的自定义斜杠命令 (`./.claude/commands/`) 和子智能体，统一团队处理复杂任务（如发布流程、安全审计）的方式。
4.  **质量与合规**：利用 Hooks 系统，在项目中强制执行代码格式化、安全扫描等质量门禁。

### DevOps / SRE / 平台工程师 - 聚焦自动化、集成与治理

1.  **深度自动化**：全面掌握 Hooks 系统，将其用于 CI/CD 流程自动化、环境验证、以及与内部系统的集成。
2.  **扩展能力边界**：学习和部署 MCP 服务器，将 Claude Code 与公司的监控系统、日志平台、工单系统（Jira, Asana）等进行深度集成。
3.  **企业级部署与治理**：研究[第三方集成方案](https://docs.anthropic.com/en/docs/claude-code/third-party-integrations)，如通过 Amazon Bedrock 或 Google Vertex AI 进行部署，配置企业代理和 LLM 网关。
4.  **安全与监控**：精通 [IAM](https://docs.anthropic.com/en/docs/claude-code/iam) 和企业级策略配置，利用 [OpenTelemetry](https://docs.anthropic.com/en/docs/claude-code/monitoring-usage) 进行全面的使用情况监控、成本分析和安全审计。

---

## 结语：重塑开发者价值

与高级 AI 智能体协作，要求开发者从代码的实现者，转变为开发流程的架构师。我们的核心竞争力不再是写代码的速度，而是定义问题的精度、构建上下文的深度、以及编排人机协作流程的巧度。掌握这套系统性的方法论，将使我们能够驾驭 AI 这一强大的生产力工具，去解决更复杂、更具创造性的问题。

感谢吴恩达与Elie老师，再见！

>吴恩达老师的教程通俗易懂，学习曲线较为平缓，犹记得几年前学习他的机器学习教程，快结束的时候非常感动，印象深刻，推荐大家对计算机、AI感兴趣的可以多去 https://www.deeplearning.ai/ 网站逛逛~

---

## 附录 (Appendix)

### A. 核心命令参考

这张速查表整合了 Claude Code 最核心的命令行标志和交互式斜杠命令，是日常高效使用的关键。

| 分类             | 命令 / 标志                      | 描述                                                    |
| :--------------- | :------------------------------- | :------------------------------------------------------ |
| **会话启动**     | `claude`                         | 启动一个新的交互式会话。                                |
|                  | `claude -c`, ` --continue`       | 继续上一次的会话。                                      |
|                  | `claude -r`, ` --resume`         | 从历史会话列表中选择一个恢复。                          |
|                  | `claude -p "prompt"`             | 在非交互模式下执行单个任务并打印结果。                  |
| **会话管理**     | `/clear`                         | 完全清空当前对话历史，开始全新会话。                    |
|                  | `/compact [instr.]`              | 压缩对话历史，可选附加指令以保留关键信息。              |
|                  | `/model`                         | 查看或切换当前会话使用的 AI 模型。                      |
|                  | `ESC` / `ESC ESC`                | `ESC` 中断当前任务，`ESC ESC` 回滚对话到上一个时间点。  |
| **上下文与记忆** | `@path/to/file`                  | 在 Prompt 中引用文件或目录，为其提供精准上下文。        |
|                  | `/init`                          | 扫描代码库，自动创建 `CLAUDE.md` 文件作为项目长期记忆。 |
|                  | `/memory`                        | 在编辑器中直接打开 `CLAUDE.md` 记忆文件。               |
|                  | `# instruction`                  | 在对话中快速添加一条记忆到 `CLAUDE.md`。                |
| **扩展与集成**   | `/mcp`                           | 管理模型上下文协议（MCP）服务器连接。                   |
|                  | `/agents`                        | 管理自定义的子智能体。                                  |
|                  | `/hooks`                         | 配置 Hooks，定制 AI 工具执行生命周期中的行为。          |
|                  | `/install-github-app`            | 启动将 Claude Code 集成到 GitHub 仓库的流程。           |
| **权限与安全**   | `/permissions`                   | 查看和管理工具的使用权限。                              |
|                  | `--dangerously-skip-permissions` | **[慎用]** 在非交互模式下跳过所有权限提示。             |
| **实用工具**     | `/config`                        | 查看和修改本地配置。                                    |
|                  | `/doctor`                        | 检查 Claude Code 安装的健康状况。                       |
|                  | `/cost`                          | **[非订阅用户]** 显示当前会话的 token 使用和成本。      |

### B. 架构级 Prompt 模式

以下是课程中展示的、超越简单指令的、具有架构设计思想的 Prompt 模式，可作为解决复杂问题的模板。

- **模式一：测试驱动调试 (TDD)**

  - **场景**：修复一个行为不明确的 Bug。
  - **核心思想**：不直接要求修复，而是要求先建立可验证的失败场景，再进行修复。
  - **Prompt 模板 (Lesson 4)**
    ```
    The RAG chatbot returns 'query failed'. I need you to:
    1. Write tests for the core components in @backend/search_tools.py, @backend/ai_generator.py, and the RAG system itself.
    2. Save the tests in a `tests/` directory within @backend.
    3. Run these tests to identify the failing component.
    4. Propose a fix based on the test results.
    Think.
    ```

- **模式二：关注点分离重构 (SoC Refactoring)**

  - **场景**：整理一个逻辑混杂的单体脚本或 Notebook。
  - **核心思想**：明确定义目标模块结构和各自的职责，让 AI 执行代码的“搬迁”和“重组”。
  - **Prompt 模板 (Lesson 7)**

    ```
    Refactor the @EDA.ipynb for e-commerce data analysis.

    **Requirements:**
    1.  **Structure:** Organize into logical sections (Intro, Loading, Prep, Metrics, Summary) with proper markdown documentation.
    2.  **Code Quality:** Create reusable functions with docstrings and move core logic into separate Python modules: `business_metrics.py` and `data_loader.py`.
    3.  **Configurability:** Refactor the analysis to be configurable by date range.

    **Deliverables:** A refactored notebook, two Python modules, and a `requirements.txt`.
    ```

- **模式三：“布局即 Prompt” 的 UI 生成**

  - **场景**：将数据或逻辑产品化为可视化界面。
  - **核心思想**：用自然语言清晰地描述出 UI 的“线框图”和组件布局，为 AI 提供明确的视觉目标。
  - **Prompt 模板 (Lesson 7)**

    ```
    Convert `@EDA_Refactored.ipynb` into a professional Streamlit dashboard with this exact layout:

    ## Layout Structure
    - **Header**: Title + date range filter (applies globally)
    - **KPI Row**: 4 cards (Total Revenue, Monthly Growth, Average Order Value, Total Orders)
    - **Charts Grid**: 2x2 layout (Revenue trend, Top categories, Revenue by state, etc.)

    ## Key Requirements
    - Use Plotly for all charts
    - Filter update charts correctly
    - Professional styling with trend arrows/colors
    ```

- **模式四：端到端“设计到代码” (Design-to-Code)**
  - **场景**：从一个视觉设计稿（如 Figma）完整构建一个应用。
  - **核心思想**：分两步走，先利用 MCP 进行“视觉复刻”，再通过自主研究 API 实现“数据注入”，将设计、实现、验证、数据绑定全流程委托给 AI。
  - **Prompt 模板 (Lesson 8)**
    ```
    Using the figma mockup link [paste link], use the figma dev MCP server to build the UI in this Next.js application. Use the recharts library for charts. Then, use the playwright MCP server to verify the implementation visually against the mockup.
    ```
    **后续指令:**
    ```
    Populate these charts with real-world data from the FRED API.
    ```
