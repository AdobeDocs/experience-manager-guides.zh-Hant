---
title: 為雲端服務設定DITA Assets復寫
description: 瞭解如何為雲端服務設定Dita資產復寫
feature: Output Generation
role: Admin
level: Experienced
source-git-commit: 356ea6edd5e688fb1f77e737c705ed0bd4d2e7f0
workflow-type: tm+mt
source-wordcount: '60'
ht-degree: 3%

---

# 設定DITA資產復寫

若要設定資產處理功能，請執行下列步驟：

1. 使用[組態覆寫](../cs-install-guide/download-install-additional-config-override.md)中提供的指示來建立組態檔。

1. 在設定檔案中，提供下列（屬性）詳細資訊：

   | PID | 屬性索引鍵 | 屬性值 |
   |---|---|---|
   | `com.adobe.fmdita.config.ConfigManager` | `publish.replicate` | **預設值：** &quot;true&quot; |
