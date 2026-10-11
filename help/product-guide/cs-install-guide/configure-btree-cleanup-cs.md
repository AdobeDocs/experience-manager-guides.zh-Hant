---
title: 設定雲端服務的B樹狀目錄清理工作
description: 設定雲端服務的B樹狀目錄清理工作
feature: Output Generation
role: Admin
level: Experienced
exl-id: de464e92-f17b-4c99-98f2-fdba8d214129
TQID: 'https://experienceleague.adobe.com/-n4Winzqo-HNb2FDH6RI223UT9uvuOc8-OT7mgXjblc'
product_v2:
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
    internal-label: Experience Manager Guides
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
feature_v2:
  - id: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
    internal-label: Configuration
  - id: a3bd6397-2eb2-4908-a61c-226e26855dca
    internal-label: Publishing
subfeature_v2:
  - id: fd6cc9e1-e5e5-494e-b7b1-a32f2d6cd7c9
    internal-label: Output generation
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 81a0e7f0736ba4970673dd87a888a4c60d3c1b4e
workflow-type: tm+mt
source-wordcount: '132'
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
