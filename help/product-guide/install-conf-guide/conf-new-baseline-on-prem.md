---
title: 設定內部部署的新基準線
description: 瞭解如何啟用或停用內部部署的新基準線
feature: Configuration
role: Admin
level: Experienced
source-git-commit: 8d231bdbf00adb354bc31616e880495b00a3959c
workflow-type: tm+mt
source-wordcount: '125'
ht-degree: 1%

---

# 為內部部署設定新基準線

>[!IMPORTANT]
>
> 透過程式碼部署系統設定，而不是在執行階段環境中手動套用。

下列步驟說明如何在內部部署環境中啟用新基準線。

1. 開啟Adobe Experience Manager Web主控台設定頁面。

   存取設定頁面的預設URL為：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜尋並選取&#x200B;**com.adobe.fmdita.config.ConfigManager**&#x200B;套件。

1. 啟用設定&#x200B;**啟用較快的基準線(v2)**。 您也可以使用確切的設定名稱`enable.baseline.v2`來搜尋。

1. 選取「**儲存**」。

>[!NOTE]
>
>啟用此功能後，您必須將現有的基準線移轉到新的基準線。 如需逐步指示和逐步解說影片，請檢視[Experience Manager Guides中的新基準線(Beta)](../user-guide/web-editor-baseline-v2.md)。

