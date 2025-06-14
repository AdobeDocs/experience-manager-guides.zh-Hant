---
title: 建立和自訂原生PDF範本
description: 瞭解如何建立及自訂原生PDF範本。
exl-id: 7660da8e-8a1e-4493-b99b-9b5de9a7483f
feature: Output Generation
role: Admin
level: Experienced
source-git-commit: a6c87e6f9a68962488e70985a0513dcb05eaa9cd
workflow-type: tm+mt
source-wordcount: '1151'
ht-degree: 0%

---

# PDF範本 {#PDF-template}

使用範本可確保內容版面配置與結構的一致性。 由於範本是預先定義的，您可以避免重新處理每個新專案或更新中出現的格式問題。 範本可讓您設計頁面配置、樣式內容，以及套用各種設定來自訂PDF。

## 工廠和自訂PDF範本

有些工廠範本是現成可用的範例，開發人員可將其當作基礎範本，根據組織需求建立自訂範本。



## 建立新的PDF範本 {#create-pdf-template}

您可以使用樣式表來建立具有特定頁面配置的自訂PDF範本，並定義頁面配置元件（例如TOC、索引、字彙表）或DITA元件（例如標題、段落、清單）的格式。

若要建立新的PDF範本，請執行下列步驟：

1. 在Web編輯器中，移至&#x200B;**輸出**&#x200B;標籤。
1. 選取&#x200B;**範本** 左側面板中的<img src="./assets/template.png" alt= "範本圖示" width="25">。

   <img src="assets/create-pdf-template.png" alt="建立PDF範本" width="400">

1. 在&#x200B;**範本**&#x200B;視窗中，選取&#x200B;**範本**&#x200B;旁的&#x200B;**+**&#x200B;圖示，並選擇&#x200B;**PDF範本**。
1. 在&#x200B;**新增PDF範本**&#x200B;對話方塊中，選取要用來作為建立自訂範本基礎的工廠範本。 您也可以使用搜尋方塊來搜尋範本。
1. 指定範本的標題。

   >[!NOTE]
   >
   >  您也可以在建立和複製範本時預覽範本的縮圖。 建立範本後，使用&#x200B;**選項**&#x200B;功能表中的&#x200B;[**屬性**](#properties-option)&#x200B;編輯或刪除縮圖。

1. 按一下&#x200B;**建立**。

   新範本已建立並新增到&#x200B;**範本**&#x200B;面板中。

## 複製PDF範本 {#duplicate-pdf-template}

如果要建立與現有範本具有相同頁面配置及格式的新範本，您可以建立副本。 複製範本後，您可以視需要進一步自訂其元件。

若要複製現有PDF範本，請遵循下列步驟：

1. 在Web編輯器中，移至&#x200B;**輸出**&#x200B;標籤。
1. 選取&#x200B;**範本** 左側面板中的<img src="./assets/template.svg" alt= "範本圖示" width="25">。 這會開啟&#x200B;**範本**&#x200B;視窗。
1. 將滑鼠停留在您要複製的範本上，並選取&#x200B;**...** *選項*&#x200B;圖示，然後從內容功能表中選擇&#x200B;**複製**。

   這會開啟&#x200B;**重複PDF範本**&#x200B;對話方塊。

   <img src="assets/duplicate-template.png" alt="複製PDF範本" width="350">

   *在&#x200B;**複製PDF範本**&#x200B;對話方塊中選取要複製的範本、預覽縮圖，以及更新標題。*

1. 指定範本的標題。

   **Title**&#x200B;欄位已預先填入為與來源範本相同標題的副本。 如果具有相同標題的範本存在，您將會檢視錯誤訊息。



1. 若要指定偏好的標題，請移除預先填入的標題並指定標題。
1. 按一下&#x200B;**複製**。

   在&#x200B;**範本**&#x200B;下已建立並新增重複的範本。

## 範本上的其他作業

您也可以從&#x200B;**選項**&#x200B;功能表對範本執行下列操作：

<img src="assets/PDF-template-options.png" alt="複製PDF範本" width="350">

### 刪除

選取「刪除」選項，刪除選取的範本。 然後，在確認提示中選取「是」。
預設集已從&#x200B;**範本**&#x200B;中移除。

### 屬性{#properties-option}

選取此選項可檢視和編輯範本的屬性。 您可以預覽範本的現有縮圖。 您也可以編輯或刪除縮圖。 您也可以變更範本的標題和說明。

### 在Assets UI中檢視

選取此選項即可在Assets UI中檢視範本。 開啟範本的根位置時，您可以檢視範本的所有資源。

