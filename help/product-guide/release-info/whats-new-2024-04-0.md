---
title: 發行說明 | Adobe Experience Manager Guides，2024.4.0版的新增功能
description: 瞭解2024.4.0版Adobe Experience Manager Guidesas a Cloud Service中的新功能和增強功能。
source-git-commit: 9a0d2886012bd1695387a93984ccac5127384db3
workflow-type: tm+mt
source-wordcount: '1806'
ht-degree: 0%

---

# 2024.4.0版的新增功能

本文介紹2024.4.0版Adobe Experience Manager Guides的新增和增強功能。

如需此版本中修正的問題清單，請檢視 [已修正2024.4.0版本中的問題](fixed-issues-2024-04-0.md).

瞭解 [2024.4.0版的升級指示](upgrade-instructions-2024-04-0.md).

## 能夠使用預先設定的語言群組將內容翻譯成多種語言

Experience Manager指南現在可讓您建立語言群組，並輕鬆將內容翻譯成多種語言。 此功能可協助您根據組織的需求組織和管理翻譯。

例如，如果您需要為某些歐洲國家/地區翻譯您的內容，您可以建立一個歐洲語言的語言群組，例如英文(EN)、法文(FR)、德文(DE)、西班牙文(ES)和義大利文(IT)。



![翻譯面板](assets/translation-languages-2404.png){width="300" align="left"}

*選取您要翻譯檔案的語言群組或語言。*

>[!NOTE]
>
>如果語言的目標資料夾遺失或目標語言與來源相同，則會呈現灰色並顯示警告符號。

作為管理員，您可以建立語言群組並將其設定為多個資料夾設定檔。 身為作者，您可以檢視在資料夾設定檔上設定的語言群組。


整體而言，建立語言群組可提升翻譯專案的效率和生產力，最終改善多種語言的本地化流程。


瞭解如何 [從網頁編輯器翻譯檔案](../user-guide/translate-documents-web-editor.md).



## 在翻譯後自動刪除或停用翻譯專案

現在，作為管理員，您可以將翻譯專案設定為在完成翻譯後自動停用或刪除。 此功能可協助您有效率地使用資源，並在完成翻譯後管理檔案。

刪除專案會永久移除專案中存在的所有檔案和資料夾。 刪除翻譯專案也能讓您釋出已佔用的磁碟空間。

如果您想稍後再使用翻譯專案，可以停用這些專案。

![](assets/editor-setting-translation.png){width="550" align="left"}


*設定翻譯專案的語言群組和清理設定。*


