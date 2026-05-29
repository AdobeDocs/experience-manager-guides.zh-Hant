---
title: 設定新編輯器
description: 瞭解如何啟用或停用新編輯器
feature: Configuration
role: Admin
level: Experienced
source-git-commit: 8d231bdbf00adb354bc31616e880495b00a3959c
workflow-type: tm+mt
source-wordcount: '79'
ht-degree: 2%

---

# 為內部部署設定新編輯器

>[!IMPORTANT]
>
> 透過程式碼部署系統設定，而不是在執行階段環境中手動套用。

下列步驟說明如何在On-Premise環境中啟用新編輯器。

1. 開啟Adobe Experience Manager Web主控台設定頁面。

   存取設定頁面的預設URL為：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜尋並選取&#x200B;**com.adobe.fmdita.config.ConfigManager**&#x200B;套件。

1. 啟用設定&#x200B;**啟用編輯器2.0** (`enable.markup.editor`)。

1. 選取「**儲存**」。

