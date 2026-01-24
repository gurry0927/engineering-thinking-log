# 個人成長地圖 (Personal Growth Map)

這是一份動態更新的技能與職涯進化圖。它記錄了我如何從「非資訊背景」轉型為「AI 工程師」的過程，並將目前累積的「自動化能力」轉化為未來「機器學習」的基石。

## 🗺️ 技能演進圖 (Skill Tree)

```mermaid
graph TD
    %% 核心出發點
    Start["數學背景 / 教學經驗"] --> Logic["邏輯推理力"]
    Start --> UX["非技術者視角 (UX)"]

    %% 第一階段：自動化基石 (2025-09)
    Logic --> GAS["GAS 腳本開發<br/>(09/17)"]
    Logic --> PRD["PRD 需求定義<br/>(09/18)"]
    UX --> PRD
    GAS --> API["API 串接基礎<br/>(09/16)"]
    GAS --> Auth["權限控管<br/>(09/17)"]
    
    %% 第二階段：系統架構
    API --> Arch["系統架構設計 (P-01)<br/>(09/19)"]
    Auth --> Arch
    PRD --> Arch
    Arch --> State["狀態管理與日誌系統<br/>(09/18)"]

    %% 第三階段：資料科學與 ML (目標)
    State --> Pipeline["Data Pipeline / ETL"]
    API --> ML_Service["AI 服務整合 (LLM)"]
    Pipeline --> ML["機器學習工程 (Model Landing)"]
    ML_Service --> ML

    %% 樣式設定
    style Start fill:#f9f,stroke:#333,stroke-width:4px
    style GAS fill:#bbf,stroke:#333
    style Arch fill:#bfb,stroke:#333
    style ML fill:#fbb,stroke:#333,stroke-dasharray: 5 5
```

## 🏆 當前能力等級 (Status)

| 領域 | 熟練度 | 關鍵里程碑 | 獲得日期 |
| :--- | :--- | :--- | :--- |
| **自動化開發 (GAS)** | ⭐⭐⭐ | 成功實作 P-01 兩階段系統 | 2025-09-17 |
| **產品定義 (PRD)** | ⭐⭐⭐ | 成功將教案經驗遷移至需求文件 | 2025-09-18 |
| **API 串接** | ⭐⭐ | 成功解決 Drive API 版本衝突 | 2025-09-16 |
| **架構設計** | ⭐⭐ | 建立「狀態管理」與「全自動回傳」 | 2025-09-19 |
| **Gmail 自動化** | ⭐⭐ | 實現附件抓取與自動歸檔 | 2025-09-24 |
| **機器學習 (ML)** | ⭐ | (目標) 維持 Kaggle 清洗資料手感 | - |

## 🚀 未來進化路徑 (Roadmap)

### 1. 短期：自動化專家 (0-6 個月)
- [ ] 掌握更加複雜的 Webhook 處理（如：非同步訊息回傳）。
- [ ] 在公司內部推薦使用 Odoo/ERPNext 等開源框架。

### 2. 中期：AI 落地工程師 (6-18 個月)
- [ ] 將大模型 (GPT/Gemini) 整合進現有的自動化 Pipeline。
- [ ] 實作第一個具備 RAG (檢索增強生成) 的企業內部知識庫機器人。

### 3. 長期：ML 工程師 (18+ 個月)
- [ ] 轉向處理更核心的數據模型，實現「AI 工程師」的職稱實質化。

---
> **最後更新日期**：2025-09-24 (入職第兩週)
