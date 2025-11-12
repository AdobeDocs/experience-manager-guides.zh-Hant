---
title: 設定雲端服務的B樹狀目錄清理工作
description: 設定雲端服務的B樹狀目錄清理工作
feature: Output Generation
role: Admin
level: Experienced
source-git-commit: 5b29b2b5f725b5d9a2029fb232e62f387a5338fd
workflow-type: tm+mt
source-wordcount: '125'
ht-degree: 3%

---

# 設定B樹狀結構清理

設定B-tree清理工作並管理`Guides BTree deletion`設定，讓您的系統最佳化並維持儲存空間整潔。

## 設定B-tree清理工作

執行以下步驟來設定B-tree清理工作：

1. 使用[組態覆寫](../cs-install-guide/download-install-additional-config-override.md)中提供的指示來建立組態檔。

1. 在設定檔案中，提供下列（屬性）詳細資訊：

   | PID | 屬性索引鍵 | 屬性值 |
   |---|---|---|
   | `com.adobe.guides.utils.schedulers.GuidesBTreesCleanupSchedulerJob` | `cronExpression` | **預設值：** &quot;0 0 0 * * ？&quot; |


## 設定參考線B樹狀結構刪除啟用設定

執行以下步驟以啟用設定：

1. 使用[組態覆寫](../cs-install-guide/download-install-additional-config-override.md)中提供的指示來建立組態檔。

1. 在設定檔案中，提供下列（屬性）詳細資訊：

   | PID | 屬性索引鍵 | 屬性值 |
   |---|---|---|
   | `com.adobe.fmdita.config.ConfigManager` | `btree.deletion.enabled` | **預設值：** &quot;True&quot; |