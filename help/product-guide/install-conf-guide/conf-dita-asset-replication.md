---
title: 設定DITA Assets復寫
description: 瞭解如何設定Dita資產復寫
feature: Output Generation
role: Admin
level: Experienced
source-git-commit: 453da51a42984b912547570f2e1de70806b41171
workflow-type: tm+mt
source-wordcount: '109'
ht-degree: 3%

---

# 設定DITA資產復寫

下列標籤提供根據Experience Manager Guides設定設定DITA資產複製功能的指示： Cloud Service或內部部署。

>[!BEGINTABS]

>[!TAB Cloud Service]

1. 使用[組態覆寫](../install-conf-guide/download-install-config-override.md)中提供的指示來建立組態檔。

1. 在設定檔案中，提供下列（屬性）詳細資訊：

   | PID | 屬性索引鍵 | 屬性值 |
   |---|---|---|
   | `com.adobe.fmdita.config.ConfigManager` | `publish.replicate` | **預設值：** &quot;true&quot; |

>[!TAB 內部部署]

1. 開啟Adobe Experience Manager Web主控台設定頁面。

   存取設定頁面的預設URL為：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜尋並選取&#x200B;*com.adobe.fmdita.config.ConfigManager*&#x200B;套件。

1. 根據您的需求設定設定`Replicate DITA assets`。 預設會啟用此設定。


   ![](assets/dita-assets-replication.png){width="350" align="left"}


1. 選取「**儲存**」。

>[!ENDTABS]
