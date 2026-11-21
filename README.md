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
- [x] 推送到 GitHub
- [ ] 学会分支操作

## 第一次推送踩过的坑

把本地代码推到 GitHub 的路上，遇到了 5 个问题，记下来免得下次又踩：

**1. 官方下载太慢**
GitHub 官方直链只有 0.02 MB/s，63.8 MB 要下 1 小时。改用清华镜像 `mirrors.tuna.tsinghua.edu.cn`，11.8 MB/s，5 秒下完。

**2. Hosts 模式会连 SSH 一起拦**
302 把 `github.com` 写进 hosts 指向 `127.0.0.1`，但它只监听 443。所以 `ssh git@github.com` 实际是连本机 22 端口，直接 `Connection refused`。
解法：在 `~/.ssh/config` 里把 `HostName` 写死成 GitHub 真实 IP（`140.82.113.4`），绕开 hosts 解析。

**3. Git 自带凭据管理器崩溃**
`git-credential-manager.exe` 一运行就 `0xE0434352`（CLR 异常）。走 HTTPS 推送必然失败。
解法：全程用 SSH，不碰 HTTPS。

**4. 建仓库报 `Something went wrong!`**
邮箱已验证、服务正常、账号没封，最后确认是**新账号冷却期**——注册 50 分钟内建仓库会被静默拒绝。等了一小时，重试成功。

**5. 差点把 `target/` 推上去**
Java 项目编译后会生成几百 MB 的 `target/`，一旦提交进 Git 历史，以后谁都删不掉（只能重写历史）。
解法：动手前先写好 `.gitignore`。

### 关于 CRLF 警告

Windows 上每次提交都会看到：

```
warning: in the working copy of 'README.md', LF will be replaced by CRLF
```

这是正常的。Git 配了 `core.autocrlf=true`，工作区用 CRLF、仓库里存 LF。**不是错误，不用管。**
