---
title: 發行說明 | 2024.4.0版Adobe Experience Manager Guides的新增功能
description: 瞭解2024.4.0版Adobe Experience Manager Guidesas a Cloud Service中的新功能和增強功能。
exl-id: e9db535a-5ad5-4ff0-94af-b4425594316a
source-git-commit: 5d99274da8fdacbd255d426fa4913b5773ca45f8
workflow-type: tm+mt
source-wordcount: '1806'
ht-degree: 28%

---

# 2024.4.0版的新增功能

本文介紹2024.4.0版Adobe Experience Manager Guides的新增功能和增強功能。

有關此版本中的問題修正清單，請查看 [2024.4.0 版本中修正的問題](fixed-issues-2024-04-0.md)。

瞭解2024.4.0版](upgrade-instructions-2024-04-0.md)的[升級指示。

## 能夠使用預先設定的語言群組將內容翻譯成多種語言

Experience Manager Guides 現在允許您建立語言群組並輕鬆將您的內容翻譯成多種語言。此功能可協助您根據組織的需求組織和管理翻譯。

例如，如果您需要為歐洲某些國家/地區翻譯您的內容，您可以為英語 (EN)、法語 (FR)、德語 (DE)、西班牙語 (ES) 和義大利語 (IT) 等歐洲語言建立語言群組。



![翻譯面板](assets/translation-languages-2404.png){width="300" align="left"}

*選取您想要翻譯文件的語言群組或語言。*

>[!NOTE]
>
>如果某種語言的目標資料夾遺失或目標語言與原始語言相同，則會變成灰色並顯示警告標誌。

作為管理員，您可以建立語言群組並將其設定到多個資料夾設定檔中。作為作者，您可以查看資料夾設定檔中設定的語言群組。


整體而言，建立語言群組可以提高翻譯專案的效率和生產力，最終改善跨多種語言的本地化流程。


瞭解如何[從網頁編輯器](../user-guide/translate-documents-web-editor.md)翻譯檔案。



## 在翻譯後自動刪除或停用翻譯專案

現在，作為管理員，您可以將翻譯專案設定為在完成翻譯後自動停用或刪除。 此功能可協助您有效率地使用資源，並在完成翻譯後管理檔案。

刪除專案會永久移除專案中存在的所有檔案和資料夾。 刪除翻譯專案也能讓您釋出已佔用的磁碟空間。

如果您想稍後再使用翻譯專案，可以停用這些專案。

![](assets/editor-setting-translation.png){width="550" align="left"}


*設定翻譯專案的語言群組和清理設定。*


深入瞭解如何[自動刪除或停用翻譯專案](../user-guide/translate-documents-web-editor.md#automatically-delete-or-disable-a-completed-translation-project)。


## 在預覽執行個體上的大量啟用集合中啟用地圖的輸出

現在，除了在發佈執行個體上啟用大量啟用集合的輸出之外，Experience Manager Guides還可提供在&#x200B;**預覽**&#x200B;執行個體上啟用它的功能，因為Cloud Service會提供。


此功能可協助您將內容啟用至預覽執行個體，讓您在將其啟用至&#x200B;**Publish**&#x200B;執行個體之前，先檢視其外觀和運作方式。


![已建立大量啟動集合稽核歷程記錄標籤](assets/bulk-collection-audit-history.png){width="800" align="left"}

*在&#x200B;**稽核歷史記錄**索引標籤中檢視已啟動地圖輸出的相關資訊。*


深入瞭解[大量啟用](../user-guide/conf-bulk-activation-publish-map-collection.md)。

## 資料來源聯結器的增強功能

2024.4.0 版本的資料來源連接器進行了以下增強：

### 連線至Salsify、Akeneo和Microsoft Azure DevOps Boards (ADO)資料來源

除了現有的立即可用連接器之外，Experience Manager Guides 還提供適用於 Salsify、Akeneo 和 Microsoft Azure DevOps Boards (ADO) 資料來源的連接器。作為管理員，您可以下載並安裝這些連接器。然後，設定已安裝的連接器。

### 複製並貼上範例查詢以建立內容片段或主題

您可以輕鬆地在產生器中複製並貼上範例資料查詢以建立內容片段或主題。使用此功能，您不必記住語法或手動建立查詢。不是手動輸入查詢，而是您可以複製並貼上範例查詢，加以編輯，然後用它來依您的要求撷取資料。

![插入內容片段對話框](assets/insert-content-snippet.png){width="800" align="left"}

*複製並編輯範例查詢以建立內容片段。*

### 使用檔案聯結器連線至JSON資料檔案


現在，身為管理員，您可以設定 JSON 檔案連接器以使用 JSON 資料檔案作為資料來源。使用連接器從您的電腦或 Adobe Experience Manager Assets 匯入 JSON 檔案。然後，作為作者，您可以使用產生器建立內容片段或主題。

此功能可協助您使用 JSON 檔案中儲存的資料並在各種片段中重複使用它。每當您更新 JSON 檔案時，內容也會動態更新。

### 設定聯結器的多個資源URL以建立內容片段或主題

作為管理員，您可以為某些聯結器設定多個資源URL，例如Generic REST Client、Salsify、Akeneo和Microsoft Azure DevOps Boards (ADO)。

然後，作為作者，連接資料來源以使用產生器建立內容片段或主題。此功能很方便，因為您不必為每個 URL 建立資料來源。它可協助您從單一內容片段或主題中特定資料來源的任何資源快速擷取資料。

檢視資料來源聯結器的詳細資訊，以及如何[從使用者介面](../cs-install-guide/conf-data-source-connector-tools.md)設定資料來源聯結器。

了解如何 [使用資料來源中的資料](../user-guide/web-editor-content-snippet.md)。

## 使用新的使用者偏好設定UI自訂您的Web Editor體驗

網頁編輯器中的&#x200B;**使用者偏好設定**&#x200B;對話方塊現在包含新的&#x200B;**外觀**&#x200B;標籤。 此新標籤可讓您方便地在網頁編輯器介面中設定最常見的外觀喜好設定。

您可以設定為依標題或檔案名稱檢視檔案，並變更應用程式的主題和來源檢視。 它也可協助您進行設定，以在存放庫檢視中找出開啟的檔案，並處理不斷行空格。

使用者偏好設定的![外觀標籤](assets/user_preference_editor_appearance.png){width="550" align="left"}

*根據您的喜好自訂外觀。*

在[左側面板](../user-guide/web-editor-features.md#id2051EA0M0HS)區段中進一步瞭解&#x200B;**使用者偏好設定**&#x200B;功能說明。

## 在網頁編輯器的存放庫檢視中找出開啟的檔案

選取&#x200B;**使用者偏好設定**&#x200B;中的&#x200B;**永遠尋找存放庫中的檔案**&#x200B;選項，以在存放庫檢視中快速瀏覽並尋找您的檔案。 您不需要手動搜尋。

在編輯時，此功能也可協助您輕鬆檢視檔案在存放庫階層內的位置。

如需詳細資訊，請檢視[在存放庫檢視](../user-guide/web-editor-edit-topics.md#locate-an-open-file-in-the-repository-view)中找到開啟的檔案。


## 改善網頁編輯器中不間斷空格的處理方式

Experience Manager Guides可讓您在網頁編輯器中編輯檔案時顯示不斷行空格指示器。 它也能改善不中斷空格的處理方式。
它會將多個連續的空格轉換為單一空格，以保留檔案在網頁編輯器中的「所見即所得」檢視。 此功能也有助於改善檔案的整體外觀和專業性。


如需詳細資訊，請檢視網頁編輯器的[其他功能](../user-guide/web-editor-other-features.md)。




## 在Adobe Experience Manager Assets上停用選擇性資料夾的後處理


身為管理員，您現在可以在Experience Manager Assets上停用選擇性資料夾的UUID後處理與產生。 此設定可能有所幫助，尤其是在處理許多資產或複雜的資料夾結構時。 它還有助於多位使用者同時快速上傳資產，而不會互相干擾。  

停用資料夾的後處理也會影響其所有子資料夾。 不過，Experience Manager Guides現在提供選擇性地為已忽略資料夾內的個別子資料夾啟用後處理的功能。

瞭解如何[停用資料夾](../cs-install-guide/conf-folder-post-processing.md)的後處理。

## 在存放庫檢視中搜尋和篩選檔案的改版體驗

現在，您有增強的篩選檔案體驗。改進的檔案篩選功能讓使用者更能輕鬆地搜尋和瀏覽檔案。


![在存放庫視圖中搜尋檔案](assets/repository-filter-search-2404.png){width="300" align="left"}

*搜尋包含文字`general purpose.`* 的檔案

享受像是更快存取相關檔案和更直覺的使用者介面等優勢，使您的搜尋體驗更流暢、更有效率。

![快速搜尋篩選器](assets/repository-filter-search-quick.png) {width="300" align="left"}

*使用快速篩選器搜尋 DITA 和非 DITA 檔案。*

進一步了解[左面板](../user-guide/web-editor-features.md#id2051EA0M0HS)區段中的&#x200B;**篩選器搜尋**&#x200B;功能。

## 分隔清單，可依據其位置檢視和插入有效元素

在Web編輯器中編輯檔案時，您現在可以檢視在目前位置及目前位置以外有效的分隔元素清單。 您可以根據需求，從下列選項中選擇元素：

* **位於目前位置**&#x200B;的有效元素，您可以在目前游標位置本身插入。
* **目前位置**&#x200B;之外的有效元素，您可以在元素階層中目前元素的任何父項之後插入。

![插入專案對話方塊](assets/insert-element-dialog.png){width="300" align="left"}

*檢視有效元素的隔離清單，以在目前位置插入元素。*


此有效元素的分割清單可協助您維持內容結構並遵循DITA標準。

深入瞭解[次要工具列](../user-guide/web-editor-features.md#2051ea0j0y4)區段中的&#x200B;**插入元素**&#x200B;功能。


## 內容屬性型別會顯示為下拉式功能表

現在，內容屬性&#x200B;**Type**&#x200B;會以下拉式功能表形式顯示。 您可以從下拉式清單中檢視並選取目前標籤的完整階層標籤。

此下拉式選單可協助您快速存取階層結構內的相關標籤。


內容屬性中的![型別下拉式功能表](assets/content-properties-type.png){width="300" align="left"}

*從階層中選取目前標籤的標籤。*

在[右側面板](../user-guide/web-editor-features.md#id2051eb003yk)區段中進一步瞭解&#x200B;**內容屬性**&#x200B;功能。



## 改善從對應編輯器大量檢查檔案時的效能

Experience Manager Guides改善了從地圖編輯器簽入大量檔案功能的效能和體驗。 此項改善可協助您更快地簽入大量檔案。
您也可以從**另存為新版本和解除鎖定**&#x200B;對話方塊檢視檔案的簽入作業進度。 最後，成功訊息會在作業完成且所有選取的已出庫檔案都已入庫後出現。

![另存為新版本並解除鎖定對話方塊](./assets/save-version-lock.png){width="300" align="left"}

*檢視從對應編輯器大量簽入的檔案清單和狀態。*

瞭解如何[使用進階地圖編輯器](../user-guide/map-editor-advanced-map-editor.md)

## 透過DITA-OT產生輸出時下載暫存檔案

您也可以下載當您透過DITA-OT發佈AEM網站、HTML、自訂、JSON或PDF輸出時產生的暫存檔案。 此功能可協助您分析輸出產生過程中可能發生的任何問題，並有效進行疑難排解。  
如果您已選取任何已傳遞給使用DITA-OT產生的輸出的中繼資料屬性，也可以下載metadata.xml檔案。 

如需預設集的詳細資訊，請檢視[瞭解輸出預設集](../user-guide/generate-output-understand-presets.md)。


## 以微服務型發佈的IMS OAuth憑證取代IMS JWT憑證


已棄用服務帳戶(JWT)認證，改用&#x200B;**OAuth伺服器對伺服器**&#x200B;認證。 使用服務帳戶(JWT)憑證的應用程式將在2025年1月1日之後停止運作。 您必須在2025年1月1日之前移轉至新認證，以確保您的應用程式繼續運作。


Experience Manager Guides的雲端發佈服務現在由Adobe IMS OAuth型驗證保護。 瞭解如何[使用OAuth驗證](../knowledge-base/publishing/configure-microservices-imt-config.md)設定微服務型發佈。
