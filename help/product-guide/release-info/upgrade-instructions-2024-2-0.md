---
title: 發行說明 | 2024.2.0版Adobe Experience Manager Guides中的升級指示和修正問題
description: 瞭解相容性矩陣，以及如何升級至2024.2.0版的Adobe Experience Manager Guidesas a Cloud Service。
exl-id: 7aaa4317-eb96-4fff-8a45-b38b9dfc234a
source-git-commit: e40ebf4122decc431d0abb2cdf1794ea704e5496
workflow-type: tm+mt
source-wordcount: '866'
ht-degree: 2%

---

# 2024.2.0版的升級指示

本文介紹2024.2.0版Adobe Experience Manager Guides as a Cloud Service的升級指示和相容性矩陣。

如需新功能和增強功能的詳細資訊，請參閱 [2024.2.0 版本中的新增功能](whats-new-2024-2-0.md)。

如需此版本中已修正的問題清單，請檢視[2024.2.0版本](fixed-issues-2024-2-0.md)中已修正的問題。


## 相容性矩陣

本節列出2024.2.0版Experience Manager Guides as a Cloud Service支援之軟體應用程式的相容性矩陣。

### FrameMaker和FrameMaker Publishing Server

| Experience Manager Guides雲端版 | FMPS | FrameMaker |
| --- | --- | --- |
| 2024.2.0 | 不相容 | 2022或更高 |
| | | |


### 氧氣聯結器

| Experience Manager Guides雲端版 | 氧氣聯結器視窗 | 氧氣聯結器Mac | 在氧氣視窗中編輯 | 在氧氣Mac中編輯 |
| --- | --- | --- | --- | --- |
| 2024.2.0 | 3.5-uuid 1 | 3.5-uuid 1 | 2.3 | 2.3 |
|  |  |  |  |


### 知識庫範本版本

| 元件封裝名稱 | 元件版本 | 範本版本 |
|---|---|---|
| 適用於Cloud Service的Experience Manager Guides元件內容套件 | dxml-components.all-1.2.2 | aem-site-template-dxml.all-1.0.15 |

## 升級至2024.2.0版

Experience Manager Guides會在升級最新（最新）版本的Experience Manageras a Cloud Service時自動升級。


如果您尚未針對現有版本執行先前步驟，請針對Experience Manager Guidesas a Cloud Service執行下列步驟：

### 透過servlet啟用指令碼觸發的步驟

(僅限在2023年6月之前版本的Experience Manager Guidesas a Cloud Service上使用)

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

在先前的回應JSON中，索引鍵`lockNodePath`會保留指向存放庫中建立且指向已提交工作的節點的路徑。 它將在作業完成後自動刪除，然後您可以參照此節點來瞭解作業的狀態。

請等到此工作完成後，再繼續後續步驟。

>[!NOTE]
>
> 您應該檢查節點是否仍然存在，以及工作的狀態。

```
GET
http://<aem_domain>/var/dxml/executor-locks/translation-map-upgrade/1683190032886.json
```

### 後續處理現有內容以使用中斷連結報告的步驟

(僅限在2023年6月之前版本的Experience Manager Guidesas a Cloud Service上使用)

執行以下步驟後續處理現有內容並使用新的中斷連結報表：

1. （選擇性）如果系統中有超過100,000個DITA檔案，請將`org.apache.jackrabbit.oak.query.QueryEngineSettingsService`下的`queryLimitReads`和`queryLimitInMemory`更新為較大的值（任何大於現有資產數的值，例如200,000），然後重新部署。

   - 使用安裝和設定Adobe Experience Manager Guidesas a Cloud Service中&#x200B;*設定覆寫*&#x200B;區段中提供的指示來建立設定檔。
   - 在設定檔中，提供下列（屬性）詳細資料以設定`queryLimitReads`和`queryLimitInMemory`選項：

     | PID | 屬性索引鍵 | 屬性值 |
     |---|---|---|
     | org.apache.jackrabbit.oak.query.QueryEngineSettingsService | querylimitereads | 值：200000預設值： 100000 |
     | org.apache.jackrabbit.oak.query.QueryEngineSettingsService | queryLimitInMemory | 值：200000預設值： 100000 |

1. 對伺服器執行POST要求（使用正確的驗證） - `http://<server>//bin/guides/reports/upgrade`。

1. 此API會傳回jobId。 若要檢查工作的狀態，您可以將具有工作識別碼的GET要求傳送至相同的端點 — `http://<server>/bin/guides/reports/upgrade?jobId= {jobId}`
（例如： `http://localhost:8080/bin/guides/reports/upgrade?jobId=2022/9/15/7/27/7dfa1271-981e-4617-b5a4-c18379f11c42_678`）

1. 工作完成後，先前的GET請求會成功回應。 如果作業由於某個原因而失敗，則可以從伺服器記錄中看到失敗。

1. 如果您在步驟1中變更了`queryLimitReads`的值，請恢復為預設值或先前的現有值。

### 為現有內容建立索引，以使用「報表」標籤下新的尋找和取代與主題清單的步驟：

(僅限在2023年6月之前版本的Experience Manager Guidesas a Cloud Service上使用)

執行以下步驟來索引現有內容，並在報表標籤底下的對應層級和主題清單中使用新的尋找和取代文字：

1. 對伺服器執行POST要求（使用正確的驗證） - `http://<server:port>/bin/guides/map-find/indexing`。 (選用：您可以傳遞地圖的特定路徑來編列索引，預設情況下，所有地圖都會編列索引|| 例如： `https://<Server:port>/bin/guides/map-find/indexing?paths=<path of the MAP in repository>`)

1. 此API將傳回jobId。 若要檢查工作的狀態，您可以將具有工作識別碼的GET要求傳送至相同的端點 — `http://<server:port>/bin/guides/map-find/indexing?jobId={jobId}`（例如： `http://localhost:8080/bin/guides/reports/upgrade?jobId=2022/9/15/7/27/7dfa1271-981e-4617-b5a4-c18379f11c42_678`）

1. 工作完成後，先前的GET請求會成功回應。 如果作業由於某個原因而失敗，則可以從伺服器記錄中看到失敗。

1. 如果您在步驟1中變更了queryLimitReads的值，請恢復為預設值或先前的現有值。

### 處理`'fmdita rewriter'`衝突的步驟

Experience Manager Guides有&#x200B;[**自訂sling重寫程式**](../cs-install-guide/conf-output-generation.md#custom-rewriter)&#x200B;模組，可處理交叉對映時產生的連結（兩個不同對映之主題之間的連結）。

如果您的程式碼基底中有另一個自訂Sling重寫程式，請使用大於50的`'order'`值，因為Experience Manager Guides Sling重寫程式使用`'order'` 50。  若要覆寫此值，您需要大於50的值。 如需詳細資訊，請檢視[輸出重寫管道](https://sling.apache.org/documentation/bundles/output-rewriting-pipelines-org-apache-sling-rewriter.html)。

在此升級期間，由於`'order'`值從1000變更為50，因此您必須將現有的自訂重寫程式（若有的話）與`'fmdita-rewriter'`合併。
