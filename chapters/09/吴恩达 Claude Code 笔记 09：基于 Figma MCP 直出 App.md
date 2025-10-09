


> “Design to Code”——这个口号在软件开发领域回响了十余年，无数工具尝试搭建从设计师的创意到工程师代码之间的桥梁，但往往收效甚微。现在，AI Agent 的出现，似乎第一次让我们看到了实现这一梦想的曙GIT。本期，我们将见证 Claude Code 作为这座桥梁的构建者，完成从设计到产品的惊人一跃。

欢迎来到《吴恩达 Claude Code 笔记》的第九期，也是我们课程解读系列的最后一期。我是手工川。

经历了前面八期的学习和实践，我们已经从基础的代码理解、功能开发，一路走到了测试驱动调试、并行开发、乃至云端 GitHub 流程自动化。我们手中的 Claude Code，其形象也从一个“代码补全工具”，逐渐成长为一个能够深度参与软件工程全生命周期的“智能体伙伴”。

今天，我们将迎来本系列课程的终极实战项目，一个足以被称为“毕业设计”的挑战：**完全从零开始，仅依据一份 Figma 设计稿，构建一个功能完备、接入真实数据的 Next.js 全栈应用。**

这不仅仅是一次对 Claude Code 综合能力的全面检验，更是一次对未来 AI 原生开发工作流的深刻预演。

### 本期要点 (Key Insights)

1.  **AI 的“眼睛”与“手”**：深入理解 MCP (Model Context Protocol) 服务器的核心价值，看 Claude Code 如何通过连接 Figma MCP Server“看见”设计稿，并通过连接 Playwright MCP Server“验证”自己的开发成果。
2.  **两阶段开发范式**：掌握从“视觉复刻”到“功能实现”的两步走开发流程。第一步，AI 专注于将设计稿转化为高质量的前端组件代码；第二步，AI 通过自主研究 API 文档，为静态页面注入真实的数据灵魂。
3.  **开发者的角色演变**：在本工作流中，开发者不再是代码的编写者，而是需求的定义者、工具链的配置者、以及 AI 工作成果的验收者，真正成为一名“AI 开发工作流的架构师”。
4.  **全链路能力整合**：本次实战是前序所有课程知识的集大成者，综合运用了 Agentic 规划、工具使用（Tool Use）、Web 搜索、文件操作等多种核心能力。

### 手工川笔记

“Design to Code”的承诺，我听了不下十年。从早期的 Photoshop 插件，到后来的 Sketch、Zeplin、Avocode，再到 Figma 自己的代码生成功能，每一代工具都在努力缩短设计与开发之间的距离。但它们大多停留在“样式翻译”的层面——将设计元素的 CSS 属性提取出来，生成的代码往往缺乏结构性、可维护性差，离真正的生产代码相去甚远。

本期课程所展示的工作流，我认为代表了一种根本性的范式转变。AI Agent 的介入，让“Design to Code”**从“翻译”升级为了“理解与创造”**。

这背后的关键，正是 **MCP (Model Context Protocol)**。如果说 Claude Code 是一个聪明的大脑，那么 MCP 就是为这个大脑接上了“感官”和“四肢”的神经接口。通过 Figma MCP，它获得了“视觉”，能够理解设计稿的布局、组件和设计语言；通过 Playwright MCP，它获得了与浏览器“交互”的能力，可以像人一样打开页面、截图、验证 UI。

当一个 AI 同时拥有了“视觉”、“交互能力”和强大的“代码生成逻辑”，它就不再是一个被动的翻译器了。它成为了一个能够**看懂需求、动手实现、并自行检验**的初级前端工程师。而我们，则成为了它的“产品经理”和“技术总监”。这，就是未来。

## 环境搭建与“感官”连接

我们的终极项目，目标是复刻一个展示美国联邦储备经济数据（FRED）的仪表盘。起点，只有一份 Figma 设计稿。

