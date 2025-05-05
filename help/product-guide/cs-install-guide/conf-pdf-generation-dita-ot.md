---
title: 設定單一主題PDF產生
description: 瞭解如何設定單一主題PDF的產生
exl-id: 5b66fd3b-6450-49ce-b06e-d2d5bab37990
feature: Web Editor Configuration
role: Admin
level: Experienced
source-git-commit: 0513ecac38840a4cc649758bd1180edff1f8aed1
workflow-type: tm+mt
source-wordcount: '268'
ht-degree: 0%

---

# 設定單一主題PDF產生 {#id22ADC70M0XA}

透過AEM Guides，您可以產生個別主題的PDF或整個地圖檔案。 您可以使用原生PDF或DITA-OT方法，以PDF格式發佈主題。 使用原生PDF方法，根據W3C CSS3和CSS分頁媒體標準產生功能豐富的PDF輸出。 您可以使用DITA-OT方法，從地圖圖示板為地圖產生PDF輸出。

>[!NOTE]
>
> 原生PDF是在目前版本的AEM Guides中產生PDF的預設方法。

若要在主題預覽模式中透過DITA-OT啟用舊PDF產生，請執行下列步驟：

1. 以管理員身分登入Adobe Experience Manager並下載UI設定檔。

1. 若要這麼做，請按一下頂端的Adobe Experience Manager連結，然後選擇&#x200B;**工具**。
1. 從工具清單中選取&#x200B;**指南**，然後按一下&#x200B;**資料夾設定檔**。
1. 按一下&#x200B;**全域設定檔**&#x200B;圖磚。
1. 選取&#x200B;**XML編輯器設定**&#x200B;索引標籤，然後按一下頂端的&#x200B;**編輯**&#x200B;圖示
1. 按一下「**下載**」圖示，在本機系統上下載ui\_config.json檔案。 您可以接著對檔案進行變更，然後上傳相同的檔案。
1. 在`ui_config.json`檔案中，尋找下列組態：

   ```
   {
                           "component": "button",
                           "variant": "action",
                           "quiet": true,
                           "icon": "filePDF",
                           "title": "Download as PDF",
                           "on-click": "EDITOR_SAVE_AS_PDF"
                           }
   ```

   並將其取代為

   ```
   {
                           "component": "button",
                           "icon": "filePDF",
                           "variant": "action",
                           "quiet": true, "title": "Export as PDF",
                           "on-click": "DOWNLOAD_TOPIC_PDF",
                           "show" : ["@isPreviewMode", "@isXmlMode"]
                           }
   ```

1. 儲存檔案並上傳。

執行上述指定步驟後，如果您從「網頁編輯器」的「使用者偏好設定」中選擇相同的資料夾設定檔，您會在主題的預覽模式中看到產生PDF的選項。

**上層主題：**&#x200B;[&#x200B;自訂Web編輯器](conf-web-editor.md)
