---
name: daily-planner
description: Generate daily work reports and manage daily planning. Integrates with Things MCP (todos), Jira MCP (tickets), and Obsidian MCP (documents). Use when the user asks to plan their day, generate a work report, check today's tasks, or review open tickets. Triggers include phrases like "plan my day", "what's on my plate today", "daily report", "today's tasks", or "my open tickets".
---

# 每日規劃

建立結構化筆記格式的完整每日計畫，適用於 Obsidian 或 Notion 等工具。

## 任務管理

所有待辦事項都通過 **Things MCP** 管理。使用 Things MCP 工具來：

- 檢索現有任務
- 始終將新任務建立到收件匣
- 更新任務狀態
- 按專案和區域組織（`get_projects`、`get_areas`）

## 工單管理

所有工單都通過 **Jira** 管理。使用 Jira MCP 工具

## 專案管理

所有專案都通過 **Obsidian** 管理。

**範本屬性**

| 屬性 | 說明 | 範例 |
|------|------|------|
| `jira` | Jira 工單鍵值 | `proj-123` |
| `space` | Jira 專案識別碼 | `TWPE` 或 `TWECP` |
| `created` | 文檔建立日期 | `2025-01-15` |
| `updated` | 最後更新日期 | `2025-01-20` |

- **路徑模式**：`Work/Projects/[ProjectName].md`
- **範本**：`assets/project.md`

## 每日筆記

- **路徑模式**：`DailyNote/YYYY/MM/YYYY-MM-DD.md`
- **取得今日筆記**：使用 `mcp__mcp-obsidian__obsidian_get_periodic_note` 並設定 `period: "daily"`

## 會議紀錄

所有專案都通過 **Obsidian** 管理。

- **路徑模式**：`Work/meetings/[meeting].md`
- **範本**：`assets/meeting_minutes.md`

**範本屬性**

| 屬性 | 說明 | 範例 |
|------|------|------|
| `date` | 會議日期 | `2025-01-15` |
| `participants` | 參加者 | ["Dustin", "Ryan Lee"] |

## 工作

### 產生每日工作報告

按序依次處理工作項目，每個步驟完成後等待使用者確認：

#### 第一步：檢視我的未結 Jira 工單

使用 `mcp__atlassian__searchJiraIssuesUsingJql` 搭配 JQL：
```
assignee = currentUser() AND statusCategory not in (Done) ORDER BY updated DESC
```

Fields：`["summary","status","issuetype","priority","created","updated","duedate","project"]`，maxResults：`50`

展示工單列表並請使用者 review、更新工單狀態或備註，待處理完畢後繼續。

#### 第二步：檢視今日待辦清單

使用 `mcp__things__get_today` 檢索今日應完成的任務。

展示任務列表並請使用者 review、完成或更新任務狀態，待處理完畢後繼續。

#### 第三步：整理今日筆記

使用 `mcp__mcp-obsidian__obsidian_get_periodic_note` 並設定 `period: "daily"` 來檢索今日筆記內容。

根據前兩個步驟的結果和今日筆記，產生最終的每日報告。

#### 最終輸出範本

```markdown
# 每日報告 - {date}

## Jira 工單
| 鍵值 | 摘要 | 狀態 | 優先度 | 截止日期 |
|-----|------|------|--------|---------|
| {ticket data} |

## 今日任務
| 任務 | 備註 | 專案/區域 |
|------|------|---------|
| 標題 | 備註摘要 | 專案或區域 |

## 今日筆記
{每日筆記的摘要內容，如可用}
```

## **重要規則**

- 建立或編輯 Obsidian 筆記時，請始終叫用 `obsidian-markdown` skill 以確保正確的 Obsidian Flavored Markdown 語法（wikilinks、callouts、frontmatter 等）。
