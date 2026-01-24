# Drive API v2 vs v3：權限處理的相容性陷阱

## 核心概念
在 Google Apps Script (GAS) 中使用進階服務時，不同版本的 API 在處理資源授權（如 Permissions）時有顯著差異。v2 常見於舊專案，而 v3 是現代標準，兩者不可混用。

## 詳細筆記

### 1. 衝突點：Permissions 處理
*   **v2 (Permissions.insert)**：直接建立權限關聯。
*   **v3 (Permissions.create)**：介面與參數對應與 v2 不同。
*   **現象**：如果你用了 v2 的代碼架構卻連結了 v3 的 Library，就會收到權限不足或參數錯誤。

### 2. Debug 心得：如何找到這種「幽靈錯誤」
*   **錯誤訊息具備欺騙性**：系統只會回報 `403 Forbidden` 或 `Internal Error`，而不會主動告訴你「你版本不對」。
*   **比對官方文件**：當 AI 給出的代碼沒錯，但環境一直報錯時，第一件事就是檢查「Service Dashboard」裡啟用的版本號與代碼中呼叫的資源是否對齊。

### 3. 進階建議
如果要確保穩定性，建議新專案全面對齊 v3，並查看 [Google API Migration Guide](https://developers.google.com/drive/api/v3/about-sdk)。

---

## 外部建議與提議 (AI Suggestions)
- [ ] Drive API v2 到 v3 的快速轉換速查表。
