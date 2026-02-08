---
name: secretary
description: "Manage Obsidian notes (projects, daily notes, meeting minutes) and optionally generate daily reports. Integrates with Jira MCP, Things MCP, and Obsidian MCP. Use when the user asks to: (1) Create, update, or organize project notes, (2) Update or review daily notes, (3) Create meeting minutes, (4) Manage Obsidian documents, or (5) Generate a daily report (only when explicitly requested). Triggers include phrases like 'update my project note', 'create meeting minutes', 'add to my daily note', 'organize my Obsidian', 'manage documents', or 'generate daily report'."
---

# Secretary

助理職責：管理 Jira 工單、Todo 任務、維護 Obsidian 文件，產生日常工作報告。

## Jira 工單管理

所有工單都通過 **Jira** 管理。使用 Jira MCP 工具來：

- 搜尋和檢索議題
- 建立新工單
- 更新工單狀態和轉換
- 新增評論和工時日誌

## Todo 任務管理

所有待辦事項都通過 **Things MCP** 管理。使用 Things MCP 工具來：

- 檢索現有任務
- 建立新任務到收件匣
- 更新任務狀態
- 按專案和區域組織（`get_projects`、`get_areas`）

## Obsidian 文件管理

所有文件都通過 **Obsidian** 維護。支援的文件類型：

- **專案筆記**：`Work/Projects/[ProjectName].md`
  - 範本：`assets/project.md`
  - 屬性：`jira`（工單鍵值）、`space`（Jira 專案碼）、`created`、`updated`

- **每日筆記**：`DailyNote/YYYY/MM/YYYY-MM-DD.md`
  - 取得方法：`mcp__mcp-obsidian__obsidian_get_periodic_note` with `period: "daily"`

編輯 Obsidian 文件時，始終使用 `obsidian-markdown` skill 確保正確的語法。

## 產生每日報告（可選）

**只有在使用者明確要求時，才執行此工作流程。** 例如："Generate today's daily report" 或 "Create a daily report"。

### 工作流程

按序依次完成以下步驟，每個步驟完成後等待使用者確認：

#### 第一步：檢視未結 Jira 工單

使用 `mcp__atlassian__searchJiraIssuesUsingJql` 搭配 JQL：
```
assignee = currentUser() AND statusCategory not in (Done) ORDER BY updated DESC
```

Fields：`["summary","status","issuetype","priority","created","updated","duedate","project"]`，maxResults：`50`

展示工單列表供使用者 review、更新工單狀態或備註。

#### 第二步：檢視今日待辦清單

使用 `mcp__things__get_today` 檢索今日應完成的任務。

展示任務列表並請使用者 review、完成或更新任務狀態。

#### 第三步：檢視 Obsidian 每日筆記

使用 `mcp__mcp-obsidian__obsidian_get_periodic_note` 並設定 `period: "daily"` 來檢索今日筆記。

根據筆記內容協助整理或更新。

#### 第四步：產生每日報告

根據 Jira 工單、Todo 任務和 Obsidian 筆記，產生結構化的日報：

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

## Obsidian 筆記
{每日筆記的摘要內容，如可用}
```

## **重要規則**

- 編輯 Obsidian 筆記時，始終使用 `obsidian-markdown` skill 確保正確的語法。
