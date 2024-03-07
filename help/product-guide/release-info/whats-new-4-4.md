---
title: 發行說明 | Adobe Experience Manager Guides 4.4.0版的新增功能
description: 瞭解Adobe Experience Manager Guides 4.4.0版的新增和增強功能
role: Leader
source-git-commit: 8f8075b205725a55b93286c804b879353b4d965d
workflow-type: tm+mt
source-wordcount: '2307'
ht-degree: 0%

---

# 4.4.0版的新增功能（2024年1月）

本文介紹4.4.0版Adobe Experience Manager Guides中的新功能和增強功能。

如需此版本已修正的問題清單，請檢視 [已修正4.4.0版本中的問題](../release-info/fixed-issues-4-4.md).

瞭解 [4.4.0版的升級指示](../release-info/upgrade-instructions-4-4.md).



## 網頁編輯器中的翻新版本記錄功能

現在，Experience Manager指南提供增強的版本記錄功能，可讓您比較檔案在一段時間內所做的變更。 在新的並排檢視中，您可以輕鬆將目前版本的內容和中繼資料與相同檔案的任何先前版本進行比較。 您也可以檢視比較版本的標籤和註解。 作為管理員，您可以控制主題中要顯示的版本中繼資料及其值 **版本記錄** 對話方塊。

![版本記錄對話方塊](assets/version-history-dialog-web-editor.png){width="800" align="left"}
*預覽不同版本主題中的變更。*


