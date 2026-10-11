---
title: 設定參考存放區清理工作
description: 設定參考存放區清理工作
feature: Output Generation
role: Admin
level: Experienced
exl-id: 58f98313-fc91-43b3-9553-aa5ab4946925
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
    internal-label: Experience Manager Guides
feature_v2:
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
source-wordcount: '247'
ht-degree: 3%
---
# 設定參考存放區清理

設定參考存放區清理工作並管理`Guides BTree deletion`設定，讓您的系統保持最佳化和存放區整潔。

## 設定參考存放區清理工作

下列標籤提供根據Experience Manager Guides設定來設定參考存放區清理工作的指示： Cloud Service或內部部署。

>[!BEGINTABS]

>[!TAB Cloud Service]

1. 使用[組態覆寫](download-install-config-override.md)中提供的指示來建立組態檔。

1. 在設定檔案中，提供下列（屬性）詳細資訊：

   | PID | 屬性索引鍵 | 屬性值 |
   |---|---|---|
   | `com.adobe.guides.utils.schedulers.GuidesBTreesCleanupSchedulerJob` | `cronExpression` | **預設值：** &quot;0 0 0 * * ？&quot; |

>[!TAB 內部部署]

1. 開啟Adobe Experience Manager Web主控台設定頁面。

   存取設定頁面的預設URL為：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜尋並選取&#x200B;*com.adobe.guides.utils.schedulers.GuidesBTreesCleanupSchedulerJob*&#x200B;套件組合。

1. 更新cron運算式以設定參考存放區清理排程器工作執行頻率。

1. 設定參考存放區清理排程器，如下所示。

   ![](assets/btree-cleanup-config.png)

1. 選取「**儲存**」。

>[!ENDTABS]

## 設定參考線B樹狀結構刪除啟用設定

下列標籤會提供根據您的Experience Manager Guides設定啟用設定的指示： Cloud Service或內部部署。

>[!BEGINTABS]

>[!TAB Cloud Service]

1. 使用[組態覆寫](download-install-config-override.md)中提供的指示來建立組態檔。

1. 在設定檔案中，提供下列（屬性）詳細資訊：

   | PID | 屬性索引鍵 | 屬性值 |
   |---|---|---|
   | `com.adobe.fmdita.config.ConfigManager` | `btree.deletion.enabled` | **預設值：** &quot;True&quot; |

>[!TAB 內部部署]

1. 開啟Adobe Experience Manager Web主控台設定頁面。

   存取設定頁面的預設URL為：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜尋並選取&#x200B;*com.adobe.fmdita.config.ConfigManager*&#x200B;套件。
1. 啟用設定&#x200B;**Guides btree刪除已啟用** (btree.deletion.enabled)。

   ![](assets/btree-cleanup-setting.png)

1. 選取「**儲存**」。

>[!ENDTABS]
