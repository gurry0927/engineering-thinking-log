# 核心專業總覽 (Master Career Profile)

> **「我不只是代碼的編寫者，更是系統邏輯的守門員。」**
> 這是 2025 年我從「非技術背景」跨入「生產級架構」後最核心的身份認同。

---

## 📄 專業定位 (Positioning)
**跨領域 AI 系統架構師 (Hybrid AI Solution Architect / Engineer)**
擅長將混亂的業務流程拆解為可維護、可驗證的穩健系統。核心競爭力在於對「系統風險」的敏銳預判與對「資料結構」的深度定義，偏好架設世界觀與建立規則，確保系統在雜訊中仍能穩定運作。

---

## 🛠️ 核心工程信念 (Core Engineering Beliefs)
> 這是從實務踩坑中提煉出的系統設計真相，也是我定義「高品質工程」的邊界：

1. **越彈性就越不彈性 (Controlled Constraint)**：
   - 真正的彈性來自於清晰的邊界與約束；無約束的系統最終只能靠人腦補位，導致不可控。
   - **區分「UI 呈現」與「系統實體」**：學會利用隱藏屬性（如 `isSheetHidden()`）在不破壞資料結構的前提下優化使用者界面，達成「功能完整但視覺精簡」的設計。
2. **資料庫只存事實，不處理邏輯與狀態 (Immutable Facts over Derived States)**：
   - 資料庫應僅記錄「發生了什麼」，而非「現在該怎麼解讀」。邏輯與狀態應解耦至應用層處理。
3. **異步與容錯設計 (Resilient Asynchrony)**：
   - 不再假設世界是同步且一次成功的。透過「分流觸發 + 佇列、重試、防重複 (Idempotency)」設計，對抗變動與失敗。
4. **可溯源性優先於標準答案 (Traceability over Accuracy)**：
   - 清洗規則會變，業務定義會翻。保護原始資料與清洗過程的聯動，使資料可回放、可解釋，才是真正的信任來源。

---

## 🛠️ 核心能力與哲學 (Core Philosophy)

### 1. 系統性容錯與資料流保護 (Systemic Fault Tolerance)
**「系統一定會出問題，設計在於讓它壞了也救得回來。」**
偏好並行冗餘、非同步處理 (Queue-like processing / Asynchronous workflows) 與冪等性 (Idempotency) 設計。確保同一任務重跑時不會產生冗餘資料，且能透過完整 Log 與狀態管理機制實現可觀測性。

### 2. 生產級 AI 落地 (Production-Ready AI Engineering)
不追求實驗室等級的精度，追求「商業現實的轉化率」。擅長將模糊的需求轉譯為具備 **失敗重試 (Retry)**、**緩衝機制** 與 **標記標註** 的系統。對於資料不乾淨、缺乏唯一鍵的環境，具備設計「不中斷匹配機制」的實戰經驗。

### 3. 技術轉譯與專業邊界 (Technical Translation & Boundaries)
**「工程師不該用心理健康換取流程錯誤。」**
理解並運用 PM 作為風險緩衝區（Shield），主動將不合理的需求或缺失的資料風險推回決策層。擅長「留證執行」與「風險選項法」，確保在混亂的組織中保住專業地基與執行力。

### 4. 資料治理與結構誠實 (Data Governance & Integrity)
**「工具只是放大器，結構亂，用什麼都會亂。」**
堅持「單一事實來源 (SSOT)」原則，拒絕透過「工人智慧」掩蓋系統性缺陷。能辨識結構中不可逆之設計點，並在關鍵時刻執行「結構停損」。

