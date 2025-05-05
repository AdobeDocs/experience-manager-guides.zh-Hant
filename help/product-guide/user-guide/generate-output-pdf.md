---
title: PDF預設集型別
description: 瞭解您可以使用Adobe Experience Manager Guides建立的PDF預設集型別。
exl-id: f12c91fd-3f95-478e-a9cd-68d037206ee8
feature: Publishing
role: User
source-git-commit: 558cc1a724a483353eb5d912354e1ab37dab348a
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 0%

---

# PDF輸出預設集概述 {#id205BE600HAH}

透過Experience Manager Guides，您可以建立PDF預設集，以產生個別主題的PDF或整個地圖檔案。 您可以使用下列三種方法之一，以PDF格式發佈您的內容：

**DITA-OT**

使用此方法，從「地圖」主控台或「地圖」控制面板產生地圖的PDF輸出。 您可以針對在「地圖」主控台或「地圖」控制面板中開啟的地圖，建立輸出預設集，在產生PDF之前設定發佈屬性。

如需使用DITA-OT方法建立PDF輸出預設集的詳細資訊，請檢視[建立DITA-OT PDF輸出預設集](./generate-output-pdf-dita-ot.md)

**FrameMaker Publishing Server (FMPS)**

>[!NOTE]
>
> FMPS發佈選項僅適用於Map儀表板。

使用此方法可產生PDF輸出，不僅來自DITA內容，也來自AEM存放庫中可用的FrameMaker檔案(.book和.fm)。 您可透過設定輸出預設集來建立PDF，並使用FrameMaker Publishing Server (FMPS)發佈。 您可以針對PDF和其他格式設計並設定輸出的外觀，並將相同的外觀儲存在設定檔案(.sts)中。 然後FMPS會使用此設定檔案來產生DITA map或.book檔案的輸出。 若要建立或編輯輸出預設集，請檢視[瞭解輸出預設集](../user-guide/generate-output-understand-presets.md)。

如需設定FMPS的詳細資訊，請檢視[從FrameMaker檔案產生輸出](../user-guide/fm-output-generatation.md)。

**原生PDF**

此方法可根據W3C CSS3和CSS分頁媒體標準產生功能豐富的PDF輸出。 透過原生PDF發佈，您可以使用範本來設定內容的版面和樣式，並套用各種設定以微調PDF。 此外，您可以使用範本編輯器修改和建立自己的範本。

如需建立原生PDF預設集的詳細資訊，請檢視[建立原生PDF輸出預設集](../web-editor/native-pdf-web-editor.md)。





**父級主題：**&#x200B;[&#x200B;瞭解輸出預設集](generate-output-understand-presets.md)
