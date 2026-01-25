---
name: committer
description: 建立 git commit，使用 markdown 格式的簡潔 commit message。當使用者想要 commit 變更時使用。
user-invocable: true
disable-model-invocation: false
allowed-tools: Bash
---

# Commit 變更

你正在協助使用者根據其特定需求建立 git commit。

## 步驟

1. **檢查目前狀態**：平行執行這些 command：
   - `git status` 查看所有變更（永遠不要使用 -uall flag）
   - `git diff` 查看已 staged 和未 staged 的變更
   - `git log -5 --oneline` 了解 commit message 風格

2. **分析變更**：檢閱所有變更並決定哪些 file 應該被 commit

3. **建立 commit message**：
   - 必須使用 markdown 格式（用 `##` 作為標題）
   - 必須盡可能簡潔（最多 1-2 句）
   - 專注於變更了什麼（WHAT）以及為什麼（WHY），而非如何（HOW）
   - 遵循 git log 中現有的 commit 風格

4. **Stage files**：使用 `git add <specific-files>` 加入相關 file
   - 優先使用 file name 加入特定 file
   - 不要 commit 包含 secret 的 file（.env、credentials.json 等）

5. **建立 commit**：使用 HEREDOC 格式並加上 Co-Authored-By 行：
   ```bash
   git commit -m "$(cat <<'EOF'
   ## Your commit title

   Brief description of the changes.

   Co-Authored-By: Claude Sonnet 4.5 <noreply@anthropic.com>
   EOF
   )"
   ```

6. **驗證**：commit 後執行 `git status` 確認成功

## 重要規則

- commit message 永遠使用英文撰寫
- 加入新 file 前永遠先詢問確認
- 永遠建立新的 commit（除非明確要求，否則不要使用 --amend）
- 如果 pre-commit hook 失敗，修正問題後建立新的 commit（不要 amend）
- 除非明確要求，否則永遠不要跳過 hook（--no-verify）
- 除非使用者明確要求，否則不要 push
- 如果沒有變更，不要建立空的 commit
- commit 前，向使用者展示 commit message 和已 staged 的 file，詢問確認後再 commit

## Commit Message 格式範例

```
## Add user authentication
- Implemented JWT-based authentication with refresh tokens.
- Implemented cookie base authentication.

Co-Authored-By: Claude Sonnet 4.5 <noreply@anthropic.com>
```
