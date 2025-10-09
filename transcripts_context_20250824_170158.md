# transcripts - 项目上下文

## 项目结构

```
transcripts
├── 00. Overview.md ✅
├── 01. Introduction.md ✅
├── 02. What is Claude Code?.md ✅
├── 03. Course Notes.md ✅
├── 04. Setup & Codebase Understanding.md ✅
├── 05. Adding Features.md ✅
├── 06. Testing, Error Debugging and Code Refactoring.md ✅
├── 07. Adding Multiple Features Simultaneously.md ✅
├── 08. Exploring Github Integration & Hooks.md ✅
├── 09. Refactoring a Jupyter Notebook & Creating a Dashboard.md ✅
├── 10. Creating Web App based on a Figma Mockup.md ✅
├── 11. Conclusion.md ✅
└── 12. Prompts & Summaries of Lessons.md ✅
```

### 文件状态说明

- ✅ 高优先级文件（已包含）：README、package.json、配置文件等
- ☑️ 中优先级文件（已包含）：代码文件（.py、.js、.ts等）  
- ✅ 低优先级文件（已包含）：文档、配置等其他文件
- ⏭️ 跳过的文件：被忽略规则排除的文件
- 💾 二进制文件：图片、视频、压缩包等
- 📊 文件过大：超过大小限制的文件  
- 🚫 超出限制：超过文件数量限制的文件

## 项目文件内容

本文档包含了 13 个主要文件的内容。


### 01. Introduction.md

```markdown
Transcript

0:02 Welcome to Claude Code, the Highly Agentic Coding Assistant.

0:05 This short course is built in partnership with Anthropic

0:08 and Anthropic's Elie Schoppik is back to share with us

0:11 best practices for how to use Claude Code.

0:13 I'm really excited about this short course.

0:15 Claude Code's my personal favorite coding assistant right now,

0:18 and it has boosted my and many other developers' productivity

0:22 by a large margin. And it is a

0:24 tool with a lot of depth to it.

0:27 And so I want to get together with Anthropic,

0:29 to teach, hopefully the definitive course on

0:32 all of the most important ideas behind

0:35 how to use it in a systematic way.

0:37 Thanks, Andrew. I'm excited to be back

0:39 here and start like you mentioned from explaining

0:41 what the tool is, how it works,

0:43 all the way towards using it in parallel

0:45 with many different tools including Git worktrees and MCP servers.

0:50 What we've seen over the last couple

0:52 years is AI assisted coding has evolved rapidly.

0:54 It started from maybe people asking LLMs occasional coding questions.

0:58 suggestions to then GitHub autocomplete to then,

1:01 your various tools that became

1:03 more and more autonomous.

1:05 And Claude Code, when it was released,

1:08 was definitely a step up in terms of the degree of agency

1:10 or the amount of stuff that the coding assistant

1:13 could do by itself. And so

1:15 I think many people were surprised that

1:17 you could set a task that Claude would work on for

1:20 many minutes or sometimes even more than a few minutes.

1:23 And now there are developers that are orchestrating

1:25 not just a single Claude instance, but even several of them.

1:28 working in parallel on different parts

1:30 of a codebase. But coordinating all this

1:32 has to set the best practices that is not widely known

1:36 and if you have not worked

1:37 with people close to the best practices,

1:39 I think there could be a big uplift

1:41 still for mastering these best practices

1:45 and knowing how they drive that amazing productivity

1:47 that I'm seeing many developers have using Claude Code.

1:50 So as we start to talk about those best practices,

1:53 a key tip for working with Claude Code is providing clear context

1:57 to help Claude code achieve the task you want efficiently.

2:00 This means pointing Claude code to the relevant files,

2:03 clearly describing the features and functionality that you want

2:06 and making sure that you're properly extending

2:09 the capabilities of Claude code

2:11 with MCP servers and other tools in that ecosystem.

2:14 In this course, you'll apply those best practices to three different examples.

2:18 We'll start with a RAG chatbot

2:19 and you'll implement the features from

2:21 the front end to the back end,

2:22 including refactoring code, writing tests,

2:26 and then using the GitHub integration to

2:28 work with pull requests and fixing issues.

2:30 You'll make use of many Claude Code features

2:32 like planning, thinking modes, creating parallel sessions,

2:35 and managing Claude's memory.

2:37 For the second example, we'll shift gears and work with Jupyter notebooks

2:40 to explore e-commerce data.

2:42 We'll refactor notebooks using Claude Code, remove redundant code,

2:46 and create powerful dashboards with web applications.

2:49 Finally, we'll move to create a visual mockup

2:51 based in Figma and use Claude Code,

2:54 the Figma MCP server and a different

2:56 MCP server to import the design,

2:59 iterate, test, and build agentically a powerful front-end application.

3:03 If you're not currently a Claude Code user,

3:05 I think learning this set of

3:08 ideas will give you a meaningful acceleration

3:10 in the way that which you can engineer systems.

3:13 And even if you are a current Claude Code user,

3:15 I think having Ellie share these best practices

3:18 with you in a comprehensive and systematic way,

3:21 will, I hope, leave you with quite a few new things

3:24 you try that will be useful. your work.

3:27 I'd like to thank from DeepLearning.AI, Hawraa Salami,

3:29 who had contributed to this course.

3:32 In the next video, Elie will share

3:35 Claude Code's underlying architecture,

3:37 and you might be surprised by how simple the architecture is.

3:41 Claude Code relies on just a small number of tools to search

3:44 for patterns within your code files,

3:46 to list directories, look at files, do regex.

3:50 It does not rely on semantically embedding

3:52 your code in the code base or transforming it into

3:55 searchable structure. And one of the things that

3:58 I think has made Claude Code effective

3:59 is how it agentically can read through your code

4:03 to take notes in a file called code.md to figure out autonomously

4:08 what is going on your codebase to then

4:10 drive decision-making on how to advance your code.

4:13 That's right. And because of that, and not

4:15 having a need to index the codebase,

4:16 you can ensure the codebase stays local.

4:19 We'll talk about some of the security ramifications with that.

4:22 So let's get started. And I'll see you in the next video.
```


### 07. Adding Multiple Features Simultaneously.md

```markdown
---
title: Claude Code A Highly Agentic Coding Assistant  DeepLearning.AI
slug: claude-code-a-highly-agentic-coding-assistant-deep-1755233065646
source: https://learn.deeplearning.ai/courses/claude-code-a-highly-agentic-coding-assistant/lesson/oo58a/adding-multiple-features-simultaneously
datetime: 2025-08-15T04:44:25.646Z
---


0:02 You can open multiple sessions with Claude

0:04 Code to work on many features in parallel.

0:08 To manage these sessions and make sure you're not

0:11 overwriting the same file, you can use Git worktrees.

0:14 So let's add Git worktrees to add

0:16 three features to the chatbot in parallel.

0:19 I'll see you there. So I'm going to hop back into Claude.

0:21 And as we saw earlier, Claude Code comes built in

0:24 with quite a few slash commands.

0:27 But you can also make your

0:28 own. To make your own custom commands,

0:29 inside of the dot claude folder.

0:32 Let's make a new folder called commands.

0:34 And inside of here, we're going to make a markdown file

0:38 with the name of the command that we'd like.

![截图：/implement-feature 命令](https://poketto.oss-cn-hangzhou.aliyuncs.com/c332e0100fc758372c9b7fa1453b81bc.png?x-oss-process=image/quality,q_90/rotate,0)


```markdown
You will be imp lementing a new feature in this codebase

$ARGUMENTS

IMPORTANT: Only do this for front-end features，
Once this feature is built, make sure to write the changes you made to file called frontend-changes.md
Do not ask for permissions to modify this file， assume you can always do it.
```

0:40 The command here that I'm going to make is called implement feature.

0:44 So I'll create a markdown file called implement-feature.md

0:48 Inside here, I can place whatever I'd like.

0:51 But what I want to show you that's very special

0:54 is if you have any arguments you

0:56 want to pass to your custom command, you can reference it using

1:01 this $ARGUMENTS variable.

1:03 So what I'm asking for here

1:04 is that when this command is used,

1:06 I'll be specifying that you're implementing a new feature.

1:09 The user can then specify whatever that feature is,

1:13 and then I want to make

1:14 sure that Claude Code is well aware

1:15 to only do this for front-end features,

1:18 and to write the changes made to a file called frontend-changes.md

1:22 You can imagine there are many different use cases for custom commands,

1:26 certain ways you want to run tests or run files.

1:29 and anything that you put in here

1:31 does not automatically get added to your context,

1:34 unlike a CLAUDE.md

1:36 So if you want something to be applied

1:39 to every single instance of Claude Code that you make,

1:42 use your CLAUDE.md file.

1:44 But if you just have specific commands

1:46 that you may or may not use across different conversations,

1:50 right here is a great place to put them.

1:52 I'm going to be using this custom command

1:54 when I start talking about worktrees.

1:56 But before we do that, let's quit out of Claude Code,

1:59 hop back in and just verify

2:01 that we can see that custom command.

2:04 And here, I see implement feature, and I see the description

2:07 is coming from the first part of this markdown file.

2:10 Now that I've added this custom command,

2:13 let's go ahead and add and commit it.

2:15 I could do this from the command line,

2:17 but I'm actually going to ask Claude to do that for me.

![截图：让 cc 自己 commit](https://poketto.oss-cn-hangzhou.aliyuncs.com/a6f23a05365d18543e84acde475113ea.png?x-oss-process=image/quality,q_90/rotate,0)


2:20 **Add and commit changes made**.


```markdown
add and commit changes made
```

```ad-note

感觉老师的这条自动 commit prompt 还是挺有用的，记一下 ：**Add and commit changes made**。

考虑到我们经常需要自动commit，所以封装成一个 slash command 会更好，具体见我们附录中基于手工川meta command 生成的手工川 git-add-commit command。

