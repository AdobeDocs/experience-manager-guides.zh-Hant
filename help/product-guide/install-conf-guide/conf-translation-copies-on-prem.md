---
title: 在內部部署的翻譯工作流程中設定目的地副本初始化
description: 瞭解如何在內部部署的翻譯工作流程中啟用或停用目的地復本的初始化
feature: Configuration
role: Admin
level: Experienced
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
    internal-label: Experience Manager Guides
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 81a0e7f0736ba4970673dd87a888a4c60d3c1b4e
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
