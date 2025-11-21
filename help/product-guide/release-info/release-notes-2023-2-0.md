---
title: 發行說明 | Adobe Experience Manager Guides as a Cloud Service，2023年2月發行
description: 2月發行的Adobe Experience Manager Guides as a Cloud Service
exl-id: c639b136-11ed-4a8b-a595-4bb5da879747
feature: Release Notes
role: Leader
source-git-commit: 6e23f52fc9124d0f07f8108da1b5fe574f553469
workflow-type: tm+mt
source-wordcount: '869'
ht-degree: 0%

---

# 2023年2月發行的Adobe Experience Manager Guides as a Cloud Service

此發行說明涵蓋升級指示、相容性矩陣，以及2023年2月版Adobe Experience Manager Guides (後來稱為&#x200B;*AEM Guides as a Cloud Service*)中修正的問題。

如需新功能和增強功能的詳細資訊，請參閱[AEM Guides as a Cloud Service 2023年2月版本的新增功能](whats-new-2023-2-0.md)。

## 升級至2023年2月發行版本

請升級您目前的AEM Guides as a Cloud Service設定，方法是執行下列步驟：
1. 請檢視雲端服務的Git程式碼，並切換至雲端服務管道中設定且與您要升級的環境對應的分支。
2. 將Cloud Services Git程式碼的`<dox.version>`檔案中的`/dox/dox.installer/pom.xml`屬性更新為2023.2.235。
3. 提交變更並執行雲端服務管道，以升級至2023年2月版本的AEM Guides as a Cloud Service。

## 索引現有內容的步驟(僅限使用9月之前的AEM Guides as a Cloud Service版本時)

執行以下步驟來索引現有內容，並在地圖層級使用新的尋找和取代文字：

* 對伺服器執行POST要求（使用正確的驗證） - `http://<server:port>/bin/guides/map-find/indexing`。
(選用：您可以傳遞地圖的特定路徑來編列索引，預設情況下，所有地圖都會編列索引 || 範例： `https://<Server:port>/bin/guides/map-find/indexing?paths=<map_path_in_repository>`)

* 此API將傳回jobId。 若要檢查工作的狀態，您可以將具有工作識別碼的GET要求傳送至相同的端點 — `http://<server:port>/bin/guides/map-find/indexing?jobId={jobId}`
(例如： http://&lt;_localhost:8080_>/bin/guides/map-find/indexing？jobId=2022/9/15/7/27/7dfa1271-981e-4617-b5a4-c18379f11c42_678)

* 工作完成後，上述GET要求將回應為成功，並提及是否有任何地圖失敗。 可以從伺服器記錄檔確認已成功編制索引的對應。

## 相容性矩陣

本節列出AEM Guides as a Cloud Service 2023年2月版本支援之軟體應用程式的相容性矩陣。

### FrameMaker和FrameMaker Publishing Server

| AEM Guides雲端版 | FMPS | FrameMaker |
| --- | --- | --- |
| 2023.02.0 | 不相容 | 2022或更高 |
| | | |

*從2020.2開始的FMPS版本支援AEM中建立的基準和條件。

### 氧氣聯結器

| AEM Guides雲端版 | 氧氣聯結器視窗 | 氧氣聯結器Mac | 在氧氣視窗中編輯 | 在氧氣Mac中編輯 |
| --- | --- | --- | --- | --- |
| 2023.02.0 | 2.8-uuid-8 | 2.8-uuid-8 | 2.3 | 2.3 |
|  |  |  |  |  |

## 已修正的問題

以下列出各種區域中修正的錯誤：

### 製作

* 網頁編輯器HTML中的變更導致`<dl>`和`<dlentry>`發生問題。 (11024)
* 有些屬性不會被視為有條件屬性，而會造成問題。 (10895)
* 三個層級或更多巢狀`<indexterm>`未巢狀內嵌於原生PDF匯出中。 (10799)
* 從「作者」檢視切換至「Source」檢視時，內容會在任務內文中消失。 (10735)
* 評論在評論任務中被錯誤放置。 (10625)
* **復原**&#x200B;或&#x200B;**取消復原**&#x200B;在某些檔案上無法正常運作。 (10373)
* 複製和貼上動作不會保留自訂中繼資料。 (10367)
* XML編輯器中的還原選項會將使用者帶至頁面頂端。 (10091)
* 執行資產的複製和貼上操作後，會移除節點屬性。 (10053)
* mimetype是針對DITA資產建立和更新的硬式編碼。 (8979)
* 對於透過Assets UI上傳的檔案，版本記錄中的版本建立者名稱是&quot;fmdita-serviceuser&quot;。 (8910)
* 雲端上安裝AEM Guides時，無法複製和貼上內容片段。 (11315)
* 使用自訂結構描述載入內容時，瀏覽器（網頁編輯器）會凍結。 (11211)

### 管理

* 複製DITA map資產（從資產UI ）會導致複製的資產中出現錯誤的基準線。 (11218)
* 如果檔案大小超過AEM所允許的上限（預設為2 GB），上傳檔案時不會顯示警告訊息。 (10817)
* 網頁編輯器 — 基準線 | 在網頁編輯器內的新基準線儀表板中，「最新」欄的行為是不同的。 (10808)
* 翻譯 | 由於/libs/fmdita/i18n/ja.json無效，翻譯工作未開始。 (10543)
* 翻譯 | 從翻譯儀表板（人工翻譯）建立的範圍設定翻譯專案中發生錯誤。 (10526)
* 翻譯 | 若整個語言資料夾的資產位於使用中的翻譯專案中，該資料夾的後置處理會遭到封鎖。 (10332)
* 如果版本在基線編輯器中變更並儲存，則任何資產都會出現多個快顯視窗。 (10399)
* 工作階段洩漏發生於`com.day.cq.search.impl.builder.QueryBuilderImpl.createResourceResolver(QueryBuilderImpl.java:210)`。 (10279)

### 發佈

* 主題重新產生不適用於某些案例。 (10635)
* Publishlistener不會在資訊記錄中顯示要求的資料，而且其中也包含一些垃圾記錄檔。( 10567)
* 原生PDF | 使用「新增至資料夾設定檔」選項建立輸出預設集時，PDF產生會因「Null指標」例外而失敗。 (10950)
* 原生PDF | 旋轉表格標題時發生問題。 (10555)
* 原生PDF | 巢狀`<indexterm>`未巢狀內嵌於原生PDF匯出中。 (10521)
* 原生PDF | 附錄中的巢狀topicref會在暫時HTML中全部轉換為h1。 (10454)
* 使用FrameMaker Publishing Server 2020產生的PDF基準線發佈失敗。 (10551)
* 原生PDF | 將`xref`新增至影像不會轉譯產生的PDF上的影像。 (11346)
* 原生PDF | 影像標籤會將display-inline屬性新增至所有影像。 (10653)
* 原生PDF | 預設會在產生的輸出中隱藏草稿註解。 (10560)
* 原生PDF | navtitle不適用於topichead。 (10509)
