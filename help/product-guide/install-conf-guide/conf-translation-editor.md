---
title: 在編輯器中設定翻譯功能
description: 瞭解如何在編輯器中設定翻譯功能
feature: Web Editor Configuration
role: Admin
level: Experienced
exl-id: 22d7e1c7-2059-43fb-b7aa-3ae4a6072678
source-git-commit: cc73b81787a3c3dbe8390d93e558064327e59965
workflow-type: tm+mt
source-wordcount: '150'
ht-degree: 0%

---

# 在用於Cloud Service的編輯器中設定翻譯功能

編輯器提供強大的翻譯功能，可將您的內容翻譯成多種語言。

您可以使用編輯器中的&#x200B;**管理**&#x200B;索引標籤來翻譯您的內容。 此標籤預設為可用。

若要隱藏編輯器中的&#x200B;**管理**&#x200B;標籤，請執行下列步驟：

1. 以系統管理員身分登入&#x200B;**Adobe Experience Manager**。
1. 按一下頂端的&#x200B;**Adobe Experience Manager**&#x200B;連結，然後選擇&#x200B;**工具**。
1. 從工具清單中選取&#x200B;**指南**，然後按一下&#x200B;**資料夾設定檔**。
1. 按一下&#x200B;**全域設定檔**&#x200B;圖磚。
1. 按一下&#x200B;**XML編輯器組態**。
1. 按一下頂端的&#x200B;**編輯**&#x200B;圖示。
1. 下載`ui\_config.json`檔案。從下載的檔案中移除下列程式碼片段：

   ```json
   {
       "component":"tab",
       "id":"workflow",
       "title":"Manage",
       "on-click":"APP_MODE_CHANGE",
       "items":
       [
           {
               "component":"label",
               "label":"Manage"
           }
       ]
   },
   ```

1. 上傳更新的ui\_config.json檔案。

請注意，**管理**&#x200B;篩選器已無法使用。

**父級主題：**&#x200B;[&#x200B;自訂編輯器](customize-overview.md)
