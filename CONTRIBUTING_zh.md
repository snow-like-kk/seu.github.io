如果您完全不了解 GitHub 开源项目的贡献流程，强烈建议您阅读：[first contributions](https://github.com/firstcontributions/first-contributions)

# 为 seu.github.io 贡献代码

如果您有兴趣为 seu.github.io 项目做贡献，我们热烈欢迎您的参与。首先，我们非常鼓励这种积极的态度。以下是一些贡献指南，供您参考。

## 主题

- [报告安全问题](#reporting-security-issues)
- [报告常规问题](#reporting-general-issues)
- [代码和文档贡献](#code-and-doc-contribution)
- [参与帮助任何事情](#engage-to-help-anything)

## 报告安全问题

安全问题会被我们认真对待。按照我们的一贯原则，我们不鼓励公开讨论任何安全问题。如果您发现了 seu.github.io 的安全问题，请不要在公开场合讨论，甚至不要在公共问题区打开问题。

安全问题始终被严肃对待。根据我们的一贯原则，我们不鼓励任何人公开传播安全问题。如果您发现了 seu.github.io 的安全问题，请不要在公开场合讨论，甚至不要在公共问题区开设公开问题。

## 报告常规问题

坦白来说，我们将每一位 seu.github.io 的用户视为非常友善的贡献者。在使用 seu.github.io 之后，您可能会对该项目有一些反馈。如果是这样，欢迎通过 [NEW ISSUE](https://github.com/SEU-Master/seu.github.io/issues/new/choose) 提交一个问题。

由于我们在分布式方式下进行项目协作，我们非常欣赏 **书写良好**、**详细**、**明确** 的问题报告。为了提高沟通效率，我们希望每个人在提交问题之前，先搜索一下您的问题是否已经存在。如果您发现已有相同问题，请在现有问题下添加您的详细信息，而不是重新开一个新的问题。

有很多情况下您可以提交问题：

- 错误报告
- 功能请求
- 性能问题
- 功能提议
- 功能设计
- 帮助请求
- 文档不完整
- 测试改进
- 项目相关问题
- 等等

同时，我们必须提醒您，在提交新问题时，请务必删除您的帖子中的敏感信息。敏感信息可能包括密码、密钥、网络位置、私密业务数据等。

## 代码和文档贡献

我们鼓励任何能够改进项目 seu.github.io 的行动。在 GitHub 上，您可以通过 PR（拉取请求）对 seu.github.io 进行任何改进。

- 如果您发现拼写错误，尽量修正它！
- 如果您发现 bug，尽量修复它！
- 如果您发现一些冗余代码，尽量去除它们！
- 如果您发现缺少测试用例，尽量添加它们！
- 如果您能够增强某个功能，请 **不要** 犹豫！
- 如果您觉得代码不明确，请添加注释以便说明！
- 如果您觉得代码不美观，尝试重构它！
- 如果您能帮助改善文档，那就更好了！
- 如果您发现文档不正确，直接修复它！
- ...

实际上不可能列举所有情况。请记住一个原则：

> 我们期待着您提交的任何 PR。

既然您已经准备好通过 PR 来改进 seu.github.io，我们建议您查看一下 PR 的规则。

- [工作区准备](#workspace-preparation)
- [分支定义](#branch-definition)
- [提交规则](#commit-rules)
- [PR 描述](#pr-description)
- [开发环境](#developing-environment)

### 工作区准备

为了提交一个 PR，我们假设您已经注册了 GitHub 账号。然后，您可以按照以下步骤完成准备工作：

1. **FORK** seu.github.io 到您的仓库。为此，您只需点击 [SEU-Master/seu.github.io](https://github.com/SEU-Master/seu.github.io) 主页面右上角的 "Fork" 按钮。这样，您将获得一个属于您的仓库，地址为 `https://github.com/<your-username>/seu.github.io`，其中 `your-username` 是您的 GitHub 用户名。

2. **CLONE** 您自己的仓库到本地。使用命令 `git clone https://github.com/<your-username>/seu.github.io` 将仓库克隆到本地计算机。然后，您可以创建新的分支来完成您想要做的修改。

1. **设置 Remote** 为 `https://github.com/SEU-Master/seu.github.io`，使用以下两个命令：

   ```shell
   git remote add upstream https://github.com/SEU-Master/seu.github.io
   git remote set-url --push upstream no-pushing
   ```

   配置好远程仓库后，您可以通过以下命令检查您的 git 远程配置：

   ```shell
   $ git remote -v
   origin     https://github.com/<your-username>/seu.github.io.git (fetch)
   origin     https://github.com/<your-username>/seu.github.io.git (push)
   upstream   https://github.com/SEU-Master/seu.github.io (fetch)
   upstream   no-pushing (push)
   ```

   配置好这些后，您可以轻松地将本地分支与上游分支同步。

1. **创建分支** 用于添加新特性或修复问题

   更新本地工作目录和远程 Fork 仓库：

   ```shell
   cd seu.github.io
   git fetch upstream
   git checkout main
   ```

   创建一个新的分支：

   ```shell
   git checkout -b <new-branch>
   ```

   在 `new-branch` 上进行更改，之后构建并测试代码。

2. **提交更改** 到本地分支，提交前请进行 lint 检查，并进行签名提交：

   ```shell
   git rebase upstream/main
   golangci-lint run -c .golangci.yml # lint 检查
   git add -A  # 将更改添加到暂存区
   git commit -s -m "message for your changes" # -s 添加 Signed-off-by 标签
   ```

3. **推送分支** 到您的 Fork 仓库，建议每个 PR 只包含一次提交：

   ```shell
   # 与上游同步
   git fetch upstream main
   git rebase upstream/main

   git rebase -i <commit-id> # 使用交互式模式将多个提交合并为一个提交
   git push # 推送到远程仓库，如果是第一次推送，使用 git push --set-upstream origin <new-branch>
   ```

   您也可以使用 `git commit -s --amend && git push -f` 来更新之前的提交。

   如果您在同一分支中开发了多个特性，您应该在每次推送之前，通过重新基准化到主分支来分别创建 PR：

   ```shell
   # 创建新的分支，例如 git checkout -b feature/infra
   git checkout -b <new branch>
   # 更新一些代码，特性1
   git add -A
   git commit -m -s "feature one"
   git push # 如果是第一次推送，运行 git push --set-upstream origin <new-branch>
   # 创建 PR 并合并
   # 更新新特性，特性2，首先与主分支重新基准化。
   git rebase upstream/main # 将当前分支与 upstream/main 分支重新基准化
   git add -A
   git commit -m -s "feature two"
   # 创建 PR 并合并
   ```

4. **提交拉取请求 (PR)** 到 `labring/seu.github.io:master` 分支

   提交 PR 前，建议先审查一下您的更改，确保您的代码与主分支没有冲突，并且没有包含冗余的代码。

### 分支定义

目前我们假设所有通过拉取请求（pull request）贡献的代码都是针对 `seu.github.io` 项目的 [master 分支](https://github.com/labring/seu.github.io/tree/master)。在贡献代码之前，了解分支的定义将大有帮助。

作为贡献者，请再次牢记，所有的贡献都是通过拉取请求提交到 `master` 分支。虽然在 `seu.github.io` 项目中有多个其他分支，我们通常将它们称为 rc 分支、发布分支和回退分支。

在正式发布版本之前，我们会检出一个 rc（发布候选）分支。在这个分支上，我们会进行更多的测试，而不仅仅是在 `main` 分支上。

当正式发布版本时，会有一个发布分支，在打标签之前会先创建该分支。打完标签后，我们会删除该发布分支。

当将某些修复回移到已发布版本时，我们会检出回退分支。回退完成后，修复的效果会体现在 [SemVer](http://semver.org/) 的版本号中的 PATCH 部分（MAJOR.MINOR.PATCH）。

### 提交规则

在 `seu.github.io` 项目中，我们特别重视两条提交规则：

- [提交信息](#提交信息)
- [提交内容](#提交内容)

#### 提交信息

提交信息可以帮助评审者更好地理解提交的 PR 目的，也有助于加速代码审查过程。我们鼓励贡献者使用**明确**的提交信息，而不是模糊不清的信息。一般来说，我们提倡以下类型的提交信息：

- `docs:` xxxx。例如，“docs: 添加存储安装文档”。
- `feature:` xxxx。例如，“feature: 使结果按顺序显示”。
- `bugfix:` xxxx。例如，“bugfix: 修复输入 nil 参数时的 panic 错误”。
- `style:` xxxx。例如，“style: 格式化 Constants.java 的代码风格”。
- `refactor:` xxxx。例如，“refactor: 简化代码以提高可读性”。
- `test:` xxxx。例如，“test: 为 InsertIntoArray 函数添加单元测试用例”。
- `chore:` xxxx。例如，“chore: 集成 travis-ci”。这是用于维护变更的类型。
- 其他可读且明确的表达方式。

另一方面，我们不鼓励贡献者使用以下模糊不清的提交信息：

- ~~fix bug~~
- ~~update~~
- ~~add doc~~

#### 提交内容

提交内容表示一个提交中所有更改的内容。我们最好将相关内容打包在一个提交中，这样评审者可以在没有其他提交帮助的情况下完成审查。换句话说，一个提交的内容应该能够通过 CI 检查，避免代码混乱。简而言之，我们需要遵循以下两条小规则：

- 避免在一个提交中进行过大的更改；
- 每个提交内容需要完整且可审查。

无论提交信息如何，或提交内容是什么，我们都更加注重代码审查过程。

### PR 描述

PR 是向 `seu.github.io` 项目文件提交更改的唯一方式。为了帮助评审者更好地理解你的目的，PR 描述不需要过于详细。我们鼓励贡献者遵循 [PR 模板](https://github.com/labring/seu.github.io/tree/main/.github/PULL_REQUEST_TEMPLATE.md) 来完成拉取请求。

### 开发环境

作为贡献者，如果你想对 `seu.github.io` 项目做出贡献，我们需要就开发环境中使用的工具版本达成一致。以下是一些指定版本的依赖：

- golang: v1.16+
- golangci-lint: 1.46.2

当你在本地环境中开发 `seu.github.io` 项目时，你应该使用 Makefile 中的子命令来帮助自己检查和构建 `seu.github.io` 的最新版本。为了方便开发者，我们使用 Docker 来构建 `seu.github.io`，这样可以减少开发环境中的问题。

## 参与帮助

我们选择 GitHub 作为 `seu.github.io` 协作的主要平台，因此 `seu.github.io` 的最新更新总是会出现在这里。尽管通过 PR 提交贡献是显而易见的方式，但我们仍然呼吁以其他方式参与。

- 如果可以，回复他人的问题；
- 帮助解决其他用户的问题；
- 帮助审查他人的 PR 设计；
- 帮助审查他人在 PR 中的代码；
- 讨论 `seu.github.io` 以使事情更清晰；
- 在 GitHub 之外推广 `seu.github.io` 技术；
- 撰写关于 `seu.github.io` 的博客等。

总之，**任何帮助都可以视为贡献。**