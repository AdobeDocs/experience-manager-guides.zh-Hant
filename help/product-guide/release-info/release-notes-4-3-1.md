---
title: 發行說明 | Adobe Experience Manager Guides 4.3.1版中的升級指示和修正問題
description: 瞭解錯誤修正以及如何升級至Adobe Experience Manager Guides 4.3.1版
exl-id: 3fb6dc31-ec6e-40f5-ab3f-a6e591da315e
feature: Release Notes
role: Leader
source-git-commit: 1b25f1df67fa2442ab79830dc2ac5a6eabd0394c
workflow-type: tm+mt
source-wordcount: '1308'
ht-degree: 1%

---

# 4.3.1版Adobe Experience Manager Guides （2023年10月）

此發行說明涵蓋升級指示、相容性矩陣，以及Adobe Experience Manager Guides 4.3.1版(後來稱為&#x200B;*Experience Manager Guides*)中修正的問題。

如需新功能和增強功能的詳細資訊，請參閱[Adobe Experience Manager Guides 4.3.1版的新增功能](./whats-new-4-3-1-release.md)。

## 升級至Experience Manager Guides的4.3.1版


您可以輕鬆地將您目前的Experience Manager Guides版本升級至4.3.1版。在繼續升級至Experience Manager Guides 4.3.1版之前，您必須先考量下列幾點：
您可以將目前的Experience Manager Guides版本升級至4.3.1版


- 如果您是使用4.3.0、4.2或4.2.1版，則可以直接升級至4.3.1版。
- 如果您使用的是4.1或4.1.x版，則必須先升級至4.3.0、4.2或4.2.x版，才能升級至4.3.1版。
- 如果您使用的是4.0版，則必須先升級至4.2版，才能升級至4.3.1版。
- 如果您使用的是3.8.5版，則必須先升級至4.0版，才能升級至4.2版。
- 如果您使用的版本早於3.8.5，請參閱產品特定安裝指南中的升級Experience Manager Guides區段。


>[!NOTE]
>
>升級Experience Manager Guides版本前，您必須先安裝AEM Service Pack。

如需詳細資訊，請參閱[升級指示](../install-guide/upgrade-xml-documentation.md)。

## 相容性矩陣

本節列出Experience Manager Guides 4.3.1版支援之軟體應用程式的相容性矩陣。

### Adobe Experience Manager

**4.3.1非UUID**
版本6.5 Service Pack 18、17、16、15或14

**4.3.1 UUID**
版本6.5 Service Pack 18、17、16、15或14

如需詳細資訊，請參閱「安裝與設定Adobe Experience Manager Guides」指南中的&#x200B;*技術需求*&#x200B;一節。

### FrameMaker和FrameMaker Publishing Server

| 發行 | FMPS 2022 | FMPS 2020 | Fm 2022 | Fm 2020 |
| --- | --- | --- | --- | --- |
| 4.3.1 （非UUID） | 2022或更高 | 2020.2或更新版本* | 2022或更高 | 2020.3或更高版本 |
| 4.3.1 (UUID) | 2022或更高 | 2020.2或更新版本* | 2022或更高 | 2020.4或更新版本 |
| | | | |

*從2020.2開始的FMPS版本支援AEM中建立的基準和條件。

### 氧氣聯結器

| 發行 | 氧氣聯結器視窗 | 氧氣聯結器Mac | 在氧氣視窗中編輯 | 在氧氣Mac中編輯 |
| --- | --- | --- |--- |--- |
| 4.3.1 （非UUID） | 2.3-regular-5 | 2.3-regular-5 | 1.6 | 1.6 |
| 4.3.1 (UUID) | 3.2-uuid-5 | 3.2-uuid-5 | 2.3 | 2.3 |
|  |  |   |



### 知識庫範本版本

| 元件封裝名稱 | 元件版本 | 範本版本 |
|---|---|---|
| 適用於Cloud Service的Experience Manager Guides元件內容套件 | dxml-components.all-1.2.2 | aem-site-template-dxml.all-1.0.15 |

## 已修正的問題

以下列出各種區域中修正的錯誤：

### 製作

- 未設定建立基準線的&#x200B;**日期**&#x200B;的下午時數。 (12712)
- 無法在網頁編輯器的`<codeblock>`元素中貼上JSON程式碼。 (12326)
- 大型檔案不會顯示未儲存的版本變更及其指標。 (11784)
- 以韓文編輯時，第一個字元會變更為預設字元。 (10049)

- 前置詞會在網頁編輯器的預覽模式中重複。 (13133)
- `Choicetable`列未顯示或無法選取。 (12616)
- 使用自訂結構描述建立主題時，Web編輯器會在特定案例中擲回驗證錯誤。 (12576)
- 從對映範本建立對映時，復本主題範本參照不會在內容資料夾中建立復本。 (12150)

- DITA map中的搜尋方塊沒有關閉按鈕。 (11867)
- 在Web編輯器中儲存長檔案時，`DirtyChecker`會擲回具有長棧疊追蹤的例外狀況，並填入記錄檔。 (11860)
- 建立DITA主題需要對應資料夾節點的刪除許可權，不過對應可以透過寫入許可權來建立。 (11706)
- 當斜線出現時，網頁編輯器會顯示不正確的標題。 (10949)

- 如果主題的標題包含斜線「/」，編輯器中的索引標籤只會顯示在該斜線後面的字母。 (13455)
- 在編輯器中顯示預覽後，影像預覽並未消失。 (13454)
- 升級至4.x後，部分現有版本或其標籤不會顯示在「版本記錄」中。(13247)
- Assets UI中的「版本記錄」面板顯示&#x200B;**目前**&#x200B;欄位的不正確時間戳記。 (12624)
- 「存放庫檢視」或「地圖檢視」中未解析具有conref標題的主題。(13304)


### 發佈

- 原生PDF | 產生PDF輸出時，主題的順序未固定。 (13157)
- 原生PDF| `<p>`元素沒有可用的預設樣式標籤。 (12559)
- 原生PDF | 套用至內容區域的內嵌樣式不會套用至前後關聯的主題。 (13510)
- 產生AEM Site輸出時未傳播`DeliveryTarget`屬性。  (13132)
- 針對發生特定錯誤的內容產生AEM網站輸出時，**Publish**&#x200B;工作流程卡住。 (12000)

- 原生PDF | 包含多個Xref會延伸文字超過欄寬。 (13004)
- 原生PDF | 當主題和標題具有相同的ID時，會導致PDF輸出的產生格式錯誤。 (12644)
- 原生PDF | 在DITA map中將outputclass新增至父`<topicref>`元素並將自訂樣式套用至outputclass時，該樣式會套用至主題內文中的元素，包括區段標題。 (12166)
- 如果DITA map有多個ditavalref，則增量發佈無法運作。 (12117)
- AEM網站 | 使用keydef將主題作為變數來建立對應，然後新增processing-role=resource-only會建立一些未預期的頁面。 (12099)
- 如果來自AEM DAM的任何資產用於AEM網站以外的任何輸出，則中繼資料「jcr：createdBy」不會反映發佈者的名稱或上次修改DITA map或主題的使用者名稱。 (12090)
- AEM Sites | DITA地圖的navtitle中帶有主題標題（包含不支援的字元）會導致頁面URL錯誤。 (11978)
- 原生PDF | 在Frontmatter和Backmatter支援topichead / topicmeta / navtitle時發生問題。 (11969)
- 原生PDF | 為大型檔案產生PDF非常耗時。 (11955)
- 原生PDF | 重新命名預設集會在產生PDF輸出時擲回NullPointerException。 (11889)
- PDF輸出中未顯示`<conref>`內容。 (11131)
- 在頁面配置編輯器的「作者」和「Source」檢視之間切換時，`<div>`元素內會新增一個額外空間。 (10750)
- 在AEM Cloud Manager上復寫的內容在Publish執行個體上不可見。 (9564)


### 管理

- 即使資產不存在`dc:format`屬性，也不會顯示版本記錄。 (10463)
- 當主題ID與GUID不同時，內容參照是損壞的複製貼上DITA檔案。 (12614)
- 在動態基準線中，標籤清單不會從DITA map工作復本的直接參照中提取。 (11917)
- 使用瀏覽所有主題功能時，基準線在「地圖儀表板」上顯示不正確的檔案數目。 (13265)
- 在Web編輯器中，基準線顯示先前版本（而非選取的DITA檔案版本）的標題。 (13444)

### 檢閱

- 有關主題的評論會顯示不正確的評論。 (13453)
- Experience Manager Guides中「檢閱」頁面上的「關閉」按鈕會將使用者帶往AEM首頁。 (13535)
- 對於稽核中主題，附件不會顯示在編輯器的右側面板上。 (13011)



### 轉換

- 從&#x200B;**Translation**&#x200B;儀表板匯出的基準線失敗，且未以目標語言開啟。 (13466)

- 會建立新的翻譯專案，而非新增工作至所選的現有翻譯專案。  (10214)
- 已翻譯檔案的標題會取代來源檔案的標題而顯示。 (11630)
- 自動核准有時無法運作，且如果「翻譯狀態」中設定的值不正確，則會發生例外狀況。 (13607)
- 從「翻譯」儀表板匯出的基線會失敗，且不會以目標語言開啟。 (12993)
- 在翻譯中使用「基準線」時，有些檔案遺失。 (13021)
