# 生產級管線設計 (Production-Ready Pipeline)：防重複、重試與狀態管理

## 📌 背景
在大規模自動化流程中（如 kintone 歸檔專案），「寫入成功」只是基本，真正的挑戰在於「當網路斷掉、API 限流、或有人瘋狂點擊時，系統會不會炸掉」。

## 🛠️ 五大核心可靠性機制

### 1. 防重複觸發 / 冪等性 (Idempotency)
- **問題**：使用者重複點擊送出，導致資料庫出現兩筆重複報價。
- **解法**：在寫入前檢查是否存在相同 `Source_ID` 或 `Timestamp`；或在 GAS 中設置 `LockService` 鎖定同步區間。

### 2. 失敗重試機制 (Retry Logic)
- **問題**：kintone API 暫時性超時或連線不穩定。
- **解法**：使用 `try/except` 包裹 API 調用，設計指數退避 (Exponential Backoff) 策略，在幾秒後自動再次嘗試。

### 3. 排隊系統 (Queueing / Throttling)
- **問題**：一次處理上百筆資料，導致 API 超過額度。
- **解法**：將任務寫入中繼表 (Queue Table)，設計分段處理邏輯，確保每次僅執行 10 筆。

### 4. 狀態管理 (State Tracking)
- **問題**：不知道哪一筆成功、哪一筆失敗，出事時無法補救。
- **解法**：資料表必備 `Status` 欄位（Pending, Processing, Completed, Failed）。

### 5. 錯誤日誌 (Log Management)
- **重點**：不僅要記錯誤訊息，還要記下**「發生錯誤時的原始 Payload」**，讓開發者能重現問題。

## 💡 總結：架構師的直覺
新手只看 Happy Path（順利運行）；**老手專門研究「如果這裡斷掉會怎樣」**。這種對異常情況的預判（Exception Handling），決定了系統能否在無人看管的情況下存活。

---
> **心法**：不要期待環境是完美的，要在混亂的環境中建構不倒的邏輯。
