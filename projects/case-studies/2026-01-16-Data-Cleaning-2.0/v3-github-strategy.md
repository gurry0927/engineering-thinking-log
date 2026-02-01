# 專案作品化策略：面對不確定性的資料清洗思維

> [!NOTE]
> 本文件紀錄了將「客戶資料清洗 2.0」抽象為 GitHub 作品的設計思路與核心論點。

## 🎯 核心標語 (Core Tagline)
> **"How do you know your cleaned data is correct — when there is no ground truth?"**

## 🏗️ 核心架構：面向可審計性的設計 (Design for Auditability)
不展示複雜的 Regex 規則，而是展示應對資料風險的結構化立場：

1. **三軌 ID 隔離 (ID Isolation)**
   - `Raw ID`: 鎖定原始關係，決不遺失。
   - `Normalized ID`: 僅作為候選身分，隨時演進。
   - `Mapping Table`: 獨立的對應關係層，支援 Rollback 與重算。

2. **認知層級的標註 (Epistemic Labeling)**
   - `mapping_method`: 紀錄每一筆結果是來自規則、AI 或人工覆寫。
   - `confidence_level`: 承認系統的不確定性。

3. **可修正的生命週期 (Correctable Lifecycle)**
   - 強調與平台功能（如 Odoo Merge）的整合，而不是取代人的最終決策。

## 🧠 分享敘事線 (Narrative Path)
1. **命名焦慮**：一開始追求找到「正確名字」，隨即陷入直覺失效的泥淖。
2. **結構恐懼**：意識到比命名更危險的是「資料悄悄遺失」。
3. **現實接受**：體認到「沒有唯一正解」，並據此設計了可承受錯誤的結構。

## 🚀 價值定義
這個 Repo 展示的不是一個 API 呼叫工具，而是：**「當系統規模超出人類直覺、且資料缺乏唯一標準時，工程師應如何設計一個負責任的 Data Pipeline。」**
