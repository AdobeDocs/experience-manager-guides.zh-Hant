---
title: 啟用新的PDF引擎
description: 瞭解如何在Experience Manager Guides中啟用新的PDF引擎
feature: Web Editor Configuration
role: Admin
level: Experienced
source-git-commit: f3f30400f776f746427e257e2c937ff3413aa9ac
workflow-type: tm+mt
source-wordcount: '74'
ht-degree: 2%

---


# 設定原生PDF引擎v2

原生PDF的新發佈引擎（即&#x200B;_原生PDF引擎v2_）提供&#x200B;_原生PDF引擎v1_&#x200B;問題的更新PDF演算功能及修正。

使用[組態覆寫](../install-conf-guide/download-install-config-override.md)中提供的指示來建立組態檔。 在設定檔案中，提供下列（屬性）詳細資訊：

| PID | 屬性索引鍵 | 屬性值 |
|-----|--------------|----------------|
| `com.adobe.fmdita.publish.config.GuidesPublishConfiguratorService` | `guides.publish.config` | `{"PDF_ENGINE": "v2"}` <br>預設值： `v1` |