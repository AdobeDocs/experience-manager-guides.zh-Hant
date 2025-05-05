---
title: 發行說明 | Adobe Experience Manager Guides 4.2.1版的新增功能
description: 瞭解Adobe Experience Manager Guides 4.2.1版中的新功能和增強功能
exl-id: 441aa7ec-d88c-42cb-83f0-d0f6e58bfa41
feature: What's New
role: Leader
source-git-commit: 6d8c01f20f7b59fed92c404561b647d9ebecb050
workflow-type: tm+mt
source-wordcount: '710'
ht-degree: 0%

---

# Adobe Experience Manager Guides 4.2.1版的新增功能（2023年5月）

本文介紹Adobe Experience Manager Guides 4.2.1版(後來稱為&#x200B;*AEM Guides*)中的新功能和增強功能。

如需有關升級指示、相容性矩陣，以及此版本中修正問題的詳細資訊，請參閱[發行說明](release-notes-4-2-1.md)文章。

## 從網頁編輯器導覽至AEM首頁

現在您可以輕鬆從網頁編輯器導覽至AEM導覽頁面。

![](assets/web-editor-launch-page.png){width="800" align="left"}

* 按一下&#x200B;**參考線**&#x200B;圖示(![](assets/aem-guides-icon.png))，返回AEM導覽頁面。


如需詳細資訊，請參閱[AEM導覽頁面](../user-guide/web-editor-launch-editor.md#id2056BG00RZJ)。

## PDF發佈中的進階中繼資料支援

AEM Guides現在為對應至PDF輸出中中繼資料的中繼資料提供進階支援。 中繼資料選項包括有關檔案及其內容的資訊，例如作者姓名、檔案標題、關鍵字、版權資訊和其他資料欄位。

<img src="assets/pdf-metadata.png" alt=" 原生pdf中繼資料">

您可以匯入XMP檔案，而AEM Guides可以從該檔案中挑選資訊。 您也可以選擇使用下拉式清單提供中繼資料名稱和值。 您也可以直接在名稱欄位中輸入內容，以新增自訂中繼資料。

如需詳細資訊，請參閱[建立PDF輸出預設集](../web-editor/native-pdf-web-editor.md)中的&#x200B;**中繼資料**&#x200B;功能說明。

### 增強型大綱檢視面板

AEM Guides提供改良的「大綱檢視」面板，讓您取得檔案中使用之元素的階層檢視。

<img src="assets/select-element-content-outline-view_cs.png" alt=" 原生pdf中繼資料">

「大綱檢視」提供下列增強功能：

* 「檢視選項」下拉式清單會顯示在「大綱檢視」面板上方。 如果元素有ID、屬性和文字，您可以從下拉式清單中選取它們，以便與元素一起顯示。 可以在「大綱檢視」面板中顯示的屬性是由管理員在&#x200B;**編輯器設定**&#x200B;中設定的「顯示屬性」設定所決定。

* 您可以使用搜尋功能，依名稱、ID、文字或屬性值來搜尋元素。

如需詳細資訊，請參閱[左側面板](../user-guide/web-editor-features.md#id2051EA0M0HS)區段中的大綱檢視功能說明。

## 從網頁編輯器產生多媒體報表

AEM Guides提供為您的技術檔案產生報表的功能。  您可以使用此功能來檢視主題清單和管理檔案的中繼資料。 您現在也可以從Web編輯器的&#x200B;**報表**&#x200B;索引標籤中，檢視目前地圖的所有參考中所使用的多媒體。

您可以產生多媒體報表，其中包含目前地圖內參考中所使用多媒體的詳細資訊。 您可以彈性地篩選和排序報表中列出的多媒體檔案。
您也可以產生CSV來下載DITA map中所使用多媒體的目前快照。

<img src="assets/web-editor-reports-multimedia.png" alt="多媒體報告" width="600">

如需詳細資訊，請參閱從網頁編輯器[&#128279;](../user-guide/reports-web-editor.md)的DITA map報告中的產生多媒體報告功能說明。

## 原生PDF | 變更列以指示目錄中已變更的主題

AEM Guides現在可讓您快速識別PDF輸出目錄中的變更主題。  它會在目錄中已變更的主題左側顯示變更列。 您可以按一下目錄中的主題並檢視詳細變更。

<img src="assets/change-marker-toc.png" alt="在目錄中變更標籤 " width="500">

如需詳細資訊，請參閱[使用自訂變更列樣式](../native-pdf/change-bar-style.md)。



## 原生PDF | 設定註腳元件中頁面標籤的樣式

現在您可以在註腳中設定頁面標籤的樣式。 例如，您可以新增括弧或變更其顏色。 這些樣式可協助使用者輕鬆識別檔案中的頁面標籤。

如需詳細資訊，請參閱[在註腳中使用自訂樣式](../native-pdf/footnote-number-style.md)。

## 在網頁編輯器中開啟並播放視訊或音訊檔案

AEM Guides現在提供在網頁編輯器中開啟和播放音訊或視訊檔案的功能。 您可以變更音量或視訊檢視。 在捷徑功能表中，您也有&#x200B;**下載**、變更&#x200B;**播放速度**&#x200B;或檢視&#x200B;**子母畫面**&#x200B;的選項。

<img src="assets/video-web-editor.png" alt="播放視訊" width="600">

如需詳細資訊，請參閱[左側面板](../user-guide/web-editor-features.md#id2051EA0M0HS)區段中的「存放庫檢視」功能說明。
