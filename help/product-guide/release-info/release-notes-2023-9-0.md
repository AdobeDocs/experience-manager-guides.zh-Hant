---
title: 發行說明 | 2023年9月發行的Adobe Experience Manager Guides中的升級指示和修正問題
description: 瞭解錯誤修正以及如何升級至2023年9月發行的Adobe Experience Manager Guides as a Cloud Service
exl-id: 795b86a0-e763-404a-a4bb-35d3d2a42672
feature: Release Notes
role: Leader
source-git-commit: 6e23f52fc9124d0f07f8108da1b5fe574f553469
workflow-type: tm+mt
source-wordcount: '1485'
ht-degree: 0%

---

# 2023年9月發行的Adobe Experience Manager Guides as a Cloud Service

此發行說明涵蓋升級指示、相容性矩陣，以及2023年9月版Adobe Experience Manager Guides (後來稱為&#x200B;*AEM Guides as a Cloud Service*)中修正的問題。

如需新功能和增強功能的詳細資訊，請參閱[AEM Guides as a Cloud Service 2023年9月版的新增功能](whats-new-2023-9-0.md)。

## 升級至2023年9月發行

請升級您目前的AEM Guides as a Cloud Service設定，方法是執行下列步驟：

1. 請檢視雲端服務的Git程式碼，並切換至雲端服務管道中設定且與您要升級的環境對應的分支。
2. 將Cloud Services Git程式碼的`<dox.version>`檔案中的`/dox/dox.installer/pom.xml`屬性更新為2023.9.0.359。
3. 提交變更並執行雲端服務管道，以升級至2023年9月版本的AEM Guides as a Cloud Service。

## 透過servlet啟用指令碼觸發的步驟

(僅限您使用2023年6月之前版本的AEM Guides as a Cloud Service)

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

(僅限您使用2023年6月之前版本的AEM Guides as a Cloud Service)

執行以下步驟後續處理現有內容並使用新的中斷連結報表：

1. （選擇性）如果系統中有超過100,000個dita檔案，請將`queryLimitReads`下的`org.apache.jackrabbit.oak.query.QueryEngineSettingsService`更新為較大的值（任何大於現有資產數的值，例如200,000），然後重新部署。

   - 使用安裝和設定Adobe Experience Manager Guides中&#x200B;*設定覆寫*區段中提供的指示
as a Cloud Service，以建立設定檔。
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

(僅限您使用2023年6月之前版本的AEM Guides as a Cloud Service)

執行以下步驟來索引現有內容，並在報表標籤底下的對應層級和主題清單中使用新的尋找和取代文字：

1. 對伺服器執行POST要求\（使用正確的驗證\） - `http://<server:port\>/bin/guides/map-find/indexing`。 (選用：您可以傳遞地圖的特定路徑來編列索引，預設情況下，所有地圖都會編列索引\|\| 例如： `https://<Server:port\>/bin/guides/map-find/indexing?paths=<map\_path\_in\_repository\>`)

1. 您也可以傳遞根資料夾，為特定資料夾（及其子資料夾）的DITA map建立索引。 例如 `http://<server:port\>/bin/guides/map-find/indexing?root=/content/dam/test`。請注意，如果同時傳遞路徑引數和根引數，則只會考慮路徑引數。

1. 此API將傳回jobId。 若要檢查工作的狀態，您可以將具有工作識別碼的GET要求傳送至相同的端點 — `http://<server:port\>/bin/guides/map-find/indexing?jobId=\{jobId\}`\（例如： `http://localhost:8080/bin/guides/map-find/indexing?jobId=2022/9/15/7/27/7dfa1271-981e-4617-b5a4-c18379f11c42`\）


1. 工作完成後，先前的GET請求會回應成功，並提及是否有任何地圖失敗。 可以從伺服器記錄檔確認已成功編制索引的對應。

## 相容性矩陣

本節列出AEM Guides as a Cloud Service 2023年9月發行版本支援之軟體應用程式的相容性矩陣。

### FrameMaker和FrameMaker Publishing Server

| AEM Guides雲端版 | FMPS | FrameMaker |
| --- | --- | --- |
| 2023.09.0 | 不相容 | 2022或更高 |
| | | |


### 氧氣聯結器

| AEM Guides雲端版 | 氧氣聯結器視窗 | 氧氣聯結器Mac | 在氧氣視窗中編輯 | 在氧氣Mac中編輯 |
| --- | --- | --- | --- | --- |
| 2023.09.0 | 3.1-uuid 17 | 3.1-uuid 17 | 2.3 | 2.3 |
|  |  |  |  |  |


### 知識庫範本版本

| 元件封裝名稱 | 元件版本 | 範本版本 |
|---|---|---|
| 適用於Cloud Service的AEM Guides元件內容套件 | dxml-components.all-1.2.2 | aem-site-template-dxml.all-1.0.15 |

## 已修正的問題

以下列出各種區域中修正的錯誤：

### 製作

- 雖然已選取「解除鎖定檔案」選項和「不儲存」選項，但不會在Web編輯器中解除鎖定主題檔案。 (12558)
- 無法簽出網頁編輯器中的檔案，儘管選擇NO選項在簽入前捨棄變更。 (12557)
- 在Web編輯器內的主工具列中，鎖定和解鎖檔案圖示的工具提示與「存放庫檢視」中顯示的圖示不一致。(12555)
- 「取消簽出」和「解除鎖定」選項會顯示在Web編輯器中尚未在「地圖檢視」中籤出的檔案。 (12556)
- 無法在現有的「topicref」連結中選取PDF資產。 (12477)。
- 在「存放庫檢視」中，使用搜尋/篩選功能後無法拖曳主題或影像。 (12396)
- 開啟一個搜尋的檔案後，「尋找和取代」面板中的搜尋結果會停用。 (12142)
- 側邊鍵盤上的「8」數字鍵在AEM Guides編輯器中無法運作。 (12106)

- 前置詞會在網頁編輯器的預覽模式中重複。 (13133)
- `Choicetable`列未顯示或無法選取。 (12616)
- 使用自訂結構描述建立主題時，Web編輯器會在特定案例中擲回驗證錯誤。 (12576)
- 從對映範本建立對映時，復本主題範本參照不會在內容資料夾中建立復本。 (12150)
- DITA map中的搜尋方塊沒有關閉按鈕。 (11867)
- 在Web編輯器中儲存長檔案時，`DirtyChecker`會擲回具有長棧疊追蹤的例外狀況，並填入記錄檔。 (11860)
- 建立DITA主題需要對應資料夾節點的刪除許可權，不過對應可以透過寫入許可權來建立。 (11706)
- 當斜線出現時，網頁編輯器會顯示不正確的標題。 (10949)


### 管理

- DITA map中繼資料屬性中的&quot;title&quot;欄位被地圖的`<title>`元素覆寫。 (10702)
- 當主題ID與GUID不同時，內容參照是損壞的複製貼上DITA檔案。 (12614)
- 在動態基準線中，標籤清單不會從DITA map工作復本的直接參照中提取。 (11917)

### 發佈

- 重新命名原生PDF預設集時發佈失敗。 (12564)
- 複製原生PDF範本會複製到預設範本位置，而不是提供的自訂範本位置。 (12563)

- 原生PDF | 包含多個Xref會延伸文字超過欄寬。 (13004)
- 原生PDF | 當主題和標題具有相同的ID時，會導致PDF輸出的產生格式錯誤。 (12644)
- 原生PDF | 在DITA map中將outputclass新增至父`<topicref>`元素並將自訂樣式套用至outputclass時，該樣式會套用至主題內文中的元素，包括區段標題。(12166)
- 如果DITA map有多個ditavalref，則增量發佈無法運作。 (12117)
- AEM網站 | 使用keydef將主題作為變數來建立對應，然後新增processing-role=resource-only會建立一些未預期的頁面。 (12099)
- 如果AEM DAM的任何資產用於AEM網站以外的任何輸出，則中繼資料「jcr:createdBy」不會反映發佈者的名稱或上次修改DITA map或主題的使用者名稱。 (12090)
- AEM Sites | DITA地圖的navtitle中帶有主題標題（包含不支援的字元）會導致頁面URL錯誤。 (11978)
- 原生PDF | 在Frontmatter和Backmatter支援topichead / topicmeta / navtitle時發生問題。 (11969)
- 原生PDF | 為大型檔案產生PDF非常耗時。 (11955)
- 原生PDF | 重新命名預設集會在產生PDF輸出時擲回NullPointerException。 (11889)
- `<conref>`內容未顯示在PDF輸出中。 (11131)
- 在頁面配置編輯器的「作者」和「Source」檢視之間切換時，`<div>`元素內會新增一個額外空間。 (10750)
- 在AEM Cloud Manager上復寫的內容在發佈執行個體上不可見。 (9564)

### 翻譯

- 匯出重新命名的翻譯基準線的程式會失敗。 (12993)
- 已翻譯檔案的標題會取代來源檔案的標題而顯示。 (11630)
