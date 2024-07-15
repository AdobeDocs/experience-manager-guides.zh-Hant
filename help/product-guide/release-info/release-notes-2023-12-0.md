---
title: 發行說明 | 2023年12月發行的Adobe Experience Manager Guides中的升級指示和修正問題
description: 瞭解錯誤修正以及如何升級至2023年12月版的Adobe Experience Manager Guidesas a Cloud Service。
feature: Release Notes
role: Leader
exl-id: 63efe42a-b817-49df-8f76-df8d7acf9194
source-git-commit: e40ebf4122decc431d0abb2cdf1794ea704e5496
workflow-type: tm+mt
source-wordcount: '1319'
ht-degree: 1%

---

# 2023年12月發行的Adobe Experience Manager Guidesas a Cloud Service

此發行說明涵蓋升級指示、相容性矩陣，以及2023年12月版Adobe Experience Manager Guidesas a Cloud Service(後來稱為&#x200B;*Experience Manager Guidesas a Cloud Service*)中修正的問題。

如需新功能和增強功能的詳細資訊，請檢視[2023年12月發行的Experience Manager Guides新增功能as a Cloud Service](whats-new-2023-12-0.md)。

## 升級至2023年12月發行版本

請升級您目前的Experience Manager Guidesas a Cloud Service設定，方法是執行下列步驟：

1. 檢視Cloud Service的Git程式碼，並切換到在Cloud Service管線中設定的分支，該分支與您要升級的環境相對應。
2. 將Cloud Service Git程式碼的`/dox/dox.installer/pom.xml`檔案中的`<dox.version>`屬性更新為2023.12.0.16。
3. 提交變更並執行Cloud Service管道，以升級至2023年12月版本的Experience Manager Guidesas a Cloud Service。

## 透過servlet啟用指令碼觸發的步驟

(僅限使用2023年6月發行之Experience Manager Guidesas a Cloud Service之前的版本時)

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

## 後續處理現有內容以使用中斷連結報告的步驟

(僅限使用2023年6月發行之Experience Manager Guidesas a Cloud Service之前的版本時)

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

1. 如果您在步驟1中變更了`queryLimitReads`的值，請還原為預設值或先前的現有值。

## 為現有內容建立索引，以使用「報表」標籤下新的尋找和取代與主題清單的步驟：

(僅限使用2023年6月發行之Experience Manager Guidesas a Cloud Service之前的版本時)

執行以下步驟來索引現有內容，並在報表標籤底下的對應層級和主題清單中使用新的尋找和取代文字：

1. 對伺服器執行POST要求（使用正確的驗證） - `http://<server:port>/bin/guides/map-find/indexing`。 (選用：您可以傳遞地圖的特定路徑來編列索引，預設情況下，所有地圖都會編列索引|| 例如： `https://<Server:port>/bin/guides/map-find/indexing?paths=<map_path_in_repository>`)

1. 您也可以傳遞根資料夾，為特定資料夾（及其子資料夾）的DITA map建立索引。 例如 `http://<server:port>/bin/guides/map-find/indexing?root=/content/dam/test`。請注意，如果同時傳遞路徑引數和根引數，則只會考慮路徑引數。

1. 此API會傳回jobId。 若要檢查工作的狀態，您可以將具有工作識別碼的GET要求傳送至相同的端點 — `http://<server:port>/bin/guides/map-find/indexing?jobId={jobId}`（例如： `http://localhost:8080/bin/guides/map-find/indexing?jobId=2022/9/15/7/27/7dfa1271-981e-4617-b5a4-c18379f11c42_678`）


1. 工作完成後，先前的GET請求會以成功回應，並提及是否有任何地圖失敗。 可以從伺服器記錄檔確認已成功編制索引的對應。

## 處理`'fmdita rewriter'`衝突的步驟

Experience Manager Guides有&#x200B;[**自訂sling重寫程式**](../cs-install-guide/conf-output-generation.md#custom-rewriter)&#x200B;模組，可處理交叉對映時產生的連結（兩個不同對映之主題之間的連結）。

如果您的程式碼基底中有另一個自訂Sling重寫程式，請使用大於50的`'order'`值，因為Experience Manager Guides Sling重寫程式使用`'order'` 50。  若要覆寫此值，您需要大於50的值。 如需詳細資訊，請檢視[輸出重寫管道](https://sling.apache.org/documentation/bundles/output-rewriting-pipelines-org-apache-sling-rewriter.html)。

在此升級期間，由於`'order'`值從1000變更為50，因此您必須將現有的自訂重寫程式（若有的話）與`'fmdita-rewriter'`合併。


## 相容性矩陣

本節列出Experience Manager Guides 2023年12月as a Cloud Service版本支援之軟體應用程式的相容性矩陣。

### FrameMaker和FrameMaker Publishing Server

| Experience Manager Guides雲端版 | FMPS | FrameMaker |
| --- | --- | --- |
| 2023.12.0 | 不相容 | 2022或更高 |
| | | |


### 氧氣聯結器

| Experience Manager Guides雲端版 | 氧氣聯結器視窗 | 氧氣聯結器Mac | 在氧氣視窗中編輯 | 在氧氣Mac中編輯 |
| --- | --- | --- | --- | --- |
| 2023.12.0 | 3.3-uuid.5 | 3.3-uuid.5 | 2.3 | 2.3 |
|  |  |  |  |


### 知識庫範本版本

| 元件封裝名稱 | 元件版本 | 範本版本 |
|---|---|---|
| 適用於Cloud Service的Experience Manager Guides元件內容套件 | dxml-components.all-1.2.2 | aem-site-template-dxml.all-1.0.15 |

## 已修正的問題

以下列出各種區域中修正的錯誤：



### 製作

- 網站編輯器索引標籤中的&#x200B;**標題**&#x200B;會在點(.)之後被截斷 設定的 Cookie。(14372)
- Assets UI中重複對應名稱的錯誤訊息未更新。 (14320)
- 拖放資產期間，版本建立邏輯中發生錯誤。 (14291)
- 可重複使用的內容會略過元素ID。 (14213)
- 在&#x200B;**輸出**&#x200B;索引標籤下隱藏&#x200B;**語言變數**&#x200B;面板的設定控制項遺失。 (14194)
- 在「版面」檢視中使用專門的結構描述來新增參照或主題時，Web編輯器會擲回應用程式錯誤。 (14094)
- 指向`<dlentry>`或`<dt>`元素的錨點連結無法顯示連結文字。 (13543)
- 網頁編輯器中的&#x200B;**我的最愛**&#x200B;集合無法載入。 (13495)
- 以含空格的唯一ID建立時，引文會顯示不可點按的連結。 (13447)
- 在Bookmap的&#x200B;**配置**&#x200B;檢視中，使用&#x200B;**向右移動**&#x200B;讓選取的章節成為子元素無法運作。 (12567)
- 在Google Chrome和Microsoft Edge瀏覽器中，XML編輯器的預覽視窗會遭截斷。 (10755)
- 網頁編輯器無法包裝可能上層元素內的元素。 (8791)

### 發佈

- Fmdita元件的硬式編碼路徑為`delegator.jsp`，無法覆蓋AEM Sites元件。 (13993)
- 原生PDF發佈輸出中PDF反應器的標籤檢視未按預期運作。 (13622)
- AEM網站發佈在具有範圍對等連結的大型地圖提交到資料存放區時遇到問題。 (13531)
- 無法使用Experience Manager Guides大量發佈儀表板啟用網站。 (13439)
- 元素標籤本地化在AEM Sites輸出中無法正常運作。 (12144)
- 透過網頁編輯器UI建立的資料夾設定檔層級輸出預設集中遺失&#x200B;**ditaval**&#x200B;選項。 (11903)

### 管理

- AEM雲端環境因大型節點而發生MongoWrite例外狀況。 (13509)

### 轉換

- **接受/拒絕**&#x200B;按鈕錯誤地出現在自動核准的人工翻譯中。 (14318)
- 將非英文DITA檔案轉換成AEM頁面時，會發生國際化(i18n)問題。 (14286)
- 已翻譯的內容無法從暫存翻譯專案同步，且DITA XML編輯器翻譯精靈對已核准的工作不正確地顯示&#x200B;**進行中**&#x200B;狀態。 (9938)

### 親和力

- 無法導覽作者畫布使用者介面，因為焦點被困在主題編輯器中。 (13517)

## 已知問題

Adobe已發現2023年12月版本的下列已知問題：
- 升級至2023年12月版本時，會斷斷續續發生「取得無效的DTD錯誤」。
