# 工程圖 AI 門窗表處理系統 (P-04)

## 📌 專案簡介
本專案為解決「工程圖門窗表 (PDF)」人工讀取緩慢且易錯的問題。系統整合了電腦視覺 (OpenCV) 與大語言模型 (LLM)，實現從圖紙裁切到數據結構化的自動化流程，並成功部署於雲端生產環境。

## 🚀 專案演進紀錄 (Evolution History)

### Phase 1 (2025-11-15 ~ 2025-11-25)
**核心目標**：建立從 PDF 圖檔到 JSON 數據的解析引擎。
- **功能項目**：
    - **影像預處理 (OpenCV)**：自動裁切門窗表特定區域，過濾雜訊，提升 AI 辨識率。
    - **AI 解析引擎 (GPT API)**：使用 Python 調用 ChatGPT API 進行表格數據提取。
    - **異構資料清洗 (Heterogeneous Data Cleaning)**：處理不同事務所格式不一（如 W, Width, 寬）的欄位對應與單位換算。
    - **多工平行處理 (Parallelism)**：針對大型 PDF 檔案設計平行處理邏輯，解決 GCP Cloud Run 超時與掛起問題。
    - **LineBot 入口**：使用者直接透過 Line 上傳 PDF，非技術人員也能輕鬆操作。

## ⚙️ 技術架構
- **Front-end**: Line Messaging API
- **Back-end**: Python (Flask/FastAPI)
- **Computer Vision**: OpenCV
- **AI Engine**: ChatGPT API (採用「先規則匹配後語義辨識」之混合架構)
- **Deployment**: Docker + GCP Cloud Run

## 🧩 遇到的挑戰與解決方法

### 1. 異構格式的語義對齊
- **挑戰**：各家建築師事務所提供的門窗表格式極度不統一，欄位命名與單位標註（mm/cm/m）混亂，難以用單一規則解析。
- **解決**：設計了 **「規則式 (Regex) + 語義層 (LLM API)」** 的雙層解析機制。先用正則快速處理 80% 標準格式，剩下的由 LLM 進行語義判定。

### 2. 雲端環境超時 (GCP Hang/Timeout)
- **挑戰**：處理複雜 PDF 時，Cloud Run 容易掛起。
- **解決**：改用異步並行處理 (Async Pipeline)，優化 Webhook 回傳機制。

## 🔬 專案定位：資料工程與 AI 的結合
本專案不僅是 AI 應用，更是深度的 **資料工程 (Data Engineering)** 實踐。它解決了從「非結構化影像」到「結構化數據」的關鍵轉換，為後續的採購與成本分析打下了乾淨的數據基礎。

---
> **備註**：本專案體現了「架構思維驅動開發」的核心競爭力，證明了在 AI 時代，能將「髒資料」洗乾淨並工程化落地的能力，才是數據科學家的核心競爭力。
