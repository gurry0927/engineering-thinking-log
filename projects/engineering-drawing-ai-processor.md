# 工程圖 AI 門窗表處理系統 (P-04)

## 📌 專案簡介
本專案為解決「工程圖門窗表 (PDF)」人工讀取緩慢且易錯的問題。系統整合了電腦視覺 (OpenCV) 與大語言模型 (LLM)，實現從圖紙裁切到數據結構化的自動化流程，並成功部署於雲端生產環境。

## 🚀 專案演進紀錄 (Evolution History)

### Phase 1 (2025-11-15 ~ 2025-11-25)
**核心目標**：建立從 PDF 圖檔到 JSON 數據的解析引擎。
- **功能項目**：
    - **影像預處理 (OpenCV)**：自動裁切門窗表特定區域，過濾雜訊，提升 AI 辨識率。
    - **AI 解析引擎 (GPT API)**：使用 Python 調用 ChatGPT API 進行表格數據提取。
    - **多工平行處理 (Parallelism)**：針對大型 PDF 檔案設計平行處理邏輯，解決 GCP Cloud Run 超時與掛起問題。
    - **LineBot 入口**：使用者直接透過 Line 上傳 PDF，非技術人員也能輕鬆操作。

## ⚙️ 技術架構
- **Front-end**: Line Messaging API
- **Back-end**: Python (Flask/FastAPI)
- **Computer Vision**: OpenCV
- **AI Engine**: ChatGPT API / (Early testing with Gemini)
- **Deployment**: Docker + GCP Cloud Run

## 🧩 遇到的挑戰與解決方法

### 1. 數據安全性與 API Key 保護
- **挑戰**：初期地端版易導致 API Key 洩漏風險。
- **解決**：將系統容器化並部署至 GCP Cloud Run，將 Secret 儲存於雲端環境變量中，確保代碼與 Key 分離。

### 2. 雲端環境超時 (GCP Hang/Timeout)
- **挑戰**：處理複雜 PDF 時，Cloud Run 容易掛起。
- **解決**：
    - 改良為**平行處理 (Parallel Processing)** 模式。
    - 優化 Line 與 GCP 之間的通訊邏輯，確保 Webhook 快速回傳 `200 OK`，處理任務則在背景異步執行。

---
> **備註**：本專案完全由開發者自主發想架構，利用 AI（Claude/GPT）作為編碼助手實現細節，體現了「架構思維驅動開發」的核心競爭力。
