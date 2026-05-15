---
title: 設定雲端服務的B樹狀目錄清理工作
description: 設定雲端服務的B樹狀目錄清理工作
feature: Output Generation
role: Admin
level: Experienced
exl-id: de464e92-f17b-4c99-98f2-fdba8d214129
TQID: https://experienceleague.adobe.com/-n4Winzqo-HNb2FDH6RI223UT9uvuOc8-OT7mgXjblc
product_v2: id: fae5e35a-80c9-4b94-9352-1a060a6aab1did: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 132
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
