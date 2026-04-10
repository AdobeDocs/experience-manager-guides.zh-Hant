---
title: 設定查詢的LimitReads數目
description: 瞭解如何設定查詢的LimitReads數目
feature: Web Editor Configuration
role: Admin
level: Experienced
source-git-commit: 6f3f05419f4f5cdd45ab580cdee6fa869f20f01d
workflow-type: tm+mt
source-wordcount: '101'
ht-degree: 1%

---

# 設定On-Premise查詢的LimitReads數目

若要增加查詢一次可讀取的節點數，請執行下列步驟：

1. 開啟Adobe Experience Manager Web主控台JMX頁面。

   存取設定頁面的預設URL為：

   ```http
   http://<server name>:<port>/system/console/jmx
   ```

1. 搜尋並按一下&#x200B;**QueryEngineSettings**。

1. 變更&#x200B;**LimitReads**&#x200B;屬性的屬性值。

1. 按一下&#x200B;**儲存**。


當您增加這個屬性值時，它有助於您為較大的DITA map產生報表。

**上層主題：**&#x200B;[&#x200B;自訂Web編輯器](customize-overview.md)
