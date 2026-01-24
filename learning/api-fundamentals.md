# API 101：萬物皆可串的「功能按鈕」

## 核心概念
API (Application Programming Interface) 是系統之間溝通的「標準化接口」。只要有 API，你就不用管對方系統內部怎麼跑，只要「按鈕」按對，它就會給你結果。

## 詳細筆記

### 1. API 的本質
*   它是一個**網址** (Endpoint)。
*   它是一套**規則** (Protocol)。
*   它是**捷徑**：不用自己種菜煮飯，直接點外送。

### 2. 三大組成要素
*   **Request (請求)**：你送出的參數（通常是 JSON 格式）。
*   **Method (方法)**：
    *   `GET`：向對方拿資料（如：查詢天氣）。
    *   `POST`：送資料給對方（如：回覆 LINE 訊息）。
*   **Response (回應)**：對方回傳的結果，包含狀態碼（如 200 代表成功）。

### 3. 工具橋樑：Google Apps Script (GAS)
當前公司主要使用的工具。透過 `UrlFetchApp.fetch()`，GAS 就像一根連接線，把 Google 表單的資料推送到 LINE 的 API 接口。

## 學習心得
為什麼大家一直問「有沒有 API」？因為有 API 就代表「這件事可以被自動化」，且不用重新發明輪子。對 API 的理解力，直接決定了解決辦公室效率問題的速度。

---

## 外部建議與提議 (AI Suggestions)
- [ ] API 入門速查表（Google Sheet + Line Bot 專用實戰版）。
