---
title: 發行說明 | 2023年11月發行的Adobe Experience Manager Guides中的升級指示和修正問題
description: 瞭解錯誤修正以及如何升級至2023年11月發行的Adobe Experience Manager Guides as a Cloud Service
exl-id: 80839890-075f-4187-a167-444c73215496
feature: Release Notes
role: Leader
source-git-commit: 6e23f52fc9124d0f07f8108da1b5fe574f553469
workflow-type: tm+mt
source-wordcount: '1673'
ht-degree: 1%

---

# 2023年11月發行的Adobe Experience Manager Guides as a Cloud Service

此發行說明涵蓋升級指示、相容性矩陣，以及2023年11月版Adobe Experience Manager Guides as a Cloud Service (後來稱為&#x200B;*Experience Manager Guides as a Cloud Service*)中修正的問題。

如需新功能和增強功能的詳細資訊，請檢視[Experience Manager Guides as a Cloud Service 2023年11月版本的新增功能](whats-new-2023-11-0.md)。

## 升級至2023年11月發行版本

請升級您目前的Experience Manager Guides as a Cloud Service設定，方法是執行下列步驟：

1. 請檢視雲端服務的Git程式碼，並切換至雲端服務管道中設定且與您要升級的環境對應的分支。
2. 將Cloud Services Git程式碼的`<dox.version>`檔案中的`/dox/dox.installer/pom.xml`屬性更新為2023.11.0.406。
3. 提交變更並執行雲端服務管道，以升級至2023年11月版本的Experience Manager Guides as a Cloud Service。

## 透過servlet啟用指令碼觸發的步驟

(僅限使用2023年6月發行的Experience Manager Guides as a Cloud Service之前的版本時)

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

(僅限使用2023年6月發行的Experience Manager Guides as a Cloud Service之前的版本時)

執行以下步驟後續處理現有內容並使用新的中斷連結報表：

1. （選擇性）如果系統中有超過100,000個DITA檔案，請將`queryLimitReads`下的`queryLimitInMemory`和`org.apache.jackrabbit.oak.query.QueryEngineSettingsService`更新為較大的值（任何大於現有資產數的值，例如200,000），然後重新部署。

   - 使用安裝和設定Adobe Experience Manager Guides as a Cloud Service中&#x200B;*設定覆寫*&#x200B;區段提供的指示來建立設定檔。
   - 在設定檔中，提供下列（屬性）詳細資料以設定`queryLimitReads`和`queryLimitInMemory`選項：

     | PID | 屬性索引鍵 | 屬性值 |
     |---|---|---|
     | org.apache.jackrabbit.oak.query.QueryEngineSettingsService | querylimitereads | 值：200000預設值： 100000 |
     | org.apache.jackrabbit.oak.query.QueryEngineSettingsService | queryLimitInMemory | 值：200000預設值： 100000 |

1. 對伺服器執行POST要求（使用正確的驗證） - `http://<server:port>//bin/guides/reports/upgrade`。

1. 此API會傳回jobId。 若要檢查工作的狀態，您可以將具有工作識別碼的GET要求傳送至相同的端點 — `http://<server:port>/bin/guides/reports/upgrade?jobId= {jobId}`
（例如： `http://localhost:8080/bin/guides/map-find/indexing?jobId=2022/9/15/7/27/7dfa1271-981e-4617-b5a4-c18379f11c42_678`）

1. 工作完成後，先前的GET請求會成功回應。 如果作業由於某個原因而失敗，則可以從伺服器記錄中看到失敗。

1. 如果您在步驟1中變更了`queryLimitReads`的值，請還原為預設值或先前的現有值。

## 為現有內容建立索引，以使用「報表」標籤下新的尋找和取代與主題清單的步驟：

(僅限使用2023年6月發行的Experience Manager Guides as a Cloud Service之前的版本時)

執行以下步驟來索引現有內容，並在報表標籤底下的對應層級和主題清單中使用新的尋找和取代文字：

1. 對伺服器執行POST要求（使用正確的驗證） - `http://<server:port>/bin/guides/map-find/indexing`。 (選用：您可以傳遞地圖的特定路徑來編列索引，預設情況下，所有地圖都會編列索引 || 例如： `https://<Server:port>/bin/guides/map-find/indexing?paths=<map_path_in_repository>`)

1. 您也可以傳遞根資料夾，為特定資料夾（及其子資料夾）的DITA map建立索引。 例如 `http://<server:port>/bin/guides/map-find/indexing?root=/content/dam/test`。請注意，如果同時傳遞路徑引數和根引數，則只會考慮路徑引數。

1. 此API會傳回jobId。 若要檢查工作的狀態，您可以將具有工作識別碼的GET要求傳送至相同的端點 — `http://<server:port>/bin/guides/map-find/indexing?jobId={jobId}`（例如： `http://localhost:8080/bin/guides/map-find/indexing?jobId=2022/9/15/7/27/7dfa1271-981e-4617-b5a4-c18379f11c42`）


1. 工作完成後，先前的GET請求會回應成功，並提及是否有任何地圖失敗。 可以從伺服器記錄檔確認已成功編制索引的對應。

## 處理`'fmdita rewriter'`衝突的步驟

Experience Manager Guides有&#x200B;[**自訂sling重寫程式**](../cs-install-guide/conf-output-generation.md#custom-rewriter)&#x200B;模組，可處理交叉對映時產生的連結（兩個不同對映之主題之間的連結）。

如果您的程式碼基底中有另一個自訂Sling重寫程式，請使用大於50的`'order'`值，因為Experience Manager Guides Sling重寫程式使用`'order'` 50。  若要覆寫此值，您需要大於50的值。 如需詳細資訊，請檢視[輸出重寫管道](https://sling.apache.org/documentation/bundles/output-rewriting-pipelines-org-apache-sling-rewriter.html)。

在此升級期間，由於`'order'`值從1000變更為50，因此您必須將現有的自訂重寫程式（若有的話）與`'fmdita-rewriter'`合併。


## 相容性矩陣

本節列出Experience Manager Guides as a Cloud Service 2023年11月版本支援之軟體應用程式的相容性矩陣。

### FrameMaker和FrameMaker Publishing Server

| Experience Manager Guides Guides雲端版 | FMPS | FrameMaker |
| --- | --- | --- |
| 2023.11.0 | 不相容 | 2022或更高 |
| | | |


### 氧氣聯結器

| Experience Manager Guides雲端版 | 氧氣聯結器視窗 | 氧氣聯結器Mac | 在氧氣視窗中編輯 | 在氧氣Mac中編輯 |
| --- | --- | --- | --- | --- |
| 2023.11.0 | 3.2-uuid 5 | 3.2-uuid 5 | 2.3 | 2.3 |
|  |  |  |  |  |


### 知識庫範本版本

| 元件封裝名稱 | 元件版本 | 範本版本 |
|---|---|---|
| 適用於Cloud Service的Experience Manager Guides元件內容套件 | dxml-components.all-1.2.2 | aem-site-template-dxml.all-1.0.15 |

## 已修正的問題

以下列出各種區域中修正的錯誤：



### 製作

- 儲存主題時，conref `<ph>`元素後的空格會消失。 (13642)
- 嘗試在後處理完成之前儲存DITA檔案時發生應用程式錯誤。 (13571)
- 如果主題的標題包含斜線`/`，編輯器中的索引標籤只會顯示後面跟著的字母。 (13455)
- 在編輯器中顯示預覽後，影像預覽並未消失。 (13454)
- 在其他主題中使用根對映定義的索引鍵時，插入關鍵字快顯視窗沒有出現。 (12950)
- 在「版本記錄」面板中預覽高度很高的圖形時，無法看到關閉圖示。 (12867)
- 無法為基準線修改&#x200B;**版本建立於**&#x200B;欄的時區。 (12711)
- Assets UI中的&#x200B;**版本記錄**&#x200B;面板顯示&#x200B;**目前**&#x200B;欄位的不正確時間戳記。 (12624)
- 從檔案名稱以數字字元開頭的範本建立DITA檔案會導致名稱空間錯誤。 (12188)
- 在網頁編輯器中，插入&#x200B;**標籤時會開啟**&#x200B;索引鍵參考`varname`視窗。 (10940)
- 網頁編輯器中無法辨識Zip檔案，而且您無法拖放它們。 (12709)
- 套用了一些屬性的內容在「作者」或「預覽」模式中不會反白顯示。 (11063)
- 在編輯主題後關閉主題時，系統會將您重新導向至AEM首頁，而非返回資料夾檢視。 (13306)
- 在處理已複製並貼入雲端服務的檔案時，會發生延遲。 (12457)
- 即使使用者未從「使用者偏好設定」明確設定，Rootmap設定仍會保留在網頁編輯器中。 (11551)


### 發佈

- 發佈為內容片段功能無法用於搜尋結果中列出的檔案。 (14090)
- 在原生PDF發佈中，範本配置上的背景顏色選擇需要在恢復為`None`時重新載入頁面。 (13621)
- 在AEM網站發佈中，在具有範圍對等連結的大型DITA map認可資料存放區時發生問題。 (13530)
- 在原生PDF發佈中，由於頁首和頁尾中的影像不顯示替代文字，導致協助工具受損。 (12829)
- 如果沒有自動新增的擴充功能，在原生PDF中複製頁面配置將無法運作。 (12534)
- 使用原生PDF發佈產生PDF輸出時，檔案名稱會在句點後截斷。 (13620)
- 在原生PDF發佈中使用的範本的「版面配置」工具列中，**編輯內容**&#x200B;選項的圖示和工具提示顯示不正確。 (13492)
- 自訂中繼資料無法在最終輸出中使用。 (12116)
- fmdita重寫程式與使用者的重寫程式設定衝突，並導致顯示長URL而非連結。 (12076)
- 在AEM網站預設集中，**為每個主題**&#x200B;產生個別PDF的選項無法運作。 (11555)
- 原生PDF發佈不支援CMYK色域轉換。 (10754)
- 動態基準線呼叫使用名稱而非標題，導致匯出DITA map API失敗。 (14268)

### 管理

- 複製貼上具有不含GUID的自參照連結的DITA檔案時，內容參照會中斷。 (13540)
- 在Web編輯器中，基準線顯示先前版本（而非選取的DITA檔案版本）的標題。 (13444)
- 網頁編輯器UI中的&#x200B;**報表**&#x200B;索引標籤無法顯示2023年7月升級Experience Manager Guides as a Cloud Service之前建立的舊DITA Map的主題清單。 (11852)
- 未建立大型DITA map的條件預設集。 (10936)
- 報表中的中斷連結清單下會顯示自我參照連結。 (13539)

### 檢閱

- 先前和目前版本的並排檢閱面板在2023年10月發行的Experience Manager Guides as a Cloud Service中不正確。 (14156)
- **檢閱**&#x200B;工作流程的電子郵件範本自訂不適用於重疊節點。 (13954)
- Experience Manager Guides中「檢閱」頁面上的「**關閉**」按鈕會將使用者帶往AEM首頁。 (13535)
- 以韓文建立片段時會出現損壞的字元。 (13489)
- Experience Manager Guides檢閱畫面中的韓文附件無法點選。 (13436)
- 在檢閱和共同作業畫面中，地圖示題遭到切斷，沒有檢視完整標題的選項。 (13012)

### 翻譯

- 自動核准有時無法運作，如果&#x200B;**翻譯狀態**&#x200B;上設定的值不正確，則會發生例外狀況。 (13607)
- 從「翻譯」儀表板匯出的基線會失敗，且不會以目標語言開啟。 (12993)

## 已知問題

Adobe已在2023年11月版本中找出下列已知問題。

- AEM網站輸出的選擇性主題重新產生失敗。