话说去年年末的时候，我有花一整个月时间打磨了一款自动 commit 工具，叫 [oh-my-commit](https://github.com/oh-my-commit/oh-my-commit)，它同时支持命令行和vscode两种环境，默认使用 [Convertional Commits Style](https://www.conventionalcommits.org/)。

当时花了很多时间在研究怎么在vscode插件里的webview里做好UIUX，没想到很快就进入了基于cc无界面的vibe coding时代，慢慢就没怎么用了。

但一个好的、快速的、适合自己的commit系统（尤其是与CICD集成的时候），个人觉得依旧是有价值的，所以我后续可能会考虑进一步优化其支持 slash command、hook、mcp等。
```

2:22 This is nice so that Claude Code can create

2:24 a nice commit message

2:26 with some descriptive information for what was done.

2:29 We'll see that it's adding the .claude folder

2:31 and committing with the commands necessary.

2:34 We can see here that this has been added to the repository.

2:37 And since we've granted permissions for this already,

2:40 we don't have to respond again.

2:42 If you're ever curious where that lives,

2:44 inside of the claude folder,

2:46 there is a settings.local.json file

2:49 Inside of this file, we can specify

2:52 what commands we've allowed so that we don't need

2:54 to confirm every single time.

![截图：配置放行命令](https://poketto.oss-cn-hangzhou.aliyuncs.com/b915e36af835640c4c2f8585402b2a58.png?x-oss-process=image/quality,q_90/rotate,0)


2:57 As you can see here, as well,

2:58 when we use playwright, we gave permissions.

3:00 And if you'd like to add your own,

3:02 you can easily do so in this file,

3:04 or even with the handy /permissions command.

3:08 Now that we've got that custom command set up,

3:10 let's talk a little bit about how we

3:12 might want to work in parallel with Claude Code.

3:14 Instead of just opening up multiple terminal

3:17 windows and working directly on this code base,

3:20 we're going to use Git to make sure

3:23 that we don't overwrite existing files when we have

3:27 multiple instances of Claude Code.

3:29 I might have two different instances of

3:31 Claude Code operating on the same file.

3:34 And if I do that with

3:35 the environment that I'm in right now,

3:37 there's going to be overwriting, bug

3:39 creation and quite a bit of confusion.

3:42 Thankfully, Git has an excellent option here

3:44 to use a feature called worktrees.

3:46 And worktrees allow me to essentially create copies of the codebase,

3:51 operate in isolation,

3:53 and then at the end, merge those in together. And in fact,

3:57 I can use Claude to help with that merging

4:00 and management of my worktrees.

4:02 To get started with worktrees,

4:03 I'm going to first make a folder called .trees

4:06 And inside of this worktrees folder,

4:09 I'm going to go ahead and add a couple worktrees.

4:12 Let's add a work tree using the Git worktree add command.

4:15 and then we'll specify the folder as well

4:19 as the name of the work tree that I want to add.

4:21 We'll call this one ui\_feature. We'll

4:23 then go ahead and add another one

4:26 called testing\_feature,

... (省略 337 行) ...


10:12 This can be quite valuable when you have small merge conflicts

10:15 that you don't want to manually go through each time.

10:18 Having tests here is also quite valuable

10:20 to make sure that once we've finished, we could

10:22 run our tests and the code base works as expected.

10:25 It's now continuing with the merge as expected.

10:27 and it's going to commit all of

10:29 these changes with the resolved merge conflicts.

![截图：cc自动处理merge冲突](https://poketto.oss-cn-hangzhou.aliyuncs.com/baf727d0751c3518001b1747b6c0bde6.png?x-oss-process=image/quality,q_90/rotate,0)


10:31 If I'd like after, I can ask for it to remove

10:34 these worktrees or I can keep them there if I need.

10:36 So I'll do a quick test to

10:38 make sure that these files are here

10:40 as expected and that the merge configurations

10:41 are what are expected here as well.

10:43 We can also head back to the browser and

10:46 see if our front end changes are implemented as expected.

10:48 Looks like Claude Code has finished up, we've added necessary dependencies,

10:52 we've modified our pyproject.toml

10:54 We've added tests.

10:56 we've implemented the light dark themes.

10:58 We've implemented our black code formatter

11:01 to make sure that code is as expected in a certain format.

11:04 and added that configuration in the same file

11:06 that we worked on with another work tree.

11:09 We fixed up any conflicts.

![截图：cc已经处理完所有任务](https://poketto.oss-cn-hangzhou.aliyuncs.com/a822e67a59571678f802b8d2b8fa3760.png?x-oss-process=image/quality,q_90/rotate,0)


11:11 Let's make sure this is working

11:12 as expected. So back in the browser,

11:14 I now see here, I have this lovely theme

11:17 and as I toggle through, I can

11:19 see a light theme and a dark theme.

![截图：确认前端的主题切换功能已经实现](https://poketto.oss-cn-hangzhou.aliyuncs.com/8e1b87bda460a952b95cfccc212159c4.png?x-oss-process=image/quality,q_90/rotate,0)


11:21 So there might be some more things

11:22 I want to tweak here and there,

11:24 but I've been able to edit across all parts of the stack,

11:27 even do things in the linting and DevOps side of things,

11:32 all without overwriting,

11:34 causing challenging headaches through the power of Git worktrees.

11:37 In the next lesson, we're going to see how

11:40 we can use Claude Code outside of the terminal

11:42 through an integration with GitHub to allow for reviewing pull requests,

11:47 making changes and being helpful outside of the terminal ecosystem.


## Appendix

### 手工川 meta-command v3.3.0

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

    ---
    allowed-tools: [required tools]
    description: one-line description
    version: "1.0.0"
    author: "公众号：手工川"
    ---
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
```


### 04. Setup & Codebase Understanding.md

```markdown
---
title: Claude Code A Highly Agentic Coding Assistant  DeepLearning.AI
slug: claude-code-a-highly-agentic-coding-assistant-deep-1755232941815
source: https://learn.deeplearning.ai/courses/claude-code-a-highly-agentic-coding-assistant/lesson/kkth2/setup-&-codebase-understanding
datetime: 2025-08-15T04:42:21.815Z
---

Transcript

0:02 The first example we'll work on is an end-to-end RAG chatbot.

0:06 Let's use Claude Code to explore the code base.

0:09 Before we start using Claude Code

0:11 to write lots of code for us,

0:13 let's talk about how we can use this tool

0:16 to get up to speed on larger code bases.

0:19 Right here, I have an application where I can chat with Claude

0:23 about course materials from Deep Learning AI.

0:26 So let's try asking an outline of a course. For example, what

0:29 is the outline of the MCP Build Rich-Context AI Apps with Anthropic.

0:34 We'll see here that I'll get a

0:36 response with quite a bit of detail

0:38 around the lessons and descriptions for each of those lessons.

0:41 With that in mind, let's see how we can get

0:44 up to speed on the underlying code that powers this application.

0:48 Back in VS Code, I have

0:49 the terminal open here and I'm going

0:51 to hop into Claude Code just

0:53 by typing in claude and pressing enter.

0:55 In this application, I can start chatting with my codebase.

0:58 So I'm going to start with a high-level question just to

1:01 give me an overview of the codebase.

1:04 What we're going to see Claude Code do is agentically search

1:07 over the codebase, figure out some of the most important files

1:12 and give me a description of what's happening in this application.

1:15 Instead of searching through each individual file,

1:18 we're going to agentically search and find the most relevant ones.

1:21 So here we're going to get some information about

1:24 the architecture, the key components, some of the features,

1:28 and now if there are particular

1:30 things I want to dig into, I can easily do that.

1:33 I can also ask other higher level questions like how

1:36 are these documents processed?

1:38 In this application, we're using Retrieval Augmented Generation

1:42 to fetch information about these courses.

1:45 If I want to get more information about that process,

1:48 I can ask a question like this one.

1:50 We like to say that Claude Code is a fantastic

1:52 engineer alongside you,

1:54 but it's an even better explainer.

1:56 So as you're getting up to speed with new codebases,

1:59 new data sets. First, start using Claude Code

2:02 as a way to explain things to you,

2:04 so that when you ask it to write code,

2:06 you can have a better understanding of what's going on.

2:09 Here we can see the sources in the

2:12 code base that are actually splitting text into chunks,

2:15 that are adding lesson context and that are storing course metadata.

2:18 This ability to quickly get up to speed with a code base,

2:22 especially when you might not be

2:24 familiar with the underlying technology or language,

2:27 is exceptionally valuable. Instead of

2:29 navigating to each of these folders and figuring out what's going on,

2:34 we can ask more specific questions and even get diagrams

2:38 and visualizations made for us.

2:41 So the first thing I'll ask Claude

2:43 is to trace the process of handling a user's query

2:47 from front end to back end.

2:50 You can imagine you might have some limited knowledge

2:53 in one of the parts of the stack or

2:55 you're not familiar with how this is all happening.

2:58 So Claude Code is going to

2:59 give us quite some useful information here.

3:02 What's useful when you're seeing Claude Code work

3:04 is its ability to give you a bit of a to-do list,

3:07 so you can start to understand

3:09 what's happening. At any point in time,

3:12 you can press escape and guide Claude Code

3:15 to follow a different set of to-dos,

3:17 but in this case, I feel pretty good about what it's doing.

3:20 It's going to start tracing from the frontend, start following API endpoints,

3:24 analyze our Retrieval Augmented Generation system,

3:28 and then figure out how to actually generate the response.

3:31 It's reading the appropriate files that are handling these particular tasks

3:36 and finishing up its list to give us a powerful summary.

3:39 As we're in this environment,

3:41 we can stay within VS Code or open

3:43 up Claude Code in its own dedicated terminal instance.

3:47 That's completely up to you as you're working in this application.

3:50 Once it's done, we can see a

3:52 very detailed path for what's happening here.

3:55 Not only can I read each of these step-by-step,

3:58 I can even ask Claude to write this to a file,

4:00 but I'm seeing in quite a bit

4:02 of detail what's happening on the front end

4:04 with some JavaScript, what happens once that reaches my back end,

4:07 what the Retrieval Augmented Generation system is doing,

4:11 how I'm generating a response. Finally,

4:14 how I'm searching through my vector database,

4:16 how I'm filtering what's necessary, getting a response back,

4:20 and then finally, sending that to the user.

4:23 There's a lot that's going on in this application.

4:25 And I can use Claude to

4:26 dive deeper into any of those pieces.

4:29 But let's just say I learn best from visualizations.

4:32 So let's ask Claude to draw a diagram

4:34 that illustrates this flow.

4:37 We can ask Claude to draw diagrams

4:39 for web visualizations. We can ask for ASCII art.

4:43 But let's see what Claude comes up with

4:44 with its own intelligence and knowledge of how the application works.

4:49 So let's see what Claude code has come up with.

4:51 We've got a really nice diagram here

4:53 showing us the step-by-step process.

4:55 So it can't create these visual diagrams.

4:58 We could always ask it to use some something like D3.js

5:01 or recharts if we want something like a web application.

5:05 But we can see right here, we've got a really nice diagram.

5:08 From the front end, making a request to the back end,

5:11 calling the necessary functions,

5:13 generating the response necessary if there's any history involved,

5:18 talking directly to the large language model

5:21 with our system prompts and our tools and a query,

5:23 figuring out where to go next,

5:25 searching through our vector database using Chroma DB, getting back results

5:29 formatting that, sending it to the model to produce a final response.

5:34 There's quite a bit of detail that goes into this.

5:37 And if we want, we can even augment Claude with additional tools

5:41 for generating the visualizations that we want.

5:44 But out of the box, just getting this information quickly and efficiently

5:48 is going to help us get up to speed with this

... (省略 108 行) ...


8:29 shared with other team members.

8:31 As more individuals work on the codebase,

8:34 they can add to this CLAUDE.md file,

8:36 and you can even nest CLAUDE.md files

8:39 in subdirectories if you need

8:41 more specific instructions for things like the backend

8:44 or frontend or our docs that we have here.

8:46 What's really nice about using a tool

8:49 like Claude Code with Visual Studio Code,

8:51 is that as I see changes to files,

8:54 I can see those visually in my editor.

8:56 And anytime that I am using a tool in Claude Code,

9:00 it's going to ask me for permissions.

9:02 This mission critical human in the loop is really important

9:05 when you get up and running,

9:07 and if you don't need Claude to ask you every single time,

9:10 can always use this second option. We'll

9:12 go ahead and auto accept those edits

9:14 and we'll see that a CLAUDE.md file has been created for us.

9:18 To give you a quick walk through,

9:21 we can see it's given us a

9:23 project overview, key technologies, an architectural overview,

9:26 a nice little diagram here, some core components.

9:29 and much more. If we want things to change

9:32 to this particular CLAUDE.md, we can easily do so.

9:35 As it continues searching the codebase,

9:37 it makes additional edits here to my CLAUDE.md

9:40 and gives me a summary of what's been done.

9:43 When I'm using a tool like Claude Code in VS Code,

9:46 I have the ability to specify which

9:48 file I'm in and even get information

9:49 about particular lines.

9:52 To set this up, I'm going to use the /ide command.

9:55 and I can see right here

9:57 that I'm connected with Visual Studio Code.

9:58 Now that I'm in Visual Studio Code, we can see right here

10:01 that the second that I visit a file,

10:04 it's tagged right here for what's going on.

10:06 This gives Claude Code the right context

10:08 for which file I'm in and if there are questions

10:11 I have about that file, it makes it easier

10:13 for Claude Code to identify that.

10:15 If I ever want to make any changes

10:17 to my CLAUDE.md file, I can manually write that if I'd like.

10:20 Or I can use a handy command

10:22 to go ahead and use this pound key

10:24 and directly add to memory.

10:26 So I'm just going to say here, always use UV.

10:29 to run the server, do not use pip directly.

10:32 This is a package manager in the Python ecosystem

10:35 and I want to make sure that Claude doesn't get confused.

10:37 When I use this shortcut, we can see there are different places

10:41 where this memory can be saved.

10:42 We mentioned there is the Project memory

10:45 that is included in git for everyone on your team to use.

10:48 We have local memory that is gitignored

10:51 but just useful for you as the developer.

10:53 and then User memory that is applicable

10:56 to all projects you use with Claude Code.

10:59 For this one, I'll just go ahead and update the project memory.

11:02 I can see here, I've made that change.

11:04 And if I look in my CLAUDE.md, I'll see right here,

11:07 I have some mentions to using UV

11:10 to make sure that I'm doing that correctly.

11:12 If I want to be more specific, I can also say,

11:15 make sure to use UV to manage all dependencies.

11:19 I'll add this to my CLAUDE.md and

11:21 we'll see right here that it's been added.

11:23 If I take a quick look at this particular file,

11:26 we can see any mention of dependencies now includes UV.

11:39 We spoke a little bit about some of the commands

11:41 that are built into Claude Code like /emit.

11:45 There are a couple other useful

11:46 ones that I want to showcase here.

11:48 And in fact, we're going to see later on

11:50 in this course, we can even make our own.

11:52 One of the first ones I

11:53 want to walk you through is /help.

11:54 This shows me right off the bat a quick description

11:58 of all the commands. and a quick summary.

12:00 This is useful as you're getting up to speed with Claude code.

12:04 The next one I want to showcase is a command called /clear.

12:07 What this allows you to do is

12:10 clear the conversation history and start from scratch.

12:13 This is very helpful as you shift gears and build new features.

12:17 This allows you to clear the context window and start fresh.

12:20 If you want to continue the conversation,

12:23 have a smaller context window, but still

12:25 have a summary of what's been done,

12:28 we also have this command /compact

12:30 that allows you to clear the history, but keep a summary

12:33 so that you can build off with Claude having an idea

12:36 of what was done before.

12:38 One more useful command is the escape key that allows you

12:41 to get out of whatever command you're in.

12:43 So if I'm going and trying to do something like /compact

12:47 and I want to stop that process, I can always press escape.

12:50 If I start a process with Claude Code

12:52 to explain what is in the codebase.

12:55 If I want to stop that process, escape

12:57 will allow me to interrupt and continue, onwards.

13:00 So don't feel like you have to wait for

13:02 Claude Code if you're not getting what you need.

13:04 In the next lesson, we'll start using Claude Code to build features,

13:08 add to files, modify changes, and make sure

13:11 we're doing the right thing along the way.

13:14 Before we hop off, one last useful piece with

13:16 Claude Code is its ability to work with Git.

13:18 So I've made some small changes to this application,

13:21 and I want to add and commit these changes.

13:24 Instead of me manually have to write

13:26 the Git commands, write a descriptive commit message,

13:29 going to actually have Claude Code do that work for us.

13:32 And what's really nice is Claude Code's ability to add

13:35 and commit the necessary commands.

13:37 I'll go ahead and add this particular file,

13:39 not only commit, but you can see here,

13:42 I've got this really nice descriptive commit message.

13:44 That's incredibly useful as we start asking Claude Code

13:47 about historical changes with git.

13:49 and when we push this to GitHub and

13:51 other people are reading the changes

13:53 we made. So we'll add and commit

13:54 and the next lesson, we'll use Claude Code

13:57 to start writing lots of things for us.
```


### 08. Exploring Github Integration & Hooks.md

```markdown
---
title: Claude Code A Highly Agentic Coding Assistant  DeepLearning.AI
slug: claude-code-a-highly-agentic-coding-assistant-deep-1755233099599
source: https://learn.deeplearning.ai/courses/claude-code-a-highly-agentic-coding-assistant/lesson/nngi6/exploring-github-integration-&-hooks
datetime: 2025-08-15T04:44:59.598Z
---

Transcript

0:02 In this lesson, you'll learn how to use Claude

0:05 Code outside of the terminal with a GitHub integration.

0:08 You'll see how to set up Claude Code

0:11 to review pull requests and fix issues in GitHub.

0:14 You'll then learn how to execute code before

0:17 and after using tools through Claude Code hooks. Let's dive in.

0:21 We left off in the last section merging our wortrees together,

0:25 but we forgot to ask Claude to remove those worktrees.

0:28 So we're going to hop back into Claude. So

0:30 I'm going to go and pass in the resume flag

0:32 to go back to a previous

0:35 conversation that I had with my worktrees.

![会话列表](https://poketto.oss-cn-hangzhou.aliyuncs.com/ef3ab82e6a280dcc5d85b866a1e175d9.png?x-oss-process=image/quality,q_90/rotate,0)


0:38 In this particular conversation, we can now

0:40 go back to where we were before

0:42 and finish up with removing our worktrees.

0:45 So let's ask Claude, remove the .trees folder

0:47 and the underlying worktrees, and once you're done,

0:50 push this code to GitHub. So

0:52 let's go ahead and give Claude Code

0:54 a second to run the necessary git commands

0:56 to remove that folder and then pushed our merge code

0:59 to GitHub. 

! [清理 worktrees](https://poketto.oss-cn-hangzhou.aliyuncs.com/5d55c23627e0ec99c0b43d13332102a1.png?x-oss-process=image/quality,q_90/rotate,0)



We'll go ahead and give Claude Code access to

1:03 see the underlying worktrees so that we not only

1:05 remove the worktrees,

1:08 but also delete the corresponding branches.

1:11 We'll go ahead and remove these particular trees.

1:14 now remove the directory and then remove the underlying branches.

1:17 Now that we've done that, let's go ahead

1:19 make sure that worked as expected, which is good.

1:21 we don't have that folder. And

1:23 now, let's push this code to GitHub.

1:25 We'll confirm that we want to

1:26 run the git push origin main command

1:28 and it looks like our code is pushed to GitHub.

![推送 github](https://poketto.oss-cn-hangzhou.aliyuncs.com/d4e11586ecbd8878bb64a9fddcde5712.png?x-oss-process=image/quality,q_90/rotate,0)


1:31 Now that we've committed and pushed our code to GitHub,

1:34 let's start installing the GitHub integration that comes with Claude Code.

1:38 I'll do that using the /install-GitHub-app command.

1:42 Here you might see that you need to

1:44 include additional authentication using the command line interface.

![/install-github-app](https://poketto.oss-cn-hangzhou.aliyuncs.com/0dea1c62dc13c355223998b779567245.png?x-oss-process=image/quality,q_90/rotate,0)


1:48 So if you see those setup instructions, make sure to follow them.

1:51 We'll now be able to install the GitHub

1:54 app for the current repository that we're working in.

1:56 So let's go ahead and do

1:58 that. This will open up the browser.

1:59 And if I have not yet configured

2:01 this, I'll have the option to install.

![github + claude](https://poketto.oss-cn-hangzhou.aliyuncs.com/b331081bbb7c07b00cfc640ba8e090d1.png?x-oss-process=image/quality,q_90/rotate,0)


2:04 What this integration allows us to do is use Claude Code

2:07 in pull requests and issues

2:09 to respond to feedback, fix errors,

2:12 modify code, and much more.

2:15 In order for this functionality to exist,

2:17 it's built on top of the software development kit

2:19 that comes with Claude Code. This SDK allows you

2:23 to use Claude Code outside

2:25 of the terminal interface. So let's head back to the terminal.

2:29 specify the workflows we want to install.

2:32 These workflows allow for tagging Claude in issues

2:35 and using Claude to automatically review code in our pull requests.

2:40 Let's install both. We'll create a long-lived token.

![确认两个都安装](https://poketto.oss-cn-hangzhou.aliyuncs.com/4729c7a591314a4e1ae3ab39533e89c5.png?x-oss-process=image/quality,q_90/rotate,0)


2:44 and here we'll have to authorize and authenticate with Claude.

![授权claude](https://poketto.oss-cn-hangzhou.aliyuncs.com/b699c18b921752ea5c173bba61779f3b.png?x-oss-process=image/quality,q_90/rotate,0)


2:48 Once that's done, 

![授权成功](https://poketto.oss-cn-hangzhou.aliyuncs.com/f0f71bef87cf91a2530a1f715c583b0b.png?x-oss-process=image/quality,q_90/rotate,0)


we can head back

2:49 and we'll see that it's creating the repository information,

2:53 setting up any additional information I need,

2:55 and sending me right back to GitHub

2:57 to open a pull request.

![自动打开 github 提交 pr](https://poketto.oss-cn-hangzhou.aliyuncs.com/c2888d3dc1649f26dfbf1e96640cef97.png?x-oss-process=image/quality,q_90/rotate,0)


2:59 with the changes that had been made.

3:01 We can see here automatically,

3:03 this pull request allows for GitHub Actions

3:06 to enable bug fixes, writing tests and code reviews.

3:10 We can change this if we like,

3:11 or we can go ahead and create a pull request

3:14 with the default information. In this pull request, we can see

3:18 that not only have we created

3:20 a YAML file for Claude to operate,

3:23 we also have one for code reviews.

3:24 Here we can see out of the

3:26 box, we have some pretty sane defaults. We can filter

3:29 by authors, we can specify what this is running on.

3:32 But out of the box, we get

3:33 quite a bit of really nice functionality.

3:35 If you'd like to modify the prompt

3:36 that you have in your code review, you can do that here.

3:40 And since this is a file that is tracked by git,

3:42 you can constantly edit this if you need.

3:45 I'm going to go ahead now and merge this in,

3:47 so we can start using Claude Code in GitHub.

3:50 We can go ahead and see right out of

3:52 the box that a Claude GitHub action has actually started.

![claude bot 在 github 上正在 review 代码](https://poketto.oss-cn-hangzhou.aliyuncs.com/22176e7e629685266153462a46f5ecfe.png?x-oss-process=image/quality,q_90/rotate,0)


3:54 This is what we're going to see out

3:56 of the box in our future pull requests.

3:58 It's going to read and analyze files, check code quality,

4:01 identify security considerations, and out of the box,

4:05 we now have a new teammate, Claude,

4:07 to check the work that we

4:08 and our other team members are doing.

4:10 This sometimes takes a little bit of

4:11 time to start, but once this has finished,

4:13 we'll get some detailed assessments from Claude,

4:15 and we'll be able to merge in the pull request

4:17 when we're ready. So it looks like the review is done,

4:19 and depending on the prompt that we give it, we can specify

4:23 how much depth and information we want here.

4:25 We see some things that are working well,


... (省略 96 行) ...


6:16 And here, I can even choose what to prioritize if I'd like.

6:20 But what you're seeing here is the same

6:22 thing we saw just outside of the

6:24 terminal. Not only can we use Claude

6:25 to tackle issues and pull requests,

6:28 we can also use Claude to review code as we saw before.

![claude bot 在github上肝活和日常一样，也会有todo list](https://poketto.oss-cn-hangzhou.aliyuncs.com/43fa5bc729075235a5edf790404381c0.png?x-oss-process=image/quality,q_90/rotate,0)


6:30 As we start to see its plan, we'll notice

6:33 what the changes are that are being

6:35 made, where in the codebase it's proposing things,

6:38 and as we see the pull request, we can start to

6:40 see some of the thinking and logic behind what's being done.

6:43 Seems like this one isn't too tough,

6:44 so it's going to follow these steps,

6:46 test the changes, commit and push those.

6:48 It's now made the commit necessary.

6:50 We can see the underlying description here.

6:53 If we'd like, we can create this pull request,

6:55 or we can just have Claude do all that work for us.

6:58 When we create the pull request.

6:59 We see exactly what was generated in the commit.

7:02 And now, let's go take a look and see what Claude did.

7:05 We can take a look at the underlying files that we changed.

7:08 There wasn't too much here. We can merge this in.

7:10 As we saw before, Claude's also going to take

7:12 some time and review the code that Claude wrote.

7:15 And this can actually be quite helpful because

7:16 as much as we want to trust Claude,

7:18 it's nice to have another Claude double checking its work.

7:21 So it looks like Claude Code

7:22 has approved the task I have here.

7:23 Let's merge this in. And then we'll head back to the terminal

7:26 and make sure to pull down the changes. is that we have.

7:29 So I'll head over to VS Code, pull down the changes.

7:34 And let's see if our front end looks any better.

7:37 And there we have it. The header

7:39 is taken out, the horizontal rows taken out.

7:40 We might want to bring back that

7:42 horizontal row or move this to another place.

7:44 But now we know how to do it,

7:46 not only in the terminal, but also in GitHub.

![claude bot 已经实现了需求](https://poketto.oss-cn-hangzhou.aliyuncs.com/6e4f235a087c0662c99a0159962044dc.png?x-oss-process=image/quality,q_90/rotate,0)


7:49 One more piece of functionality that I want

7:51 to show is something that was recently released,

7:53 which is the ability to add

7:55 what's called a hook to Claude Code.



![claude code cook 机制图解](https://poketto.oss-cn-hangzhou.aliyuncs.com/42a9c56c859ba26b669cd3b7675ed00d.png?x-oss-process=image/quality,q_90/rotate,0)



7:57 If you're familiar here with this idea of

7:59 hooks. This is going to feel very similar.

8:01 The idea is that as we have different operations in Claude Code,

8:05 like executing a tool or something happening after a tool,

8:09 we can inject specific code to run at any

8:12 point in the life cycle of Claude Code's operation.

8:16 Let me show you what I mean

8:17 by that. Back in VS code, I'm going

8:18 to hop in back to Claude again. And

8:21 while we can make these changes manually, I

8:23 want to show you the editor that we have.

8:25 So I'm going to type in slash hooks.

![/hooks](https://poketto.oss-cn-hangzhou.aliyuncs.com/c26aab5a73edf584912095be61d54791.png?x-oss-process=image/quality,q_90/rotate,0)


8:28 manage configurations for tool events.

8:30 What you're seeing might look a little bit scary,

8:33 but it's our obligation to let you know.

8:35 If you are running arbitrary shell commands,

8:38 you have to be very careful about what you're doing.

8:40 There are quite a few different events that we can run hooks.

8:43 Before a tool is executed, we can

8:45 even stop that tool from being executed.

8:48 We can do something after, when a notification is sent,

8:51 when the user submits a prompt, when something stops,

8:53 or even before a subagent concludes its

8:56 response. So we have the ability to

8:58 programmatically to tap in to any of these events.

![有多种 hooks 可供选择](https://poketto.oss-cn-hangzhou.aliyuncs.com/936208b771d5699f98c51d0dacbe33f8.png?x-oss-process=image/quality,q_90/rotate,0)


9:02 I want to show a simple example with a PostToolUse hook.

9:06 Start by adding a matcher. In this matcher,

9:08 I can specify the tools that I want

9:11 to be matched for this hook to run.

9:14 I'm going to add a very, very

9:15 simple example here. Anytime there is a Read

9:18 or anytime there is a Grep,

9:21 I'm going to run a simple terminal command.

9:23 The new hook or command I'm

9:25 going to run is the say command.

9:27 The say command, runs the computer's audio

9:29 and a path for what text you'd like it to say.

![在post-tool hook里实现电脑播报](https://poketto.oss-cn-hangzhou.aliyuncs.com/47ad678ba2e5ccad4c8673c4985a2411.png?x-oss-process=image/quality,q_90/rotate,0)


9:33 So if I've done this correctly, after we have read something

9:36 or use the grep tool to find something

9:38 in a file, our machine should say, all done.

9:41 Let's add this again in our project settings.

9:43 We mentioned earlier the settings.local.json file where we can specify permissions.

9:49 This is also where your hooks live.

9:51 Inside of our .claude,

9:53 we can see in our settings.local.json,

9:56 not only do we have our permissions,

9:58 but we now have a hook that we've defined.

10:00 PostToolUse is the name of the hook,

10:02 the matcher, which if you take out will apply to anything.

10:06 But here, reading or grep,

10:09 go run the command say 'All done!' when we're done.

10:11 Let's try this out. I'm going to quit out of Claude Code.

10:14 I'm going to open it up again.

10:16 read the contents of the run.sh file.

![settings文件内已经更新，测试是否有效](https://poketto.oss-cn-hangzhou.aliyuncs.com/83f0f3ce3650097a17af37cfee5b624c.png?x-oss-process=image/quality,q_90/rotate,0)


10:19 This should use the read tool as expected. All done.

10:22 And once it's done, it notifies us and tells us all done.

10:25 Well, this is kind of a fun little example, you can

10:28 imagine executing code like running tests or running linters

10:31 or potentially stopping tools from being

10:33 used if that's not what we want

10:35 or even having Claude review itself when certain things happen.

10:38 There's a lot you can do with

10:39 hooks and there's so much more that's coming.

10:41 So make sure to look at the

10:42 documentation to see everything you can do.

10:44 And you can always use Claude Code to

10:47 write hooks for you and modify them accordingly.

10:49 In the next section, we'll explore using Claude Code with Jupyter notebooks

10:52 to create visualizations, refactor code, and operate in a slightly different environment.
```


### 10. Creating Web App based on a Figma Mockup.md

```markdown
---
title: Claude Code A Highly Agentic Coding Assistant  DeepLearning.AI
slug: claude-code-a-highly-agentic-coding-assistant-deep-1755233194963
source: https://learn.deeplearning.ai/courses/claude-code-a-highly-agentic-coding-assistant/lesson/vvq28/creating-web-app-based-on-a-figma-mockup
datetime: 2025-08-15T04:46:34.963Z
---

Transcript

0:02 In this last

0:03 lesson, you'll connect Claude to the Figma MCP server

0:06 to import a design mockup to Claude Code and develop the application.

0:10 Let's have some fun.

0:11 Now that we've seen how to use Claude Code to get up to speed on code bases

0:16 to create applications and work across many different environments,

0:20 I want to showcase a really powerful ability for Claude Code

0:23 to work alongside MCP servers, to take mockups from tools like Figma

0:29 and turn them into web applications quickly.

0:32 In order to do that.

0:33 We're going to be making use of the Figma MCP server.

0:36 And in order to do that, you will need a Figma account.

0:39 We'll also provide an alternative if you want to use that

0:42 without subscribing to Figma as dev mode.

0:45 We're also going to be using our Playwright MCP server,

0:49 so that we can analyze a mock up from Figma, generate the necessary HTML

0:54 and then programmatically test that by opening it in the browser

0:58 and taking screenshots of how best to interact with this application.

![使用nextjs初始化项目](https://poketto.oss-cn-hangzhou.aliyuncs.com/fce2025404ca9d907d2c52b9c3780e3b.png?x-oss-process=image/quality,q_90/rotate,0)


1:02 Since I'm building a front end application with a more modern technology

1:06 stack, I'm going to be using Next.js to do that.

1:09 So I'm just going to start by creating a Next.js application

1:13 with the latest version inside of the folder that I'm in.

1:17 I'll follow most of these same defaults, and I'll go ahead

1:20 and let it install the necessary dependencies.

1:23 If you have not worked with Next.js before, that's more than fine.

1:26 It's a couple of command line commands and then will be in the browser

1:29 before you know it.

1:30 While this is installing, let's go take a look at the mockup that we have in Figma.

1:35 In Figma,

1:36 I have a mock right here for a dashboard that I'd like

1:39 to build using Federal Reserve Economic data.

1:42 This mock right here in Figma is not the most detailed in terms

1:46 of all the layers

1:47 and all the analytics behind, but this is enough to get me started.

1:51 What I'm going to do in Figma is first, make sure that I have gone

1:55 to preferences and selected enable dev mode MCP server.

![目标 figma 工程界面](https://poketto.oss-cn-hangzhou.aliyuncs.com/cb9d9eb09861263dbd5542a385d3bb1f.png?x-oss-process=image/quality,q_90/rotate,0)


1:59 Once I have that selected, I'm going to take this particular layer

2:03 that I have and copy it because I'm going to need

2:05 that when I specify what to use with the MCP server.

2:09 Now that I've successfully created this Next.js application, we need to add

2:13 to Claude the two MCP servers that I want to use for Figma and for Playwright.

2:18 I'm going to go ahead and add the necessary

2:20 command here to bring in the MCP server for Figma.

2:24 And then I'll do the same for Playwright.

2:27 So I'm going to add an MCP server for Playwright,

2:30 and that is started locally using the following command.

2:33 And even though we already added this, remember

2:36 we're in a separate project and a separate environment.

2:39 So this does not get applied to every single Claude Code application I built.

2:44 We have to do this for each one to make sure I've done this correctly.

![项目增加 figma mcp](https://poketto.oss-cn-hangzhou.aliyuncs.com/d37d4cb2df691c89b2d45e80415c2b3a.png?x-oss-process=image/quality,q_90/rotate,0)


2:47 I'm going to hop into Claude and I'm going to use the slash MCP command

2:51 to make sure this looks good.

2:52 If I take a look, I can see that both of these are connected.

![查看 mcp 列表](https://poketto.oss-cn-hangzhou.aliyuncs.com/76c4e9ced5fc43f785f985853d074d3d.png?x-oss-process=image/quality,q_90/rotate,0)


2:55 And if I take a look at the dev mode MCP server, I can see

2:58 there are five tools available to get underlying code, to get an image,

3:03 to get design rules around a particular mock up that I have in Figma.

3:08 Now that we've connected to both of our MCP servers,

3:11 let's go and ask Claude to use the following Figma mockup

3:14 and the Figma MCP server to analyze and build the underlying code necessary.

3:19 We'll ask it to use the recharge library for creating charts,

3:22 and then we'll check how this application looks using the Playwright MCP server.

![prompt：cc + figma-mcp](https://poketto.oss-cn-hangzhou.aliyuncs.com/02da78ebb7f6464bd44e8219fc9ae94f.png?x-oss-process=image/quality,q_90/rotate,0)


3:31 But before I do this, I want to go ahead and make a quick change.

3:35 If you are able to make this change and you're

3:38 not on the pro plan, you can use Opus as a different model.

3:41 If not, Sonnet will still do a fine job, but Opus will do

3:44 slightly better for a little bit more of a complex task.

3:47 Once I have switched to that model,

3:49 let's go ahead and run our prompt and see how it does.

3:52 Well, first need to connect to our MCP servers.

3:55 Make sure we use the correct mock up and the tools necessary

3:58 to read the underlying code to power this mock.

4:01 Here we can see we're using the Get image tool from the Figma dev MCP server,

4:05 followed by the Get Code tool to get the underlying code behind that

4:09 mock. We'll then make sure we install

4:11 the necessary dependencies using npm or the package manager.

4:15 And here we're going to see it's not installed.

4:17 So Claude Code is most likely going to ask us to install that.

4:20 We'll do so and continue onwards.

4:22 Since we're inside of this Next.js application.

4:25 We're going to be doing the majority of the work in the app folder.

4:28 We'll analyze any global CSS and here start creating the main dashboard

4:33 structure. Here we're going to add a little bit of metadata.

![cc 正在修改网站meta信息](https://poketto.oss-cn-hangzhou.aliyuncs.com/63056053e2f333f7bbee1a4feeb613a6.png?x-oss-process=image/quality,q_90/rotate,0)


4:35 And this looks good.

4:37 So for future edits I'll just let Claude go ahead and run those.

4:40 We're now going to create the dashboard layout

4:42 and build this with more of a component based architecture in react.

4:46 Now that we've created the underlying structure, let's start to make sure things

4:49 look as expected.

4:50 And since I've already run the server here, I'm just going to say

4:54 don't run the server.

4:55 It's already running. Continue on.

4:57 We're now going to test with Playwright and take a look at how things are.

5:00 We'll go ahead and navigate to localhost 3000.

5:03 Take a picture of that as well.

5:04 And let's go ahead and let it take a screenshot.

5:05 We can see here in Playwright.

5:07 So far it's looking pretty good compared to the mock.

5:10 We've got a little extra styling on some of these bars,

5:12 but this is a pretty good start from where we began with the mock right over here.

5:16 In fact, I'd actually argue this looks a little bit nicer.

![cc 已经复刻了目标 figma（甚至效果更好）](https://poketto.oss-cn-hangzhou.aliyuncs.com/bea5dbd2f2da2faa8bdb70a9aa414140.png?x-oss-process=image/quality,q_90/rotate,0)


5:20 We're still going to see some changes that are being made.

5:22 There's a layout in the sidebar

5:23 that needs to be modified, and we can always have Claude

5:26 go back and forth and iterate across this particular mock.

5:29 One important thing to mention is that this mock in Figma does

5:32 not have a tremendous amount of layers and underlying components.

5:36 So a lot of this is going to depend on the quality of the underlying mock

5:40 that you have.

5:41 But this is a really good start with very minimal amount of time.

5:44 We can see here what's been built and what's closely matching.

5:47 Now let's take a look at how things are.

5:49 We can see with a little bit of work from the model and using MCP servers

5:52 to verify visualizations and build off our mocks.

5:56 Things that might have taken days to do and build from scratch

5:59 can be done over the course of minutes.

6:01 So you might be wondering what comes next here.

6:03 This mock that we have is just the start of what you might imagine building.

6:08 And this data is actually available through an API.

6:12 So I could ask Claude Code, populate these charts

6:15 with real world data from the Federal Reserve Economic data.

6:19 We'll go ahead and ask Claude Code to use one of its web search

6:22 tools to go ahead and find information to update with actual data.

6:27 Here we'll look at CPI, unemployment yields and so on.

6:31 But you can imagine this might be data that you're fetching from a back end.

6:35 But here we're going to showcase Claude's ability to research

6:38 how to work with the API documentation how to fetch data.

6:42 And it might be possible that we need an API key to do so.

6:45 So as we start doing some of this research, Claude is going to let us know

6:48 what we need to make sure things are working as expected. In that mock,

6:53 there were a couple other

6:54 pieces in the nav bar that were just meant for visualizations,

6:58 but we can add whatever underlying functionality we want next.

7:01 So after it's done some research, it realizes that in order for me

7:05 to fetch actual data from the Federal Reserve,

7:08 I'm going to need to put in an API key.

7:11 I can go ahead to my account, get an API key.

![确认 Fred API Key](https://poketto.oss-cn-hangzhou.aliyuncs.com/3f89175ee96e84813134ef8ddaae2fd6.png?x-oss-process=image/quality,q_90/rotate,0)


7:16 This is a relatively simple process that you can see here.

7:19 Once I have my API key, it's going to start writing

7:22 additional code for me to fetch data and display data visually.

7:27 So I'm going to go ahead and update my API key inside of here.

7:35 Now that I've updated the API key, let's see where cloud is at

7:39 with building additional data.

![在本地环境变量中更新 API Key](https://poketto.oss-cn-hangzhou.aliyuncs.com/1228d82156b824e7d1651e7ca23fb3d8.png?x-oss-process=image/quality,q_90/rotate,0)


7:41 It's now written a service to fetch economic data.

7:44 We're now going to update the dashboard and fetch real data using our API.

7:56 We're going to test this in Playwright.

7:57 And we're going to go ahead and then take a look at what we have in the browser.

8:00 We'll go see how this looks visually.

8:02 And if there's any underlying code that needs to be modified to make

8:05 this more visually appealing,

8:17 with just a little bit of prompting,

8:18 we can go from a mock with some fake data

8:21 to actually using real world information across a true data source for this data.

8:26 When we're done, we'll head back to localhost 3000.

8:29 Take a look at what we have and see that the data

8:31 that we'll be fetching is not something that's actually fictitious,

8:35 but real unemployment, ten year treasuries and so on.

8:38 We set up quite a bit here

8:39 to proxy our requests and quite a few more interactive features.

8:43 So let's go see what that looks like.

8:45 We've gone from our mock here with some fake data

8:48 and not a lot of functionality to something quite powerful.

8:51 In just a short period of time.

8:52 The data we're loading here has data that is actually reflective

8:56 of real world information.

8:58 And as we imagine adding more functionality,

9:01 we can tab through for what this will look like.

9:03 But with just a small amount of work with an MCP server pulling data

9:07 from real world environments and building UI from Figma mocks,

9:11 you can start to imagine how quickly front end development can go,

9:15 especially for building powerful real world interfaces.

9:18 You might want to verify that this data is actually coming from the source,

9:22 and we built that here with this detailed functionality.

9:25 So we can easily see where this data is coming from, what things look like,

9:30 and track that back to the dashboards that we're building as well.

9:33 So right here we're just showing some key indicators.

9:36 But maybe the next thing I want to do is start building my own interface or use

9:40 another Figma mark for things like inflation, employment and so on.

9:44 So we'll start with this piece of data, but I'd love to see what else

9:47 you can build using this interface and all the data at your fingertips.
```


### 12. Prompts & Summaries of Lessons.md

```markdown
---
title: Claude Code A Highly Agentic Coding Assistant  DeepLearning.AI
slug: claude-code-a-highly-agentic-coding-assistant-deep-1755233480230
source: https://learn.deeplearning.ai/courses/claude-code-a-highly-agentic-coding-assistant/lesson/hhfj3/prompts-&-summaries-of-lessons
datetime: 2025-08-15T04:51:20.229Z
---

# Prompts & Summaries of Lessons

This note includes the links to the prompts used in the lessons, additional resources and a summary of Claude Code features.

**Note**: To mark this reading item as complete, make sure to scroll down to the end and click on "Mark as Complete".

## Prompts

Here are the links to the lessons' notes and prompts:

-   [Prompts of Lesson 2: Setup & Codebase Understanding](https://github.com/https-deeplearning-ai/sc-claude-code-files/blob/main/reading_notes/L2_notes.md)
-   [Prompts of Lesson 3: Adding Features](https://github.com/https-deeplearning-ai/sc-claude-code-files/blob/main/reading_notes/L3_notes.md)
-   [Prompts of Lesson 4: Testing, Error Debugging and Code Refactoring](https://github.com/https-deeplearning-ai/sc-claude-code-files/blob/main/reading_notes/L4_notes.md)
-   [Prompts of Lesson 5: Adding Multiple Features Simultaneously - Using Git Worktrees](https://github.com/https-deeplearning-ai/sc-claude-code-files/blob/main/reading_notes/L5_notes.md)
-   [Notes for Lesson 6: References to GitHub Integration & Hooks](https://github.com/https-deeplearning-ai/sc-claude-code-files/blob/main/reading_notes/L6_notes.md)
-   [Prompts of Lesson 7: Refactoring a Jupyter Notebook & Creating a Dashboard](https://github.com/https-deeplearning-ai/sc-claude-code-files/blob/main/reading_notes/L7_notes.md)
-   [Prompts of Lesson 8: Creating Web App based on a Figma Mockup](https://github.com/https-deeplearning-ai/sc-claude-code-files/blob/main/reading_notes/L8_notes.md)

## Additional Resources

To learn more about these features as well as other features, you can check:

-   [Claude Code Documentation](https://docs.anthropic.com/en/docs/claude-code/overview)
-   [Claude Code Common Workflows](https://docs.anthropic.com/en/docs/claude-code/common-workflows)
-   [Claude Code Best Practices](https://www.anthropic.com/engineering/claude-code-best-practices)
-   [Claude Code Use Cases](https://www.anthropic.com/news/how-anthropic-teams-use-claude-code)

There's also a great course on Anthropic Academy that you can check out to see more examples with Claude Code:

-   [Claude Code in Action](https://anthropic.skilljar.com/claude-code-in-action)

## Summary of Claude Code Features

### Managing Project Memory

-   `/init`: Claude Code scans your codebase and creates CLAUDE.md file inside your project directory.
    
    -   CLAUDE.md guides Claude through your codebase, pointing out important commands, architecture and coding style. It's automatically included in the context each time you launch Claude Code.
    -   Here's an [example](https://github.com/https-deeplearning-ai/ragchatbot-codebase/blob/main/CLAUDE.md) of a CLAUDE.md file generated by `init` for the RAG chatbot example.
-   `#`: Use `#` to quickly add a memory. Useful when you see Claude Code repeats an error.
    
    -   **Example 1**: since the project is a `uv` project, we added these to CLAUDE.md file using `#`:
        -   `#`use uv to run python files or add any dependencies
    -   **Example 2**: you can inform Claude Code about the database schema, in this case since you have a vector database, you can inform Claude Code about the collections stored in the vector database:
        -   `#`The vector database has two collections:
            -   `course_catalog`:
                -   stores course titles for name resolution
                -   metadata for each course: title, instructor, course\_link, lesson\_count, lessons\_json (list of lessons: lesson\_number, lesson\_title, lesson\_link)
            -   `course_content`:
                -   stores text chunks for semantic search
                -   metadata for each chunk: course\_title, lesson\_number, chunk\_index

### Summary of Claude Code Commands

| Command | Description |
| --- | --- |
| `/clear` | clears current conversation history |
| `/compact` | summarizes current conversation history |
| `ESC` | interrupt Claude to redirect or correct it |
| `ESC ESC` | rewind the conversation to an earlier point in time |
| `@` | Mention files with `@` to include its content in your request |
| `/mcp` | Manage MCP connection & check available MCP servers with their provided tools ([MCP with Claude Code](https://docs.anthropic.com/en/docs/claude-code/mcp)) |

You can use regular bash command within Claude Code, but you need to start the command with `!` (for example: `!pwd`). You can type `exit` to quit Claude Code.

| Shortcuts | Description |
| --- | --- |
| `shift`+`tab` | switch between planning and auto-accept mode |
| take a screenshot | `cmd`\+ `shift`\+ `ctrl` + `4` (Mac) or `Win` + `Shift` + `S` (Windows) |
| paste a screenshot | `Ctrl` + `V` (might not work on Windows) |

### Additional Claude Features

-   **Extended Thinking Mode**
    
    For complex tasks (e.g., complex architectural changes, debugging complicated issues), you can use the word "think" to trigger [extended thinking mode](https://docs.anthropic.com/en/docs/claude-code/common-workflows#use-extended-thinking). There are several levels of thinking: "think" < "think hard" < "think harder" < "ultrathink." Each level allocates more thinking budget for Claude.
    
-   **Use of subagents**
    
    You've learned that one of the out-of-the-box tools for Claude Code is **Task**, which Claude Code can use to launch subagents for complex multi-step tasks. You can explicitly ask Claude Code to use subagents to brainstorm ideas or to investigate multiple aspects of a question or a problem you want to solve. These built-in agents are of general purpose.
    
    You can also create your customized specialized subagents. Each subagent has its own context window, and you can define a custom system prompt and specific tools for each subagent. This part is not covered in this course, but you can check the details in the documentation [here](https://docs.anthropic.com/en/docs/claude-code/sub-agents).
```


### 05. Adding Features.md

```markdown
---
title: Claude Code A Highly Agentic Coding Assistant  DeepLearning.AI
slug: claude-code-a-highly-agentic-coding-assistant-deep-1755232992543
source: https://learn.deeplearning.ai/courses/claude-code-a-highly-agentic-coding-assistant/lesson/zzhtb/adding-features
datetime: 2025-08-15T04:43:12.543Z
---

Transcript

0:02 Now that you have an understanding

0:03 of the chatbot codebase, let's add features to the UI

0:06 and implement a new tool for the chatbot.

0:09 Now that we've gotten up to speed on this codebase,

0:12 let's talk a little bit about

0:14 some features we might want to add.

0:16 We saw before, in this application,

0:18 when we ask for an outline of a course,

0:21 we get some really detailed information

0:23 and we even see some of the sources that are referenced.

0:27 At the same time, when we see

0:29 these sources that are referenced, it would be really nice

0:32 to be able to click on these as links and go to

0:35 the source of truth.

0:37 So we want to build an interface

0:39 where the front end and back end

0:41 are correctly rendering links to show where

0:44 this data is coming from

0:46 and not just some text.

0:48 So let's hop over to Claude and talk

0:50 a little bit about how to get started.

0:52 What we're going to do here instead of

0:54 just asking Claude to implement the feature necessary,

0:57 we're going to make use of two important pieces.

1:00 The first one is referencing the correct file,

1:03 and the second is using plan mode.

1:06 When we talk about referencing the correct file,

1:08 Claude Code is only as good

1:10 as the context that you give it.

1:12 So when you ask Claude Code to make changes,

1:15 it's important to make sure that we're figuring

1:18 out the right files we need to modify.

1:20 We can have Claude Code try to figure this out,

1:23 but if we know out of the box

1:25 what files need to be modified, giving

1:28 in Claude Code this context right

1:30 away makes the tool much more

1:31 efficient. So let's see how that's done.

1:34 I'm going to open up Claude Code and to reference a file,

1:37 I simply use this at and tag that file.

1:41 For a folder, I can reference files inside.

1:44 For a file directly, I can go ahead

1:47 and even use tab to complete for the full file name.

1:50 With that in mind,

1:52 let's talk next about the second

1:54 important piece when building features or making

1:57 larger changes. Instead of having Claude trying to figure out what

2:01 needs to be done and write the code right away.

2:04 We're going to follow a slightly

2:06 different pattern. We're going to plan first.

2:08 We're going to have Claude create a detailed

2:11 plan for what changes need to be done.

2:14 And if we approve that plan,

2:16 we're then going to have Claude Code

2:17 make changes to quite a few files.

2:19 When you have slightly larger changes to make,

2:22 we always recommend starting with plan mode

2:25 so you can give Claude the opportunity

2:27 to figure out what needs to be done

2:29 before it needs to make those changes. To activate plan mode,

2:33 I'm going to press shift tab twice.

2:35 And we'll see here that plan mode is on.

2:38 Let's showcase what needs to be done. I'm going

2:39 to bring in a prompt that I have here,

2:41 and I'm going to ask it

2:43 to build an interface with source citations.

2:46 You can notice here that I'm referencing the correct files

2:49 as well as referencing other files where changes need to be made.

2:53 So let's give Claude the opportunity to come up

2:56 up with a plan for how to solve this particular problem.

2:59 As always, it's going to read through

3:01 the files that it thinks are most necessary.

3:03 It's going to trace its way from the front end

3:06 to the back end and understand what needs to be implemented.

3:09 Once we finish getting a plan, we're going to have the opportunity

3:12 to either approve it or to give Claude

3:14 some feedback for what might need to be changed.

3:17 But here, Claude is not directly writing any code.

3:21 As we see here, we can accept and

3:23 then continue to auto-accept edits so we can

3:25 don't have to keep asking for permission.

3:27 We can manually approve them or we

3:29 can tell Claude to change the

3:30 plan. Taking a quick look at this,

3:32 I feel pretty good about what we need to do.

3:34 So let's use that plan with our auto-accept edits.

3:37 If you ever want to turn this on on its own,

3:40 you can press shift tab just one time.

3:42 We'll see the to-do list necessary.

3:45 We'll see what changes need to be made.

3:47 And now we're going to let Claude Code

3:49 write to the files that it seems necessary,

3:51 and then we can test that the implementation works correctly.

3:54 correctly. We'll see here, files are being modified,

3:57 changes are being made to the codebase.

4:00 And since we added the auto

4:01 accept, we don't have to keep giving

4:03 permission over and over.

4:05 Very common workflow that we see is users start by asking

4:10 for permission each time.

4:11 And as more trust is given by the human to Claude Code,

4:15 the auto-accept edits come on a bit more.

4:17 We can see here finally, that we

4:19 can start the application to test the implementation.

4:22 But in fact, the server is running already.

4:25 So I'm just going to tell Claude, no, thank you.

4:27 I'll say right off the that, the server is running.

4:30 No need to start it yourself.

4:32 If I want Claude Code to always do that,

4:35 this is a great opportunity to just

4:37 put something into the CLAUDE.md file as well.

4:40 Now that I've let Claude Code know that, it's

4:42 going to tell me the changes that have been made.

4:44 So let's test this. Now let's try asking the same question.

4:48 Let's ask for an outline of a course.

4:51 And if this has been built

4:52 correctly, you should be able to see

4:54 links below for each one of these particular features.

4:58 If I take a look, right here I have links

5:01 that will take me to the right place,

5:03 but the interface is a little bit difficult to see

... (省略 314 行) ...


12:07 content. So let's go and ask Claude Code

12:10 using the Playwright MCP server

12:12 visit the page that we're at

12:15 and view the new chat button.

12:18 I want that button to look the same as the other

12:22 links below for Courses and Try Asking.

12:27 Make sure this is left aligned

12:30 and that the border is removed.

12:33 Before it starts taking this action,

12:35 it's going to ask me for approval for these particular tools.

12:39 We'll see that it will visit

12:40 that page, take a screenshot and do do what's necessary.

12:44 Let's follow that and not ask for

12:46 permission each time to use this particular tool.

12:49 We can see here that the browser has opened a

12:52 new tab programmatically to our page to take a screenshot.

12:56 We'll ask Claude Code to take that screenshot

12:58 and analyze what it sees.

13:01 Here it can see the exact issue that's happening and instead of

13:05 us manually having to take the

13:07 screenshots necessary, it can programmatically fix itself.

13:09 We could have a more specific prompt as well, that keeps asking

13:13 Claude Code to make those changes necessary.

13:15 Since I don't have auto accept on, I can see the change

13:18 that's being made in VS Code.

13:20 And right out of the box, I don't

13:22 see a border and background with this

13:23 new change. That looks good to me.

13:25 Let's make those changes and continue making other changes.

13:28 I can see left align looking good.

13:31 and any other changes that need to be made here.

13:34 It's going to take another screenshot to

13:36 verify that the changes it's made look correct.

13:38 that it has the right icon prefixes used.

13:41 match other sections. With that in

13:43 mind, let's go see how he did.

13:45 I'm going to refresh the page. and it's looking good.

13:48 It's got an extra plus here. So why don't we go ahead

13:50 and ask it to take that

13:52 out. But it's left aligned and it's

13:53 using the icon that we like before.

13:56 So let's go ahead and fix this up and say,

13:59 there are now two plus icons, remove the

14:01 one closer to the text "+ New Chat"

14:04 We can see here there's already a plus in the HTML content,

14:07 so we'll remove that and let's see

14:09 what's done here. So instead of adding

14:11 that extra plus, we can see here what's being done.

14:13 If we need another snapshot, we

14:15 can visit and take a snapshot necessary.

14:18 As we can see here, Claude Code

14:20 saw there was not an open tab, so it fixed itself,

14:23 opened it up again and took the necessary screenshot.

14:27 Let's see what that looks like now. Much better.

14:30 As you can imagine, building complex interfaces

14:33 using tools like MCP playwright

14:36 makes building, designing and testing a breeze. We've made some really

14:40 nice front end changes. Let's now go and visit the back end.

14:43 Like we did before, we're going to start

14:46 fresh and instead of building off of this

14:48 conversation, we're going to start with a new one.

14:50 So let's clear the conversation history and start again.

14:54 This time, we want to build some features on the back end.

14:58 So let's put in a prompt, talk

14:59 about what's going to be done here.

15:01 I need to add another tool

15:03 that allows me to visit a particular course

15:07 and for each of those courses, see the

15:09 lesson number and the lesson title and description about that as well.

15:14 Right now, the data that I get

15:16 when I take a look at a course

15:18 is relatively high level. Let's see what I mean.

15:21 What we're going to ask Claude Code to do

15:23 here is to make a change to our search\_tools.py file.

15:27 Let's take a look at that. And

15:28 in this file, we can see right now

15:30 that we just have one tool for searching

15:34 content and getting details about that particular course. This second tool

15:39 is going to allow us to get more descriptive information

15:43 for each of the lessons in these courses.

15:45 So let's see what Claude can do. As we've done previously,

15:49 let's make a plan and make

15:51 sure we're first okay with that plan

15:53 before we start making changes to individual files.

15:56 Claude Code can see the current

15:57 architecture, had to implement the outline tool,

16:00 and since we have that CLAUDE.md

16:02 previously, it's going to more quickly be able

16:04 to understand what needs to be done.

16:07 We can take a look at what needs to be implemented,

16:09 we can make sure that we're doing

16:11 the right things in the right files.

16:12 We can see that once we create this tool,

16:15 we update the system prompt to make

16:17 sure that we get that additional data,

16:19 and then we register that tool in our RAG system.

16:22 As always, if there's anything we want to

16:24 change or suggest, we can do that now.

16:27 But let's see what Claude Code can do for us.

16:29 If this works as expected,

16:31 we should be able to ask questions about a

16:34 course and get much more detail for those particular

16:37 lessons in the course.

16:39 We can see here that not only are we

16:42 modifying the underlying Python code, but also the system prompt

16:44 and here we're registering that new tool that we've made.

16:48 Once we finished our to-do list,

16:50 we can head back to the browser

16:52 and see what things look like

16:54 and if this has been implemented correctly.

16:56 We'll see a nice summary of what's been made

16:58 and we can always change things at any point in time.

17:01 Back in the browser, let's go ahead and try asking

17:04 for some information about a course.

17:06 If this works as expected.

17:08 We should be able to get more detailed information

17:11 including a link for that particular course.

17:14 Here, we can see the names of the lessons

17:16 and if we would like, we can even build additional functionality

17:20 to get sources for each one of those.

17:22 In the next lesson, we'll talk about what happens

17:25 when things go wrong and how we can use

17:27 Claude Code to debug, to write tests,

17:29 and make sure that we feel confident in

17:32 the software that we're writing alongside Claude Code.
```


### 02. What is Claude Code?.md

```markdown
---
title: Claude Code A Highly Agentic Coding Assistant  DeepLearning.AI
slug: claude-code-a-highly-agentic-coding-assistant-deep-1755232825677
source: https://learn.deeplearning.ai/courses/claude-code-a-highly-agentic-coding-assistant/lesson/rrigm/what-is-claude-code?
datetime: 2025-08-15T04:40:25.677Z
---
![](https://poketto.oss-cn-hangzhou.aliyuncs.com/3f9021a06982247afd8d0996319c5e1a.png?x-oss-process=image/quality,q_90/rotate,0)


0:02 In this first lesson, we'll go

0:04 through the agentic workflow of Claude Code,

0:06 the tools it uses to navigate your codebase,

0:09 and the memory it keeps across sessions. Let's dive in.

0:12 So let's talk a little bit about what Claude Code actually is.

![](https://poketto.oss-cn-hangzhou.aliyuncs.com/63580cffd9e1dbbcfbca9fabcc3bef97.png?x-oss-process=image/quality,q_90/rotate,0)



0:17 When we talk about agentic systems,

0:20 we think a lot about a model, a set of tools,

0:23 and some environment to run those tools.

0:26 Models are great at handling input and returning output.

0:30 But in many situations, those models don't know about your codebase,

0:35 how to find files, and how to handle multiple tasks.

0:39 So instead of just talking directly to a model,

0:41 we're going to provide a very lightweight harness for that model.

0:45 And through the command line, we're going to

0:48 use that harness to leverage the model's intelligence

0:51 to perform complex coding tasks.

0:53 So instead of giving a task directly to the model

0:57 and trying to find all kinds of information in a codebase.

1:00 We're going to provide a set of tools.

1:02 We're going to provide an environment

1:05 and a couple other pieces of functionality

1:08 to enable the model

1:10 to come through codebases and solve much more complex problems.

1:13 What are those pieces of functionality that we're talking about here?

1:16 Enabling the model to have memory,

1:19 enabling our model here to remember preferences of the user

1:23 and the codebase we're going through or the task at hand.

1:27 also going to give the model an environment

1:30 where it can figure out what data it needs,

1:33 formulate a plan and then take action.

1:35 With just a small amount of code,

1:37 we can leverage the model's intelligence to achieve quite remarkable results.

1:42 With Claude Code, your options

1:44 are Opus or Sonnet, depending on the complexity,

1:47 the kind of task you're handling, and your subscription.

![](https://poketto.oss-cn-hangzhou.aliyuncs.com/986edc400a6172c8751cec330b0a5ae0.png?x-oss-process=image/quality,q_90/rotate,0)


1:50 When we talk about what Claude Code can do,

1:53 it's very tempting to just think this is the tool for

1:56 for writing lots of code. But as we progress in this course,

1:59 we're actually going to start with one of the most powerful features

2:03 of Claude Code, which is its ability

2:06 to discover, explain, and design.

2:09 Before you start writing code with Claude Code,

2:12 use it as a way to get

2:14 up to speed on a code base.

2:15 We'll talk quite a bit about writing code with Claude Code,

2:19 but we'll also talk about ways in which you can use it

2:22 outside of the terminal in environments like GitHub. We'll talk a bit

2:25 bit about refactoring, debugging errors

2:28 and where this tool really shines.

2:31 Not only is this useful for coding,

2:33 but also across data analysis and any environment

2:37 where the model's intelligence can create compelling

2:41 visualizations, assets or deliverables for you.

2:44 We mentioned that we give the model a harness.

![](https://poketto.oss-cn-hangzhou.aliyuncs.com/0e94ba808dd948c1ee74ee0ab0d7d582.png?x-oss-process=image/quality,q_90/rotate,0)


2:47 We give the model an environment

2:49 to gather context and take an action.

2:52 We talked a bit about the

2:53 memory that we provide to the model.

2:54 And in a little bit, we'll talk

2:56 about what that underlying memory looks like.

2:58 Now, let's talk about the tools

3:01 or additional functionality that we let the model know about.

![](https://poketto.oss-cn-hangzhou.aliyuncs.com/58a8e5a43a6d4f67b7a18d438d044dc2.png?x-oss-process=image/quality,q_90/rotate,0)


3:04 To give an illustration of tool use,

3:06 you can imagine that the user asks

3:08 what code is written in a particular file.

3:11 The model does not know how to navigate or

3:14 find files, and that's where tool use comes into play.

3:17 Out of the box, Claude Code

3:19 provides a relatively small list of

3:21 tools. One of those being the ability

3:23 to read a file. Now that the model knows what to do,

3:27 it can go ahead and read that file,

3:29 get the contents of that file,

3:31 and return the data to a user.

3:33 This ability of tool use allows the model to go

3:36 from a simple assistant to an extremely sophisticated agentic tool.

3:40 We mentioned some of the tools

3:42 that Claude Code comes built in with.

3:44 Here is a list of the tools that we have.

![claude code tools](https://poketto.oss-cn-hangzhou.aliyuncs.com/f55588d920cb9a50b06f307ee2fe886b.png?x-oss-process=image/quality,q_90/rotate,0)


3:46 Some of those for editing across different kinds of files.

3:49 Some of those for reading across different files.

3:52 and some for doing additional actions

3:55 like finding patterns,

3:57 searching things across the web,

3:59 and even creating or running sub-agents

4:02 to handle very difficult and challenging tasks.

4:05 Finally, since we're in the command line,

4:07 we're going to need a tool to execute bash or shell commands.

![](https://poketto.oss-cn-hangzhou.aliyuncs.com/cd7553aaea8c3ab9847fe81e1baef150.png?x-oss-process=image/quality,q_90/rotate,0)


4:12 Tool use is what allows Claude Code

4:15 to gather the context and information that it needs.

4:18 This allows Claude Code to tackle harder problems.

4:21 It also allows Claude Code

4:23 to not have to index your entire code base

4:25 and lead into potential security concerns.

4:28 Finally, Claude Code is quite extensible.

4:30 While you just saw the list of tools

4:32 that Claude Code comes built in with,

4:34 you can also add additional tools

4:36 by connecting to MCP servers.

4:39 MCP, or the model context protocol,

4:42 is an open-source model agnostic protocol

4:44 that allows for data and AI systems to communicate easily.

4:48 These MCP servers can

4:51 add functionality to Claude Code

4:53 for a variety of different tasks

4:55 and we'll explore a few of them over this course.

![](https://poketto.oss-cn-hangzhou.aliyuncs.com/1023eca732154acc9a4f10f94e543e81.png?x-oss-process=image/quality,q_90/rotate,0)


4:58 I want to take a little more time to

5:00 talk about what we mean by not indexing a codebase.

5:03 Instead of creating a structured representation of the codebase

5:08 and constantly analyzing that,

5:10 Claude Code instead uses a feature called agentic search.

5:13 Instead of requiring that that codebase is sent to a server

5:17 and potentially leaving the ecosystem that you're in,

5:20 Claude Code instead uses

5:22 one or many different agents and sets of tools

5:26 to find what it's looking for in your codebase.

5:29 This allows your code to not

5:31 have to be completely added to context

5:34 or to have to leave the ecosystem that it's in,

5:37 which can create certain security considerations.

![](https://poketto.oss-cn-hangzhou.aliyuncs.com/a105ee24f593a90650dec2258d84fa6f.png?x-oss-process=image/quality,q_90/rotate,0)


5:40 When we talk about the memory of Claude or its ability

5:43 to remember what has happened in previous conversations

5:46 or across all kinds of

5:49 actions. This is done using a markdown file

5:52 called claude.md

![](https://poketto.oss-cn-hangzhou.aliyuncs.com/b302ff1c4aecb6784e353817970ab5fe.png?x-oss-process=image/quality,q_90/rotate,0)


5:54 In your claude.md file, you can define common configurations

5:58 or style guidelines.

5:59 These files get automatically loaded

6:02 into context when launched.

6:04 The conversation that you have with claude code

6:07 is stored locally on your machine.

6:09 You can clear that over the course of a conversation,

6:13 so you can start with a new context window.

6:16 But if for some reason, you need to continue

6:18 that previous one or resume the

6:20 earlier conversation, you can do so easily.

![](https://poketto.oss-cn-hangzhou.aliyuncs.com/3454998310c95e9ec4444d292f99706c.png?x-oss-process=image/quality,q_90/rotate,0)


6:24 I'm going to head over to the

6:25 terminal that I have inside of VS Code.

6:28 And we can see I have a

6:29 folder here called demo with nothing in it.

6:31 So let's start by opening up Claude Code using the claude command.

6:35 Depending on where this file is, and especially the first time,

6:39 it may ask if I trust the

6:41 files in this folder, which I do.

6:43 We've gotten a couple nice tips here for getting

6:45 started, but I'm just going to start with a very simple prompt.

6:48 Make a cool visualization for me.

6:51 I'm just getting started. What we're

6:52 going to see here is Claude Code

6:54 start to make a to-do list of actions to take.

6:57 You can imagine this task might be to search across a codebase,

7:00 to edit files, to write tests, to deliver insights,

7:04 or in our case to create a visualization.

7:07 Depending on how Claude is feeling,

7:09 this might be particles or fireworks or something else,

7:11 but I just want to show you how quickly

7:13 out of the box you can

7:14 start to see changes with Claude Code.

![](https://poketto.oss-cn-hangzhou.aliyuncs.com/1c59a8a371cb7cbb0345d3c81c9f35ab.png?x-oss-process=image/quality,q_90/rotate,0)


7:16 Since we're doing this inside of Visual Studio Code

7:19 and Claude Code has an integration with that editor,

7:22 we're going to see visually the changes that are being made.

7:26 I'll accept those and in future editions,

7:28 I'll let Claude Code do that without requesting permission from me.

7:32 We can see here, we have a visualization that's built.

7:35 Let's go ahead and open it in the browser.

7:37 I'll ask Claude Code to do that for

7:39 me. It will confirm. This is the command.

7:40 Let's go see what it looks like.

![](https://poketto.oss-cn-hangzhou.aliyuncs.com/e38826af07da436f587e1f18a11868ef.png?x-oss-process=image/quality,q_90/rotate,0)


7:42 And here we are with our visualization.

7:43 Can add some particles.

7:45 lookin' a bit better. You can toggle the animation,

7:48 see what's going on, and clear what we have here.

7:51 We can expand on this as much as we want.

7:53 We can change the functionality, we

7:55 can add whatever we want right here.

7:57 But I just want to show you

7:59 out of the box how seamless it is

8:01 to get up and running with this particular tool.

8:03 In the next lesson, we'll explore how

8:05 to use Claude Code across a larger codebase

8:07 and take a step back and see just how powerful it is

8:10 for explaining larger and more complex code bases.
```


### 00. Overview.md

```markdown
---
title: Claude Code A Highly Agentic Coding Assistant  DeepLearning.AI
slug: claude-code-a-highly-agentic-coding-assistant-deep-1755234900992
source: https://www.deeplearning.ai/short-courses/claude-code-a-highly-agentic-coding-assistant/?utm_campaign=anthropicC3-launch&utm_medium=headband&utm_source=dlai-homepage#course-outline
datetime: 2025-08-15T05:15:00.992Z
---

## What you'll learn

-   Use Claude code to explore, develop, test, refactor, and debug codebases.
    
-   Extend the capabilities of Claude Code with MCP servers such as Playwright and Figma MCP servers.
    
-   Apply Claude Code best practices to three projects: exploring and developing the codebase of a RAG chatbot, refactoring a Jupyter notebook for e-commerce data and transforming it into a dashboard, and building a web app from a Figma mockup.
    

## About this course

Learn the best practices for agentic coding with Claude Code in this new short course, **Claude Code: A Highly Agentic Coding Assistant**, built in partnership with Anthropic, and taught by Elie Schoppik, Head of Technical Education.

AI coding assistants have evolved rapidly, from tools that help with occasional coding questions and code completion to tools that can autonomously generate code. Claude Code pushed the degree of autonomy by acting as a highly agentic assistant that can plan, execute, and improve code with minimal human input, for more than a few minutes. You and your teammates can now run multiple instances of Claude code and work in parallel on different parts of the codebase. However, coordinating all this involves a set of best practices that can significantly boost your productivity.

In this course, you’ll learn best practices for using Claude Code to improve your coding workflow. You’ll learn key tips on how to provide Claude Code with clear context, such as specifying the relevant files, clearly defining the features and functionality, and connecting Claude Code to MCP servers.

You’ll apply these best practices to three examples: exploring a RAG chatbot codebase, analyzing ecommerce data in a Jupyter notebook, and creating a web app based on a Figma mockup.

In detail, using Claude Code, you’ll: 

-   Understand the underlying architecture of Claude Code, the tools it uses to navigate your codebase, and how it stores memory across sessions.  
-   Explore and understand the codebase of a RAG chatbot and how information flows between the frontend and the backend.
-   Initiate a CLAUDE.md file inside your project directory containing information and guidelines about your codebase that Claude Code can remember across sessions. 
-   Get context into Claude Code by mentioning the relevant files and providing screenshots or images, and control the context using escape, clear, and compact commands.
-   Add features to the frontend and backend of the  RAG chatbot: ask Claude Code to plan first to improve its performance, use thinking mode for harder tasks, and brainstorm ideas using Claude Code’s subagents.
-   Write tests to evaluate the RAG chatbot functionalities, and refactor parts of the chatbot.  
-   Use git worktrees to run multiple Claude sessions simultaneously, each focused on adding an independent feature to the chatbot.
-   Fix Github issues, and create, review and merge Github pull requests using Claude Code’s Github integration.   
-   Execute code before and after using tools through Claude Code hooks.
-   Refactor a Jupyter notebook for e-commerce data analysis and transform it into a dashboard.
-   Connect Claude to the Figma MCP server to import a design mockup to Claude Code,  and develop a web interface showing economic data from the Federal Reserve Economic Data. 
-   Use Playwright MCP server to automatically open a web browser, take screenshots, and guide Claude Code to improve the UI design of an application. 

By the end of this course, you’ll have a set of best practices you can apply to speed up and improve your coding workflow.

## Who should join?

This course is ideal for anyone who wants to explore how AI coding assistant tools like Claude Code can enhance their development process. Whether you’re building applications, debugging code, or exploring unfamiliar codebases, you’ll gain practical skills to work more efficiently with AI-assisted workflows. You can make the best of the course if you’re familiar with Python and Git.

## Course Outline

10 Lessons・0 Code Examples

-   Introduction
    
    Video・4 mins
    
-   What is Claude Code?
    
    Video・8 mins
    
-   Course Notes
    
    Reading・1 mins
    
-   Setup & Codebase Understanding
    
    Video・14 mins
    
-   Adding Features
    
    Video・17 mins
    
-   Testing, Error Debugging and Code Refactoring
    
    Video・12 mins
    
-   Adding Multiple Features Simultaneously
    
    Video・11 mins
    
-   Exploring Github Integration & Hooks
    
    Video・10 mins
    
-   Refactoring a Jupyter Notebook & Creating a Dashboard
    
    Video・12 mins
    
-   Creating Web App based on a Figma Mockup
    
    Video・9 mins
    
-   Conclusion
    
    Video・1 min
    
-   Quiz
    
    Reading・7 mins
    
-   Prompts & Summaries of Lessons
    
    Reading・1 min
    

## Instructor

![Elie Schoppik](/_next/image/?url=https%3A%2F%2Fhome-wordpress.deeplearning.ai%2Fwp-content%2Fuploads%2F2025%2F05%2FInstructors-profile-picture-62.png&w=256&q=75)

### Elie Schoppik

Head of Technical Education at [Anthropic](https://www.anthropic.com/)

-   [](https://www.linkedin.com/in/eschoppik/)
-   [](https://x.com/eschoppik)
```


### 11. Conclusion.md

```markdown
---
title: Claude Code A Highly Agentic Coding Assistant  DeepLearning.AI
slug: claude-code-a-highly-agentic-coding-assistant-deep-1755233224541
source: https://learn.deeplearning.ai/courses/claude-code-a-highly-agentic-coding-assistant/lesson/00vs7/conclusion
datetime: 2025-08-15T04:47:04.540Z
---

Transcript

0:02 Congratulations on making it this far.

0:04 You've learned how to use Claude Code

0:06 to explore, test, refactor, and debug code bases.

0:10 You can make the best out of Claude Code

0:12 when you give it clear instructions,

0:14 clarify the context,

0:16 and point it to the relevant files in your codebase.

0:18 Make sure to add your codebase rules to CLAUDE.md

0:20 and any information that you'd like

0:22 Claude Code to remember about your project.

0:25 Consider extending Claude Code capabilities

0:28 and connecting it to MCP servers like Playwright and Figma.

0:31 Thank you for joining me on this journey.

0:33 and I can't wait to see what you'll build with Claude Code.

![完美，撒花，感谢Elie老师](https://poketto.oss-cn-hangzhou.aliyuncs.com/ddcf13ea1db81c84139c7f2851e32cb8.png?x-oss-process=image/quality,q_90/rotate,0)

```


### 03. Course Notes.md

```markdown
---
title: Claude Code A Highly Agentic Coding Assistant  DeepLearning.AI
slug: claude-code-a-highly-agentic-coding-assistant-deep-1755232875274
source: https://learn.deeplearning.ai/courses/claude-code-a-highly-agentic-coding-assistant/lesson/00vs42k/course-notes
datetime: 2025-08-15T04:41:15.274Z
---

# Course Notes

This note includes the instructions on how to **install Claude Code**, and the **links to the coding examples and prompts** used in the lessons.

**Note**:

-   To mark this reading item as complete, make sure to scroll down to the end and click on **"Mark as Complete"**.
-   There's a second reading item at the end of this course. To get **100% course completion**, make sure to also mark it as complete.

## Claude Code Installation

To follow along with the lessons, here's how you can install Claude Code.

1.  Install [Node.js](https://nodejs.org/en/download), then run:
    
    `npm install -g @anthropic-ai/claude-code`
    
    For more installation guides, you can find them [here](https://docs.anthropic.com/en/docs/claude-code/setup). If you're using Windows, make sure to check the Windows Setup [here](https://docs.anthropic.com/en/docs/claude-code/setup#windows-setup).
    
2.  Once you have Claude Code installed, you can:
    
    -   launch it from your terminal: navigate to your project folder & then type `claude`
    -   launch it from the terminal integrated within VS Code by typing `claude`, the extension will auto-install.
        -   If you run into issues, ensure that `code` command is available. If not installed, use Cmd+Shift+P (Mac) or Ctrl+Shift+P (Windows/Linux) and search for “Shell Command: Install ‘code’ command in PATH”
    
    For more info, check [Claude Code IDE Integrations](https://docs.anthropic.com/en/docs/claude-code/ide-integrations).
    

## Links to Course Codebase Examples

Here are the links to the coding examples covered in the lessons:

1.  Codebase for the RAG chatbot (Lessons 2-6)
    
    -   Here's [the repo](https://github.com/https-deeplearning-ai/starting-ragchatbot-codebase.git) of the starting codebase used in lesson 2.
    -   Lessons 3-6 add features to the starting codebase.
    -   Here's [the state](https://github.com/https-deeplearning-ai/ragchatbot-codebase.git) of the codebase after lesson 5.
    
    Feel free to fork the starting codebase and follow the lessons' activities.
    
2.  E-commerce data analysis (Lesson 7)
    
    -   Here are [the lesson's files](https://github.com/https-deeplearning-ai/sc-claude-code-files/tree/main/lesson7_files).
    -   It includes the data, the starting and refactored notebooks, and the dashboard file.
    
    Feel free to fork this repo, and try lesson 7 tasks using the starting notebook and the data folder.
    
3.  Figma design mockup (Lesson 8)
    
    -   Here's [the link](https://github.com/https-deeplearning-ai/sc-claude-code-files/blob/main/additional_files/key-indicators.fig) to the Figma mockup design (which you can open with [Figma Desktop App](https://help.figma.com/hc/en-us/articles/5601429983767-Guide-to-the-Figma-desktop-app)).
    -   In lesson 8, you will build a Next.js app based on this mockup.
    -   Here's the [link](https://github.com/https-deeplearning-ai/FRED-dashboard.git) to the repo of the app we got during filming.

## Prompts and Summaries of Lessons

You can find the prompts used in each lesson and a summary of Claude Code features in the optional reading item at the end of the course (Prompts & Summaries of Lessons). You can also find them in this [repo](https://github.com/https-deeplearning-ai/sc-claude-code-files/tree/main/reading_notes).

## Claude Code Cost

If you'd like to install Claude Code to try the lessons:

-   you can use the Pro or Max [subscription](https://www.anthropic.com/claude-code#:~:text=Pro,Sign%20up). The pro subscription is enough for the lessons' activities.
-   Or, you can be billed based on API usage. For a given session, you can see the cost using the `/cost` command.
```


### 06. Testing, Error Debugging and Code Refactoring.md

```markdown
---
title: Claude Code A Highly Agentic Coding Assistant  DeepLearning.AI
slug: claude-code-a-highly-agentic-coding-assistant-deep-1755233031183
source: https://learn.deeplearning.ai/courses/claude-code-a-highly-agentic-coding-assistant/lesson/33kzc/testing,-error-debugging-and-code-refactoring
datetime: 2025-08-15T04:43:51.183Z
---

Transcript

0:00 The codebase is now missing tests

0:02 for evaluating the RAG pipeline of the chatbot.

0:06 Let's implement these tests and use them to debug an error

0:09 that the chatbot is having processing the queries, and finally, refactor

0:14 how the chatbot handles its tool use. Let's dive in.

0:18 So far we've seen how to get up to speed with codebases

0:21 and implement features to build a slightly more powerful experience.

0:26 Now let's go ahead and imagine that it's

0:28 been some time since we've worked on this

0:29 application. We're coming back and we want to start using it again.

0:32 So let's hop back to our application

0:34 and ask for some details on what's covered in Lesson 5.

0:38 We might expect to see a response

0:40 that gives us information, but right now, something's wrong.

0:43 It might be tempting to just

0:45 copy this error, put it into Claude,

0:46 take a screenshot, hope it solves the problem.

0:48 But we're going to do something a little bit different.

0:51 Instead of just getting the answer that we might want

0:54 or leading Claude on some wild goose chase.

0:58 We're going to take a bit more of a methodical approach here.

1:00 We know that things are wrong in our application,

1:02 but we also know that we don't have too many tests here

1:05 to programmatically verify that that's the case.

1:09 So what we're going to do is put in a prompt

1:11 that not only mentions what the error is,

1:13 but also specifies where we need to write tests.

1:17 If we go back to our code base,

1:19 the error we're looking at could be

1:21 from a variety of different Python files.

1:24 In our AIGenerator, this is where we handle interactions with Anthropic's API.

1:28 And there could be problems in the prompt

1:31 or even some of the logic

1:32 we have for getting this part working.

1:35 In our rag\_system.py,

1:36 this is the orchestrator for everything that's happening with Retrieval Augmented Generation.

1:42 And in our search\_tools, here's where we define the underlying tool

1:46 definition where there could potentially be problems.

1:49 So what we're going to ask Claude to do

1:51 is write tests for these specific files just to start.

1:54 We're then going to ask Claude to run those tests

1:56 and through that, verify what is not working and make

1:59 the appropriate fix. What's so powerful about this approach

2:03 is by starting with our tests, we

2:05 can start to build a robust foundation

2:07 for building more off of the codebase

2:09 and understanding when things go wrong, why they're failing.

2:12 So let's open up Claude and put in a prompt.

2:15 Since this is a little bit more challenging,

2:18 we're also going to ask Claude to think a lot.

2:22 This is going to trigger Claude's ability

2:24 to enable extended thinking

2:26 and allocate a few more tokens

2:28 towards the thinking process. we're also going to see this process

2:32 and if something doesn't appear right, we

2:33 can always stop Claude in its tracks.

2:35 We'll go ahead and make sure the plan mode is on

2:38 because first we want to make sure before Claude starts writing tests,

2:41 it understands what it needs to

2:43 do and we can approve that process.

2:45 As we start to read the files necessary,

2:47 we're going to see Claude's thinking process.

2:49 We're not only going to see the files that we're reading,

2:52 but also what it needs to examine and what it should do.

2:57 So let's go see what Claude's plan has. It's

2:59 It seems like there's some kind of configuration issue,

3:02 maybe some complex tool calling with failure points

3:05 and some limited error propagation between components.

3:09 So it's possible that the error is just getting caught somewhere.

3:12 It's then going to propose a structure for tests

3:14 based on these files, which looks good to us.

3:18 use the pytest framework and mock whatever

3:19 it is in ChromaDB that we need

3:21 to get some unit tests and integration tests up and running.

3:26 You can see right now it's starting to make

3:28 a folder for my tests, where it'll be running.

3:29 writing these. It's a great start.

3:32 We'll go ahead and make sure we add

3:34 any necessary dependencies here as well with UV.

3:38 Let's go install our dependencies,

3:40 make sure we have pytest working as expected, and that looks good.

3:42 We're also going to see the thinking part

3:44 here to make sure that we're doing what's expected.

3:46 As we start to write these particular tests,

3:48 we can start exploring the code that's been written for us.

3:51 Here we can see tests for the course search tool,

3:54 fixtures and mocks that we need to make.

3:56 This looks like a good start. We'll

3:58 see the same thing for our AI generator.

3:59 and our RAG system and our vector store.

4:02 It seems like it's identified a critical

4:03 config issue which may solve the bug,

4:06 but writing these tests is going to give us complete assurance

4:08 that this is actually the problem

4:10 and that this is the correct fix.

4:20 Now that we've created these tests, let's run them using UV.

4:23 Let's go make sure we have the correct dependencies

4:25 so that we can run those tests as expected.

4:27 So from its finding, it's telling us that it's

4:29 seems like there's something wrong with these max results

4:33 or the number of chunks that were

4:34 returning when we perform our vector search. So let's see

4:38 what we're getting when we take a look at our MAX\_RESULTS.

4:40 And this confirms the issue that we have.

4:42 For some reason, this happens to be zero.

4:44 Once we go ahead and change this, we should expect

4:46 that not only our tests are working as expected,

4:49 but that the results we get are complete.

4:51 We can verify this by taking a look and

4:53 making sure we get the file that we expect.

4:55 Now that Claude Code is wrapping up,

4:57 it can provide a comprehensive summary of its

4:59 findings, which I can wait to

5:01 see or if I feel good now,

5:02 I can stop Claude in its tracks.

5:05 But I'll take a look at what

5:06 it gives me. It's completed its debugging.

5:08 It's found the critical issue, and it's created a few tests,

5:11 as well as some infrastructure to

5:12 keep running tests as we go forward.

5:15 Let's go see if this worked as expected.

... (省略 78 行) ...


6:58 prompt that I have where I'm

6:59 going to ask Ask Claude to refactor

7:01 the backend ai\_generator.py

7:03 to support two calls in separate rounds.

7:06 The current behavior is what I'm describing

7:08 as well as the desired behavior.

7:10 While this might not be required,

7:12 it's often helpful, as we've seen,

7:15 to give Claude as much information as possible,

7:17 especially when the tasks are a little bit more complex.

7:20 We're also going to give Claude an example flow.

7:23 Something like search for a course that

7:25 discusses the same topic as another course.

7:28 Just to give Claude a sense of what needs to be done.

7:30 Notice here, there are a couple of different

7:32 tools that need to be used as expected.

7:34 We'll give Claude some requirements,

7:36 and then a couple of notes as well

7:38 to make sure we're doing the right thing.

7:40 We're going to make sure that

7:42 we write tests that verify external behavior

7:44 instead of worrying about internal state details.

7:47 Or we're also going to ask Claude to

7:49 do is figure out a couple different plans.

7:52 Don't implement any code,

7:53 but dispatch two subagents to brainstorm potential options.

7:58 In this situation, I'm not exactly sure what the optimal refactoring is.

8:03 So instead of letting Claude Code decide just one

8:05 option, I'm actually going to give it the opportunity

8:07 to figure out multiple options in parallel.

8:11 So let's use that particular prompt

8:12 and I'll turn off auto accept to make sure

8:15 that as I'm going through, I can

8:16 confirm each of the changes that

8:18 I want. So let's run that prompt.

8:20 We should expect to see the two parallel subagents

8:23 being dispatched using a tool called task.

8:26 And as we see those agents dispatched,

8:28 we'll start to see two plans

8:30 for how we can solve this problem.

8:32 It's then up to us to decide which one to implement.

8:35 We can see that both of these are operating in parallel,

8:38 reading across files and figuring out two different approaches for this refactor.

8:42 So it looks like it's come back with

8:44 some recommendations for how best to tackle this.

8:46 One approach is iterative, another more comprehensive.

8:50 We can see here that Claude is actually going

8:52 to give us an option to choose either option B

8:55 for better long-term maintainability or option A for a safer implementation.

8:59 scroll up more. If I scroll up more, I

9:01 can get some details into what it's trying to do.

9:04 One option supporting some iteration for handling tools,

9:07 the other for a slightly more complicated implementation

9:11 for multi-round logic with different helper methods for that process.

9:15 From first glance, it seems like approach A is a bit simpler.

9:18 So why don't we start with

9:19 that? I'm going to select approach A,

9:20 but I'm also now going to enable plan mode

9:23 to make sure I have a comprehensive plan and

9:26 can accept before making the changes that I want.

9:29 Let's implement approach A.

9:30 and get a more detailed plan to verify

9:32 that this is exactly what we want to do.

9:34 We know that there needs to be some modification

9:36 in the way that which we call these tools,

9:39 but let's make sure this is all being

9:40 done in the right place before we go ahead

9:42 and have Claude Code write the solution for us.

9:45 Now let's take a look at what's being done here.

9:47 We'll update our method signature for a maximum number of rounds,

9:50 update our system prompt, and here where the

9:53 core refactoring is done in our handle tool execution.

9:56 If this is done as expected, we

9:57 should see the user query, we should see

9:59 multiple tools being called and then a final response.

10:03 This shouldn't modify anything else and should solve the problem for us.

10:07 We can see here that this is backwards compatible,

10:10 and we're not changing the internal RAG system or any API endpoints.

10:14 So let's proceed and see if

10:16 this can solve our problem for us.

10:17 As we see what's being implemented,

10:20 we can see changes to existing methods,

10:22 and most importantly, we can see here that

10:25 we're updating the tests and running the tests

10:27 to verify that the implementation works correctly.

10:31 Instead of context switching to the browser

10:33 or asking other people to test,

10:35 I can do this all from inside the terminal

10:37 in Claude Code.

10:45 So we'll see here, we're going to update our system prompt,

10:47 make sure that our tests are as expected.

10:50 And then we'll add a test to make

10:51 sure the sequential tool calling works as expected.

10:54 Let's run our tests, make sure they're passing as expected.

10:57 Let's verify in the browser, this is doing what

10:59 if you want. Let's try asking first

11:02 for a details of a course's lesson.

11:06 So here we can see

11:07 that not only are we getting this information,

11:10 but also the title here as well, as expected.

11:12 We're getting information about this lesson,

11:14 as well as some of the sections and topics discussed.

11:18 Now let's do something a little more complex.

11:20 What's so special about seeing the title here is

11:22 that we don't get that with just one tool call.

11:25 The first tool call just gives us an outline of the course.

11:29 The second tool call gives us that detail

11:31 of the particular lesson and in our case the title.

11:34 Now let's ask, Are there any other courses that cover

11:37 the same topic as Lesson 5 of the MCP course?

11:42 In order to do this, we're going

11:44 to need to make multiple tool calls

11:45 to get information about this particular MCP course

11:48 and outline and then information about other courses and their outlines

11:53 to see if there's any overlap.

11:55 Unfortunately, it looks like there are no other courses

11:58 that cover building an MCP client, which does seem accurate.

12:01 In this lesson, we've seen how to use Claude Code to

12:05 not only fix bugs, but write tests throughout the entire process.

12:09 We built for ourselves a solid foundation to keep coding on

12:12 and made a nice refactor to get more complicated query answers appropriately.

12:17 In the next lesson, we'll improve our

12:20 productivity by running multiple sessions of Claude Code

12:23 and making sure we don't have overlaps or

12:26 overwrites using Git worktrees. I'll see you there.
```


### 09. Refactoring a Jupyter Notebook & Creating a Dashboard.md

```markdown
---
title: Claude Code A Highly Agentic Coding Assistant  DeepLearning.AI
slug: claude-code-a-highly-agentic-coding-assistant-deep-1755233141190
source: https://learn.deeplearning.ai/courses/claude-code-a-highly-agentic-coding-assistant/lesson/33kzr/refactoring-a-jupyter-notebook-&-creating-a-dashboard
datetime: 2025-08-15T04:45:41.190Z
---

Transcript

0:02 Claude Code has tools for reading and editing Jupyter notebooks.

0:06 In this lesson, we'll go through

0:08 our second example and use Claude Code

0:10 to refactor a Jupyter notebook and transform it into a dashboard.

0:14 Let's get to it. So far we've

0:16 seen how to use Claude Code to

0:17 work with web applications on the front end and back end.

0:20 Now let's shift gears and showcase how to

0:23 use Claude Code to work with a Jupyter notebook.

0:25 I have a Jupyter notebook here

0:27 with some e-commerce data that is fictitious.

0:30 This ecommerce data is reading information from a few CSVs

0:34 that I have in this ecommerce\_data folder.

0:37 I'm using pandas to read data from the CSV.

0:41 I'm displaying some information here, reading some other CSVs,

0:45 and as you can see here,

0:46 I'm getting the answers that I want,

0:48 but this data is not really the most organized.

0:50 I'm getting some statistical information,

0:53 but the formatting and the display might not

0:55 be what I'd like out of the box.

0:57 As I go through and take a

0:58 look at some more of this information.

1:00 I can start to see that I'm beginning to do some more

1:02 complicated procedures here. One of the things that I'd

1:06 like to get out of this data

1:08 are some insights around things like how

1:09 much revenue did we generate year over year.

1:11 Specifically, 2023 to 2022.

1:15 I have the necessary operations here

1:17 to do what I want. In fact, there's a little

1:19 bit of merging between two different CSVs and data frames.

1:22 And here, I'm working my way towards the answer that I want,

1:25 but there are some warnings that I'm seeing here.

1:28 at the same time, it takes a while just to show visually

1:31 what I want and how best to display it.

1:33 So while I do end up getting the numbers that I want,

1:35 it's a little bit tedious and messy. I

1:37 want a way to better showcase this information

1:39 and I want to explore how I can refactor this Jupyter notebook.

1:43 As we see in a few other sections,

1:45 I'm trying to calculate some high level metrics like average order values

1:48 and not only am I looking for

1:50 this number, but this is just for 2023.

1:52 What happens when I want 2024 and so on.

1:55 As we scroll down, we'll see some visualizations

1:58 that are pretty good. But I think we could do better.

2:00 As we work our way towards the

2:01 bottom, we're still calculating more of these

2:03 high level values like sales by state.

2:05 We're generating some visualizations again, but I think we could do

2:08 much better as we start to use tools like Claude Code.

2:11 So with that in mind, let's

2:13 showcase how we can use Claude Code

2:14 to refactor this notebook and better

2:17 consolidate our business logic from our presentation.

2:19 So I'm going to go ahead and open up Claude, and

2:21 I'm going to put in a prompt that I have here

2:23 that references the notebook as well as the other files that

2:27 that I'm working with. I'm going to

2:28 go ahead and paste in this prompt.

2:30 And then I want to talk a

2:31 little bit about what's actually happening here.

2:33 So before I paste in this prompt,

2:35 I'm actually going to make a new markdown file

2:37 just to showcase what this looks like and

2:39 walk through why we've done what we're doing here.

2:42 Notice here, I'm referencing the name of the file using this sign,

2:45 as well as the name of the folder using this as well.

2:48 If you're ever unsure of how best to prompt

2:51 or how best to ask Claude for what to do,

2:54 you can always ask Claude as well. So many

2:56 times, I find myself using tools like Claude AI

2:58 or even Claude Code and just asking

3:00 Claude, here's what I want to do,

3:02 give me the best possible prompt to accomplish this task.

3:06 In our case, we have some Refactoring Requirements

3:09 for how we want the structure to be laid out.

3:11 We have Code Quality Improvements and some asks that we have

3:14 for particular Python files that we want.

3:17 What we're asking Claude to do

3:19 here is create a separate Python file

3:21 for loading our data and processing it.

3:23 And then another Python file for calculating these metrics.

3:27 This separation of concerns is going to allow us to better test

3:30 and better understand what the code is that's powering

3:34 these visualizations that we make in our refactored notebook.

3:37 We're also asking for improved visualizations.

3:40 We're being a little bit more

3:41 specific with what we mean by that.

3:43 Finally, we want to have a little bit

3:45 more configuration around the data that we're working with.

3:48 In general, it's a good practice to

3:50 let Claude know what you're expecting here.

3:52 So instead of just refactor this, give me

3:55 underlying asset for a refactored notebook.

3:57 Give me a way to document

3:59 my functions and calculate my business metrics.

4:02 and then give me some other important files for the dependencies I'm

4:05 working on, as well as a README explaining how to use this.

4:08 So let's go ahead and copy this and paste it in.

4:11 And you'll notice that after you paste a certain number

4:14 of lines, Claude Code is not going to show you everything.

4:16 to keep things a little bit more concise in the terminal.

4:19 So let's go ahead and run this prompt.

4:21 As we've done with other kinds of tools,

4:23 we're going to be using a slightly different suite of tooling here.

4:26 instead of reading, we're going to be dealing with notebook reading.

4:29 But the same to-do list that we

4:31 saw before, it's going to be executed

4:32 just like we've gotten very accustomed to with Claude Code.

4:36 Here we're using that read notebook.

4:38 We're going to explore those cells, we're going to analyze the structure

4:41 and create the refactored notebook that we expect.

4:44 Once this is done, we should expect

4:45 to see not only some powerful visualizations,

4:48 but also some other files with helper functions

4:51 for loading data, processing data,

4:54 and calculating the business metrics that we need.

5:01 accept the changes to these Python files

5:04 and we'll see that Python is being

... (省略 144 行) ...


7:43 things are looking good as expected.

7:45 So we've done a nice job refactoring this notebook

7:48 to more visually display information and separate our concerns.

7:50 But what I'd like to do now is

7:52 move from a notebook to a web-based interface

7:54 with a nice dashboard powered by Streamlit.

7:57 If you're not familiar with Streamlit, it's a Python library

8:00 that's useful for displaying interfaces, particularly dashboards,

8:03 and it's very easy to seamlessly transition

8:06 from notebooks to these Python files.

8:08 So let's go ahead and make

8:09 a new markdown file with our prompt

8:11 that we'll call convert-to-dashboard.md

8:13 And let's walk through what we're going to

8:15 put in here. We're going to ask Claude

8:17 to convert our refactored notebook into a professional

8:20 professional Streamlit dashboard with this exact layout.

8:23 We could start just with this first line,

8:25 but in order to avoid lots of back

8:26 and forth, let's just tell Claude what we want.

8:29 We want a header with a title and filter,

8:31 we want KPIs with cards for revenue,

8:33 growth, toward average order value and total

8:35 orders. And then we want some charts.

8:38 revenue, categories, revenue by state, and a bar chart with satisfaction.

8:42 At the bottom row, we want two cards,

8:44 and we want to be specific for the way

8:46 in which we display our data and render this information.

8:49 So with that in mind, let's

8:50 go ahead and give this a shot.

8:51 Let's migrate from notebooks to visual interfaces using Streamlit.

8:55 We can see that it's created our dashboard,

8:58 and as it's going, we can take

8:59 a look at what's being done here.

9:01 We're importing Streamlit, bringing in pandas,

9:03 bringing in some visualizations including Plotly.

9:06 And then here you can see we're displaying some custom CSS for

9:09 styling, setting up our page configuration.

9:12 Most of this really comes from that st

9:14 object that I have to work with Streamlit. We've updated our requirements.

9:18 txt, and here we're actually going to create a README

9:21 displaying everything that's going on in the dashboard.

9:23 In fact, I'll just tell Claude right now,

9:26 don't make a new README, just modify the one we have.

9:29 In many of these longer plans, it's

9:30 very easy to just let Claude go,

9:32 but sometimes you want to stop the process

9:35 and have it navigate the way that

9:36 you want. Now that we've created this dashboard,

9:38 let's open up a new terminal window to start our server.

9:41 In this terminal window on the left, I'll start the server using

9:44 streamlit run and then the Python file that's going to be

9:48 displayed dashboard.py. We can see here

9:50 that I don't have the Streamlit command.

9:53 So I can see here, in

9:54 order to get everything up and running,

9:56 I need to install these dependencies.

9:57 So let's go ahead and do that.

9:59 I'll run my pip install command,

10:01 install all the necessary dependencies and make sure

10:04 that when the server loads, I don't have

10:06 any issues with the dependencies in this application.

10:08 Once that's done, I'll go ahead and run my server.

10:11 And I'll do that using the streamlit run command.

10:14 So let's go ahead and type in streamlit

10:16 run and the name of our Python file.

10:17 Python file just like it suggests right here.

10:20 Back in the browser, here's what things look like.

10:22 I've got some revenue, I've got some growth.

10:24 As we scroll down a little bit,

10:25 we're definitely going to want to verify

10:27 that these numbers are what we expect.

10:28 And we see that some things are still missing a little bit.

10:32 When we take a look at this

10:33 dashboard, it's a pretty good start, but we

10:34 can see that we're missing a couple things.

10:37 It looks like these cards here are empty

10:39 and actually redundant because we're getting the information that we want.

10:44 At the same time, it's a little difficult to start with 2024.

10:47 because we're not seeing much information year over year.

10:51 So maybe we should ask Claude

10:53 to not only clean up these pieces,

10:55 but also start with a default year of 2023,

10:59 so we can have some slightly nicer visualizations.

11:02 but also make sure we have the ability

11:04 to filter based on the month as well.

11:06 The reason why we'll want to start with 2023

11:09 is because we don't have data for every single month for 2024.

11:14 So as we start to look at

11:15 this, the monthly growth is

11:16 a little bit confusing.

11:19 And the data here, we just don't have yet.

11:22 So let's go make those asks, put them back in Claude.

11:24 This is a good start, but I want to

11:26 implement the following changes.

11:28 Let's go ahead and make a

11:30 new line here and first we'll start

11:32 with making sure the default year is 2023.

11:36 Next, ask Claude to add filters for months as well.

11:40 And then finally, we'll make sure

11:42 to remove the empty card for each.

11:46 So, let's update the code in our dashboard for these particular tasks.

11:48 We'll set the default year to 2023, which looks good.

11:52 And here we'll add some filters for months.

11:53 Now let's update the revenue chart to handle

11:55 the case where we're filtering by a specific month.

11:58 We can see the CSS is changing as well.

12:00 So it looks like this chart container

12:01 should be a little bit cleaner than before.

12:03 Let's go back to the browser, see what things look like.

12:06 We can see that 2023 is

12:07 the default, which is a good start.

12:09 We can also see that those

12:11 empty cards are gone, which is great.

12:13 We'll stop here for now, but you can imagine as you keep

12:15 prompting, you can create more powerful visualizations.

12:18 But in a short period of time, we started with a notebook

12:20 that was a bit disorganized,

12:22 was a little hard to read and understand.

12:25 And we migrated now to a dashboard that we can deploy,

12:28 share with team members and iterate on quickly.

12:31 In the next lesson, we'll build a Next.js application

12:34 and use Claude Code to connect to MCP servers

12:38 for Figma and Playwright to take a mockup and build a

12:42 powerful web application with Claude Code quickly.
```


---

*此文档由 Context Packer 自动生成*
*项目路径: /Users/mark/my-docusaurus/my-website/my-documents/album/DeepLearning.ai-Courses-ClaudeCode/transcripts*
*生成时间: 2025年 8月24日 星期日 17时01分58秒 CST*
