# LineBot 檔案搜集與驗證系統 (P-02)

## 📌 專案簡介
本專案是一個具備「跨群組管理」能力的 LineBot。其核心任務是監聽各群組中的檔案上傳事件，自動驗證格式與檔名，並整合 Google Sheet 進行全流程狀態追蹤。

## 🚀 專案演進紀錄 (Evolution History)

### Phase 1 (2025-10-01)
**核心目標**：建立安全且可追蹤的檔案存取機制。
- **功能項目**：
    - **多群組監聽**：記錄 `GroupId` 以支援多個業務群組的檔案收集。
    - **非對稱驗證流程**：解決 API 限制，採用「先存檔、後驗證、不符即刪」的策略。
    - **狀態碼管理**：
        - `5`: 暫存/待驗證。
        - `10`: 驗證通過。
        - `-1`: 格式/名稱錯誤（已刪除）。
    - **資料存續**：同時記錄 `UserId` 以保留個人化推播的擴充空間。

## ⚙️ 技術架構
- **Interface**: Line Messaging API (File Message Event)
- **Engine**: Google Apps Script (GAS)
- **Database**: Google Sheet (Metadata Tracking)
- **Storage**: Google Drive (Physical Files)

## 🧩 遇到的挑戰與解決方法

### 1. 消失的檔名 (The Missing Filename Case)
- **挑戰**：Line API 在 Webhook 事件中不直接傳送檔案名稱，導致無法在第一時間進行規則檢查。
- **解決**：重定義流程順序。程式先透過 `getMessageContent` 下載二進制流，存入 Drive 生成實體檔案後，再讀取該檔案的 Property (`getName()`) 進行判斷。若不合規則，則觸發自動刪除。

### 2. 精準回傳與隱私權限
- **挑戰**：在匿名程度較高的群組中，難以確保能私訊通知特定上傳者。
- **解決**：在資料表中強制收集 `GroupId` 作為首要通知通道，同時保留 `UserId`。

---
> **備註**：此專案僅描述邏輯架構與技術挑戰，不包含任何公司內部敏感數據或私有代碼。
