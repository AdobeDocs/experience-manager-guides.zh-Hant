---
title: 設定查詢的LimitReads數目
description: 瞭解如何設定查詢的LimitReads數目
feature: Web Editor Configuration
role: Admin
level: Experienced
exl-id: 53748636-f3d1-4b3b-a772-2730b78741cb
source-git-commit: cc73b81787a3c3dbe8390d93e558064327e59965
workflow-type: tm+mt
source-wordcount: '100'
ht-degree: 2%

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

**父級主題：**[&#x200B;自訂編輯器](customize-overview.md)
