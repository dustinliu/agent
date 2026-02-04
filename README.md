# Skill Copier

從 skills 資料庫複製 skills 到各 IDE（Claude Code、Cursor、Antigravity）的 skills 目錄。

## 專案結構

```
.
├── pyproject.toml         # 專案配置（使用 uv 管理）
├── deploy.py              # 主要 script
├── test_deploy.py         # 測試檔案（37 個測試案例）
├── skills_config.toml     # Config 檔案範例
└── README.md
```

## 安裝

### 使用 uv（推薦）

```bash
# 安裝 dependencies 並設置 virtual environment
uv sync

# 或者如果只需要執行，不需要開發環境
uv sync --no-dev
```

### 使用 pip

```bash
# 安裝為可編輯 package
pip install -e .

# 安裝開發 dependencies
pip install -e ".[dev]"
```

## 快速開始

### 1. 編輯 Config 檔案

編輯 `skills_config.toml`，設定你的 skills 來源和目標 IDE 目錄：

```toml
# 只需列出 skill 名稱
skills = [
    "architect",
    "frontend-design",
    "my-custom-skill",
]

# 定義所有 skill 來源目錄（會自動搜尋）
[sources]
paths = [
    "~/src/agent-skills/skills",  # 外部 skills 資料庫
    "./skills",                    # 本地 skills
]

# 設定目標 IDE
[targets.claude_code]
path = "~/.claude/skills"
enabled = true  # 啟用這個 target

[targets.cursor]
path = "~/.cursor/skills"
enabled = false  # 不啟用
```

### 2. 執行 Script

**使用 uv（推薦）**：

```bash
# Dry-run 模式（只查看不實際執行）
uv run deploy --dry-run

# 實際建立連結
uv run deploy

# 使用自訂 config
uv run deploy my_config.toml
```

**直接執行**（需要先 `uv sync` 或 `pip install -e .`）：

```bash
# 如果已經安裝了 package，可以直接使用 console script
deploy
deploy --dry-run
deploy my_config.toml
```

**使用 Python 直接執行**：

```bash
python deploy.py
python deploy.py --dry-run
python deploy.py my_config.toml
```

## 功能特色

✅ **自動搜尋 skills**：只需指定名稱，自動在多個來源目錄中搜尋
✅ **支援多個 IDE**：同時複製到 Claude Code、Cursor、Antigravity 等
✅ **彈性路徑**：支援絕對路徑、相對路徑、`~` (home directory)
✅ **自動建立目錄**：不存在的目標目錄會自動建立
✅ **智慧更新**：自動覆蓋已存在的目錄、檔案或 symlink
✅ **Dry-run 模式**：安全預覽不實際執行
✅ **清楚的狀態顯示**：即時顯示執行進度
✅ **完整測試覆蓋**：37 個測試案例，95.42% 覆蓋率

## 範例輸出

```
📖 讀取 config: skills_config.toml

🎯 找到 5 個 skills

📍 啟用的 targets: claude_code

🎯 處理 target: claude_code
   目標目錄: /Users/username/.claude/skills
   📁 已建立目錄: /Users/username/.claude/skills
   ✅ 已複製: architect <- /Users/username/src/agent-skills/skills/architect
   ✅ 已複製: frontend-design <- /Users/username/src/agent-skills/skills/frontend-design
   ✨ 完成: 更新/複製 2，共 2/5 個 skills

✨ 所有 skills 已複製完成!
```

## 常見使用情境

### 情境 1：複製外部 skills 資料庫到 Claude Code

```toml
skills = ["architect", "qa", "frontend-design"]

[sources]
paths = ["~/src/external-skills"]

[targets.claude_code]
path = "~/.claude/skills"
enabled = true
```

### 情境 2：同時複製到多個 IDE

```toml
skills = ["my-skill", "architect"]

[sources]
paths = ["./skills", "~/external-skills"]

[targets.claude_code]
path = "~/.claude/skills"
enabled = true

[targets.cursor]
path = "~/.cursor/skills"
enabled = true

[targets.antigravity]
path = "~/.antigravity/skills"
enabled = true
```

### 情境 3：多個 skills 來源（自動搜尋）

```toml
skills = ["architect", "qa", "my-dev-skill"]

[sources]
paths = [
    "~/external-skills",        # 外部 skills
    "~/another-repo/skills",    # 另一個來源
    "./skills",                 # 本地開發中的 skills
]

[targets.claude_code]
path = "~/.claude/skills"
enabled = true
```

**優點**：不需要知道每個 skill 在哪裡，script 會自動在所有來源中搜尋！

## 疑難排解

### 問題：來源不存在

```
⚠️ 來源不存在，跳過: /path/to/skill
```

**解決方法**：確認 config 中的 `path` 設定正確，且該目錄確實存在。

### 問題：權限不足

確保你有權限在目標目錄建立和刪除檔案/目錄。

### 問題：複製失敗

檢查：
1. 目標目錄的父目錄是否存在
2. 是否有檔案系統權限
3. 磁碟空間是否足夠

### 問題：無法移除舊的 symlink

已在 v1.1.0 修復。如果遇到 `OSError: Cannot call rmtree on a symbolic link` 錯誤，請更新到最新版本。

## 執行測試

專案包含完整的測試覆蓋（37 個測試案例）：

**使用 uv**：
```bash
# 執行所有測試
uv run pytest

# Verbose 模式
uv run pytest -v

# 執行特定測試檔案
uv run pytest test_deploy.py

# 執行特定測試 class
uv run pytest test_deploy.py::TestFindSkillInSources
```

**使用 pytest 直接執行**（需要先安裝）：
```bash
pytest
pytest -v
```

