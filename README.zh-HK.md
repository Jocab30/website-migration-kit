# 網站遷移範本

[English](README.md) | [简体中文](README.zh-CN.md) | [日本語](README.ja.md) | [繁體中文](README.zh-HK.md)

用於網站重設的 URL 清單、項目需求、SEO 交付和上線驗收範本。範例路徑為虛構資料，使用時請換成已獲批准的項目內容。

[網站上線前 SEO 檢查清單](https://zequnweb.com/zh-hk/blog/website-seo-checklist-before-launch/)。

## 範本清單

| 檔案 | 用途 |
| --- | --- |
| [url-inventory.zh-HK.csv](url-inventory.zh-HK.csv) | 決定頁面保留、遷移、合併或下線，記錄負責人和驗證結果 |
| [redirect-map.tsv](redirect-map.tsv) | 三條直接重新導向範例，與檢查器相容 |
| [project-brief.zh-HK.csv](project-brief.zh-HK.csv) | 整理受眾、範圍、語言、資料、系統整合和驗收標準 |
| [seo-deliverables.zh-HK.csv](seo-deliverables.zh-HK.csv) | 為每項 SEO 工作訂明可檢查的交付物和負責人 |
| [launch-checklist.zh-HK.csv](launch-checklist.zh-HK.csv) | 檢查內容、重新導向、索引、表單、裝置適配和上線責任 |

本頁連結的 CSV 範本均為繁體中文。

## 交付模板與實作指南

[完整網站遷移流程](MIGRATION.zh-HK.md)

這些 UTF-8 CSV 表格涵蓋企業網站的關鍵決策。為每項指定負責人並保存證據；共享表格不要填寫密碼或客戶私人資料。

- [內容收集](content-collection.zh-HK.csv)
- [產品資料](product-data.zh-HK.csv)
- [查詢驗收](inquiry-acceptance.zh-HK.csv)
- [項目交接](handover-checklist.zh-HK.csv)
- [維護計劃](maintenance-plan.zh-HK.csv)
- [案例證據](case-evidence.zh-HK.csv)
- [量測計劃](tracking-plan.zh-HK.csv)
- [多語言內容映射](multilingual-content-map.zh-HK.csv)

## 使用步驟

1. 從儲存庫的程式碼選單下載 ZIP 壓縮檔，或複製本儲存庫至本機。
2. 用試算表開啟 CSV 檔案。保留有價值的舊 URL，選擇相關的新目標，為每項決策指定負責人。
3. 只匯出真正需要重新導向的頁面，保留舊 URL 和目標 URL 兩欄，以定位字元分隔，刪除標題列，每列一條對照。
4. 用[本機重新導向檢查器](https://github.com/awesomellm/redirect-map-checker/blob/main/README.zh-HK.md)檢查對照表。
5. 在伺服器設定規則，再測試實際 HTTP 回應、目標內容、內部連結和索引設定。
6. 在驗收表中記錄表單傳送結果、上線審批、還原責任和上線後的問題。

**多欄 CSV 清單不能直接作為檢查器輸入。** 保留或下線頁面的決策不能貼入檢查器。儲存庫中的 `redirect-map.tsv` 已是兩欄、無標題列格式。

## 功能範圍與限制

這些檔案用於項目規劃，並非伺服器設定或網站爬蟲。它們不會驗證正式環境中的重新導向，也不保證排名穩定。不要把所有下線頁面都重新導向至首頁；應選擇相關的替代頁面，沒有替代內容時使用適當的找不到頁面回應。

## 參考資料

- [Google：變更網址的網站遷移](https://developers.google.com/search/docs/crawling-indexing/site-move-with-url-changes?hl=zh-TW)
- [ZequnWeb：網站上線前 SEO 檢查清單](https://zequnweb.com/zh-hk/blog/website-seo-checklist-before-launch/)

## 參與改進

請提出具體缺少的決策、驗收項目或範例。公開提交問題時請使用虛構資料。

## 維護者與授權

由獨立 B2B 網頁設計與開發工作室 [ZequnWeb](https://zequnweb.com/zh-hk/) 整理。範本與文件採用 MIT 授權條款（`LICENSE`）。
