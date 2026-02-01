# 專案實作紀錄規範 (Project Documentation Convention)

## 🎯 核心原則：思考與資料的分離
為了保持 `daily-log` 的純粹性與可讀性，我們採取「中繼導航」模式：
- **`daily-log/`**：存放當天的「元認知」體悟、關鍵決策與心態轉變（輕量）。
- **`projects/case-studies/`**：存放龐大的實作細節、AI 原始對話、程式碼片段與除錯過程（重量）。

## 📁 目錄結構
```text
/projects/case-studies/
  └── YYYY-MM-[專案名稱]/
      ├── index.md           # 專案概覽與最終架構圖
      ├── raw-process-logs.md # 龐大的原始紀錄 (即你提到很佔風頭的那份檔案)
      └── artifacts/         # 截圖、PDF 樣本或其他附屬資料
```

## 🔗 連結機制
在 `daily-log` 中，使用以下格式引用實作細節：
> 詳細的實作推導與 AI 對話原始紀錄已歸檔至：
> [專案實作紀錄](file:///Users/gurry/Documents/git/engineering-thinking-log/projects/case-studies/YYYY-MM-ProjectName/raw-process-logs.md)

## 💡 為什麼要這樣做？
1. **防止資訊過載**：避免 `daily-log` 變成混亂的代碼堆。
2. **優化 AI 檢索**：當需要 AI 針對特定專案進行分析時，可以直接指向 `/case-studies/` 下的專屬路徑。
3. **保留專業痕跡**：龐大的實作過程是您的「戰利品」，應該被妥善保存，但不應干擾日常的思考流。
