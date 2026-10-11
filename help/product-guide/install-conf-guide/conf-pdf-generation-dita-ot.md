---
title: 設定單一主題PDF產生
description: 瞭解如何設定產生單一主題PDF
feature: Web Editor Configuration
role: Admin
level: Experienced
exl-id: a456027a-56a4-48c0-a79b-2f423692abc2
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
    internal-label: Experience Manager Guides
feature_v2:
  - id: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
    internal-label: Configuration
subfeature_v2:
  - id: b0521e56-a0b2-40b6-bf47-ebc98751f9ba
    internal-label: Web Editor configuration
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 81a0e7f0736ba4970673dd87a888a4c60d3c1b4e
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 0%
---
# 為Cloud Service設定單一主題PDF產生方式

透過AEM Guides，您可以產生個別主題的PDF或整個地圖檔案。 您可以使用原生PDF或DITA-OT方法，以PDF格式發佈主題。 使用原生PDF方法，根據W3C CSS3和CSS分頁媒體標準產生功能豐富的PDF輸出。 您可以使用DITA-OT方法，從地圖儀表板為地圖產生PDF輸出。

>[!NOTE]
>
> 原生PDF是在目前版本的AEM Guides中產生PDF的預設方法。

若要在主題預覽模式中透過DITA-OT啟用舊版PDF產生，請執行以下步驟：

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

執行上述指定步驟後，如果您從編輯器的「使用者偏好設定」中選擇相同的資料夾設定檔，您將在主題的預覽模式中看到PDF產生的選項。

**父級主題：**&#x200B;[&#x200B;自訂編輯器](customize-overview.md)
