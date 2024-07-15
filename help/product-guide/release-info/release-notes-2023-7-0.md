---
title: 發行說明 | 2023年7月發行的Adobe Experience Manager Guides中的升級指示和修正問題
description: 瞭解錯誤修正以及如何升級至2023年7月發行的Adobe Experience Manager Guidesas a Cloud Service
exl-id: f1765c6a-cb8e-4a06-a6f4-f5c225b6bc88
feature: Release Notes
role: Leader
source-git-commit: 6d8c01f20f7b59fed92c404561b647d9ebecb050
workflow-type: tm+mt
source-wordcount: '926'
ht-degree: 1%

---

# 2023年7月發行的Adobe Experience Manager Guidesas a Cloud Service

此發行說明涵蓋升級指示、相容性矩陣，以及2023年7月Adobe Experience Manager Guides版本修正的問題(後來稱為&#x200B;*AEM Guidesas a Cloud Service*)。

如需新功能和增強功能的詳細資訊，請參閱[AEM Guidesas a Cloud Service2023年7月版本的新增功能](whats-new-2023-7-0.md)。

## 升級至2023年7月發行

請升級您目前的AEM Guidesas a Cloud Service設定，方法是執行下列步驟：

1. 檢視Cloud Service的Git程式碼，並切換到在Cloud Service管線中設定的分支，該分支與您要升級的環境相對應。
2. 將Cloud Service Git程式碼的`/dox/dox.installer/pom.xml`檔案中的`<dox.version>`屬性更新為2023.7.0.314。
3. 提交變更並執行Cloud Service管道，以升級至2023年7月版本的AEM Guidesas a Cloud Service。

## 透過servlet啟用指令碼觸發的步驟

(僅限使用2023年6月之前版本的AEM Guidesas a Cloud Service)

完成安裝後，您可以選擇點選觸發程式以開始翻譯工作：

POST：

```
http://localhost:4503/bin/guides/script/start?jobType=translation-map-upgrade
```

回應：

```
{
"msg": "Job is successfully submitted and lock node is created for future reference",
"lockNodePath": "/var/dxml/executor-locks/translation-map-upgrade/1683190032886",
"status": "SCHEDULED"
}
```

在先前的回應JSON中，索引鍵`lockNodePath`會保留指向存放庫中建立且指向已提交工作的節點的路徑。 它會在作業完成後自動刪除，在此之前，您可以參照此節點來瞭解作業的目前狀態。

請等到此工作完成後，再繼續後續步驟。

>[!NOTE]
>
> 您應該檢查節點是否仍然存在，以及工作的狀態。

```
GET
http://<aem_domain>/var/dxml/executor-locks/translation-map-upgrade/1683190032886.json
```

## 後續處理現有內容以使用中斷連結報告的步驟

(僅限使用2023年6月之前版本的AEM Guidesas a Cloud Service)

執行以下步驟後續處理現有內容並使用新的中斷連結報表：

1. （選擇性）如果系統中有超過100,000個dita檔案，請將`org.apache.jackrabbit.oak.query.QueryEngineSettingsService`下的`queryLimitReads`更新為較大的值（任何大於現有資產數的值，例如200,000），然後重新部署。

   - 使用安裝和設定Adobe Experience Manager Guides中&#x200B;*設定覆寫*區段中提供的指示
as a Cloud Service，以建立組態檔。
   - 在組態檔中，提供下列（屬性）詳細資訊，以設定queryLimitReads選項：

     | PID | 屬性索引鍵 | 屬性值 |
     |---|---|---|
     | org.apache.jackrabbit.oak.query.QueryEngineSettingsService | querylimitereads | 值：200000預設值： 100000 |

1. 對伺服器執行POST要求（使用正確的驗證） - `http://<server:port>//bin/guides/reports/upgrade`。

1. 此API將傳回jobId。 若要檢查工作的狀態，您可以將具有工作識別碼的GET要求傳送至相同的端點 — `http://<server:port>/bin/guides/reports/upgrade?jobId= {jobId}`
（例如： `http://localhost:8080/bin/guides/map-find/indexing?jobId=2022/9/15/7/27/7dfa1271-981e-4617-b5a4-c18379f11c42_678`）

1. 工作完成後，先前的GET請求將會成功回應。 如果作業由於某個原因而失敗，則可以從伺服器記錄中看到失敗。

1. 如果您在步驟1中變更了`queryLimitReads`的值，請恢復為預設值或先前的現有值。

## 為現有內容建立索引，以使用「報表」標籤下新的尋找和取代與主題清單的步驟：

(僅限使用2023年6月之前版本的AEM Guidesas a Cloud Service)

執行以下步驟來索引現有內容，並在報表標籤底下的對應層級和主題清單中使用新的尋找和取代文字：

1. 對伺服器執行POST要求\（使用正確的驗證\） - `http://<server:port\>/bin/guides/map-find/indexing`。 (選用：您可以傳遞地圖的特定路徑來編列索引，預設情況下，所有地圖都會編列索引\|\| 例如： `https://<Server:port\>/bin/guides/map-find/indexing?paths=<map\_path\_in\_repository\>`)

1. 您也可以傳遞根資料夾，為特定資料夾（及其子資料夾）的DITA map建立索引。 例如 `http://<server:port\>/bin/guides/map-find/indexing?root=/content/dam/test`。請注意，如果同時傳遞路徑引數和根引數，則只會考慮路徑引數。

1. 此API將傳回jobId。 若要檢查工作的狀態，您可以將具有工作識別碼的GET要求傳送至相同的端點 — `http://<server:port\>/bin/guides/map-find/indexing?jobId=\{jobId\}`\（例如： `http://localhost:8080/bin/guides/map-find/indexing?jobId=2022/9/15/7/27/7dfa1271-981e-4617-b5a4-c18379f11c42`\）


1. 工作完成後，先前的GET要求將回應為成功，並提及是否有任何地圖失敗。 可以從伺服器記錄檔確認已成功編制索引的對應。

## 相容性矩陣

本節列出AEM Guides 2023年7月as a Cloud Service版本支援之軟體應用程式的相容性矩陣。

### FrameMaker和FrameMaker Publishing Server

| AEM Guides雲端版 | FMPS | FrameMaker |
| --- | --- | --- |
| 2023.07.0 | 不相容 | 2022或更高 |
| | | |


### 氧氣聯結器

| AEM Guides雲端版 | 氧氣聯結器視窗 | 氧氣聯結器Mac | 在氧氣視窗中編輯 | 在氧氣Mac中編輯 |
| --- | --- | --- | --- | --- |
| 2023.07.0 | 2.9-uuid-2 | 2.9-uuid-2 | 2.3 | 2.3 |
|  |  |  |  |


## 已修正的問題

以下列出各種區域中修正的錯誤：

### 製作

- 內嵌/顯示屬性不會顯示在網頁編輯器的「版面」檢視中。 (12498)
- 如果您，在適用於AEM Guides的氧氣外掛程式中上傳檔案在雲端服務中無法運作！ 檔案名稱中的。 (12207)
- 使用可編輯的範本時，DITA map發佈速度非常慢。 (12075)
- 全域設定檔UI設定與資料夾設定檔不相符。 (11970)
- 複製和貼上DITA檔案時，內容參照會損毀。 (11959)
- 安裝AEM Guides後無法編輯欄檢視中的內容片段。 (7342)
- 當未包裝的xref位於子元素標籤下時，內容會遺失。 (12532)

### 發佈

- 從右側面板的「檔案」屬性將dostate變更為「結束狀態」時，核准工作流程無法運作。 (11026)
