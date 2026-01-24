# LineBot API：檔案訊息處理與身分追蹤

## 核心概念
Line Messaging API 對於檔案 (File Message) 的處理與一般的文字訊息不同，開發者必須處理「下載流」與「身分標識」兩大議題。

## 詳細筆記

### 1. 檔案訊息的限制
*   **檔名缺失**：當使用者上傳檔案時，Webhook 的 Payload 只會包含 `messageId`, `fileName` (部分情況為空), `fileSize`。
*   **最佳實作**：
    1. 使用 `https://api-data.line.me/v2/bot/message/{messageId}/content` 獲取內容。
    2. 將內容以 Blob 形式存入 Google Drive。
    3. 利用 DriveAPI 讀取檔名並執行 Business Logic 驗證。

### 2. ID 追蹤：User vs Group vs Room
*   **UserId**: 唯一標識一位使用者。但在群組中，若 User 未與 Bot 成為好友，Bot 可能無法取得其完整 Profile，且無法進行 Push 私訊。
*   **GroupId / RoomId**: 標識訊息來源的空間。
*   **策略**：為了確保「精準回傳」，資料表必須同時記錄 `UserId` 與 `GroupId`。優先推播回原 `GroupId` 以確保資訊透明，`UserId` 則作為後續進階功能（如：私人處理報告）的備用。

### 3. 動態刪除與通知
*   **代碼片段 (GAS)**：
    ```javascript
    if (!isValid(fileName)) {
      DriveApp.getFileById(fileId).setTrashed(true); // 移至垃圾桶
      replyLine(replyToken, "檔名不符規則，系統已自動刪除。");
    }
    ```

## 學習心得
在 API 限制下，設計系統就像在玩「解謎遊戲」。先接受受限的資料，透過中轉（Drive/Sheet）來補完缺失的資訊（檔名），這是建構健壯自動化流程的關鍵。

---

## 外部建議與提議 (AI Suggestions)
- [ ] 不同 SDK 版本下的 `getMessageContent` 實作範例。
