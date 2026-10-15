---
name: submit-project
description: Use when the user says 提交项目、提交、上传、push、推送到 Gitee/GitHub, or asks to commit the current project. Commits all changes with git and pushes them to https://gitee.com/ge-conghui/geconghui2026.git.
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

5. 推送。若远程分支尚无历史或被拒绝，使用带 `-u` 的强制对齐推送：

   ```powershell
   git push -u origin HEAD
   # 若被拒绝（远程已有提交），先了解差异再处理，禁止直接 force push：
   git fetch origin
   git status
   ```

6. 汇报结果：提交 hash、推送的分支、远程仓库地址；如推送失败，
   原样带回错误信息（常见：需要用户名/密码或 Gitee 私人令牌、网络问题、
   远程有他人提交需先 pull）。

## 注意

- 提交前先 `git diff --cached` / `git status` 检查，不要提交密钥、令牌等敏感信息。
- 不要修改 git 配置、不要 `--amend`、不要强制推送，除非用户明确要求。
- 本仓库无 `.gitignore`，如出现明显不该入库的临时文件，先询问用户。
