---
title: 設定關閉時儲存為新版本的提示
description: 瞭解如何設定關閉時儲存為新版本的提示
exl-id: 1b8c3eaa-a654-4563-9541-18a59b7d306c
feature: Web Editor Configuration
role: Admin
level: Experienced
TQID: https://experienceleague.adobe.com/VdnwN--C-0kLd-vo5RDFLNXNBKzU7wofWZJsvPuVGAA
product_v2: id: fae5e35a-80c9-4b94-9352-1a060a6aab1did: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
subfeature_v2: id: b0521e56-a0b2-40b6-bf47-ebc98751f9ba
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 213
ht-degree: 0%

---

# 設定關閉時儲存為新版本的提示 {#id222HBI00XXA}

當使用者嘗試使用檔案索引標籤上的&#x200B;**關閉**&#x200B;按鈕或[選項]功能表中的&#x200B;**關閉**&#x200B;選項關閉在Web編輯器中開啟的檔案時，如果檔案有未儲存的資料或未儲存的版本，就會出現一個對話方塊。 如果未儲存版本，則會提示使用者將檔案另存為新版本。

預設不會啟用&#x200B;**另存為新版本**&#x200B;核取方塊，您必須從configMgr啟用此專案。 執行以下步驟，在Web編輯器中啟用預設選項：

1. 開啟Adobe Experience Manager Web主控台設定頁面。

   存取設定頁面的預設URL為：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜尋並按一下&#x200B;**com.adobe.fmdita.xmleditor.config.XmlEditorConfig**&#x200B;套件。

1. 選取&#x200B;**關閉**&#x200B;時詢問新版本選項。

1. 按一下&#x200B;**儲存**。


選取此選項時，預設會在對話方塊中選取&#x200B;**另存為新版本**&#x200B;核取方塊。

如需詳細資訊，請參閱「使用Adobe Experience Manager Guides as a Cloud Service」指南中的&#x200B;*檔案關閉和儲存案例*&#x200B;一節。

**上層主題：**[&#x200B;自訂Web編輯器](conf-web-editor.md)
