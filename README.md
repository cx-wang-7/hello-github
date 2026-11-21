# hello-github

这是我用 Git 推送的第一个仓库，用来完整跑通一遍 GitHub 的工作流程。

## 我在做什么

- 学习用 Git 管理代码版本
- 学习把本地代码推送到 GitHub
- 为以后的课程作业和求职作品集做准备

## 环境

| 项目 | 版本 |
|---|---|
| Git | 2.56.1.windows.1 |
| 系统 | Windows 11 |
| 编辑器 | IntelliJ IDEA |

## Git 的三个核心概念

**工作区（Working Directory）**
你实际编辑文件的地方，改动最先发生在这里。

**暂存区（Staging Area）**
执行 `git add` 后，改动的文件进入暂存区。这是「我准备提交这些改动」的声明。

**版本库（Repository）**
执行 `git commit` 后，暂存区的内容被固化成一次提交，永久记录在 `.git` 目录里。

## 常用命令

```bash
git status              # 查看当前有哪些改动
git add .               # 把所有改动放进暂存区
git commit -m "说明"    # 提交，生成一个版本
git push                # 推送到 GitHub
git log --oneline       # 查看提交历史
git pull                # 拉取远程的最新改动
```

## 进度

- [x] 安装 Git
- [x] 配置 SSH 密钥
- [x] 建立本地仓库
- [ ] 推送到 GitHub
- [ ] 学会分支操作
