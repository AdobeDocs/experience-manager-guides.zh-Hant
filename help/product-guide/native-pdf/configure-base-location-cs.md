---
title: 原生PDF | 設定用於發佈雲端服務PDF的基本輸出位置
description: 設定用於發佈雲端服務PDF的基本輸出位置
feature: Output Generation
role: Admin
level: Experienced
source-git-commit: ab6f1f09de2ef758d7f05ba0a49194ac9f387dea
workflow-type: tm+mt
source-wordcount: '79'
ht-degree: 2%

---

# 設定用於發佈雲端服務輸出的基底輸出位置

若要配置基本輸出位置，請執行下列步驟：

1. 使用[組態覆寫](../cs-install-guide/download-install-additional-config-override.md)中提供的指示來建立組態檔。

1. 在組態檔中，提供下列（屬性）詳細資訊，以設定基礎輸出位置：

   | PID | 屬性索引鍵 | 屬性值 |
   |---|---|---|
   | `com.adobe.fmdita.config.ConfigManager` | `base.output.path` | **預設值：** &quot;/content/dam/fmdita-outputs&quot; |