建立自訂範本後，您可以從PDF輸出預設集的「頁面配置」中選擇它。

瞭解如何[發佈PDF輸出](https://experienceleague.adobe.com/docs/experience-manager-guides-learn/tutorials/user-guide/output-gen/web-editor/native-pdf-web-editor.html?lang=zh-Hant)。

>[!NOTE]
>
>如果您的資料夾上設定了「資料夾設定檔」，則您將只會檢視在「資料夾設定檔」上設定的PDF範本。

根據您的設定，您的管理員可以設定範本：

+++ 雲端服務

如需設定全域和資料夾層級設定檔的詳細資訊，請檢視Cloud Service安裝與設定指南中的[設定範本](../cs-install-guide/conf-folder-level.md#id1889D0IL0Y4)區段。

+++

+++ 內部部署軟體

如需設定全域和資料夾層級設定檔的詳細資訊，請檢視On-premise Installation and Configuration Guide中的[Configure authoring templates](../install-guide/conf-folder-level.md#create-custom-authoring-template-id1917d0eg0hj)區段。

+++

## 自訂PDF範本 {#customize-pdf-template}

您可以調整範本元件並使用樣式表套用樣式格式來自訂範本。

若要自訂PDF範本，請執行下列步驟：

1. 在Web編輯器中，移至&#x200B;**輸出**&#x200B;標籤。
1. 展開左側邊欄並選取&#x200B;**範本**。

   這會開啟&#x200B;**範本**&#x200B;面板。

1. 若要檢視範本的元件，請執行下列任一項作業：

   * 選取範本旁的>圖示，或按兩下範本名稱。
   * 將滑鼠停留在任何範本上並選取…… （**選項**&#x200B;圖示），然後從內容功能表中選擇&#x200B;**編輯**。

   依照預設，這會開啟範本編輯器中的&#x200B;**設定**&#x200B;面板。

   <img src="assets/customize-pdf-template.png" alt="自訂PDFTeamplte" width="350">

   >[!NOTE]
   >
   >  您的管理員可以從以下路徑下載最新的範本並取代現有的範本：
   >
   > `/libs/fmdita/pdf`

   您可以自訂的各種範本元件分為以下幾節：

   * 頁面配置：典型的PDF包含不同的頁面，例如封面或標題頁面、目錄、章節、索引、引文等。 「頁面配置」區段可讓您設計構成PDF之不同頁面的外觀。 如需詳細資訊，請檢視[頁面配置](../native-pdf/components-pdf-template.md#page-layouts)。

     除了外觀之外，您還可以定義頁面元素（例如頁首、頁尾和頁面上的內容區域）的排列。 若要進一步瞭解自訂頁面的版面，請參閱[建立及自訂頁面版面](components-pdf-template.md#create-customize-page-layout)。

   * 樣式表：「樣式表」區段中的設定可讓您自訂頁面配置元件如目錄、索引、字彙表、引文等的外觀和風格。 此外，您也可以自訂DITA內容的樣式，例如標題、段落、清單等。 若要進一步瞭解如何使用樣式表，請參閱[使用樣式表來自訂PDF](components-pdf-template.md#stylesheet-customization)。
   * 資源：儲存自訂或設計PDF範本所需的資產檔案。 Assets （例如，標誌、自訂字型、背景影像等）會儲存在「資源」中。
您也可以使用存在於存放庫中任何其他位置的資源。 您不需要為每個範本建立重複資源，您可以將它們儲存在共用資料夾中，並在所有原生PDF範本中使用它們。

     若要進一步瞭解如何利用資源，請參閱[使用資源](components-pdf-template.md#work-with-resources)。

   * 設定：設定輸出設定，以使用範本產生PDF。 本節可讓您為PDF中的各種頁面、章節開始頁面、列印標籤、引文等定義範本對應。

   您也可以排列它們在最終PDF輸出中的顯示順序。
如需套用設定的詳細資訊，請參閱[進階PDF設定](components-pdf-template.md#advanced-pdf-settings)。


1. 若要自訂範本元件，請連按兩下範本元件或選取其前的>圖示。

   例如，按兩下&#x200B;*頁面配置*&#x200B;或選取&#x200B;*頁面配置*&#x200B;前的&#x200B;*>*&#x200B;圖示以檢視可用的頁面配置。

   >[!NOTE]
   >
   >您也可以使用&#x200B;**選項**&#x200B;功能表中的&#x200B;[**屬性**](#properties-option)，更新範本的縮圖和說明。

1. 完成所需的變更後，請選取&#x200B;*儲存全部* （或`Ctrl+S`）。
