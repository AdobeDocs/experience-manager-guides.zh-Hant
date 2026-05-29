---
title: 設定雲端服務的資產處理作業
description: 瞭解如何設定雲端服務的資產處理
feature: Output Generation
role: Admin
level: Experienced
exl-id: 0b66a515-d8f1-4ea6-913f-e152ae114698
source-git-commit: 5af3356dff3c42b8a93ed97b5ee20b23976769a4
workflow-type: tm+mt
source-wordcount: '121'
ht-degree: 3%

---

# 設定資產處理功能

下列標籤提供根據Experience Manager Guides設定來設定資產處理功能的指示： Cloud Service或內部部署。

>[!BEGINTABS]

>[!TAB Cloud Service]

1. 使用[組態覆寫](download-install-config-override.md)中提供的指示來建立組態檔。

1. 在設定檔案中，提供下列（屬性）詳細資訊：

   | PID | 屬性索引鍵 | 屬性值 |
   |---|---|---|
   | `com.adobe.fmdita.config.ConfigManager` | `enable.asset.processing.scheduler` | **預設值：** &quot;true&quot; |

>[!TAB 內部部署]

1. 開啟Adobe Experience Manager Web主控台設定頁面。

   存取設定頁面的預設URL為：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜尋並選取&#x200B;*com.adobe.fmdita.config.ConfigManager*&#x200B;套件。

1. 根據您的需求，設定設定&#x200B;**啟用Guides資產處理排程工作** (`enable.asset.processing.scheduler`)。 預設會啟用此設定。

1. 選取「**儲存**」。

>[!ENDTABS]
