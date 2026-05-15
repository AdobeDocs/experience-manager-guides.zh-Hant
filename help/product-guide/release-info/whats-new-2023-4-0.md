---
title: 發行說明 | Adobe Experience Manager Guides as a Cloud Service，2023年4月發行版本
description: 2023年4月發行的Adobe Experience Manager Guides as a Cloud Service
exl-id: 269e3a13-584d-4cff-a18a-d4fa89646a5a
feature: Release Notes
role: Leader
TQID: https://experienceleague.adobe.com/c1aOcwHgxAs11yAalOnlW-ghsTP1Or32TnBwLsc59-M
product_v2: id: fae5e35a-80c9-4b94-9352-1a060a6aab1did: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: a3bd6397-2eb2-4908-a61c-226e26855dca
subfeature_v2: id: d6596f3f-92a7-43ec-b444-237db6adad05
role_v2: id: f8a45b24-4be7-4f1b-909b-60d06b483a20
topic_v2: id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 386
ht-degree: 0%

---

# 2023年4月發行的Adobe Experience Manager Guides as a Cloud Service的新增功能

本文介紹2023年4月版Adobe Experience Manager Guides （以後稱為&#x200B;*AEM Guides as a Cloud Service*）中的新功能和增強功能。

如需有關升級指示、相容性矩陣，以及此版本中修正問題的詳細資訊，請參閱[發行說明](release-notes-2023-4-0.md)文章。

## PDF發佈中的進階中繼資料支援

AEM Guides現在為對應至PDF輸出中中繼資料的中繼資料提供進階支援。 中繼資料選項包括有關檔案及其內容的資訊，例如作者姓名、檔案標題、關鍵字、版權資訊和其他資料欄位。

<img src="assets/pdf-metadata.png" alt=" 原生pdf中繼資料">

您可以匯入XMP檔案，而AEM Guides可以從該檔案中挑選資訊。 您也可以選擇使用下拉式清單提供中繼資料名稱和值。 您也可以直接在名稱欄位中輸入內容，以新增自訂中繼資料。


## 增強型大綱檢視面板

AEM Guides提供改良的「大綱檢視」面板，讓您取得檔案中使用之元素的階層檢視。

<img src="assets/select-element-content-outline-view_cs.png" alt=" 原生pdf中繼資料">

「大綱檢視」提供下列增強功能：

* 「檢視選項」下拉式清單會顯示在「大綱檢視」面板上方。 如果元素有ID、屬性和文字，您可以從下拉式清單中選取它們，以便與元素一起顯示。 可以在「大綱檢視」面板中顯示的屬性是由管理員在&#x200B;**編輯器設定**&#x200B;中設定的「顯示屬性」設定所決定。

* 您可以使用搜尋功能，依名稱、ID、文字或屬性值來搜尋元素。


## AEM Guides as a Cloud Service的微服務式發佈

AEM Guides as a Cloud Service提供的功能，可讓您透過以微服務為基礎的發佈同時執行大型發佈工作負載，並利用業界領先的Adobe I/O Runtime無伺服器平台。

現在在4月版本中，您可以使用微服務型原生PDF發佈同時執行多個發佈要求，並非常有效率地產生大量PDF輸出。
如需詳細資訊，請參閱[為AEM Guides as a Cloud Service設定新的微服務式發佈](../knowledge-base/publishing/configure-microservices.md)。
