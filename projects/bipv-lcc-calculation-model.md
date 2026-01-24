# BIPV 生命週期成本計算模型 (P-03)

## 📌 專案簡介
本專案為老闆直接交付的決策支援任務，旨在建立一個 Excel 動態模型，用於計算與比較 **BIPV (建築整合型太陽能)** 在不同建築壽命下的生命週期成本 (LCC) 與電力成本 (LCOE)。

## 🚀 專案演進紀錄 (Evolution History)

### Phase 1 (2025-10-08 ~ 2025-10-09)
**核心目標**：建立可互動的高邏輯 Excel 財務模型。
- **功能項目**：
    - **參數化 Input 模組**：可自定義折現率、初始成本 (CAPEX)、運維費 (O&M) 等。
    - **多情境比較 (Scenario Analysis)**：自動對比建材 30 年與 50 年的長期經濟效益。
    - **折現運算 (NPV)**：將未來維護與汰換成本折算為現值。
    - **殘值與退場機制**：根據直線法計算期末資產價值與退場支出。
    - **效率衰減模型**：考慮光電板 20 年後 80% 效率的發電量修正。

## ⚙️ 技術架構
- **Engine**: Microsoft Excel (Advanced Formulas)
- **Methodology**: Life Cycle Cost Analysis (LCCA)
- **Financial Concept**: Net Present Value (NPV), Equivalent Annual Cost (EAC)

## 🧩 遇到的挑戰與解決方法

### 1. 跨領域知識整合 (Finance + Energy)
- **挑戰**：對財務折現 (Discounting) 與能源衰減 (Degradation) 概念缺乏實務經驗。
- **解決**：將問題抽象化為數學模型。不深究物理參數，而是專注於「變數間的邏輯鏈結」。先撰寫 [PRD](file:///d:/git/engineering-thinking-log/learning/02-product/prd-bipv-lcc-model.md) 鎖定範疇，再逐一導出公式。

### 2. 模型靈活性需求
- **挑戰**：老闆需要能「隨時調整」數字看結果。
- **解決**：禁止使用常數 (Hardcoding)，所有公式均引用單一的 Inputs 表，並設計 Results 表整合圖表，實現「一鍵更新」。

---
> **備註**：此專案展現了開發者將「邏輯抽象能力」遷移至「財務決策模型」的能力，是從單純 Coding 轉向系統工程的重要指標。