進一步瞭解 **版本記錄** 中的功能說明 [左側面板](../user-guide/web-editor-features.md#id2051EA0M0HS) 區段。

## 管理條件預設集

您可以在DITA主題中定義條件屬性。 然後，使用條件預設集中的條件屬性，在DITA map中發佈內容。 「Experience Manager指南」現在也提供在網頁編輯器中更豐富的體驗，可幫助您更有效率地建立和管理條件預設集。 您也可以輕鬆進行編輯、複製或刪除。

![來自網頁編輯器「管理」標籤的條件預設集 ](assets/web-editor-manage-condition-presets.png){width="550" align="left"}

如需詳細資訊，請檢視 [使用條件預設集](../user-guide/generate-output-use-condition-presets.md).

## 編輯屬性的改版體驗

現在，您獲得改版體驗，可透過新增或編輯元素的屬性。 **內容屬性** 網頁編輯器中的面板。

![屬性面板](assets/attributes-multiple-properties.png){width="300" align="left"}

*從內容屬性面板新增屬性。*

您也可以輕鬆編輯和刪除屬性。
如需詳細資訊，請參閱 **內容屬性** 內的功能說明 [右側面板](../user-guide/web-editor-features.md#id2051EB003YK) 區段。

## 編寫時編輯中繼資料

現在，在製作時，您可以使用中的下拉式選單更新檔案中繼資料標籤 **檔案屬性** 在右側面板中。 您也可以選取 **編輯更多屬性** 以更新更多中繼資料。

![file-properties](assets/file-properties-general.png){width="300" align="left"}

*從右側面板更新中繼資料及編輯檔案屬性。*

如需詳細資訊，請參閱 **檔案屬性** 內的功能說明 [右側面板](../user-guide/web-editor-features.md#id2051EB003YK) 區段。

## 在地圖檢視中檢視索引鍵屬性

定義主題或地圖參照的鍵屬性時，您也可以在左側面板中檢視標題、對應圖示和鍵。 鍵會顯示為 `key=<key-name>`.

![地圖檢視中的索引鍵](assets/view-key-title-map-view.png) {width="300" align="left"}

*在「對映檢視」中檢視索引鍵屬性。*


如需詳細資訊，請參閱 **地圖檢視** 中的功能說明 [左側面板](../user-guide/web-editor-features.md#id2051EA0M0HS) 區段。

## 根據標籤複製基準線的功能

Experience Manager指南現在提供增強的使用者體驗，讓您從網頁編輯器建立基準線。
選項 **手動更新** 和 **自動更新** 更為直覺，並可協助您輕鬆選擇建立靜態基準線，還是根據標籤自動更新。

![建立新基準線](assets/dynamic-baseline-4-4.png) {width="300" align="left"}
*從網頁編輯器建立基準線。*

它也可讓您根據標籤複製基準線。 在複製時，會根據指定的標籤（如果存在）挑選參考版本，否則會從複製的基準線中挑選版本。


![複製基準線 ](assets/duplicate-baseline.png) {width="300" align="left"}

*根據標籤複製基準線或建立精確副本。*

進一步瞭解如何 [從網頁編輯器建立和管理基準線](../user-guide/web-editor-baseline.md).

## 增強的地圖集合儀表板

Experience Manager指南提供增強的地圖集合儀表板。 在地圖集合中，您可以快速大量設定DITA map的中繼資料屬性。 此功能相當實用，因為您不需要個別更新每個DITA map的中繼資料屬性。

現在，您可以檢視DITA map的檔案名稱。 您也可以檢視「基準線」。 這可協助您快速找出用於預設集的基準線。

![對應集合儀表板](assets/map-collection-dashboard.png){width="800" align="left"}

*從地圖集合儀表板檢視、編輯和產生輸出。*

瞭解如何 [使用地圖集合產生輸出](../user-guide/generate-output-use-map-collection-output-generation.md).

## 增強型翻譯面板

此 **翻譯** 面板已改善。  您可以檢視 **可用語言** 列出並快速選取您要翻譯專案的地區設定。 只要選取一個專案，您也可選擇 **全選** 將專案翻譯成所有可用語言。

![翻譯面板](assets/translation-languages-4.4.png){width="300" align="left"}



*選取您要翻譯專案的地區設定。 選擇檔案的預設版本、基準版本或最新版本以進行翻譯。*

進一步瞭解如何 [翻譯內容](../user-guide/translation.md).

## 改善「插入元素」對話方塊中的搜尋邏輯

您現在可以在「插入元素」對話方塊中輕鬆找到元素。  您可以在搜尋方塊中輸入字串，並取得以輸入字串開頭的所有有效元素清單。

例如，在編輯您要插入元素的段落時，您可以搜尋字元「t」以取得以「t」開頭的所有有效元素。


![插入對話方塊](assets/insert-element.png){width="300" align="left"}

*輸入字元以搜尋以該字元開頭的所有有效元素。*


如需詳細資訊，請檢視 **插入元素** 中的功能說明 [左側面板](../user-guide/web-editor-features.md#id2051EA0M0HS) 區段。


## 在同一層級分割清單的功能

現在，您可以在網頁編輯器中輕鬆分割清單。 選取 **分割清單** 從清單專案的前後關聯功能表中分割目前清單的選項。 從您為分割選取的清單專案開始，會在相同層級建立新清單。

![翻譯面板](assets/context-menu-split-list.png){width="300" align="left"}

*選取分割目前清單的選項。*

如需詳細資訊，請檢視 **插入清單** 中的功能說明 [左側面板](../user-guide/web-editor-features.md#id2051EA0M0HS) 區段。

## 輕鬆將DITA元素解除包裝

現在，您可以使用網頁編輯器元素內容功能表中的選項，輕鬆地將元素解除包裝。 這可協助您輕鬆地將元素的文字與其上層元素合併。
如需詳細資訊，請檢視 **解除元素包裝** 區段來自 [網頁編輯器中的其他功能](../user-guide/web-editor-other-features.md).

## 在編寫的來源模式中存取檔案屬性

現在，您可以存取右側面板的 **檔案屬性** 功能在所有四種模式或檢視中：「配置」、「作者」、「來源」和「預覽」。  即使在不同模式之間切換，這也可以幫助您檢視檔案的屬性。

如需詳細資訊，請檢視 **檔案屬性** 中的功能說明 [右側面板](../user-guide/web-editor-features.md#id2051EB003YK) 區段。


## 依標題或檔案名稱檢視檔案

您現在可以選擇在Web編輯器中檢視檔案的預設方式。 您可以從「作者」檢視中，依不同面板的標題或檔案名稱來檢視檔案清單。

![使用者偏好設定對話方塊](assets/user-preferences-2311.png){width="550" align="left"}

*變更檢視檔案的預設方式，從&#x200B;**使用者偏好設定**對話方塊。*


## 在重新整理瀏覽器時還原檔案索引標籤

當您重新整理瀏覽器時，「Experience Manager指南」會恢復網頁編輯器中已開啟檔案標籤的狀態。 如需詳細資訊，請檢視 **編輯檔案時重新整理瀏覽器** 區段在 [在網頁編輯器中編輯主題](../user-guide/web-editor-edit-topics.md).


## 使用鍵盤快速鍵進行導覽的功能

Experience Manager參考線現在也可讓您使用鍵盤快速鍵在網頁編輯器中移動游標。 您可以使用鍵盤快速鍵，快速向左或向右移動一個單字。 您也可以在鍵盤快速鍵的協助下移至行的開頭或結尾。
現在，您也可以使用鍵盤快速鍵，將游標移至下一個元素的開頭或上一個元素的結尾。
進一步瞭解 [網頁編輯器中的鍵盤快速鍵](../user-guide/web-editor-keyboard-shortcuts.md).


## 解析AEM網站輸出中的交叉對應連結

現在，在AEM網站輸出中轉譯的交叉對應連結（具有範圍對等的XREF）會根據為產生的對應設定的發佈內容的檔案標題來解析。


## 設定AEM網站輸出的URL以使用檔案標題

Experience Manager指南可讓您以管理員身分設定AEM Site輸出的URL。 如果檔案名稱不存在或包含所有特殊字元，您可以設定在AEM Site輸出的URL中以分隔符號取代它們。 您也可以使用第一個子主題名稱來取代它們。 瞭解如何 [設定AEM網站輸出的URL以使用檔案標題](../cs-install-guide/conf-output-generation.md#configure-the-url-of-the-aem-site-output-to-use-the-document-title).


## 同時發佈多個輸出預設集

「Experience Manager」提供根據套用至主題的主題標籤自動挑選主題以建立基準的功能。 現在，您也可以使用相同DITA map的自動基準線，順暢地發佈多個輸出預設集。 您不需要一次只發佈一個預設集，但可以輕鬆地同時發佈多個輸出預設集。

進一步瞭解如何 [從網頁編輯器建立和管理基準線](../user-guide/web-editor-baseline.md).

## 原生PDF增強功能

下列原生PDF增強功能已在4.4.0版本中完成：

### 在PDF輸出中使用變數

您可以使用變數來動態插入及管理可重複使用的資訊。 Experience Manager參考線可協助您在產生PDF輸出時建立、編輯和預覽變數。 您可以快速修改變數的值，讓您的檔案可攜式且易於更新。

![原生pdf變數](assets/add-variable-default.png){width="800" align="left"}

*在網頁編輯器中建立和管理變數。*

您也可以建立修訂預設值的變數集，並為變數指派替代值。 在頁面配置中插入這些變數，並使用相同的PDF配置，您就不必為每一組值建立個別的配置。 例如，您可以為每個產品發行建立一個變數集。 此變數集可包含不同產品詳細資料的變數，例如產品名稱、版本號碼和發行日期。 然後，您可以為這些變數新增不同的值。

**變數集1：Adobe集1**

* ProductName：Experience Manager指南
* 版本號碼：2311
* 發行日期： 2023年11月2日

**變數集2：Adobe集2**

* ProductName：Experience Manager指南
* 版本號碼：2310
* 發行日期： 2023年9月27日



<img src="./assets/native-pdf-variable-output.png" alt="PDF輸出中的頁尾" width="500" border="2px">

*使用PDF配置中的變數產生PDF輸出。*

您可以套用樣式，並使用HTML標示來格式化變數。  您也可以在需要時快速更新任何變數的值，並重新產生輸出。 例如，如果您需要更新版本的詳細資訊，可以在VersionNumber變數中編輯版本值並重新產生輸出。


進一步瞭解如何使用 [PDF輸出中的變數](../native-pdf/native-pdf-variables.md).


### 將資產中繼資料傳播至PDF輸出

Experience Manager現在提供將資產的中繼資料屬性從DITA map傳輸至PDF輸出的功能。
從原生PDF輸出預設集中，您可以選擇要傳播到PDF發佈流程的中繼資料。 您可以同時選取自訂和預設屬性。  選取的中繼資料屬性會傳輸到使用原生PDF產生的PDF檔案。

此功能相當實用，可協助您保持資產屬性（例如作者、建立日期或檔案標題）的一致性。 這可讓您更輕鬆地組織、搜尋和分類您的檔案。

如需詳細資訊，請檢視 **進階** 中的設定 [發佈PDF輸出](../web-editor/native-pdf-web-editor.md).

### 使用在中新增的中繼資料 `topicmeta` PDF輸出的元素

原生PDF發佈的中繼資料功能有助於內容管理，也有助於在網際網路上搜尋檔案。
<img src="assets/pdf-metadata-4-4.png" alt="中繼資料標籤" width="800">

*選取選項以新增和自訂中繼資料選項。*

現在，Experience Manager指南提供您使用在中新增中繼資料的選項 `topicmeta` DITA map的元素，以填入PDF輸出的中繼資料欄位。 依預設，會選取此選項。

此功能有助於改善檔案管理、確保一致性，並讓您的檔案可供搜尋。

若要瞭解更多，請檢視 **中繼資料** 索引標籤中的 [發佈PDF輸出](../web-editor/native-pdf-web-editor.md).

### 使用和複製現成可用的PDF範本

Experience Manager指南提供現成或原廠的PDF範本。 複製工廠PDF範本以建立自訂PDF範本。

現在，您也可以在建立和複製範本時，預覽範本的縮圖影像。 您也可以編輯或刪除此影像。 此功能對於品牌化或區分具有類似名稱的範本非常有用。
進一步瞭解 [PDF範本](../native-pdf/pdf-template.md).

![複製PDF範本對話方塊](assets/duplicate-template.png){width="550" align="left"}

*複製現有的PDF範本。*


### 變更頁面順序並每張工作表發佈多個頁面

除了根據來原始檔發佈頁面外，您也可以在發佈多頁檔案時，變更PDF的頁面順序。  這可讓您靈活地以各種順序發佈頁面，例如先發佈所有奇數或所有偶數頁面。 您也可以以小冊子的形式發佈，並像書籍一樣閱讀頁面。 您也可以決定要在單張紙上發佈的頁數。 如需詳細資訊，請檢視 [頁面組織](../native-pdf/components-pdf-template.md#page-organization) 區段。

### 根據排序索引鍵排序字彙表辭彙

現在，您也可以根據排序索引鍵來排序字彙表辭彙。 您可以使用標籤&#39;sort-as&#39;來定義辭彙表的排序索引鍵。 然後，您可以根據排序索引鍵來排序它們，以取代詞語。 這可讓您根據不同語言中使用的辭彙來排序字彙表辭彙。 您也可以為具有片語或一組字詞的辭彙表辭彙定義單一排序索引鍵。
如需詳細資訊，請檢視 [進階PDF設定](../native-pdf/components-pdf-template.md#advanced-pdf-settings).


### 改善原生PDF範本的資源管理

Experience Manager指南現在已改善原生PDF範本的資源管理。 您現在可以在多個原生PDF範本間共用及重複使用資源，例如影像、CSS檔案和字型檔案。 經過這項改善後，管理大量範本的資源就變得簡單多了。 您不需要為每個範本建立重複資源，您可以將它們儲存在共用資料夾中，並在所有原生PDF範本中使用它們。
如需詳細資訊，請檢視 [PDF範本](../native-pdf/pdf-template.md).