### 5. 可驗證性與審計思維 (Auditability & Traceability)
**「系統設計者不應追求直覺的正確，而應追求過程的可解釋性。」**
- **審計思維**：深知大規模資料下直覺不可靠，追求「錯能追源、過程可解釋、結果可修正」的系統設計。
- **架構主導與 AI 授權 (Architecture-led Delegation)**：能區分「設計權」與「實作細節」。堅持由人主導資料模型與業務流程。
- **外部化認知與 AI 協同演進 (Cognitive Externalization)**：視思維記錄為「可累積的工程資產」。
- **精準責任邊界與系統恢復力 (Responsibility & Resilience)**：堅持「正確的責任切分」。
- **系統思維的日常生活滲透 (Systemic Life Design)**：工程思維不僅用於代碼，更內化為觀察世界與處理生活任務的本能。
- **對等互利與專業尊嚴 (Reciprocity & Professional Integrity)**：堅持「互助必須對等且透明」。
- **人類輸入緩衝與事實保留 (Human Input Buffer Pattern)**：不以強硬規則對抗使用者習慣，而是透過「Raw (原始輸入層) + Normalized (正規化觀點層)」的雙欄位設計，在保留歷史真相的前提下，提供機器可用的純淨資料。
- **內外解耦生存協定 (Dual-Layer Survival Protocol)**：深諳「看透不一定要刺破」。
- **組織風險覺察與個人防火牆 (Organizational Risk & Buffer Strategy)**：具備高度的組織敏感度。
- **AI-First 文件化與人機對齊 (AI-First Documentation)**：擅長為 AI 編寫系統導引（如 AIGuide.md），將系統知識「外掛」給 AI，大幅縮短開發者與 AI、或新同事與系統間的認知對齊時間。
- **協同開發與專業邊界委外 (Strategic Delegation)**：能精準識別個人能力邊界。
- **策略性可見度管理 (Strategic Visibility Management / Pacing)**：具備高度的組織生存智慧，能透過「分批展示 (Pacing)」控制資訊流與工作量，在確保持續輸出亮點的同時，防止組織產生不合理的超速期待，維護開發者的長期能量。
- **基礎設施現代化與異步設計 (Infrastructure Modernization & Async)**：具備將 PoC 級應用（如 GAS）重構為生產級架構（如 Python VM + Cloudflare）的能力。擅長設計異步任務與超時機制，確保多使用者環境下的系統穩定性與公平性。
- **數位分身與人格化輸出 (Digital Twin & Identity Propagation)**：擅長利用結構化思考日誌。

### 6. 角色定義與風險隔離 (Role Definition & Risk Isolation)
**「在模糊地帶建立清晰的責任界線。」**
具備識別「決策權、建議權、執行權」三者落差的能力。當身處角色模糊的組織時，能主動設計「中立轉述」與「邊界防禦」機制，確保工程資源專注於實質成果而非政治內耗。

### 7. 人機協作與穩定性防禦 (Human-AI Collaboration & Defense)
**「AI 負責開發效率，而我負責系統穩定。」**
體認到 AI 產出的「快速結果」與「結構穩定」之間的落差。不盲目追求 AI 產出量，堅持對 AI 生成代碼進行深度 Review，並能在「先跑再說」的急躁文化中，守住最後一道技術測試與品質底線。

---

## 🏆 2025 年度關鍵戰功 (Key Milestones)

- **[P-07] 大規模非結構化文件解析**：針對 3000 頁以上 PDF，設計多階段 AI 解析工作流，將單頁作業時間從 30 分鐘降至 60 秒。
- **[P-05] 企業級資料庫架構轉向**：主導公司從「分散式 Excel」走向「正規關聯式架構 (3NF)」，建立企業單一事實來源 (SSOT)。
- **[P-04] 智能影像處理系統**：結合 OpenCV 預處理與 LLM 視覺推論，完成工程圖紙結構化數據提取。

---

## 📈 成長地圖與演進 (Evolution)
- **大腦更新紀錄**：[MINDSET-EVOLUTION.md](./2025-12-23-Mindset-Evolution.md)
- **技能演進詳情**：[PERSONAL-GROWTH-MAP.md](./2025-12-17-Personal-Growth-Map.md)
- **給面試官的戰略建議**：[interview-strategy-for-pathfinders.md](./2025-12-18-Interview-Strategy-For-Pathfinders.md)

---
> **結語**：在混亂中建立秩序，是我身為工程師的藝術表現。
