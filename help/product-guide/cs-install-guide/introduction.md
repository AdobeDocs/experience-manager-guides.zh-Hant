---
title: 關於本指南
description: 瞭解本指南
exl-id: cdd40267-3f0c-40d2-acbc-2ebe43633c2f
feature: Introduction
role: Admin
level: Experienced
source-git-commit: 0513ecac38840a4cc649758bd1180edff1f8aed1
workflow-type: tm+mt
source-wordcount: '663'
ht-degree: 2%

---

# 關於本指南 {#id175MC0P0S5Z}

Adobe Experience Manager Guides \(後來稱為&#x200B;*AEM Guides*\)是功能強大、以雲端為基礎的企業級元件內容管理解決方案\(CCMS\)。 如此可啟用Adobe Experience Manager中的原生DITA支援，使AEM能夠處理以DITA為主的內容建立和傳遞。 它可讓作者使用簡單易用的內建網頁編輯器建立內容，並發佈成各種輸出格式。

本指南提供下載、安裝和設定AEM Guides的說明。 在本指南中，您將找到根據組織製作和發佈需求設定AEM Guides的詳細指示。

本指南適用於下列型別的對象：

- 負責安裝和管理AEM Guides的管理員。

- 發佈者，會執行發佈工作以產生多種格式的輸出。


## 內容結構

本指南中的資訊的組織方式如下：

- [關於本指南](#id175MC0P0S5Z)：本主題介紹本指南、目標對象，以及本指南中資訊的編排方式。

- [下載並安裝](download-install.md#)：本主題說明如何下載、安裝或升級AEM Guides。

- [使用者管理與安全性](user-admin-sec.md#)：本主題說明AEM中使用者和驗證的核心概念，以及AEM Guides建立的預設使用者群組。

- [使用自訂DITA-OT與DITA專業化](dita-ot-specialization.md#)：此主題說明如何設定自訂DITA-OT外掛程式及使用DITA專業化。

- [設定檔案狀態](customize-doc-state.md#)：此主題說明如何設定DITA檔案的自訂狀態。

- [移轉現有內容](migrate-content.md#)：本主題說明如何在AEM存放庫中內建現有內容。

- [設定檔案名稱](conf-file-names.md#)：本主題說明如何設定設定，以自動指派檔案名稱並定義有效檔案名稱字元的Regex。

- [設定主題與對應範本](conf-template-tags.md#)：此主題說明如何設定主題與對應範本，以符合您的編寫需求。 瞭解AEM中的標籤系統，以及如何設定標籤以搭配AEM Guides使用。

- [自訂網頁編輯器](conf-web-editor.md#)：此主題說明您可以在網頁編輯器中進行的各種自訂，以增強其功能。

- [依預設包含@navtitle屬性](auto-add-navtitle.md#)：此主題說明如何依預設將`@navtitle`屬性新增至對應中的參考檔案。

- [設定全域或資料夾層級的設定檔](conf-folder-level.md#)：此主題說明建立資料夾設定檔及授予特定使用者許可權的程式。

- [版本管理](version-management.md#)：本主題說明如何為開啟以在Web編輯器中編輯的檔案設定自動檔案簽出。

- [設定輸出產生設定](conf-output-generation.md#)：此主題說明您可以進行哪些設定，以自訂預設輸出產生程式。

- [設定和自訂工作流程](customize-workflows.md#)：本主題說明各種設定，以自訂AEM Guides中隨附的預設工作流程。

- [翻譯內容](translation.md#)：此主題提供AEM檔案中相關說明文章的連結，以協助您瞭解及設定翻譯架構。 此外，瞭解如何啟用元件式翻譯工作流程。

- [設定AEM Assets UI的搜尋](conf-dita-search.md#)：本主題說明如何在Assets UI中設定DITA內容搜尋，以及在搜尋中新增自訂屬性。


## Adobe Experience Manager概觀\(AEM\)

[Adobe Experience Manager \(AEM\)](https://business.adobe.com/products/experience-manager/adobe-experience-manager.html)是用於建置網站、行動應用程式和表單的全方位內容管理解決方案。 AEM可協助您管理行銷內容和資產。 AEM可as a Cloud Service使用。 AEM as a Cloud Service結合AEM內容管理系統的強大功能與AEM數位資產管理，協助您為客戶提供內容導向的個人化體驗。以下是一些可幫助您開始使用並部署至AEM as a Cloud Service的關鍵資源：

- [Experience Manageras a Cloud Service概述](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/home.html?lang=zh-Hant)
- [開始移轉至AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/getting-started.html?lang=zh-Hant)
- [開始上線Experience Manageras a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/home.html?lang=zh-Hanthttps://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/home.html?lang=en)
- [為 AEM as a Cloud Service 實作應用程式](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/home.html?lang=zh-Hant)
- [部署至 AEM as a Cloud Service ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/deploying/overview.html?lang=zh-Hant)
- [Assetsas a Cloud Service指南](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/home.html?lang=tw)

## 其他資源

以下是AEM Guides其他實用資源的清單，這些資源可在[學習與支援](https://helpx.adobe.com/tw/support/xml-documentation-for-experience-manager.html)頁面上取得：

- 使用手冊
- API參考指南
