# GAS：模板替換與檔案格式轉換郵件指南

## 核心概念
Google Docs 與 Sheets 屬於「雲端專有格式」，不具備傳統檔案系統中的實體二進制檔案。若要將其作為郵件「附件」發送，必須在程式中顯式執行「轉檔 (Export)」動作。

## 詳細筆記

### 1. 模板代換流程 (The Template Workflow)
1. **複寫範本**：`DriveApp.getFileById(templateId).makeCopy()`。
2. **替換佔位符**：使用 `DocumentApp.openById(newFileId).getBody().replaceText("{{placeholder}}", value)`。
3. **存檔與關閉**：`doc.saveAndClose()`（此步極為重要，否則後續轉檔會抓到舊內容）。

### 2. 檔案格式轉換 (Conversion)
要作為附件，必須抓取檔案的 `Blob` 並指定 MIME Type：

| 來源格式 | 目標格式 | MIME Type |
| :--- | :--- | :--- |
| **Google Docs** | PDF | `application/pdf` |
| **Google Sheets** | XLSX | `application/vnd.openxmlformats-officedocument.spreadsheetml.sheet` |
| **Google Sheets** | PDF | `application/pdf` |

### 3. 郵件發送代碼片段
```javascript
// 範例：將 Sheet 轉為 XLSX 並寄出
const blob = DriveApp.getFileById(sheetId).getAs("application/vnd.openxmlformats-officedocument.spreadsheetml.sheet");
blob.setName("Report.xlsx"); // 設定附件名稱

MailApp.sendEmail({
  to: "recipient@example.com",
  subject: "自動化報表",
  body: "附件為系統自動生成的 Excel 檔。",
  attachments: [blob]
});
```

## 學習心得
理解「雲端檔案」與「在地檔案」的區別，是從辦公室行政轉向自動化開發的重要門檻。掌握了格式轉換，就能打破 Google 生態系與外部郵件通訊的壁壘。

---

## 外部建議與提議 (AI Suggestions)
- [ ] 自動判斷類型並導出的通用 `sendAsAttachment(fileId, email)` 函數。
