---
title: 在網頁編輯器中設定翻譯功能
description: 瞭解如何在網頁編輯器中設定翻譯功能
exl-id: e25473c3-9a84-4658-87c9-6fd72bcaa2b6
feature: Web Editor Configuration
role: Admin
level: Experienced
TQID: https://experienceleague.adobe.com/7-SFQ0FXQ6bGo3pjAOK-18sEsU4-zriruioG2nMx2o0
product_v2: id: fae5e35a-80c9-4b94-9352-1a060a6aab1did: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
subfeature_v2: id: b0521e56-a0b2-40b6-bf47-ebc98751f9baid: b1ef4d86-3917-4b76-a0bc-4a4771f9b3b0
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 154
ht-degree: 0%

---

# 在網頁編輯器中設定翻譯功能 {#id21BONI0J0YR}

網頁編輯器提供強大的翻譯功能，可將您的內容翻譯成多種語言。

您可以使用網頁編輯器中的&#x200B;**管理**&#x200B;索引標籤來翻譯您的內容。 此標籤預設為可用。

若要隱藏網頁編輯器中的&#x200B;**管理**&#x200B;標籤，請執行下列步驟：

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

**上層主題：**[&#x200B;自訂Web編輯器](conf-web-editor.md)