![目标 figma 工程界面](https://poketto.oss-cn-hangzhou.aliyuncs.com/cb9d9eb09861263dbd5542a385d3bb1f.png?x-oss-process/image/quality,q_90/rotate,0)

### 项目初始化

我们首先在本地创建一个空的 Next.js 项目，这将是我们应用的基础骨架。

```bash
npx create-next-app@latest .
```

![使用nextjs初始化项目](https://poketto.oss-cn-hangzhou.aliyuncs.com/fce2025404ca9d907d2c52b9c3780e3b.png?x-oss-process/image/quality,q_90/rotate,0)

### 连接 MCP 服务器

接下来是至关重要的一步：为 Claude Code 接上“眼睛”和“手”。

1.  **连接 Figma (眼睛)**：课程中介绍了两种连接方式。
    *   **Figma 官方 MCP Server**：需要在 Figma 桌面应用的偏好设置中启用 `Enable Dev Mode MCP Server`。这需要在付费的 Pro 计划及以上才能使用。
    *   **Framelink MCP Server**：一个优秀的第三方免费替代方案，通过 Figma API Key 进行连接。

    我们在终端中使用 `claude mcp add` 命令，将 Figma MCP Server 添加到 Claude Code 的工具集中。

2.  **连接 Playwright (手/验证工具)**：我们同样使用 `claude mcp add` 命令，添加 Playwright MCP Server。

![项目增加 figma mcp](https://poketto.oss-cn-hangzhou.aliyuncs.com/d37d4cb2df691c89b2d45e80415c2b3a.png?x-oss-process/image/quality,q_90/rotate,0)

配置完成后，我们可以在 Claude Code 中使用 `/mcp` 命令，检查两个服务器是否都已成功连接。

![查看 mcp 列表](https://poketto.oss-cn-hangzhou.aliyuncs.com/76c4e9ced5fc43f785f985853d074d3d.png?x-oss-process/image/quality,q_90/rotate,0)

## 从设计稿到静态 UI 的“视觉复刻”

环境就绪，大戏开场。我们向 Claude Code 发出了第一个核心指令。

![prompt：cc + figma-mcp](https://poketto.oss-cn-hangzhou.aliyuncs.com/02da78ebb7f6464bd44e8219fc9ae94f.png?x-oss-process/image/quality,q_90/rotate,0)

这个 Prompt 的指令链条非常清晰：
1.  **输入源**：提供从 Figma 中复制的设计稿图层链接。
2.  **分析工具**：明确要求使用 `figma dev MCP server` 来分析它。
3.  **技术栈**：指定在 Next.js 应用中，使用 `recharts` 库来创建图表。
4.  **验证工具**：要求使用 `playwright MCP server` 来检查最终成果与设计稿的相似度。

为了应对这个复杂的任务，课程中建议将模型切换到能力更强的 `Opus`。

Claude Code 接收指令后，它的 Agentic 工作流启动了：
1.  **调用 Figma MCP**：使用 `Get_image` 和 `Get_Code` 工具，“看懂”了设计稿的视觉样式和基础代码。
2.  **代码实现**：在 Next.js 的 `app/` 目录下，开始创建符合 React 规范的、组件化的页面代码。
3.  **调用 Playwright MCP**：在初步完成后，它启动 Playwright，打开 `localhost:3000`，截取一张当前页面的快照，用于和原始设计稿进行对比。

片刻之后，我们看到了初步的成果。令人印象深刻的是，AI 生成的页面不仅在布局和样式上高度还原了设计稿，甚至在一些细节上（如柱状图的渐变效果）比原始设计稿还要精致一些。

![cc 已经复刻了目标 figma（甚至效果更好）](https://poketto.oss-cn-hangzhou.aliyuncs.com/bea5dbd2f2da2faa8bdb70a9aa414140.png?x-oss-process/image/quality,q_90/rotate,0)

## 从静态 UI 到动态应用的“灵魂注入”

一个漂亮的“空壳”已经完成，接下来是注入灵魂——真实数据。我们向 Claude Code 发出了第二个指令：

> populate these charts with real-world data from FRED

这个看似简单的指令，触发了一系列复杂的、真正体现 AI Agent 智能的行为：
1.  **自主研究**：Claude Code 首先使用 `WebSearch` 工具，去搜索“FRED API”，找到了官方文档。
2.  **识别依赖**：通过阅读文档，它意识到调用该 API 需要一个 API Key。
3.  **请求输入**：它暂停了任务，并向我们（用户）请求提供 FRED API Key。
4.  **编写服务**：在我们提供了 Key 之后，它编写了一个新的 `services/fredApi.js` 文件，封装了所有与 FRED API 交互的数据请求逻辑。
5.  **连接前后端**：它修改了之前的 React 组件，用 `useEffect` 和 `useState` 等 React Hooks，在组件加载时调用 API 服务，获取真实数据，并更新图表状态。

![确认 Fred API Key](https://poketto.oss-cn-hangzhou.aliyuncs.com/3f89175ee96e84813134ef8ddaae2fd6.png?x-oss-process/image/quality,q_90/rotate,0)

这个过程完美地模拟了一个人类工程师的工作流程：接到需求 -> 查阅资料 -> 发现前置条件 -> 请求资源 -> 编写代码 -> 集成调试。

![](https://poketto.oss-cn-hangzhou.aliyuncs.com/0a856dcd4d84cb30e4173e19f9bf7200.png?x-oss-process=image/quality,q_90/rotate,0)


最终，我们刷新浏览器，仪表盘上显示的不再是静态的占位符，而是来自美国联邦储备数据库的、实时更新的经济指标。在短短几分钟内，我们从一份静态的设计图，得到了一个美观、交互式且由真实数据驱动的全栈 Web 应用。

## 一个时代的落幕，一个时代的开启

随着这个终极项目的完成，我们对吴恩达与 Anthropic 这门课程的解读也走到了尾声。

回顾这九期的旅程，我们不仅仅是学会了如何使用一个新工具，更是亲身经历了一次开发思想的变革。我们从最基础的文件操作开始，逐步掌握了测试驱动、并行开发、GitHub 协作、Notebook 重构，直到今天，我们亲手“导演”了一出从设计创意到软件产品的全流程 AI 大戏。

课程的总结言简意赅，却道出了与 Agentic AI 协作的精髓：**提供清晰的指令，明确的上下文，并指向相关的文件**。这背后，是我们开发者角色的转变——从代码的“生产者”，变为 AI 工作流的“编排者”。

AI 编程的时代已经到来，但这并不意味着程序员的黄昏。恰恰相反，它将我们从繁琐、重复的底层实现中解放出来，让我们能更专注于软件的架构、用户的体验和创意的实现。世上无难事，只要有 Claude。

感谢 **Elie Schoppik** 老师的精彩讲解，也感谢各位读者的一路相伴。虽然课程解读到此结束，但 AI 辅助开发的探索之旅，才刚刚开始。在接下来的文章中，我将脱离课程本身，分享一些我**个人在使用 Claude Code 过程中的最佳实践**，以及对这一系列**搬运工作流的复盘总结**，敬请期待。

![完美，撒花，感谢Elie老师](https://poketto.oss-cn-hangzhou.aliyuncs.com/ddcf13ea1db81c84139c7f2851e32cb8.png?x-oss-process=image/quality,q_90/rotate,0)

---

## Appendix

### 课程官方资源

*   **课程项目源码 (Final Project Source Code):**
    *   本期课程最终完成的 FRED 仪表盘应用，其完整的 Next.js 源代码都可以在这里找到，是学习和参考的绝佳范例。
    *   [https://github.com/https-deeplearning-ai/FRED-dashboard](https://github.com/https-deeplearning-ai/FRED-dashboard)

*   **课程官方文件与 Prompt (Official Course Files & Prompts):**
    *   DeepLearning.AI 官方提供的、涵盖**本系列所有课程**的配套文件、数据和完整的 Prompt 文本。如果你想 1:1 复现课程中的任何一个环节，这里是你的“宝库”。
    *   [https://github.com/https-deeplearning-ai/sc-claude-code-files](https://github.com/https-deeplearning-ai/sc-claude-code-files)

*   **DeepLearning.AI 课程主页 (DeepLearning.AI Course Homepage):**
    *   观看原版视频课程，体验 Elie Schoppik 老师的亲自教学。
    *   [https://learn.deeplearning.ai/courses/claude-code-a-highly-agentic-coding-assistant](https://learn.deeplearning.ai/courses/claude-code-a-highly-agentic-coding-assistant)

### 关键指令与 Prompt

#### 1. 项目初始化

```bash
# 在你的项目目录中执行
npx create-next-app@latest .
```

#### 2. 配置 MCP 服务器

```bash
# 添加 Figma 官方 Dev Mode MCP Server
claude mcp add --transport http figma-dev-mode-mcp-server http://127.0.0.1:3845/mcp

# 添加 Playwright MCP Server
claude mcp add playwright npx @playwright/mcp@latest
```

#### 3. 核心 Prompt

*   **第一阶段：视觉复刻**
    *   *注意：在 Figma 桌面应用中选中目标图层后，按 `Cmd + L` (Mac) 或 `Ctrl + L` (Windows) 复制图层链接，替换到 Prompt 中。*
    ```
    Using the following figma mockup (在此处粘贴你的 Figma 链接) use the figma dev MCP server to analyze the mockup and build the underlying code in this next.js application. Use the recharts library for creating charts to make this a web application. Check how this application looks using the playwright MCP server and verify it looks as close to the mock as possible.
    ```

*   **第二阶段：数据注入**
    *   *注意：执行此 Prompt 前，请先前往 [FRED 官网](https://fred.stlouisfed.org/docs/api/api_key.html) 申请你自己的 API Key。*
    ```
    populate these charts with real-world data from FRED
    ```

### Figma MCP 备选方案

如果你的 Figma 账户不是付费的 Professional Plan 或更高版本，无法使用官方的 Dev Mode MCP Server，可以使用由社区提供的 Framelink Figma MCP Server 作为免费替代方案。

*   **配置 Framelink MCP Server:**
    *   *注意：将 `YOUR-KEY` 替换为你自己的 Figma API Key。*
    ```bash
    claude mcp add "Framelink Figma MCP" -- npx -y figma-developer-mcp --figma-api-key=YOUR-KEY --stdio
    ```