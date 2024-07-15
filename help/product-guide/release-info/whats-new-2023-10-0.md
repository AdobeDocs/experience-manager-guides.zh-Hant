---
title: 發行說明 | 2023年10月發行的Adobe Experience Manager Guides新增功能
description: 瞭解2023年10月發行的Adobe Experience Manager Guidesas a Cloud Service中的新功能和增強功能。
exl-id: 41bfed0d-5901-4ada-b6d7-a5be93b25ba8
feature: What's New
role: Leader
source-git-commit: 6d8c01f20f7b59fed92c404561b647d9ebecb050
workflow-type: tm+mt
source-wordcount: '623'
ht-degree: 0%

---

# 2023年10月發行的Adobe Experience Manager Guides as a Cloud Service的新增功能

本文介紹2023年10月版Adobe Experience Manager Guides (後來稱為&#x200B;*AEM Guidesas a Cloud Service*)中的新功能和增強功能。

如需有關升級指示、相容性矩陣，以及此版本中修正問題的詳細資訊，請參閱[發行說明](release-notes-2023-10-0.md)。


## 從使用者介面設定資料來源聯結器

Experience Manager Guides現在提供&#x200B;**資料來源**&#x200B;工具，可協助您設定資料來源的現成聯結器。 您可以輕鬆建立JIRA、SQL (MySQL、PostgreSQL、Microsoft SQL Server、SQLite、MariaDB、H2DB)、AdobeCommerce和Elasticsearch資料庫的聯結器。

您也可以輕鬆編輯、重新連線、複製或刪除資料來源聯結器。 瞭解如何[從使用者介面](../cs-install-guide/conf-data-source-connector-tools.md)輕鬆設定資料來源聯結器。

![資料來源聯結器列在資料來源面板](assets/data-sources-create-window.png){width="550" align="left"}中

*從資料來源面板建立並檢視資料來源聯結器。*

## 檢視主題產生器的記錄

您現在也可以檢視內容產生記錄檔。 此記錄檔可協助您檢查警告、錯誤和例外。  深入瞭解主題產生器的[選項](../user-guide/web-editor-content-snippet.md#options-for-a-topic-generator)如何協助您輕鬆產生和管理主題產生器。

## 支援資料來源範本中的Velocity工具

您現在可以在Experience Manager Guides範本中使用Velocity工具。 這些工具可協助您將各種功能套用至從資料來源擷取的資料。 建立內容片段或主題時，您可以使用範本。 此功能可協助您節省時間和精力，以手動方式將相同的函式套用至每個資料集。  這樣還可以確保獲得準確的結果。
例如，您可以使用$mathTool來執行數學函式。
進一步瞭解如何在資料來源範本中[使用Velocity工具](../user-guide/web-editor-content-snippet.md#use-velocity-tools)。


## 原生PDF增強功能

下列原生PDF增強功能已在2023年10月版本中完成：

### 重設版面第一頁的頁碼

在原生PDF輸出中，您可以重新啟動頁碼並指定開始編號的編號。 現在，您也只能對第一次出現的截面開始編號。
深入瞭解如何[使用頁面配置](../native-pdf/design-page-layout.md#page-props-page-layout)的頁面屬性。


### 在目錄中檢視沒有自動編號的章節

Experience Manager Guides會在目錄(TOC)中顯示章節編號以及章節名稱。 現在您可以選擇只發佈章節名稱，而不發佈章節編號。 檢視有關如何設定範本](../native-pdf/components-pdf-template.md#advanced-pdf-settings)的[進階PDF設定的詳細資訊。

## 從網頁編輯器下載地圖

現在，您不僅可以在網頁編輯器的地圖檢視中編輯地圖，也可以下載地圖。 您可以選擇使用特定基準下載地圖。 您也可以選擇將階層平面化，並將所有檔案和資料夾儲存在單一資料夾中。

如需詳細資訊，請參閱[左側面板](../user-guide/web-editor-features.md#id2051EA0M0HS)區段中的&#x200B;**地圖檢視**&#x200B;功能說明。

存放庫檢視中檔案的![選項功能表](assets/options-menu-repo-view-file-level-2310.png){width="550" align="left"}

*在存放庫檢視中選取檔案，然後選擇在檔案上執行動作的選項。*

## 在氧氣聯結器外掛程式中編輯檔案

Experience Manager Guides現在可讓您在網頁編輯器中選取檔案，然後選擇在氧氣聯結器外掛程式中編輯檔案。 這個選項並未啟用為現成支援的一部分。

如需詳細資訊，請參閱[左側面板](../user-guide/web-editor-features.md#id2051EA0M0HS)區段中的檔案&#x200B;**功能說明的**&#x200B;選項。
