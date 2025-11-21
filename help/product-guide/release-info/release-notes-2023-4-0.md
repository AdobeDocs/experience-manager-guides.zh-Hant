---
title: 發行說明 | Adobe Experience Manager Guides as a Cloud Service，2023年4月發行版本
description: 2023年4月發行的Adobe Experience Manager Guides as a Cloud Service
exl-id: fa339eab-d3d0-4763-adbf-6411e39aa213
feature: Release Notes
role: Leader
source-git-commit: 6e23f52fc9124d0f07f8108da1b5fe574f553469
workflow-type: tm+mt
source-wordcount: '597'
ht-degree: 0%

---

# 2023年4月發行的Adobe Experience Manager Guides as a Cloud Service

此發行說明涵蓋升級指示、相容性矩陣，以及2023年4月Adobe Experience Manager Guides版本(後來稱為&#x200B;*AEM Guides as a Cloud Service*)中修正的問題。

如需新功能和增強功能的詳細資訊，請參閱[AEM Guides as a Cloud Service 2023年4月版本的新增功能](whats-new-2023-4-0.md)。

## 升級至2023年4月發行版本

請升級您目前的AEM Guides as a Cloud Service設定，方法是執行下列步驟：

1. 請檢視雲端服務的Git程式碼，並切換至雲端服務管道中設定且與您要升級的環境對應的分支。
2. 將Cloud Services Git程式碼的`<dox.version>`檔案中的`/dox/dox.installer/pom.xml`屬性更新為2023.4.249。
3. 提交變更並執行雲端服務管道，以升級至2023年4月版本的AEM Guides as a Cloud Service。

## 索引現有內容的步驟(僅限使用9月之前的AEM Guides as a Cloud Service版本時)

執行以下步驟，為現有內容編制索引，並在地圖層級使用新的尋找和取代文字：

* 對伺服器執行POST要求（使用正確的驗證） - `http://<server:port>/bin/guides/map-find/indexing`。
(選用：您可以傳遞地圖的特定路徑來編列索引，預設情況下，所有地圖都會編列索引 || 範例： `https://<Server:port>/bin/guides/map-find/indexing?paths=<map_path_in_repository>`)

* 此API將傳回jobId。 若要檢查工作的狀態，您可以將具有工作識別碼的GET要求傳送至相同的端點 — `http://<server:port>/bin/guides/map-find/indexing?jobId={jobId}`
(例如： http://&lt;_localhost:8080_>/bin/guides/map-find/indexing？jobId=2022/9/15/7/27/7dfa1271-981e-4617-b5a4-c18379f11c42_678)

* 工作完成後，上述GET要求將回應為成功，並提及是否有任何地圖失敗。 可以從伺服器記錄檔確認已成功編制索引的對應。

## 相容性矩陣

本節列出AEM Guides as a Cloud Service 2023年4月發行版本支援之軟體應用程式的相容性矩陣。

### FrameMaker和FrameMaker Publishing Server

| AEM Guides雲端版 | FMPS | FrameMaker |
| --- | --- | --- |
| 2023.04.0 | 不相容 | 2022或更高 |
| | | |


### 氧氣聯結器

| AEM Guides雲端版 | 氧氣聯結器視窗 | 氧氣聯結器Mac | 在氧氣視窗中編輯 | 在氧氣Mac中編輯 |
| --- | --- | --- | --- | --- |
| 2023.04.0 | 2.9-uuid-2 | 2.9-uuid-2 | 2.3 | 2.3 |
|  |  |  |  |  |



## 已修正的問題

以下列出各種區域中修正的錯誤：

* 原生PDF | 如果發佈的內容具有包含brackets()的輸出類別，會導致發佈凍結。 (11596)
* 在移動（拖放）至具有追蹤變更的現有清單專案時，發生問題。 (11570)
* 當作為新清單專案移動（拖放）並開啟追蹤變更時發生問題。 (11569)
* 「追蹤變更」開啟時，縮排或減少縮排清單專案無法如預期運作。 (11568)
* 在開啟「追蹤變更」的行上新增內容，然後關閉「追蹤變更」並不會實際將其關閉。 (11567)
* 難以拖放清單專案，文字會移動來取代清單專案。 (11566)
* 已完成檢閱不會在唯讀模式下開啟。 (11387)
* AEM網站搜尋中發生問題（在2-3層節點之外無法運作）。 (11352)
* 以綠色（追蹤變更）顯示的元素中進行製作時，即使追蹤變更已停用，新內容仍會顯示為追蹤變更。 (7021)

### 因應措施的已知問題

Adobe已識別AEM Guides as a Cloud Service 2023年4月版本的下列已知問題。

* 原生PDF | 輸出預設集明確開啟前，不會填入舊中繼資料。
