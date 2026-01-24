# Gmail 自動化：使用 GAS 讀取與處理附件

## 核心概念
Google Apps Script (GAS) 提供了 `GmailApp` 服務，讓開發者無需處理複雜的 OAuth 流程即可直接在 Google 雲端操作信箱。這對於建立「自動歸檔附件」或「郵件觸發工作流」非常高效。

## 詳細筆記

### 1. 基礎操作：讀取附件
*   **入口選擇**：無需在 Gmail 內尋找腳本，直接在任何 GAS 專案（甚至是獨立腳本）中使用即可。
*   **關鍵代碼**：
    ```javascript
    var threads = GmailApp.getInboxThreads(0, 5); // 抓最新 5 封
    var attachments = threads[0].getMessages()[0].getAttachments();
    var fileName = attachments[0].getName(); // 抓取附件檔名
    ```

### 2. 進階：Gmail API (Advanced Service)
*   若需要更細緻的 Metadata（如原始郵件 Header）或執行更複雜的搜尋，需在 GAS「服務」中啟用 **Gmail API**。

### 3. 自動化歸檔流程 (Archiving Flow)
1.  **搜尋規則**：使用 `GmailApp.search("subject:發票")` 定位目標郵件。
2.  **提取附件**：遍歷郵件並抓取 Blobs。
3.  **Drive 存檔**：`DriveApp.getFolderById(id).createFile(blob)`。
4.  **分類邏輯**：根據檔案名稱 (`getName()`) 判斷資料夾 ID。

## 學習心得
「GAS 是 Google 生態系的膠水」。透過 `GmailApp`，我們可以輕易地將收件匣轉化為自動化 Pipeline 的起點，且完全無需維護伺服器。

---

## 外部建議與提議 (AI Suggestions)
- [ ] 每天定時執行一次的「自動歸檔附件」完整腳本範本。
