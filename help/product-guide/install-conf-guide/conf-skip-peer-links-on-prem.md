---
title: 為內部部署中的基準V1設定略過對等連結
description: 瞭解如何在On-Premise中啟用或停用基線V1的對等連結略過
feature: Configuration
role: Admin
level: Experienced
source-git-commit: 8d231bdbf00adb354bc31616e880495b00a3959c
workflow-type: tm+mt
source-wordcount: '101'
ht-degree: 1%

---

# 針對On-Premise中的舊基準設定略過對等連結

下列步驟說明如何在內部部署環境中啟用略過舊基準線的對等連結。

1. 開啟Adobe Experience Manager Web主控台設定頁面。

   存取設定頁面的預設URL為：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜尋並選取&#x200B;**com.adobe.fmdita.config.ConfigManager**&#x200B;套件。

1. 啟用設定&#x200B;**略過基準V1**&#x200B;的對等連結(guides.baseline.v1.skip.peer.links)。 預設會停用此設定。

1. 選取「**儲存**」。
