# GAS 進階：doPost(e) —— 與外部世界對談的窗口

## 核心概念
`doPost(e)` 是 Google Apps Script (GAS) Web App 的核心入口之一。與 `doGet` 不同，它是為接收「資料流」而設計的。

## 詳細筆記

### 1. `doPost(e)` 的定位
*   **入口點**：當外部服務以 HTTP POST 方法呼叫你的 Web App URL 時觸發。
*   **角色比喻**：如果是 `doGet` 是餐廳菜單，`doPost` 就是「外送收貨區」。你需要點收資料（Payload），處理訂單（Logic），最後給予回條（Response）。

### 2. 典型應用場景
*   **Line / Telegram Bot Webhook**：接收傳訊軟體的訊息通知。
*   **表單自定義提交**：從個人 React/Vue 前端將資料以 JSON 格式發送到 GAS。
*   **內部系統串接**：不同系統間的自動化觸發或資料同步。

### 3. 測試的必要性（交界點檢核）
工程師習慣在每個架構都測一下 `doPost`，是為了驗證「系統邊界」的穩定性：
1.  **解析測試**：能否正確處理傳入的 `e.postData.contents`（如 JSON.parse）。
2.  **安全性測試**：是否正確驗證了來源的 Token。
3.  **回傳測試**：回條格式（JSON/Text）是否符合呼叫端的規範。

## 學習心得
雖然同事視其為常識，但釐清 `doPost` 作為「系統交會點」的物理屬性，對於設計健壯的架構至關重要。不測試交界點，系統內部寫得再好也無法被觸發。

---

## 外部建議與提議 (AI Suggestions)
- [ ] 模擬外部 POST 呼叫的簡易程式片斷 (JavaScript fetch & curl)。
