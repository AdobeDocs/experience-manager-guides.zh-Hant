---
title: 升級雲端服務的其他設定
description: 瞭解升級雲端服務的額外設定
source-git-commit: 1ded80114aa25761fcca3f540d8b14ad7f5c4a31
workflow-type: tm+mt
source-wordcount: '849'
ht-degree: 0%

---

# 升級AEM Guides as Cloud Service的其他設定

>[!INFO]
>
>若您已設定自訂資料夾設定檔設定(`ui_config.json`)，則本文適用。 在每次升級後，請視需要檢閱並修改您的設定，以確保與最新變更相容。

根據您升級的版本，整合較新Cloud Service版本中引入的變更可能需要額外的設定步驟。

有些設定僅適用於特定版本。 請確定您參閱下方的設定區段，並套用適用於您的設定的必要設定。

## 在所有輸出預設集的DITAVAL檔案上套用搜尋篩選器的步驟

若要確保篩選器正常運作，請更新ui_config.json。 變更&#x200B;**browseFilters** > **非DITA檔案** > **Ditaval檔案**&#x200B;下列出的屬性，如下所示：

```
{
  "title": "Ditaval Files",
  "property": "LOWER_NAME",
  "operation": "like",
  "value": ".ditaval"
}
```

## 為內容片段執行B-Tree移轉的步驟

如果未顯示內容片段的參考，您可以選擇執行移轉工作：

張貼：

```
http://localhost:4503/bin/guides/script/start?jobType=cf-reference-store-btree-migration
```


回應：

```
{
"msg": "Job is successfully submitted and lock node is created for future reference",
"lockNodePath": "/var/dxml/executor-locks/cf-reference-store-btree-migration/1683190032886",
"status": "SCHEDULED"
}
```

在上一個回應JSON中，索引鍵`lockNodePath`保留存放庫中建立之節點的路徑，指向已提交的工作。 工作完成後，系統會自動將其刪除。 您可以參照此節點來瞭解作業的狀態。

請等到此工作完成後，再繼續後續步驟。

>[!NOTE]
>
>您應該檢查節點是否仍然存在，以及工作的狀態。

GET：

```
http://<aem_domain>/var/dxml/executor-locks/cf-reference-store-btree-migration/1683190032886.json
```

## 處理`'fmdita rewriter'`衝突的步驟

Experience Manager Guides有&#x200B;[**自訂sling重寫程式**](../cs-install-guide/conf-output-generation.md#custom-rewriter)&#x200B;模組，可處理交叉對映時產生的連結（兩個不同對映之主題之間的連結）。

如果您的程式碼基底中有另一個自訂Sling重寫程式，請使用大於50的`'order'`值，因為Experience Manager Guides Sling重寫程式使用`'order'` 50。 若要覆寫此值，您需要大於50的值。 如需詳細資訊，請檢視[輸出重寫管道](https://sling.apache.org/documentation/bundles/output-rewriting-pipelines-org-apache-sling-rewriter.html)。

在此升級期間，由於`'order'`值從1000變更為50，因此您必須將現有的自訂重寫程式（若有的話）與`fmdita-rewriter`合併。

## 適用於2023年6月之前版本的設定

只有在您使用2023年6月之前發行的Experience Manager Guides as a Cloud Service版本時，才需要下列設定。 展開下列相關章節以套用必要的設定，並確保與必要的更新相容。

+++為現有內容建立索引的步驟，以使用「報表」標籤下新的尋找和取代及主題清單
執行以下步驟來索引現有內容，並在報表標籤底下的對應層級和主題清單中使用新的尋找和取代文字：

1. 對伺服器執行POST要求（使用正確的驗證） - `http://<server:port>/bin/guides/map-find/indexing`。 （選用：您可以傳遞地圖的特定路徑來為其編制索引，依預設所有地圖都會編制索引||範例： `https://<Server:port>/bin/guides/map-find/indexing?paths=<path of the MAP in repository>`）

1. 您也可以傳遞根資料夾，為特定資料夾（及其子資料夾）的DITA map建立索引。 例如 `http://<server:port\>/bin/guides/map-find/indexing?root=/content/dam/test`。請注意，如果同時傳遞路徑引數和根引數，則只會考慮路徑引數。

1. 此API會傳回jobId。 若要檢查工作的狀態，您可以將具有工作識別碼的GET要求傳送至相同的端點 — `http://<server:port>/bin/guides/map-find/indexing?jobId={jobId}`（例如： `http://localhost:8080/bin/guides/reports/upgrade?jobId=2022/9/15/7/27/7dfa1271-981e-4617-b5a4-c18379f11c42_678`）

1. 工作完成後，先前的GET請求會回應成功，並提及是否有任何地圖失敗。 可以從伺服器記錄檔確認成功編制索引的對應。

+++

+++後續處理現有內容以使用中斷連結報告的步驟 
執行以下步驟後續處理現有內容並使用新的中斷連結報表：

1. （選擇性）如果系統中有超過100,000個DITA檔案，請將`queryLimitReads`下的`queryLimitInMemory`和`org.apache.jackrabbit.oak.query.QueryEngineSettingsService`更新為較大的值（任何大於現有資產數的值，例如200,000），然後重新部署。

   - 使用安裝和設定Adobe Experience Manager Guides as a Cloud Service中&#x200B;*設定覆寫*&#x200B;區段提供的指示來建立設定檔。
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

+++

+++透過servlet啟用指令碼觸發的步驟
完成安裝後，您可以選擇開始翻譯工作：

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

在先前的回應JSON中，索引鍵`lockNodePath`會保留指向存放庫中建立且指向已提交工作的節點的路徑。 它會在作業完成後自動刪除，然後您可以參照此節點來瞭解作業的狀態。

請等到此工作完成後，再繼續後續步驟。

>[!NOTE]
>
> 您應該檢查節點是否仍然存在，以及工作的狀態。

```
GET
http://<aem_domain>/var/dxml/executor-locks/translation-map-upgrade/1683190032886.json
```

+++












