---
title: 發行說明 | 2024年2月發行的Adobe Experience Manager Guides中的升級指示和修正問題
description: 瞭解錯誤修正以及如何升級至2024年2月版的Adobe Experience Manager Guidesas a Cloud Service。
source-git-commit: 6d8c01f20f7b59fed92c404561b647d9ebecb050
workflow-type: tm+mt
source-wordcount: '1311'
ht-degree: 0%

---

# 2024年2月發行的Adobe Experience Manager Guidesas a Cloud Service

本發行說明涵蓋升級指示、相容性矩陣，以及2024年2月版Adobe Experience Manager Guidesas a Cloud Service修正的問題(以下稱為 *Experience Manager指南as a Cloud Service*)。

如需新功能和增強功能的詳細資訊，請檢視 [2024年2月版Experience Manager指南as a Cloud Service的新增功能](whats-new-2024-02-0.md).

## 升級至2024年2月發行版本

執行下列步驟，升級您目前的Experience Manager指南as a Cloud Service設定：

1. 檢視Cloud Service的Git程式碼，並切換到在Cloud Service管線中設定的分支，該分支與您要升級的環境相對應。
2. 更新 `<dox.version>` 中的屬性 `/dox/dox.installer/pom.xml` 將您的Cloud Service Git程式碼檔案改成2024.02.0.15。
3. 提交變更並執行Cloud Service管道，以升級至2024年2月版本的Experience Manager指南as a Cloud Service。

## 透過servlet啟用指令碼觸發的步驟

(僅限使用2023年6月as a Cloud Service發行Experience Manager指南之前的版本時)

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

在上一個回應JSON中，索引鍵 `lockNodePath` 儲存指向存放庫中建立的、指向已提交作業的節點的路徑。 它將在作業完成後自動刪除，然後您可以參照此節點來瞭解作業的狀態。

請等到此工作完成後，再繼續後續步驟。

>[!NOTE]
>
> 您應該檢查節點是否仍然存在，以及工作的狀態。

```
GET
http://<aem_domain>/var/dxml/executor-locks/translation-map-upgrade/1683190032886.json
```

## 後續處理現有內容以使用中斷連結報告的步驟

(僅限使用2023年6月as a Cloud Service發行Experience Manager指南之前的版本時)

執行以下步驟後續處理現有內容並使用新的中斷連結報表：

1. （選擇性）如果系統中有超過100,000個DITA檔案，請更新 `queryLimitReads` 和 `queryLimitInMemory` 在 `org.apache.jackrabbit.oak.query.QueryEngineSettingsService` 變更為較大的值（任何大於現有資產數的值，例如200,000），然後重新部署。

   - 請依照以下說明操作： *設定覆寫* 安裝與設定Adobe Experience Manager Guidesas a Cloud Service一節中的以建立設定檔。
   - 在設定檔案中，提供下列（屬性）詳細資料以設定 `queryLimitReads` 和 `queryLimitInMemory` 選項：

     | PID | 屬性索引鍵 | 屬性值 |
     |---|---|---|
     | org.apache.jackrabbit.oak.query.QueryEngineSettingsService | querylimitereads | 值：200000預設值： 100000 |
     | org.apache.jackrabbit.oak.query.QueryEngineSettingsService | queryLimitInMemory | 值：200000預設值： 100000 |

1. 對伺服器執行POST要求（使用正確的驗證） - `http://<server>//bin/guides/reports/upgrade`.

1. 此API會傳回jobId。 若要檢查作業的狀態，您可以傳送作業識別碼的GET要求至相同的端點 —  `http://<server>/bin/guides/reports/upgrade?jobId= {jobId}`
(例如： `http://localhost:8080/bin/guides/reports/upgrade?jobId=2022/9/15/7/27/7dfa1271-981e-4617-b5a4-c18379f11c42_678`)

1. 工作完成後，先前的GET請求會成功回應。 如果作業由於某個原因而失敗，則可以從伺服器記錄中看到失敗。

1. 恢復為預設值或先前的現有值 `queryLimitReads` 如果您已在步驟1中加以變更。

## 為現有內容建立索引，以使用「報表」標籤下新的尋找和取代與主題清單的步驟：

(僅限使用2023年6月as a Cloud Service發行Experience Manager指南之前的版本時)

執行以下步驟來索引現有內容，並在報表標籤底下的對應層級和主題清單中使用新的尋找和取代文字：

1. 對伺服器執行POST要求（使用正確的驗證） - `http://<server:port>/bin/guides/map-find/indexing`. (選用：您可以傳遞地圖的特定路徑來編列索引，預設情況下，所有地圖都會編列索引|| 例如： `https://<Server:port>/bin/guides/map-find/indexing?paths=<path of the MAP in repository>`)

1. 此API將傳回jobId。 若要檢查作業的狀態，您可以傳送作業識別碼的GET要求至相同的端點 —  `http://<server:port>/bin/guides/map-find/indexing?jobId={jobId}`(例如： `http://localhost:8080/bin/guides/reports/upgrade?jobId=2022/9/15/7/27/7dfa1271-981e-4617-b5a4-c18379f11c42_678`)

