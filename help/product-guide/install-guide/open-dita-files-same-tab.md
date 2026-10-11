---
title: 在同一個索引標籤中開啟DITA主題或對應檔案
description: 瞭解如何在相同標籤中開啟DITA主題或對應檔案
exl-id: 81ad2e18-3ea7-4cc1-8387-d703d1038a18
feature: Web Editor Configuration
role: Admin
level: Experienced
TQID: 'https://experienceleague.adobe.com/-QYM6xoQCkvRcpxpsWtnJb5le7-4RirhgOZk94UvzIg'
product_v2:
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
    internal-label: Experience Manager Guides
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
feature_v2:
  - id: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
    internal-label: Configuration
  - id: d90290ec-3e61-4ebd-8649-bcafe0836803
    internal-label: Reports
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
source-wordcount: '211'
ht-degree: 0%
---
# 在同一個索引標籤中開啟DITA主題或對應檔案 {#id223HI0P202H}

在某些工作流程中，當您按一下主題或地圖檔案的連結時，它會在新標籤中開啟。 這可能會導致瀏覽器中開啟許多索引標籤，進而影響您的生產力。 您可以變更在新標籤中開啟主題或地圖檔案的行為，並在目前標籤中強制開啟。 若要這麼做，請執行以下組態變更：

1. 開啟Adobe Experience Manager Web主控台設定頁面。

   存取設定頁面的預設URL為：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜尋並按一下&#x200B;**com.adobe.fmdita.xmleditor.config.XmlEditorConfig**&#x200B;套件。

1. 選取&#x200B;**在相同索引標籤**&#x200B;中開啟DITA主題/地圖選項。

1. 按一下&#x200B;**儲存**。


此設定會影響您存取主題或對應檔案的下列位置：

- 建立DITA主題\（在工作流程結束時，當您按一下&#x200B;**開啟主題**&#x200B;按鈕時\）

- 建立DITA Map \（在工作流程結束時，當您按一下&#x200B;**開啟對應**&#x200B;按鈕時\）

- DITA map主控台中的主題標籤

- DITA map主控台中的「基準線」標籤

- DITA map主控台中的「報表」索引標籤


**上層主題：**&#x200B;[&#x200B;自訂Web編輯器](conf-web-editor.md)
