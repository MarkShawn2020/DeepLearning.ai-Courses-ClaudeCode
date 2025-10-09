> 一个强大的 AI 编程助理，其价值绝不应局限于本地的单机开发。真正的工程实践是协作的、流程化的，发生在像 GitHub 这样的平台上。本期，我们将把 Claude Code 从个人终端的得力助手，提升为融入团队协作流程的自动化“虚拟队友”。

欢迎来到吴恩达 Claude Code 笔记第七期。我是手工川。

上一期，我们通过 `git worktree` 解决了在本地并行开发时多个 Claude Code 实例互相干扰的问题，实现了个人开发效率的飞跃。但这主要还是在优化“单兵作战”的体验。现代软件开发的核心是团队协作，而 GitHub 正是这个协作宇宙的中心。

一个很自然的问题是：我们的 AI 助手，能否走出本地终端，无缝地融入到 Pull Request 审查、Issue 修复这些核心的团队协作环节中去？

本期课程，Elie Schoppik 老师就为我们完整地展示了这幅蓝图。我们将学习如何将 Claude Code 与 GitHub 深度集成，并探索其更高级的定制化能力——Hooks 系统，从而实现从宏观的 CI/CD 流程到微观的工具执行环节的全方位自动化。

### 本期要点 (Key Insights)

1.  **GitHub 集成**：学习如何通过 `/install-github-app` 命令，将 Claude Code 作为一款 GitHub App 安装到仓库中，使其具备监听和响应仓库事件的能力。
2.  **自动化代码审查 (PR Review)**：了解集成后生成的 GitHub Actions 工作流，如何让 Claude 机器人自动为新的 Pull Request 提供代码分析、质量检查和安全建议。
3.  **远程任务指派 (Issue Fixing)**：掌握在 GitHub Issue 中直接 `@claude`，指派它修复 Bug 或实现功能。Claude 会自动分析问题、修改代码、并创建一个新的 PR 来解决该 Issue。
4.  **Hooks 系统**：初探 Claude Code 的高级定制功能 Hooks。理解如何通过 `PreToolUse` 和 `PostToolUse` 等钩子，在工具执行前后注入自定义的脚本，实现更精细的工作流自动化。

### 手工川笔记

这一期也有很多惊喜。

作为一名被 github 喂大的男人，说实话，挺惭愧的，对 github 的探索也仅仅牛毛而已。

