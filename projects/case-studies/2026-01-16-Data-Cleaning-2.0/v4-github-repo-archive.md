# GitHub 專案存檔：Data Cleaning with Traceability (2026-01-21)

> 專案網址：[gurry0927/data-cleaning-with-traceability](https://github.com/gurry0927/data-cleaning-with-traceability)
> 核心精神：**Design-first data cleaning patterns that prioritize traceability, reversibility, and data safety over one-time correctness.**

---

## 💡 為什麼這個專案存在？ (Why This Project Exists)
在現實世界的系統中，資料清洗很少有單一的「正確答案」。公司名稱、使用者輸入、地址等欄位本質上是：**模糊、依賴上下文、且由不同利害關係人在不同時間定義的。**

當資料量增長，人工驗證變得不可能，傳統的清洗方式（字串替換、原位覆寫）會帶來極高風險。本專案提出了一種「設計優先」的資料清洗方法，將**可追蹤性 (Traceability)**、**可逆性 (Reversibility)** 與 **安全性 (Safety)** 視為一等公民。

## 🏗️ 設計原則 (Design Principles)

### 1. 原始資料不可變 (Raw Data Is Immutable)
原始輸入資料絕對不能被覆寫。系統必須始終能夠重建原始輸入。如果原始資料丟失，未來的修正將變得不可能。

### 2. 清洗是「對應」而非「替換」 (Cleaning Is Mapping, Not Replacement)
資料清洗不是字串操作，而是一個「關係分配」問題。
- **傳統模式**：`Raw Value → Clean Value (overwrite)`
- **本專案模式**：`Raw Value → Mapping → Normalized Entity`
對應關係 (Mappings) 被視為資料本身，而非副作用。

### 3. 推遲不可逆的決策 (Postpone Irreversible Decisions)
當無法有信心地做出決策時，不要強行執行。不可逆的操作（如合併實體）必須是：**顯式的、可審計的、且可逆的。**

## 🧠 心理模型 (Mental Model)
不再問：**「這個值正確嗎？」**
而是問：**「我能否解釋這個值是如何產生的——並且我能否安全地更改它？」**
如果答案是肯定的，系統就是在運作中。

---

## 🏆 結語 (Final Note)
**Clean data is temporary. Traceable data survives change.**
（乾淨的資料是暫時的，可追蹤的資料才能在變革中倖存。）
