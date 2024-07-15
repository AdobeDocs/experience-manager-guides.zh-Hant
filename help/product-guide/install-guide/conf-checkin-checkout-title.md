---
title: 設定簽入和簽出圖示的標題
description: 瞭解如何設定簽入和簽出圖示的標題
exl-id: a8888a17-e819-4fa2-bb6f-cafe1002803a
feature: Web Editor Configuration
role: Admin
level: Experienced
source-git-commit: 0513ecac38840a4cc649758bd1180edff1f8aed1
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 0%

---

# 設定簽入和簽出圖示的標題

AEM Guides可讓您在網頁編輯器中設定簽入和簽出圖示的標題。 執行以下步驟來設定「入庫」和「出庫」圖示的標題：

1. 以管理員身分登入Adobe Experience Manager以下載UI設定檔。
1. 按一下頂端的Adobe Experience Manager連結，然後選擇&#x200B;**工具**。
1. 從工具清單中選取&#x200B;**指南**，然後按一下&#x200B;**資料夾設定檔**。
1. 按一下&#x200B;**全域設定檔**&#x200B;圖磚。
1. 選取&#x200B;**XML編輯器設定**&#x200B;索引標籤，然後按一下頂端的&#x200B;**編輯**&#x200B;圖示。
1. 在&#x200B;**XML編輯器UI組態**&#x200B;區段中，按一下&#x200B;**下載**&#x200B;圖示以在本機系統上下載`ui_config.json`檔案。
1. 在`ui_config.json`檔案中，變更「頂端列」區段中的標題。 您可以變更下列值：

   ```json
   //Change title to "Check out" instead of "Lock"
           "title": "Check out"
   
   //Change title to "Check in" instead of "@checkOutBy
            "title": "Check in"
   ```

1. 儲存檔案並上傳。
