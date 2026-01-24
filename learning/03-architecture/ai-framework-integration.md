# AI 框架整合：在 LineBot 中使用 Semantic Kernel

## 核心概念
LineBot 本質上是一個 Webhook 接收端。這意味著後端邏輯可以是任何強大的 AI 框架，如 Semantic Kernel 或 LangChain。Bot 的作用只是將 AI 的推理結果轉換為使用者可見的訊息。

## 詳細筆記

### 1. 整合流程 (Architectural Flow)
1. **Webhook 觸發**：使用者傳送訊息，LINE Server 推送到後端伺服器。
2. **AI Pipeline**：後端程式將訊息餵給 Semantic Kernel，執行其 Plugins 或 Skills（如 RAG 檢索、邏輯推理）。
3. **回傳結果**：SK 輸出的內容被包裝成 LINE 訊息格式（JSON）回傳給使用者。

### 2. 實務上的限制
*   **Time-out (3秒限制)**：LINE Messaging API 要求 Webhook 在 3 秒內回傳成功的 HTTP 狀態。AI 模型的推理時間往往超過此限。
    *   **對策**：使用**非同步處理**（立刻回傳 200 OK，然後另開 Thread 處理 AI 運算，最後用 Push API 傳回結果）。
*   **成本考量**：
    *   **LINE 訊息費**：免費版有訊息數量限制。
    *   **LLM API 費**：Semantic Kernel 必須串接外部模型（Azure OpenAI, OpenAI），這是主要開銷。

## 學習心得
「LineBot 是殼，Semantic Kernel 是心臟」。要把這顆心臟裝進殼裡，重點不在語法，而在於如何處理「網路延遲」與「非同步流」。

---

## 外部建議與提議 (AI Suggestions)
- [ ] 如何在 GAS/Cloud Run 中實現非同步回傳 LINE 訊息的代碼範本。
