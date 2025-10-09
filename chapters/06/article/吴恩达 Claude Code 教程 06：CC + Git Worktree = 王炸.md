> 这几个月我大量地使用 claude code 开发各种项目，也曾在同一个项目里启动多个 cc 实现不同的需求，经常碰到多个cc在改写文件时互相打架的问题。在学习本教程之前，我一直都是裸开N个cc让它们野蛮生长，而[上周我们的Vibe Seminar](https://mp.weixin.qq.com/s/jlDHxq4cCV-hn-tIS9I5fw)上甚至就这个问题提出了某种**文件锁**机制。
> 
> 但事实上，最佳实践是使用 `git worktree`，这是一种为当前工作区创建额外视图的技术，允许我们在同一个目录但不同的git环境里并行开发，最后一起合并。听起来很复杂，**对于新手来说，合并冲突更是一件极其头疼的事情**。但现在，是AI时代，世上无难事，只要有CC。
> 
> 本期教程，进阶必看，I mean it。

欢迎来到《吴恩达 x Anthropic：Claude Code 终极教程》的第六期。我是手工川。

在前面的课程中，我们已经体验了 Claude Code 在单个任务流中的强大能力，无论是实现新功能还是进行复杂的代码重构。但真实的开发场景往往更加复杂，我们经常需要同时处理多个不相关的任务：修复一个紧急 Bug、开发一个新功能、优化 CI/CD 流程等等。

传统的线性工作流在这种情况下会显得捉襟见肘。如果我们为每个任务都切换分支，不仅操作繁琐，而且难以在不同任务间快速预览和测试。如果直接在同一个分支上操作，又极易导致代码混乱和相互覆盖。

本期课程，Elie Schoppik 老师将为我们介绍一套旨在解决此问题的工程实践：**通过 Git Worktree 结合 Claude Code 的多会话能力，实现真正的并行开发**。同时，我们还将学习如何创建自定义的斜杠命令 (`/command`)，将高频操作封装起来，进一步优化我们的工作流。

### 本期要点 (Key Insights)

1.  **自定义命令**：学习在 `.claude/commands/` 目录下创建自定义的 Markdown 命令，通过 `$ARGUMENTS` 变量接收参数，实现工作流自动化。
2.  **Git Worktree 的核心价值**：理解 `git worktree` 如何允许我们在同一个仓库中同时检出多个工作目录，为并行开发提供物理隔离，从根本上避免文件覆盖问题。
3.  **并行开发工作流**：掌握从创建 Worktree、在隔离环境中运行独立的 Claude Code 会话，到最终合并成果的完整流程。
4.  **AI 辅助解决合并冲突**：观察 Claude Code 如何在合并不同 Worktree 的代码时，自动分析并解决冲突，展示其在处理复杂 Git 操作时的能力。

## 提升效率的第一步：自定义斜杠命令

在深入并行开发之前，课程首先介绍了一个非常实用的功能：创建自定义斜杠命令。

我们已经熟悉了 `/ask`, `/edit` 等内置命令。Claude Code 允许我们通过在项目根目录下的 `.claude/commands/` 文件夹中创建 Markdown 文件来定义自己的命令。文件名即命令名。

例如，为了封装一个“实现前端功能”的流程，我们可以创建一个 `implement-feature.md` 文件：

![截图：/implement-feature 命令](https://poketto.oss-cn-hangzhou.aliyuncs.com/c332e0100fc758372c9b7fa1453b81bc.png?x-oss-process=image/quality,q_90/rotate,0)

这个命令文件的内容是一个 Prompt 模板，其中有几个关键点：

- `$ARGUMENTS`：这是一个特殊的变量，它会捕获用户在命令后输入的所有文本。例如，当用户输入 `/implement-feature 添加一个主题切换按钮` 时，`$ARGUMENTS` 的值就是 `添加一个主题切换按钮`。
- **指令约束**：我们可以加入明确的指令，比如 `IMPORTANT: Only do this for front-end features`，来约束 AI 的行为。
- **自动化流程**：可以定义一系列固定的操作，比如 `write the changes you made to file called frontend-changes.md`，将重复性工作自动化。

```ad-tip {TITLE: "自定义命令 vs. CLAUDE.md"}

`CLAUDE.md` 文件中的内容会在 **每次** 启动 Claude Code 会话时自动加载到上下文中，它适合存放项目级的、全局性的背景信息和高频指令。

而 `.claude/commands/` 中的自定义命令则 **不会** 自动加载。它们只有在被用户显式调用时才会生效。这种设计非常适合封装那些非全局、特定场景下才会使用的工作流。
```

课程中，Elie 老师还演示了一个常见操作：让 Claude Code 自行提交代码变更。

![截图：让 cc 自己 commit](https://poketto.oss-cn-hangzhou.aliyuncs.com/a6f23a05365d18543e84acde475113ea.png?x-oss-process/image/quality,q_90/rotate,0)

这个 `add and commit changes made` 的 Prompt 确实很实用。我的思考是，对于像 `commit` 这样高频且有固定规范的操作，将其封装成一个强大的自定义命令会是更好的选择。这让我想起了我去年花了不少时间打磨的一个自动化 commit 工具 [oh-my-commit](https://github.com/oh-my-commit/oh-my-commit)，它支持 Conventional Commits 规范，并提供了 VS Code 插件。虽然现在基于 Claude Code 的无界面开发模式越来越主流，但我认为一个好的 commit 系统，尤其是在与 CI/CD 集成时，价值依旧。因此，我基于课程的启发，设计了一个更完备的 `/git-add-commit` 命令（详见文末附录），它能自动分析代码变更、遵循 Conventional Commits 风格并生成中文信息。

此外，为了避免每次执行 `git` 等命令时都弹出授权确认，我们可以在 `.claude/settings.local.json` 文件中配置命令白名单，实现真正的自动化。

![截图：配置放行命令](https://poketto.oss-cn-hangzhou.aliyuncs.com/b915e36af835640c4c2f8585402b2a58.png?x-oss-process/image/quality,q_90/rotate,0)

## 并行开发的基石：Git Worktree

现在，我们来解决核心问题：如何同时在同一个代码库上安全地进行多项开发任务？

直接打开多个终端窗口，在同一个分支上运行多个 Claude Code 实例，几乎必然会导致灾难。当两个实例试图修改同一个文件时，后保存的会覆盖先保存的，造成代码丢失和逻辑混乱。

Git 提供了完美的解决方案：`worktree`。

```ad-tip {TITLE: "Git Worktree"}

`git worktree` 是一个 Git 命令，它允许你将仓库的多个分支同时检出到文件系统上的不同目录中。每个目录都是一个独立的、功能齐全的工作区，拥有自己的工作文件、暂存区和分支状态，但它们共享同一个底层的 `.git` 数据库。

这与 `git clone` 不同。`clone` 会创建一个全新的、独立的仓库副本。而 `worktree` 只是创建了多个“视图”或“工作台”，它们都指向同一个中央仓库。这使得它非常轻量，且便于在不同任务之间共享提交和对象。
```

### 实践流程：创建并行工作环境

![](https://poketto.oss-cn-hangzhou.aliyuncs.com/21a672ef92f20794b3c2d7649d56e360.png?x-oss-process=image/quality,q_90/rotate,0)


课程中，我们通过以下步骤建立了并行开发环境：

1.  **创建 Worktree 目录**：首先，创建一个用于存放所有 Worktree 的文件夹，例如 `.trees`，并将其加入 `.gitignore`。
2.  **添加 Worktree**：针对每一项开发任务，使用 `git worktree add` 命令创建一个新的工作目录。每个 Worktree 都会自动基于 `main` 分支创建一个同名的新分支。

    ```bash
    # 任务1: UI 功能开发
    $ git worktree add .trees/ui_feature

    # 任务2: 测试框架增强
    $ git worktree add .trees/testing_feature

    # 任务3: 代码质量工具集成
    $ git worktree add .trees/quality_feature
    ```

执行后，我们的项目结构会如下图所示：


![](https://poketto.oss-cn-hangzhou.aliyuncs.com/5a79f343992c27fb84b798f882522c8e.png?x-oss-process=image/quality,q_90/rotate,0)



现在我们有了三个物理隔离但共享 Git 历史的工作区。接下来，我们为每个 Worktree 目录打开一个独立的终端窗口，并分别启动 Claude Code 会话。

### 并行执行三项任务

我们在三个并行的会话中，分别给 Claude Code 分配了不同的任务：

1.  **UI Feature (位于 `.trees/ui_feature`)**：
    - **任务**：使用我们刚创建的 `/implement-feature` 命令，添加一个亮色/暗色主题切换按钮。
    - **Prompt**：`/implement-feature Toggle Button Design - Create a toggle button...`
2.  **Testing Feature (位于 `.trees/testing_feature`)**：
    - **任务**：增强现有的测试框架，为 FastAPI 端点添加 API 测试。
    - **Prompt**：`Enhance the existing testing framework for the RAG system...`
3.  **Quality Feature (位于 `.trees/quality_feature`)**：
    - **任务**：集成 `black` 代码格式化工具，并创建运行质量检查的脚本。
    - **Prompt**：`Add essential code quality tools to the development workflow...`


![截图：三个worktrees均已开始工作](https://poketto.oss-cn-hangzhou.aliyuncs.com/078b22a842001d4eee02d25b4d5603c4.png?x-oss-process/image/quality,q_90/rotate,0)


我观察到一个细节：Elie 老师只在第一个 UI 任务中使用了自定义的 `/implement-feature` 命令。这可能是因为后两个任务更多是工程配置而非狭义的“功能”开发。

这三个 Claude Code 实例开始并行工作。它们各自修改文件、安装依赖。值得注意的是，**任务 2（测试）和任务 3（代码质量）都需要修改 `pyproject.toml` 这个配置文件**。由于它们在不同的 Worktree 中操作，因此不会发生实时覆盖。这个潜在的冲突被推迟到了最后的合并阶段。

## 整合成果：合并与冲突解决

当所有任务在各自的 Worktree 中完成后，我们为每个 Worktree 的变更分别创建了 commit。

```bash
# 在 .trees/ui_feature 终端中
claude> add and commit with a descriptive message

# 在 .trees/testing_feature 终端中
claude> add and commit with a descriptive message

# 在 .trees/quality_feature 终端中
claude> add and commit with a descriptive message
```

现在，我们关闭这三个终端，回到主工作目录的终端，准备将所有成果合并到 `main` 分支。

我向 Claude Code 发出了一个总括性的指令，让它负责整个合并过程，并处理可能出现的任何冲突。

![截图：让 cc merge 所有 features](https://poketto.oss-cn-hangzhou.aliyuncs.com/0a70328439d019c2235153919fc35b09.png?x-oss-process/image/quality,q_90/rotate,0)

Claude Code 开始按顺序合并 `ui_feature`、`testing_feature` 和 `quality_feature` 分支。前两个合并很顺利。当合并 `quality_feature` 时，预期的冲突发生了——因为 `main` 分支（已经合并了 `testing_feature` 的变更）和 `quality_feature` 分支都修改了 `pyproject.toml` 文件。

此时，Claude Code 展现了它处理复杂工作流的能力。它检测到了合并冲突，并自动进入冲突解决模式。

![截图：cc自动处理merge冲突](https://poketto.oss-cn-hangzhou.aliyuncs.com/baf727d0751c3518001b1747b6c0bde6.png?x-oss-process/image/quality,q_90/rotate,0)

它分析了 `pyproject.toml` 文件中的冲突标记，理解了双方的修改意图（一方添加了 `pytest` 配置，另一方添加了 `black` 配置），然后智能地将两部分配置合并到了一起，生成了一个正确的、无冲突的文件版本。最后，它自动完成了合并提交。

这个过程相当流畅。对于开发者来说，处理合并冲突，尤其是配置文件中的冲突，是一项繁琐且容易出错的任务。Claude Code 在这里的表现证明，AI 可以在版本控制的复杂环节中扮演可靠的助手角色。

![截图：cc已经处理完所有任务](https://poketto.oss-cn-hangzhou.aliyuncs.com/a822e67a59571678f802b8d2b8fa3760.png?x-oss-process/image/quality,q_90/rotate,0)

最终，我们在浏览器中验证，主题切换功能已经成功实现。至此，三项并行的开发任务全部完成并整合到了主分支中。

![截图：确认前端的主题切换功能已经实现](https://poketto.oss-cn-hangzhou.aliyuncs.com/8e1b87bda460a952b95cfccc212159c4.png?x-oss-process/image/quality,q_90/rotate,0)

## 手工川结语

本期课程的核心，是向我们展示了一套现代、高效的并行开发工作流。它并非由单一的某个工具构成，而是 **Claude Code 的多会话能力** 与 **Git Worktree 的隔离机制** 精妙结合的产物。

这个工作流的价值在于：

1.  **提升吞吐量**：它让我们能够同时启动和推进多个开发任务，极大地缩短了项目的总体交付周期。
2.  **保证安全性**：通过 Worktree 提供的物理隔离，彻底杜绝了并行开发中因文件覆盖导致的代码丢失风险。
3.  **降低心智负担**：将繁琐的 Git 操作（如合并、解决冲突）和重复性任务（如功能实现模板、提交信息生成）委托给 AI，使开发者能更专注于创造性的核心工作。

我们从中看到，AI 编程助理的演进方向，不仅仅是提升代码生成本身的质量，更在于深度融入并优化整个软件开发的工程实践。它正在从一个“结对编程的伙伴”演变为一个“开发流程的调度器与优化器”。

在下一课中，我们将把视野从本地终端扩展到云端，探索 Claude Code 如何与 GitHub 集成，以实现 PR review 等协作流程的自动化。

## Appendix

### 手工川 meta-command v3.3.0

这是我用于生成标准格式自定义命令的“元命令”，可以确保所有命令都遵循统一的结构和版本规范。

```markdown
---
allowed-tools: Write(*), Read(*), Edit(*), Append(*), Bash(ls:*), Bash(date:*)
description: Generate optimized slash commands
version: "3.3.0"
author: "公众号：手工川"
---

# Meta Command

Create slash commands using two-file architecture.

## Files to Generate

For command `XX`:

- **XX.md** - Command file
- **XX.changelog** - Version history

## Arguments Format

`<name> "<description>" [project|user] [requirements]`

## Process

1. Check if command exists:

   ls ~/.claude/commands/XX.md

2. Generate **XX.md**:

   ***

   allowed-tools: [required tools]
   description: one-line description
   version: "1.0.0"
   author: "公众号：手工川"

   ***

   # Command logic

3. Generate **XX.changelog**:

   # Changelog for XX

   ## v1.0.0 - YYYY-MM-DD

   - Initial version

   Author: 公众号：手工川
   Created: YYYY-MM-DD

## Design Principles

- Generated content should display correctly in various environments
- Use universally compatible formats for code examples

## Version Rules

- New: v1.0.0
- Patch: Bug fixes (1.0.1)
- Minor: Features (1.1.0)
- Major: Breaking (2.0.0)

## Tool Selection

- Git: `Bash(git:*)`
- GitHub: `Bash(gh:*)`
- Files: `Read(*)`, `Write(*)`, `Edit(*)`
- Search: `Glob(*)`, `Grep(*)`
- Web: `WebFetch(*)`, `WebSearch(*)`

Execute: `/meta-command <name> "<desc>" [options]`
```

### 手工川 git-add-commit command v1.0.1

基于课程启发，我设计的更强大的 `git-add-commit` 命令，支持 Conventional Commits 规范和中文消息。

```markdown
---
allowed-tools: [Bash(git:*), Read(*), Grep(*), LS(*)]
description: Add and commit with conventional style
version: "1.0.1"
author: "公众号：手工川"
---

# Intelligent Git Commit Command

You are creating a git commit with the following features:

- **Default language**: Chinese (中文) for commit messages
- **Conventional Commit style**: Use conventional commit format (type(scope): description)
- **User context integration**: Accept and incorporate user-provided additional context

## Configuration Settings

    default_language: "zh-CN"
    commit_style: "conventional"
    types:
      - feat: 新功能
      - fix: 修复bug
      - docs: 文档更新
      - style: 代码格式调整
      - refactor: 重构
      - perf: 性能优化
      - test: 测试相关
      - build: 构建系统
      - ci: CI/CD配置
      - chore: 其他更改
      - revert: 回滚提交

## Workflow

1. **Analyze current changes**:

   - Run `git status` to check for uncommitted changes
   - Run `git diff --cached` to see staged changes
   - Run `git diff` to see unstaged changes
   - Identify the main type of changes and affected scope

2. **Parse user input**:

   - Check if user provided additional context or specific requirements
   - Extract any specific commit type or scope preferences
   - Consider any attention points mentioned by the user

3. **Generate commit message**:

   - Use conventional commit format: `<type>(<scope>): <description>`
   - Write description in Chinese by default
   - Incorporate user's additional context if provided
   - Keep the subject line under 50 characters
   - Add detailed body if needed (wrapped at 72 characters)

4. **Stage and commit**:
   - Ask user to confirm which files to stage (if not already staged)
   - Create the commit with the generated message
   - Show the commit result to the user

## Example Usage

When the user runs `/git-add-commit`, you should:

1. First check the git status and changes
2. Analyze what type of changes were made
3. Generate an appropriate conventional commit message in Chinese
4. If the user provided additional context like "注意性能优化部分", incorporate it
5. Create the commit

## Important Notes

- Always analyze the TARGET directory where the command is run
- Do NOT assume anything about the current directory structure
- Support both staged and unstaged changes
- Allow user to override language or commit style if specified
- Ensure commit messages are meaningful and descriptive

## User Input Parameters

The user can provide additional context in several ways:

- Direct description: Additional text after `/git-add-commit`
- Type override: Specify a different commit type
- Language override: Request English or other language
- Scope specification: Define a specific scope for the commit

Generate appropriate conventional commit messages based on the actual changes in the target repository.
```

### 顺便推荐一款产品：支持 Worktree 并行开发的 Conductor

今天学习的本期教程对我启发很大，我本来想把这样并行开发的特性集成到自己开源的[ccm](https://github.com/markshawn2020/claude-code-manager)上，结果社群里的朋友直接推荐了一款已经实现的 C 端产品 [Conductor](https://conduct.build) 。

![](https://poketto.oss-cn-hangzhou.aliyuncs.com/30cf9f5d892d9a9ab7e6254753523f28.png?x-oss-process=image/quality,q_90/rotate,0)

我赶紧试了试，发现确实可以，以下是一些评测经历（没有收钱，也感兴趣创始团队，欢迎介绍）。

![conductor：官网首页](https://poketto.oss-cn-hangzhou.aliyuncs.com/1d355b0b67fa1c75f5a56abcc142c2ce.png?x-oss-process=image/quality,q_90/rotate,0)

![conductor：基于 git worktree](https://poketto.oss-cn-hangzhou.aliyuncs.com/f523cbe218f4d9db0ceb5567b46a3c08.png?x-oss-process=image/quality,q_90/rotate,0)

![conductor：登录后工作区首页](https://poketto.oss-cn-hangzhou.aliyuncs.com/5af10044d0f72589e3dc00f233e2f9e6.png?x-oss-process=image/quality,q_90/rotate,0)

![conductor：翻车了，似乎需要配置proxy，但没找到地方儿](https://poketto.oss-cn-hangzhou.aliyuncs.com/ae421f69c0a0e8ed285ce824f2469cc7.png?x-oss-process=image/quality,q_90/rotate,0)

简单体验了一下各个功能，我觉得产品设计还是挺棒的，它：

- 场景明确、定义良好、界面清爽
- 支持多项目（在 sidebar 里一条条可切换）
- 每个项目支持多个 space（基于 git worktree 所以不会互相干扰）
- 支持快捷选择三种思考模式（尽管官方最佳实践有四种）

我个人对这样的产品是有需求的，但和我目前的开发习惯还有些差异：

1. 我现在是在 iterm 里通过 tmux 去管理项目的，不太想去使用一个额外的 GUI（如果要用的话，我会更 prefer VSCode）
2. 在 iterm 里，我是切分多列，每一列一个项目，这样允**许我同时看所有项目的开发情况**，而非 Conductor 里每个 workspace 占满整个软件，不同 workspace 以及不同 project 得相互切换
3. 不过以上我不觉得是 Conductor 的问题，只是我的用户习惯不一样，可能对于我这样的“超级”开发者希望有更多的全局感：）

![手工川日常并行开发（iterm + tmux + cc）](https://poketto.oss-cn-hangzhou.aliyuncs.com/e75cc4767787476d23da923aaceafe0f.png?x-oss-process=image/quality,q_90/rotate,0)


所以，总之，Conductor 还是不错的，推荐大家可以下载安装使用，目前仅支持 mac，以及 proxy 代理感觉要好好弄一下：）
