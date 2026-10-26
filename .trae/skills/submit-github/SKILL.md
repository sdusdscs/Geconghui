---
name: "submit-github"
description: "Commits all changes and pushes to GitHub remote. Invoke when user says 提交到GitHub/github push, or asks to commit to GitHub repository."
---

# 提交项目到 GitHub（commit + push）

将当前项目的所有改动用 `git commit` 提交，并推送到 GitHub 远程仓库
`https://github.com/sdusdscs/Geconghui`。

## 步骤

1. 检查仓库状态与当前远程：

   ```powershell
   git status
   git remote -v
   git log --oneline -5
   ```

2. 若没有指向 `https://github.com/sdusdscs/Geconghui` 的远程，则添加
   （已有同名 `github` 但地址不符时，用 `git remote set-url github <url>` 修正）：

   ```powershell
   git remote add github https://github.com/sdusdscs/Geconghui.git
   ```

3. 暂存全部改动：

   ```powershell
   git add -A
   ```

4. 提交。提交信息用简短中文，说明改了什么；若没有可区分的改动，
   不要创建空提交，直接结束：

   ```powershell
   git commit -m "提交网页设计作业"
   ```

5. 推送到 GitHub：

   ```powershell
   git push github HEAD
   # 若远程分支尚无历史，使用：
   git push -u github HEAD
   # 若被拒绝（远程已有提交），先了解差异再处理，禁止直接 force push：
   git fetch github
   git status
   ```

6. 汇报结果：提交 hash、推送的分支、远程仓库地址；如推送失败，
   原样带回错误信息。

## 注意

- 提交前先 `git diff --cached` / `git status` 检查，不要提交密钥、令牌等敏感信息。
- 不要修改全局 git 配置、不要 `--amend`、不要强制推送，除非用户明确要求。
- 已设置公钥认证，推送时使用 SSH 或 HTTPS 均可。
