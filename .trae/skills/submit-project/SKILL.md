---
name: "submit-project"
description: "Commits all changes and pushes to Gitee remote. Invoke when user says 提交项目/提交/上传/push/推送, or asks to commit the current project."
---

# 提交项目（commit + push）

将当前项目的所有改动用 `git commit` 提交，并推送到 Gitee 远程仓库
`https://gitee.com/ge-conghui/geconghui2026.git`。

## 步骤

1. 检查仓库状态与当前远程：

   ```powershell
   git status
   git remote -v
   git log --oneline -5
   ```

2. 若没有指向 `https://gitee.com/ge-conghui/geconghui2026.git` 的远程，则添加
   （已有同名 `origin` 但地址不符时，用 `git remote set-url origin <url>` 修正）：

   ```powershell
   git remote add origin https://gitee.com/ge-conghui/geconghui2026.git
   ```

3. 暂存全部改动（本项目是静态作业，通常一次性提交所有文件）：

   ```powershell
   git add -A
   ```

4. 提交。提交信息用简短中文，说明改了什么；若没有可区分的改动，
   不要创建空提交，直接结束：

   ```powershell
   git commit -m "提交网页设计作业"
   ```

5. 推送。认证凭据已通过本机 git credential store 与 origin URL 预配置
   （令牌不在本文件中出现，也不应写入任何会提交的文件）。
   若远程分支尚无历史或被拒绝，使用带 `-u` 的强制对齐推送：

   ```powershell
   git push -u origin HEAD
   # 若被拒绝（远程已有提交），先了解差异再处理，禁止直接 force push：
   git fetch origin
   git status
   ```

6. 汇报结果：提交 hash、推送的分支、远程仓库地址；如推送失败，
   原样带回错误信息（常见：需要用户名/密码或 Gitee 私人令牌、网络问题、
   远程有他人提交需先 pull）。若认证失败，提示用户重新配置本机凭据，
   不要在对话中或文件里粘贴令牌明文。

## 认证配置（仅本机，不入库）

- 已执行：`git config credential.helper store`，并将
  `https://<用户名>:<私人令牌>@gitee.com` 写入 `%USERPROFILE%\.git-credentials`。
- origin 的 URL 中可内嵌凭据以实现免交互推送，但 `git remote -v`
  的输出含令牌，汇报结果时必须打码，不要原样粘贴到聊天里。
- 令牌泄露时：在 Gitee「设置-私人令牌」中删除旧令牌并新建，
  再用新令牌更新 `.git-credentials` 与 `git remote set-url`。

## 注意

- 提交前先 `git diff --cached` / `git status` 检查，不要提交密钥、令牌等敏感信息。
- 不要修改全局 git 配置、不要 `--amend`、不要强制推送，除非用户明确要求。
- 本仓库无根 `.gitignore`；`.opencode/.gitignore` 已排除 node_modules 等。
  如出现明显不该入库的临时文件，先询问用户。
- 任何技能文件、AGENTS.md、提交信息里都不得出现令牌明文。
