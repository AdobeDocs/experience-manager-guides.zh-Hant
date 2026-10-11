---
title: 設定標籤檢視的預設值
description: 瞭解如何設定標籤檢視的預設值
feature: Web Editor Configuration
role: Admin
level: Experienced
exl-id: d54e3a3c-9f61-43cf-a925-12e4ce948a55
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
source-wordcount: '210'
ht-degree: 0%
---
# 設定標籤檢視的預設值 {#id223GN0M0NDC}

AEM Guides可讓您在編輯器中設定「標籤檢視」的預設狀態，協助您為新使用者的工作階段預設開啟或關閉「標籤檢視」。執行以下步驟來設定「標籤檢視」的預設值：

1. 以管理員身分登入Adobe Experience Manager以下載UI設定檔。
1. 按一下頂端的Adobe Experience Manager連結，然後選擇&#x200B;**工具**。
1. 從工具清單中選取&#x200B;**指南**，然後按一下&#x200B;**資料夾設定檔**。
1. 按一下&#x200B;**全域設定檔**&#x200B;圖磚。
1. 選取&#x200B;**XML編輯器設定**&#x200B;索引標籤，然後按一下頂端的&#x200B;**編輯**&#x200B;圖示。
1. 在&#x200B;**XML編輯器UI組態**&#x200B;區段中，按一下&#x200B;**下載**&#x200B;圖示以在本機系統上下載`ui_config.json`檔案。
1. 在`ui_config.json`檔案中，變更defaultValues區段來變更預設標籤檢視狀態，如下所示：

   ```
   "defaultValues":
               {
               "tagsView": true
               }
   ```

1. 儲存檔案並上傳。

>[!NOTE]
>
> 使用者在編輯器中啟用/停用標籤檢視的偏好設定優先於此預設值。 因此，如果使用者從編輯器啟用標籤檢視，則即使跨工作階段，該檢視也會保持啟用狀態。

**父級主題：**[&#x200B;自訂編輯器](customize-overview.md)
