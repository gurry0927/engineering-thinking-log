# 可溯源與審計就緒檢查清單 (Traceability & Auditability Checklist)

> [!NOTE]
> 這是為了應對大規模資料清洗中的「不確定性焦慮」而設計的驗證體系。
> 核心目標：**使系統具備「可解釋性」，確保每一筆資料的去處都有跡可循。**

## ✅ 1. 基礎結構自檢 (Structural Integrity)
- [ ] **Raw Company 表（不可變）**：
    - `raw_company_id` 是唯一的嗎？
    - 原始字串是否完整保留且永不被覆寫？
- [ ] **Normalized Company 表（可重算）**：
    - 此表是否為純粹的「生成結果」？
    - 是否具備 Drop 掉後隨時重算的冪等性？
- [ ] **Mapping 獨立表**：
    - `raw_id` 與 `normalized_id` 的對應是否獨立儲存？
    - 是否避免了直接在原始資料上進行破壞性修改？

## ✅ 2. 分類與標註 (Contextual Traceability)
為了回答「為什麼它會在那裡」，必須補齊以下欄位：
- [ ] **mapping_method (處理方法)**：標註這筆對應是由 `rule_exact`、`regex_normalized` 還是 `ai_suggested` 產生的。
- [ ] **confidence_level (信心指標)**：分為 `high` (敢直接用)、`medium` (需抽查)、`low` (明確失敗)。
- [ ] **mapped_at (時間戳記)**：記錄是哪一個批次、哪一個時間點產生的結果。

## ✅ 3. 風險監控 (Anomalies & Diff)
- [ ] **差異監控 (Diff)**：
    - 是否有欄位記錄清洗前後的「字串長度變化」或「清洗觸發次數」？
- [ ] **自動舉手機制 (Anomaly Flag)**：
    - 清洗後字串過短、或關鍵字全部消失的案例是否會自動標記為 `Low Confidence`？

---

## 🏆 核心精神：Definition of Done (DoD)
一個負責任的資料工程交付成果，不需要保證 100% 乾淨，但必須保證：
1. **資料不遺失**：聯絡人永遠掛在 Raw ID 上。
2. **錯能追源**：每一筆對應都有方法標註。
3. **可被修正**：Mapping 表可以隨時透過更新 rule 進行修正與 Rollback。

---
> [!TIP]
> 焦慮來自於「不知情」，而信心來自於「可被審計的過程」。
