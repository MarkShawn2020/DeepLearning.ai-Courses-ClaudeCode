
欢迎来到我们的新系列，由我们（手工川）为大家搬运并解读来自 DeepLearning.AI 与 Anthropic 官方合作的课程——**Claude Code: A Highly Agentic Coding Assistant**。


![](https://poketto.oss-cn-hangzhou.aliyuncs.com/202508151313500.png?x-oss-process=image/resize,w_800/rotate,0)






本系列旨在将这门顶尖课程的内容，以更符合中文读者习惯的方式呈现出来。我们将严格遵循专业、严谨的原则，对内容进行重组和精炼，并补充必要的图表以辅助理解。

今天，让我们从课程的开篇开始，由吴恩达和 Anthropic 的 Elie Schoppik 为我们揭开 **Claude Code** 的神秘面纱。

![](https://poketto.oss-cn-hangzhou.aliyuncs.com/202508151314093.png?x-oss-process=image/resize,w_800/rotate,0)

## 你将学到什么？

在本系列课程中，你将系统地掌握使用 **Claude Code** 的核心技能与最佳实践：

*   **探索与开发：** 学会使用 **Claude Code** 来探索、开发、测试、重构和调试代码库。
*   **能力扩展：** [通过 MCP 服务器（如 Playwright 和 Figma）来扩展 Claude Code 的核心能力](https://www.deeplearning.ai/short-courses/claude-code-a-highly-agentic-coding-assistant/?utm_campaign=anthropicC3-launch&utm_medium=headband&utm_source=dlai-homepage#course-outline)。
*   **项目实战：** 将 **Claude Code** 的最佳实践应用于三个真实项目中：
    1.  探索和开发一个 RAG 聊天机器人的代码库。
    2.  重构一个用于电子商务数据分析的 Jupyter notebook，并将其转化为一个交互式仪表盘。
    3.  基于一个 Figma 设计稿，从零开始构建一个 Web 应用。

## 关于本课程

AI 编码助理正经历飞速的演进。从最初偶尔回答编程问题、提供代码补全，到如今能够自主生成和执行代码，工具的智能体化（Agentic）程度越来越高。

**Claude Code** 在这条路上迈出了关键一步，它不再是一个被动的工具，而是一个高度智能体的编程助理。它能够独立地进行规划、执行和代码优化，整个过程可持续数分钟甚至更久，且仅需少量的人工介入。更强大的是，你和你的团队现在可以同时运行多个 **Claude Code** 实例，并行处理代码库的不同部分。然而，要高效地协调这一切，需要一套尚未普及的最佳实践。

### 核心理念：提供清晰的上下文

本课程的核心，是教会你如何通过提供清晰的上下文，来最大化 **Claude Code** 的效率。关键技巧包括：

*   **明确范围：** 精准指定相关文件。
*   **定义目标：** 清晰描述所需的功能和特性。
*   **善用生态：** [通过 MCP 服务器等工具连接外部能力](https://www.deeplearning.ai/short-courses/claude-code-a-highly-agentic-coding-assistant/?utm_campaign=anthropicC3-launch&utm_medium=headband&utm_source=dlai-homepage#course-outline)。

### Claude Code 的架构与记忆机制

你可能会对 **Claude Code** 的底层架构感到惊讶——它的设计出奇的简洁。

它不依赖于将代码库进行复杂的语义嵌入或构建可搜索的索引。相反，它通过一小组核心工具（如文件搜索、目录列表、正则表达式匹配）来智能地阅读和理解你的代码。这种方法的优势在于，**你的代码库可以完全保留在本地**，确保了安全性。

**Claude Code** 的一个独特之处在于它会**主动地**在你的代码库中创建一个名为 `CLAUDE.md` 的文件。它像一个工作笔记，用来记录它对代码库的理解、关键信息和指导方针，从而实现跨会话的记忆。

![](https://poketto.oss-cn-hangzhou.aliyuncs.com/202508151332231.png?x-oss-process=image/resize,w_800/rotate,0)


## 适合人群

本课程非常适合任何希望探索 AI 编码助理以提升开发效率的开发者。无论你是正在构建应用、调试代码，还是探索不熟悉的代码库，你都将学到与 AI 协同工作的实用技能。

如果你熟悉 **Python** 和 **Git**，将会获得最佳的学习效果。

## 课程大纲

整个课程共包含 10 个核心视频课程，以及配套的测验与学习资料。

*   **入门**
    1.  `课程介绍` (视频・4 分钟)
    2.  `什么是 Claude Code？` (视频・8 分钟)
*   **核心功能与实践**
    3.  `环境设置与代码库理解` (视频・14 分钟)
    4.  `添加新功能` (视频・17 分钟)
    5.  `测试、错误调试与代码重构` (视频・12 分钟)
*   **高级工作流**
    6.  `同时添加多个功能` (视频・11 分钟)
    7.  `Github 集成与 Hooks 探索` (视频・10 分钟)
*   **项目实战**
    8.  `重构 Jupyter Notebook 并创建仪表盘` (视频・12 分钟)
    9.  `基于 Figma 设计稿创建 Web 应用` (视频・9 分钟)
*   **总结**
    10. `课程总结、测验与 Prompt 合集`

## 讲师介绍

**Elie Schoppik**



*   **Anthropic 技术教育主管**
*   前 Firebase 开发者关系工程师，拥有丰富的开发者生态建设与技术布道经验。


---

### 手工川结语

以上就是吴恩达与 Anthropic 官方课程的第一期内容。它清晰地描绘了 **Claude Code** 作为一款高度智能体化编程助理的定位、核心优势以及我们即将通过本系列学习到的内容。

从下一期开始，我们将深入探讨 **Claude Code** 的具体工作机制，并开始第一个实战项目。请保持关注！