1. 工作完成後，先前的GET請求會成功回應。 如果作業由於某個原因而失敗，則可以從伺服器記錄中看到失敗。

1. 如果您在步驟1中變更了queryLimitReads的值，請恢復為預設值或先前的現有值。

## 處理問題的步驟 `'fmdita rewriter'` 衝突

Experience Manager指南有 [**自訂sling重寫程式**](../cs-install-guide/conf-output-generation.md#custom-rewriter) 用於處理交叉地圖情況下產生的連結的模組（兩個不同地圖主題之間的連結）。

如果您的程式碼基底中有另一個自訂Sling重寫程式，請使用 `'order'` 值大於50，因為Experience Manager指南sling重寫程式使用 `'order'` 50.  若要覆寫此值，您需要大於50的值。 如需詳細資訊，請檢視 [輸出重寫管道](https://sling.apache.org/documentation/bundles/output-rewriting-pipelines-org-apache-sling-rewriter.html).

在此升級期間，由於 `'order'` 值從1000變更為50，您需要將現有的自訂重寫程式（如果有的話）與 `'fmdita-rewriter'`.


## 相容性矩陣

本節列出2024年2月as a Cloud ServiceExperience Manager指南所支援之軟體應用程式的相容性矩陣。

### FrameMaker和FrameMaker Publishing Server

| 雲端版Experience Manager指南 | FMPS | FrameMaker |
| --- | --- | --- |
| 2024.02.0 | 不相容 | 2022或更高 |
| | | |


### 氧氣聯結器

| 雲端版Experience Manager指南 | 氧氣聯結器視窗 | 氧氣聯結器Mac | 在氧氣視窗中編輯 | 在氧氣Mac中編輯 |
| --- | --- | --- | --- | --- |
| 2024.02.0 | 3.1-uuid.17 | 3.1-uuid.17 | 2.3 | 2.3 |
|  |  |  |  |


### 知識庫範本版本

| 元件封裝名稱 | 元件版本 | 範本版本 |
|---|---|---|
| 適用於Cloud Service的Experience Manager指南元件內容套件 | dxml-components.all-1.2.2 | aem-site-template-dxml.all-1.0.15 |

## 已修正的問題

以下列出各種區域中修正的錯誤：

### 製作

- 編輯器中的拼字檢查不允許選擇建議。 (15045)
- 全域導覽按鈕無法運作，且儀表板無法載入。 (14968)
- 在網頁編輯器中，下載對應功能在準備下載時無法觸發快顯通知。 (14626)
- 在網頁編輯器中，下載對應功能無法下載包含基準的對應。 (14622)
- Experience Manager指南as a Cloud Service版本2310中的DTD錯誤無效。 (14482)
- 將字彙表主題從存放庫拖曳到字彙表對應中會建立 `topicref`. (10767)
- 重新安裝Adobe Experience Manager Guides 4.3.1版後，Web編輯器會解除安裝。 (14519)
- 安裝程式4.3.1版遇到篩選器衝突，導致覆寫 `apps/cq/core/content/projects/properties`. (14517)
- 程式碼片段的預覽畫面會凍結。 (14840)

### 發佈

- 在原生PDF發佈中，條件預設集中的自訂屬性不適用於原生PDF發佈。 (14943)
- 無法從新增自訂範本 **輸出** 索引標籤進行編輯。 (14846)
- **AEM網站** 預設集因空白範本路徑而無法運作。 (14804)
- 對於主題包含MathML方程式的DITA map，AEM網站重新產生失敗。 (14790)
- 在原生PDF發佈中，PDF產生會在取得的相依性時擲回錯誤 `Node.js` 發佈。 (14445)
- AEM預設集不允許選取外部的範本 `/content` 網頁編輯器中的階層。 (14260)
- 在AEM Sites輸出中，的樣式或分行符號遺失 `<lines>` 具有子元素的元素。(12542)
- 自訂中繼資料無法在最終輸出中使用。 (12116)
- 升級至4.3.1版時，原生PDF節點中會發生一些例外狀況。 (14492)


### 管理

- **基線篩選** 檔案無法在網頁編輯器中使用檔案名稱。 (13486)
- 停用父DITA map的索引以獲得更好的效能可能會影響某些功能的功能。(12213)
- 標籤來自 `labels.json` 檔案會以隨機順序出現在網頁編輯器中。 (10508)

### 檢閱

- 右鍵快顯功能表無法用於 **Accept** 或 **拒絕** 追蹤變更。 (14607)
- 在Adobe Experience Manager Guides 4.3.1版中，在檢閱畫面中切換以關閉DITA主題無法運作。 (14537)
- 自訂稽核工作流程的電子郵件範本不適用於覆蓋。 (13954)

## 已知問題

Adobe已確認2024年2月發行版本的下列已知問題：

- 1.0版不會顯示在重複DITA檔案的UI上。
