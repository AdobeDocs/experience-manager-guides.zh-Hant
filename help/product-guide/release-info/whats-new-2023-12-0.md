---
title: 發行說明 | Adobe Experience Manager Guides的新增功能，2023年12月發行
description: 在2023年12月版本的Adobe Experience Manager Guidesas a Cloud Service中瞭解新增和增強功能。
feature: What's New
role: Leader
source-git-commit: 6d8c01f20f7b59fed92c404561b647d9ebecb050
workflow-type: tm+mt
source-wordcount: '966'
ht-degree: 0%

---

# 2023年12月版Adobe Experience Manager Guides的as a Cloud Service新增功能

本文介紹2023年12月Adobe Experience Manager Guides版本的新增和增強功能(以下稱為 *Experience Manager指南as a Cloud Service*)。

如需有關升級指示、相容性矩陣，以及此版本中修正問題的詳細資訊，請檢視 [發行說明](release-notes-2023-12-0.md).


## 在PDF輸出中使用變數

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

## 將內容發佈至ServiceNow知識庫的功能

您現在也可以將內容發佈到ServiceNow知識庫平台。

在2023年12月版本中，管理員可以建立ServiceNow知識庫伺服器的發佈設定檔。 然後，身為作者或發佈者，您可以選擇輸出預設集中的ServiceNow發佈設定檔，以將輸出發佈到指定的知識庫。

此功能可協助您將文字、影片和影像等內容發佈到ServiceNow知識庫平台，並維護完整的存放庫。


![服務現在知識庫預設集](assets/knowledgebase--output-preset.png){width="300" align="left"}

*建立ServiceNow知識庫的輸出預設集。*

進一步瞭解 [知識庫](../user-guide/generate-output-knowledge-base.md) 輸出預設集。

## 增強的地圖集合儀表板

Experience Manager指南提供增強的地圖集合儀表板。 在地圖集合中，您可以快速大量設定DITA map的中繼資料屬性。 此功能相當實用，因為您不需要個別更新每個DITA map的中繼資料屬性。

現在，您可以檢視DITA map的檔案名稱。 您也可以檢視「基準線」。 這可協助您快速找出用於預設集的基準線。

![對應集合儀表板](assets/map-collection-dashboard.png){width="800" align="left"}

*從地圖集合儀表板檢視、編輯和產生輸出。*

瞭解如何 [使用地圖集合產生輸出](../user-guide/generate-output-use-map-collection-output-generation.md).

## 在地圖檢視中檢視索引鍵屬性

定義主題或地圖參照的鍵屬性時，您也可以在左側面板中檢視標題、對應圖示和鍵。 鍵會顯示為 `key=<key-name>`.

如需詳細資訊，請參閱 **地圖檢視** 中的功能說明 [左側面板](../user-guide/web-editor-features.md#id2051EA0M0HS) 區段。

![地圖檢視中的索引鍵](assets/view-key-title-map-view.png) {width="300" align="left"}

*在「對映檢視」中檢視索引鍵屬性。*

## 根據標籤複製基準線的功能

Experience Manager指南現在提供增強的使用者體驗，讓您從網頁編輯器建立基準線。\
![建立新基準線](assets/create-new-baseline.png) {width="300" align="left"}
*從網頁編輯器建立基準線。*

它也可讓您根據標籤複製基準線。 在複製時，會根據指定的標籤（如果存在）挑選參考版本，否則會從複製的基準線中挑選版本。


![複製基準線 ](assets/duplicate-baseline.png) {width="300" align="left"}

*根據標籤複製基準線或建立精確副本。*

進一步瞭解如何 [從網頁編輯器建立和管理基準線](../user-guide/web-editor-baseline.md).

## 解析AEM網站輸出中的交叉對應連結

現在，在AEM網站輸出中轉譯的交叉對應連結（具有範圍對等的XREF）會根據為產生的對應設定的發佈內容的檔案標題來解析。


## 設定AEM網站輸出的URL以使用檔案標題

Experience Manager指南可讓您以管理員身分設定AEM Site輸出的URL。 如果檔案名稱不存在或包含所有特殊字元，您可以設定在AEM Site輸出的URL中以分隔符號取代它們。 您也可以使用第一個子主題名稱來取代它們。 瞭解如何 [設定AEM網站輸出的URL以使用檔案標題](../cs-install-guide/conf-output-generation.md#configure-the-url-of-the-aem-site-output-to-use-the-document-title).

