---
title: 在內部部署的翻譯工作流程中設定目的地副本初始化
description: 瞭解如何在內部部署的翻譯工作流程中啟用或停用目的地復本的初始化
feature: Configuration
role: Admin
level: Experienced
source-git-commit: 8d231bdbf00adb354bc31616e880495b00a3959c
workflow-type: tm+mt
source-wordcount: '111'
ht-degree: 1%

---

# 在內部部署的翻譯工作流程中設定目的地副本初始化

下列步驟說明如何在內部部署環境的翻譯工作流程中啟用目的地副本初始化。

1. 開啟Adobe Experience Manager Web主控台設定頁面。

   存取設定頁面的預設URL為：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜尋並選取&#x200B;**com.adobe.fmdita.config.ConfigManager**&#x200B;套件。

1. 根據您的需求，啟用或停用設定&#x200B;**以來源內容** ( translation.workflow.propagate.source.content)初始化目的地語言副本。 此設定僅適用於停用舊版翻譯工作流程時。

1. 選取「**儲存**」。