進一步瞭解如何 [自動刪除或停用翻譯專案](../user-guide/translate-documents-web-editor.md#automatically-delete-or-disable-a-completed-translation-project).


## 在預覽執行個體上的大量啟用集合中啟用地圖的輸出

現在，除了在發佈執行個體上啟用大量啟用集合的輸出外，Experience Manager Guides還可提供在Cloud Service上啟用它的功能 **預覽** 執行個體。


此功能可協助您將內容啟用至預覽例項，讓您在啟用至 **發佈** 執行個體。


![ 已建立大量啟動集合稽核歷史記錄標籤](assets/bulk-collection-audit-history.png){width="800" align="left"}

*在中檢視關於已啟動地圖輸出的資訊&#x200B;**稽核歷史記錄**標籤。*


進一步瞭解  [大量啟用](../user-guide/conf-bulk-activation-publish-map-collection.md).

## 資料來源聯結器的增強功能

已對2024.4.0版的資料來源聯結器進行下列增強功能：

### 連線至Salsify、Akeneo和Microsoft Azure DevOps Boards (ADO)資料來源

除了現有的現成可用聯結器外，Experience Manager指南也提供Salsify、Akeneo和Microsoft Azure DevOps Boards (ADO)資料來源的聯結器。 身為管理員，您可以下載並安裝這些聯結器。 然後，設定已安裝的聯結器。

### 複製並貼上範例查詢以建立內容片段或主題

您可以在產生器中輕鬆複製並貼上範例資料查詢，以建立內容片段或主題。 使用此功能，您不必記住語法或手動建立查詢。 與其手動輸入查詢，您可以複製並貼上範例查詢、編輯它，然後按照您的要求使用它擷取資料。

![插入內容片段對話方塊](assets/insert-content-snippet.png){width="800" align="left"}

*複製並編輯範例查詢以建立內容片段。*

### 使用檔案聯結器連線至JSON資料檔案


現在，作為管理員，您可以設定JSON檔案聯結器以使用JSON資料檔案作為資料來源。 使用聯結器從您的電腦或Adobe Experience Manager Assets匯入JSON檔案。 然後，身為作者，您可以使用產生器建立內容片段或主題。

此功能可協助您使用儲存在JSON檔案中的資料，並在各種程式碼片段中重複使用。 內容也會在每次更新JSON檔案時動態更新。

### 設定聯結器的多個資源URL以建立內容片段或主題

作為管理員，您可以為某些聯結器設定多個資源URL，例如Generic REST Client、Salsify、Akeneo和Microsoft Azure DevOps Boards (ADO)。

然後，以作者身分連線至資料來源，以使用產生器建立內容片段或主題。 此功能相當實用，因為您不需要為每個URL建立資料來源。 它可協助您從單一內容片段或主題中特定資料來源的任何資源快速擷取資料。

檢視有關資料來源聯結器及操作方法的更多詳細資料 [從使用者介面設定資料來源聯結器](../cs-install-guide/conf-data-source-connector-tools.md).

瞭解如何 [使用來自您資料來源的資料](../user-guide/web-editor-content-snippet.md).

## 使用新的使用者偏好設定UI自訂您的Web Editor體驗

此 **使用者偏好設定** Web編輯器中的對話方塊現在包含新的 **外觀** 標籤。 此新標籤可讓您方便地在網頁編輯器介面中設定最常見的外觀喜好設定。

您可以設定為依標題或檔案名稱檢視檔案，並變更應用程式的主題和來源檢視。 它也可協助您進行設定，以在存放庫檢視中找出開啟的檔案，並處理不斷行空格。

![使用者偏好設定的外觀標籤](assets/user_preference_editor_appearance.png){width="550" align="left"}

*根據您的偏好自訂外觀。*

進一步瞭解 **使用者偏好設定** 中的功能說明 [左側面板](../user-guide/web-editor-features.md#id2051EA0M0HS) 區段。

## 在網頁編輯器的存放庫檢視中找出開啟的檔案

選取 **一律在存放庫中尋找檔案** 中的選項 **使用者偏好設定** 以在存放庫檢視中快速導覽並找到您的檔案。 您不需要手動搜尋。

在編輯時，此功能也可協助您輕鬆檢視檔案在存放庫階層內的位置。

如需詳細資訊，請檢視 [在存放庫檢視中找出開啟的檔案](../user-guide/web-editor-edit-topics.md#locate-an-open-file-in-the-repository-view).


## 改善網頁編輯器中不間斷空格的處理方式

Experience Manager參考線可讓您在網頁編輯器中編輯檔案時顯示不斷行空格指示器。 它也能改善不中斷空格的處理方式。
它會將多個連續的空格轉換為單一空格，以保留檔案在網頁編輯器中的「所見即所得」檢視。 此功能也有助於改善檔案的整體外觀和專業性。


如需詳細資訊，請檢視 [網頁編輯器的其他功能](../user-guide/web-editor-other-features.md).




## 在Adobe Experience Manager Assets上停用選擇性資料夾的後處理


身為管理員，您現在可以在Experience Manager Assets上停用選擇性資料夾的UUID後處理與產生。 此設定可能有所幫助，尤其是在處理許多資產或複雜的資料夾結構時。 它還有助於多位使用者同時快速上傳資產，而不會互相干擾。  

停用資料夾的後處理也會影響其所有子資料夾。 不過，「Experience Manager指南」現在能選擇性地為忽略的資料夾內的個別子資料夾啟用後處理。

瞭解如何 [停用資料夾的後處理](../cs-install-guide/conf-folder-post-processing.md).

## 在存放庫檢視中搜尋和篩選檔案的改版體驗

現在，您有了更優異的檔案篩選體驗。 經過改寫的檔案篩選功能提供更方便您搜尋和瀏覽檔案的方法。


![在存放庫檢視中搜尋檔案](assets/repository-filter-search-2404.png){width="300" align="left"}

*搜尋包含文字的檔案`general purpose.`*

享受更快存取相關檔案和更直覺的使用者介面等好處，讓您的搜尋體驗更順暢、更有效率。

![快速搜尋篩選器 ](assets/repository-filter-search-quick.png) {width="300" align="left"}

*使用快速篩選器來搜尋DITA和非DITA檔案。*

進一步瞭解 **篩選搜尋** 中的功能 [左側面板](../user-guide/web-editor-features.md#id2051EA0M0HS) 區段。

## 分隔清單，可依據其位置檢視和插入有效元素

在Web編輯器中編輯檔案時，您現在可以檢視在目前位置及目前位置以外有效的分隔元素清單。 您可以根據需求，從下列選項中選擇元素：

* **目前位置的有效元素** 可以在目前游標位置本身插入。
* **目前位置以外的有效元素** 可在元素階層內目前元素的任何父項之後插入。

![插入元素對話方塊](assets/insert-element-dialog.png){width="300" align="left"}

*檢視有效元素的獨立清單，以在目前位置插入元素。*


此有效元素的分割清單可協助您維持內容結構並遵循DITA標準。

進一步瞭解 **插入元素** 中的功能 [次要工具列](../user-guide/web-editor-features.md#2051ea0j0y4) 區段。


## 內容屬性型別會顯示為下拉式功能表

現在，內容屬性 **型別** 顯示為下拉式功能表。 您可以從下拉式清單中檢視並選取目前標籤的完整階層標籤。

此下拉式選單可協助您快速存取階層結構內的相關標籤。


![內容屬性中的型別下拉式選單](assets/content-properties-type.png){width="300" align="left"}

*從階層中選取目前標籤的標籤。*

進一步瞭解 **內容屬性** 中的功能 [右側面板](../user-guide/web-editor-features.md#id2051eb003yk) 區段。



## 改善從對應編輯器大量檢查檔案時的效能

Experience Manager指南改善了從地圖編輯器簽入大量檔案功能的效能和體驗。 此項改善可協助您更快地簽入大量檔案。
您也可以從檢視檔案入庫作業的進度 **另存為新版本並解鎖** 對話方塊。 最後，成功訊息會在作業完成且所有選取的已出庫檔案都已入庫後出現。

![另存為新版本並解除鎖定對話方塊](./assets/save-version-lock.png){width="300" align="left"}

*檢視從地圖編輯器大量入庫的檔案清單和狀態。*

瞭解如何 [使用進階地圖編輯器](../user-guide/map-editor-advanced-map-editor.md)

## 透過DITA-OT產生輸出時下載暫存檔案

您也可以下載當您透過DITA-OT發佈AEM網站、HTML、自訂、JSON或PDF輸出時產生的暫存檔案。 此功能可協助您分析輸出產生過程中可能發生的任何問題，並有效進行疑難排解。  
如果您已選取任何已傳遞給使用DITA-OT產生的輸出的中繼資料屬性，也可以下載metadata.xml檔案。 

如需預設集的詳細資訊，請檢視 [瞭解輸出預設集](../user-guide/generate-output-understand-presets.md).


## 以微服務型發佈的IMS OAuth憑證取代IMS JWT憑證


服務帳戶(JWT)憑證已遭取代，以支援 **OAuth伺服器對伺服器** 認證。 使用服務帳戶(JWT)憑證的應用程式將在2025年1月1日之後停止運作。 您必須在2025年1月1日之前移轉至新認證，以確保您的應用程式繼續運作。


Experience Manager指南的雲端發佈服務現在由Adobe IMS OAuth型驗證提供保護。 瞭解如何 [使用OAuth驗證設定微服務型發佈](../knowledge-base/publishing/configure-microservices-imt-config.md).