![source: https://github.com/MarkShawn2020，欢迎follow~](https://poketto.oss-cn-hangzhou.aliyuncs.com/2bd2c8fb56b3de06ab48f46d398046e7.png?x-oss-process=image/quality,q_90/rotate,0)

我印象很深刻的是，前几年我经常使用的一个开源库 wechaty，其技术负责人卓桓兄很早就引入了 ai bot，帮助 review 大家的 issue，后面又引入到了他们的 discord 社区。

![wechaty dosubot 示例](https://poketto.oss-cn-hangzhou.aliyuncs.com/54147b6b22df71e4e1e44668cae5be5b.png?x-oss-process=image/quality,q_90/rotate,0)

这一期，在 Elie 老师的带领下，我们可以看到，原来在自己的 github 仓库上植入一个 ai bot 是这么 so easy 的事，甚至可以让它自动地在云端改代码，怪不得云 IDE 的估值现在真地是水涨船高，程序员真地越来越危，玩法越来越花。

至于第二个 part 的 claude code hooks，这也是一个非常有用的功能，在我们的手工川自研插件 [ccm(claude-code-manager)](https://github.com/markshawn2020/claude-code-manager) 里很早地就支持了 post-tool-use hook，以支持实时的 token 统计。

![ccm 中关于post-tool-use的一些代码](https://poketto.oss-cn-hangzhou.aliyuncs.com/3407992d6d5384b19fa441ea23bd321d.png?x-oss-process=image/quality,q_90/rotate,0)

btw，昨天学完 [第六期（CC + git worktrees）](https://mp.weixin.qq.com/s/_4oPcqy-vcQWcsAOO4DKZA) 教程后，觉得非常有用，所以当天晚上就兴奋地集成到了 ccm 里，大家可以尝试体验。

```ad-note CCM 2.4.1 重磅更新

本版本新增 ccm feat - Git Worktree 管理功能

  ccm feat add payment  # 创建特性分支
  ccm feat list        # 交互式选择(可删除)
  ccm feat merge       # 合并完成的特性

✨ 支持并行开发多个特性，互不干扰
📦 更新：npm update -g claude-code-manager
```

## 从本地收尾到云端部署

课程开始，我们首先延续了上一期的工作，做了一些清理。我们之前使用 `git worktree` 创建了多个工作区，但在合并后忘记了清理。这里我们学习了一个新技巧：使用 `claude --resume` 命令可以列出并恢复之前的会话，非常方便。

![会话列表](https://poketto.oss-cn-hangzhou.aliyuncs.com/ef3ab82e6a280dcc5d85b866a1e175d9.png?x-oss-process/image/quality,q_90/rotate,0)

我们让 Claude 清理了 `.trees` 文件夹和相关的 Git 分支，然后将所有合并后的代码推送到了 GitHub 远程仓库。至此，本地的工作告一段落，我们的舞台正式转向云端。

![推送 github](https://poketto.oss-cn-hangzhou.aliyuncs.com/d4e11586ecbd8878bb64a9fddcde5712.png?x-oss-process/image/quality,q_90/rotate,0)

## 迎接新队友：集成 Claude Code GitHub App

要让 Claude Code 在 GitHub 上“活”起来，我们需要将其作为一款 GitHub App 安装到我们的仓库中。这个过程通过一条简单的命令即可启动：

```bash
/install-github-app
```

![/install-github-app](https://poketto.oss-cn-hangzhou.aliyuncs.com/0dea1c62dc13c355223998b779567245.png?x-oss-process/image/quality,q_90/rotate,0)

这个命令会引导我们完成一系列的授权流程，包括 GitHub CLI 的认证和 Claude 服务的授权。

![github + claude](https://poketto.oss-cn-hangzhou.aliyuncs.com/b331081bbb7c07b00cfc640ba8e090d1.png?x-oss-process/image/quality,q_90/rotate,0)

安装完成后，最核心的变化是 Claude Code 会在我们的仓库中创建一个 `.github/workflows/` 目录，并自动生成两个 GitHub Actions 工作流文件：`claude.yml` 和 `code-review.yml`。

```ad-tip {TITLE: "GitHub Actions"}
GitHub Actions 是 GitHub 提供的持续集成和持续部署（CI/CD）服务。它允许你在 GitHub 仓库中自动化你的软件开发工作流。你可以创建自定义的工作流（Workflows），在仓库发生特定事件（如 `push`, `pull_request`）时，自动执行一系列任务（Jobs），例如构建、测试、打包和部署代码。这些工作流由 YAML 文件定义，存放在 `.github/workflows/` 目录下。
```

这两个 YAML 文件，实际上就是我们新入职的“AI 队友”的行动指令集：

- `code-review.yml`：定义了当有新的 Pull Request 被创建时，自动触发 Claude Code 进行代码审查的流程。
- `claude.yml`：定义了当在 Issue 或 PR 的评论中 `@claude` 时，触发 Claude Code 执行任务的流程。

值得注意的是，这些 YAML 文件是完全开放和可定制的。我们可以修改其中的 Prompt，来调整 Claude Code 审查代码时的关注点，或者限定它只对某些作者、某些分支的 PR 进行审查，提供了极高的灵活性。

完成安装并合并了包含这两个工作流文件的 PR 后，我们的 Claude Code 机器人就正式“上岗”了。

### 角色一：不知疲倦的代码审查员

为了测试效果，课程演示了合并这个安装 PR 的过程。我们立刻就看到，一个名为 "Claude" 的 GitHub Action 开始运行。

![claude bot 在 github 上正在 review 代码](https://poketto.oss-cn-hangzhou.aliyuncs.com/22176e7e629685266153462a46f5ecfe.png?x-oss-process/image/quality,q_90/rotate,0)

片刻之后，Claude 在 PR 页面留下了它的审查评论。评论内容结构清晰，包括了代码中做得好的地方以及一些潜在的改进建议。

在我看来，将 AI 作为自动化代码审查的第一道关卡，其价值巨大。它不仅能发现人类审查者可能忽略的细节问题，更重要的是，它建立了一个 **客观、一致、不知疲倦** 的审查标准。这可以极大地减轻团队中真人审查者的负担，让他们能更专注于业务逻辑、架构设计等更高层次的评审。

### 角色二：随叫随到的问题解决者

除了被动地审查 PR，我们还可以主动地给 Claude 分配任务。课程中模拟了一个场景：我们对之前版本中新增的页面 Header 不满意，想要恢复到旧版样式。

我们在 GitHub 上创建了一个 Issue，用自然语言详细描述了需求：

> The application has a new header... Let's go back to the old one. Make sure to keep the toggle theme but just make the header look like what it was before...

然后，在评论区，我们像召唤同事一样，简单地 `@claude` 并说了一句：`Claude, can you fix this for me?`

![可以直接在 github issue 里 @claude 安排肝活](https://poketto.oss-cn-hangzhou.aliyuncs.com/f2148d9d6d6b5efd6a9065d0757ad561.png?x-oss-process/image/quality,q_90/rotate,0)

这触发了 `claude.yml` 工作流。在 GitHub Actions 的日志中，我们可以看到一个熟悉的场景：Claude Code 开始了它的思考和规划过程，生成了一个 To-do list，这和我们在本地终端中看到的行为完全一致。

![claude bot 在github上肝活和日常一样，也会有todo list](https://poketto.oss-cn-hangzhou.aliyuncs.com/43fa5bc729075235a5edf790404381c0.png?x-oss-process/image/quality,q_90/rotate,0)

任务完成后，Claude 自动创建了一个新的 Pull Request，其中包含了解决该 Issue 所需的所有代码修改。更有趣的是，这个新 PR 同样触发了 Code Review 流程——**Claude 开始审查自己刚刚写的代码**。这种“自审”机制，为代码质量提供了又一层保障。

![claude bot 已经实现了需求](https://poketto.oss-cn-hangzhou.aliyuncs.com/6e4f235a087c0662c99a0159962044dc.png?x-oss-process/image/quality,q_90/rotate,0)

我们将这个 PR 合并，然后回到本地拉取最新的代码。刷新页面后，可以看到 Header 确实已经按要求恢复了旧版样式。整个流程从提出需求到代码合并，完全在 GitHub 上通过人机对话完成，这极大地改变了传统的问题处理工作流。

## 深入定制：初探 Hooks 系统

在课程的最后，Elie 老师介绍了一个更深层次的定制化功能：**Hooks（钩子）**。

![claude code cook 机制图解](https://poketto.oss-cn-hangzhou.aliyuncs.com/42a9c56c859ba26b669cd3b7675ed00d.png?x-oss-process/image/quality,q_90/rotate,0)

对于熟悉 Git Hooks 或 Webhooks 的开发者来说，这个概念会非常亲切。Hooks 允许我们在 Claude Code 内部生命周期的特定事件点，注入我们自己的代码或命令。

我们可以通过 `/hooks` 命令打开一个编辑器来管理这些钩子。

![/hooks](https://poketto.oss-cn-hangzhou.aliyuncs.com/c26aab5a73edf584912095be61d54791.png?x-oss-process/image/quality,q_90/rotate,0)

Claude Code 提供了多种可用的事件钩子，例如：

- `PreToolUse`：在某个工具即将被执行 **之前** 触发。
- `PostToolUse`：在某个工具执行完成 **之后** 触发。
- `OnUserSubmit`：当用户提交一个新的 Prompt 时触发。
- `BeforeSubagentResponse`：在子智能体返回响应之前触发。

为了演示这个功能，课程中创建了一个简单的 `PostToolUse` 钩子。它的作用是：**每当 `Read` 或 `Grep` 工具被使用后，就执行一条 `say 'All done!'` 的 Shell 命令**，让电脑语音播报“All done!”。

![在post-tool hook里实现电脑播报](https://poketto.oss-cn-hangzhou.aliyuncs.com/47ad678ba2e5ccad4c8673c4985a2411.png?x-oss-process/image/quality,q_90/rotate,0)

这个配置会被保存在 `.claude/settings.local.json` 文件中。

```json
{
  "permissions": { ... },
  "hooks": {
    "PostToolUse": [
      {
        "matcher": {
          "tool_name": {
            "$in": ["Read", "Grep"]
          }
        },
        "command": "say 'All done!'"
      }
    ]
  }
}
```

虽然 `say` 命令只是一个有趣的例子，但 Hooks 机制的潜力远不止于此。我们可以利用它来构建非常强大的自动化工作流：

- **自动化测试**：创建一个 `PostToolUse` 钩子，匹配 `Write` 或 `Edit` 工具。每当 AI 修改了代码文件后，自动运行相关的单元测试。
- **代码规范检查**：在 `PreToolUse` 钩子中匹配 `Bash(git: commit)`，在提交代码前自动运行 Linter 或 Formatter。
- **安全扫描**：在 `PostToolUse` 中匹配 `Bash(npm: install)`，每当安装了新的依赖后，自动运行 `npm audit` 进行安全漏洞扫描。

![](https://poketto.oss-cn-hangzhou.aliyuncs.com/910c31b0f6c663a889de8d7c4eb9e07c.png?x-oss-process=image/quality,q_90/rotate,0)

## 手工川结语

本期课程的内容，标志着我们对 Claude Code 的使用从“战术层面”进入了“战略层面”。

- **GitHub 集成**，是在 **宏观流程** 上实现了自动化。它将 AI 无缝嵌入了团队的 CI/CD 和协作流程中，解决了代码审查、问题修复等流程性、协作性的任务。
- **Hooks 系统**，则是在 **微观执行** 上实现了自动化。它允许我们精细地控制 AI 在执行每一个具体工具前后的行为，将我们的个人工作流、项目的特定规范，注入到 AI 的每一次操作中。

将这两者结合，我们实际上是在构建一个高度定制化、全流程自动化的“可编程开发环境”。在这个环境中，AI 不再仅仅是响应我们指令的工具，而是遵循我们预设的规则和流程，主动、可靠地执行任务的系统。开发者作为这个系统的设计者和编排者，其工作效率和对项目质量的把控能力都将得到质的提升。

在下一课，我们将把目光转向数据科学领域，探索 Claude Code 如何与 Jupyter Notebook 结合，进行数据可视化和代码重构。
