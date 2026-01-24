# 輕量級資料庫方案：Google Sheets + GAS

## 核心概念
對於開發初期、Side Project 或企業內部中小型需求，Google Sheets 配合 Google Apps Script (GAS) 可以提供一套免維運、幾乎零成本的資料庫與 API 服務。

## 詳細筆記

### 1. 方案優勢
*   **低門檻/低成本**：只要有 Google 帳號即可開啟，無需支付伺服器或資料庫授權費用。
*   **視覺化介面**：Google Sheets 本身就是最直覺的後台管理介面，非技術人員也能直接閱讀。
*   **高整合性**：與 Google Form, Gmail, Drive 達成無縫連接。

### 2. 技術特性
*   **資料量**：單個 Sheet 支援 500 萬格，足以應對數萬筆紀錄。
*   **API 化**：可將 GAS 部署為網頁應用程式 (Web App)，透過 HTTP GET/POST 進行 CRUD 操作。

### 3. 限制與邊界
*   **效能上限**：高併發或超大數據量（十萬筆以上）時讀寫效能會顯著下降。
*   **非關聯式**：缺乏正規資料庫的 Schema 限制與複雜 SQL 查詢能力。
*   **安全性**：雖有權限控管，但較難達成細粒度的資料庫權限管理。

## 學習心得
這是一個非常適合「快速原型 (Prototype)」的方案。在 09-24 的進階開發中，這項基礎認識支撐了後續更複雜的自動化系統設計。

---

## 外部建議與提議 (AI Suggestions)
- [ ] Google Sheet 當資料庫 vs Firebase / Supabase 差異對比表。
