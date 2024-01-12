---
title: 設定標籤檢視的預設值
description: 瞭解如何設定標籤檢視的預設值
exl-id: 52214459-74b8-47ec-982b-6176145348a8
feature: Web Editor Configuration
role: Admin
level: Experienced
source-git-commit: 0513ecac38840a4cc649758bd1180edff1f8aed1
workflow-type: tm+mt
source-wordcount: '214'
ht-degree: 0%

---

# 設定標籤檢視的預設值 {#id223GN0M0NDC}

AEM Guides可讓您設定「網頁編輯器」中「標籤檢視」的預設狀態，協助您為新使用者的工作階段將「標籤檢視」預設為開啟或關閉。執行以下步驟來設定「標籤檢視」的預設值：

1. 以管理員身分登入Adobe Experience Manager以下載UI設定檔。
1. 按一下頂端的Adobe Experience Manager連結，然後選擇 **工具**.
1. 選取 **指南** 從工具清單中，按一下 **資料夾設定檔**.
1. 按一下 **全域設定檔** 圖磚。
1. 選取 **XML編輯器設定** 標籤並按一下 **編輯** 圖示在頂端。
1. 在 **XML編輯器UI設定** 區段，按一下 **下載** 圖示以下載 `ui_config.json` 檔案。
1. 在 `ui_config.json` 檔案中，變更defaultValues區段來變更預設標籤檢視狀態，如下所示：

   ```json
   "defaultValues":
                   {
                   "tagsView": true
                   }
   ```

1. 儲存檔案並上傳。

>[!NOTE]
>
> 使用者在網頁編輯器中啟用/停用標籤檢視的偏好設定優先於此預設值。 因此，如果使用者從網頁編輯器啟用「標籤檢視」，即使跨工作階段，該檢視也會保持啟用狀態。

**父級主題：**[&#x200B;自訂Web編輯器](conf-web-editor.md)
