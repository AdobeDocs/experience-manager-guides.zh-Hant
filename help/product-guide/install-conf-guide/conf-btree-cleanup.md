---
title: 設定雲端服務的B樹狀目錄清理工作
description: 設定雲端服務的B樹狀目錄清理工作
feature: Output Generation
role: Admin
level: Experienced
source-git-commit: 6f3f05419f4f5cdd45ab580cdee6fa869f20f01d
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 3%

---

# 設定B樹狀結構清理

設定B-tree清理工作並管理`Guides BTree deletion`設定，讓您的系統最佳化並維持儲存空間整潔。

## 設定B-tree清理工作

下列標籤提供根據Experience Manager Guides設定來設定B樹狀目錄清理工作的指示： Cloud Service或內部部署。

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

1. 更新cron運算式以設定B樹狀目錄清理排程器工作執行頻率。

1. 如下所示設定B-tree清理排程器。

   ![](assets/btree-cleanup-config.png){align="left"}

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
1. 啟用設定`Guides btree deletion enabled`。

   ![](assets/btree-cleanup-setting.png){align="left"}

1. 選取「**儲存**」。

>[!ENDTABS]