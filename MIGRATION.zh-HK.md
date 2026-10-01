# 網站遷移完整實作示例

[English](MIGRATION.md) | [简体中文](MIGRATION.zh-CN.md) | [日本語](MIGRATION.ja.md) | [繁體中文](MIGRATION.zh-HK.md)

本例將 `/old-contact.html` 遷移至 `/contact/`，將 `/company-profile.html` 整合至 `/about/`，並移除 `/expired-campaign/`。路徑全屬虛構資料。部署後仍須檢查實際回應及目標內容，才算完成驗收。

## 1. 先決定頁面去向，再寫規則

填寫 [URL 清單](url-inventory.zh-HK.csv)，記錄舊 URL、處理方式、最終目標、理由、負責人及實測結果。有價值而毋須搬移的頁面可保留原 URL；已搬移頁面應指向相關的新內容；沒有合適替代內容的停用頁面應回傳適當的 404 或 410，而非一律轉往首頁。

仍有用途的推廣參數可以保留，已棄用參數則按明確規則處理。路徑、大小寫、查詢參數及結尾斜線須分別核對，映射檢查器會將它們視為不同 URL。

## 2. 只匯出真正需要轉址的映射

```text
/old-contact.html	/contact/
/company-profile.html	/about/
```

兩欄之間是定位字元。不要包含表頭、其他清單欄位、原樣保留的頁面或 404/410 決策。[redirect-map.tsv](redirect-map.tsv) 是可直接檢查的示例。

複製[本機檢查器](https://github.com/awesomellm/redirect-map-checker/blob/main/README.zh-HK.md)，在檢查器目錄指定匯出檔案路徑：

```sh
node check.mjs ../website-migration-kit/redirect-map.tsv https://example.com
```

修正循環、目標衝突及中間轉址，人工確認外部目標。映射關係正確，不代表伺服器已使用這些規則。

## 3. 在實際託管層設定

按[設定教學](https://github.com/awesomellm/redirect-map-checker/blob/main/DEPLOYMENT.zh-HK.md) 選擇 Cloudflare、Nginx 或 Apache。規則中的精確路徑和最終目標應與已確認清單一致，個別規則放在廣泛規則之前。先在預覽環境驗證，保留舊設定，指定回復負責人。

內部連結、標準 URL、導覽、語言切換及網站地圖直接指向最終頁面。轉址用來承接舊連結，站內新內容亦應同步使用新地址。

## 4. 部署後檢查實際 GET 回應

```sh
curl -sS -D - -o /dev/null 'https://example.com/old-contact.html?utm_source=test'
curl -sS -L --max-redirs 5 -D - -o /dev/null 'https://example.com/old-contact.html?utm_source=test'
```

第一條指令顯示初始狀態與 `Location`，第二條顯示轉址鏈。將示例網域換成你管理的網站，核對永久轉址狀態、參數處理、最終 200 回應及內容相關性。停用路徑另行測試。亦須用手機操作目標頁面，向自己管理的接收端提交事先約定的測試查詢。

## 5. 保存驗收及後續觀察

填寫[上線驗收表](launch-checklist.zh-HK.csv)、[查詢驗收表](inquiry-acceptance.zh-HK.csv)及[追蹤計劃](tracking-plan.zh-HK.csv)，記錄測試 URL、時間、結果、證據及負責人。上線後立即檢查重要舊地址、導覽及接收系統；之後按日及週觀察實際 404、網站地圖處理及相關頁面的搜尋索引。比較完整報告期間，短期波動不能直接證明成功或失敗。

## 6. 交接至可操作的程度

交付[帳戶與項目交接表](handover-checklist.zh-HK.csv)、已確認清單、實際規則、測試結果及回復步驟。企業應知道誰管理網域、託管、內容及查詢接收。本文提供規劃與驗證流程，不會部署規則，也不保證搜尋排名。

[Google 網站遷移說明](https://developers.google.com/search/docs/crawling-indexing/site-move-with-url-changes?hl=zh-TW) · [ZequnWeb 繁體中文網站](https://zequnweb.com/zh-hk/)
