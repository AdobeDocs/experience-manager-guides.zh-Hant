---
title: 發行說明 | 2023年10月發行的Adobe Experience Manager Guides中的升級指示和修正問題
description: 瞭解錯誤修正以及如何升級至2023年10月發行的Adobe Experience Manager Guides as a Cloud Service
exl-id: 536d2ec2-31a0-4533-9c29-16a27525acca
feature: Release Notes
role: Leader
source-git-commit: 6e23f52fc9124d0f07f8108da1b5fe574f553469
workflow-type: tm+mt
source-wordcount: '1045'
ht-degree: 1%

---

# 2023年10月發行的Adobe Experience Manager Guides as a Cloud Service

此發行說明涵蓋升級指示、相容性矩陣，以及2023年10月版Adobe Experience Manager Guides (後來稱為&#x200B;*AEM Guides as a Cloud Service*)中修正的問題。

如需新功能和增強功能的詳細資訊，請參閱[AEM Guides as a Cloud Service 2023年10月版本的新增功能](whats-new-2023-10-0.md)。

## 升級至2023年10月發行版本

請升級您目前的AEM Guides as a Cloud Service設定，方法是執行下列步驟：

1. 請檢視雲端服務的Git程式碼，並切換至雲端服務管道中設定且與您要升級的環境對應的分支。
2. 將雲端服務Git程式碼的`<dox.version>`檔案中的`/dox/dox.installer/pom.xml`屬性更新為2023.10.0.373。
3. 提交變更並執行雲端服務管道，以升級至2023年10月版的AEM Guides as a Cloud Service。

## 透過servlet啟用指令碼觸發的步驟

(僅限使用2023年6月發行的AEM Guides as a Cloud Service之前的版本時)

完成安裝後，您可以選擇點選觸發程式以開始翻譯工作：

張貼：

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

(僅限使用2023年6月發行的AEM Guides as a Cloud Service之前的版本時)

執行以下步驟後續處理現有內容並使用新的中斷連結報表：

1. （選擇性）如果系統中有超過100,000個DITA檔案，請將`queryLimitReads`下的`org.apache.jackrabbit.oak.query.QueryEngineSettingsService`更新為較大的值（任何大於現有資產數的值，例如200,000），然後重新部署。

   - 使用安裝和設定Adobe Experience Manager Guides as a Cloud Service中&#x200B;*設定覆寫*&#x200B;區段提供的指示來建立設定檔。
   - 在組態檔中，提供下列（屬性）詳細資訊，以設定queryLimitReads選項：

     | PID | 屬性索引鍵 | 屬性值 |
     |---|---|---|
     | org.apache.jackrabbit.oak.query.QueryEngineSettingsService | querylimitereads | 值：200000預設值： 100000 |

1. 對伺服器執行POST要求（使用正確的驗證） - `http://<server:port>//bin/guides/reports/upgrade`。

1. 此API會傳回jobId。 若要檢查工作的狀態，您可以將具有工作識別碼的GET要求傳送至相同的端點 — `http://<server:port>/bin/guides/reports/upgrade?jobId= {jobId}`
（例如： `http://localhost:8080/bin/guides/map-find/indexing?jobId=2022/9/15/7/27/7dfa1271-981e-4617-b5a4-c18379f11c42_678`）

1. 工作完成後，先前的GET請求會成功回應。 如果作業由於某個原因而失敗，則可以從伺服器記錄中看到失敗。

1. 如果您在步驟1中變更了`queryLimitReads`的值，請還原為預設值或先前的現有值。

## 為現有內容建立索引，以使用「報表」標籤下新的尋找和取代與主題清單的步驟：

(僅限使用2023年6月發行的AEM Guides as a Cloud Service之前的版本時)

執行以下步驟來索引現有內容，並在報表標籤底下的對應層級和主題清單中使用新的尋找和取代文字：

1. 對伺服器執行POST要求\（使用正確的驗證\） - `http://<server:port\>/bin/guides/map-find/indexing`。 (選用：您可以傳遞地圖的特定路徑來編列索引，預設情況下，所有地圖都會編列索引\|\| 例如： `https://<Server:port\>/bin/guides/map-find/indexing?paths=<map\_path\_in\_repository\>`)

1. 您也可以傳遞根資料夾，為特定資料夾（及其子資料夾）的DITA map建立索引。 例如 `http://<server:port\>/bin/guides/map-find/indexing?root=/content/dam/test`。請注意，如果同時傳遞路徑引數和根引數，則只會考慮路徑引數。

1. 此API會傳回jobId。 若要檢查工作的狀態，您可以將具有工作識別碼的GET要求傳送至相同的端點 — `http://<server:port\>/bin/guides/map-find/indexing?jobId=\{jobId\}`\（例如： `http://localhost:8080/bin/guides/map-find/indexing?jobId=2022/9/15/7/27/7dfa1271-981e-4617-b5a4-c18379f11c42`\）


1. 工作完成後，先前的GET請求會回應成功，並提及是否有任何地圖失敗。 可以從伺服器記錄檔確認已成功編制索引的對應。

## 相容性矩陣

本節列出AEM Guides as a Cloud Service 2023年10月發行版本支援之軟體應用程式的相容性矩陣。

### FrameMaker和FrameMaker Publishing Server

| AEM Guides雲端版 | FMPS | FrameMaker |
| --- | --- | --- |
| 2023.10.0 | 不相容 | 2022或更高 |
| | | |


### 氧氣聯結器

| AEM Guides雲端版 | 氧氣聯結器視窗 | 氧氣聯結器Mac | 在氧氣視窗中編輯 | 在氧氣Mac中編輯 |
| --- | --- | --- | --- | --- |
| 2023.10.0 | 3.2-uuid 5 | 3.2-uuid 5 | 2.3 | 2.3 |
|  |  |  |  |  |


### 知識庫範本版本

| 元件封裝名稱 | 元件版本 | 範本版本 |
|---|---|---|
| 適用於Cloud Service的AEM Guides元件內容套件 | dxml-components.all-1.2.2 | aem-site-template-dxml.all-1.0.15 |

## 已修正的問題

以下列出各種區域中修正的錯誤：

### 製作

- 未設定建立基準線的&#x200B;**日期**&#x200B;的下午時數。 (12712)
- 無法在網頁編輯器的`<codeblock>`元素中貼上JSON程式碼。 (12326)
- 大型檔案不會顯示未儲存的版本變更及其指標。 (11784)
- 以韓文編輯時，第一個字元會變更為預設字元。 (10049)


### 發佈

- 原生PDF | 產生PDF輸出時，主題的順序無法固定。 (13157)
- 原生PDF| `<p>`元素沒有可用的預設樣式標籤。 (12559)
- 原生PDF | 套用至內容區域的內嵌樣式不會套用至前後關聯的主題。 (13510)
- 產生AEM網站輸出時未傳播`DeliveryTarget`屬性。  (13132)
- 針對發生特定錯誤的內容產生AEM網站輸出時，**發佈**&#x200B;工作流程卡住。 (12000)

### 管理

- 即使資產不存在`dc:format`屬性，也不會顯示版本記錄。 (10463)


### 檢閱

- 有關主題的評論會顯示不正確的評論。 (13453)



### 翻譯

- 從&#x200B;**Translation**&#x200B;儀表板匯出的基準線失敗，且未以目標語言開啟。 (13466)

- 會建立新的翻譯專案，而非新增工作至所選的現有翻譯專案。  (10214)

## 已知問題

Adobe已在2023年10月版本中找出下列已知問題。

- 內容片段重新發佈失敗。
