---
title: 設定查詢的LimitReads數目
description: 瞭解如何設定查詢的LimitReads數目
exl-id: f6010cc3-5fec-4ec7-adf7-5ad3c9bd8879
source-git-commit: 5e0584f1bf0216b8b00f00b9fe46fa682c244e08
workflow-type: tm+mt
source-wordcount: '99'
ht-degree: 2%

---

# 設定查詢的LimitReads數目 {#id231RC0HL0ID}

若要增加查詢一次可讀取的節點數，請執行下列步驟：

1. 開啟Adobe Experience Manager Web主控台JMX頁面。

   存取設定頁面的預設URL為：

   ```http
   http://<server name>:<port>/system/console/jmx
   ```

1. 搜尋並按一下 **QueryEngineSettings**.

1. 變更的屬性值 **限制讀取** 屬性。

1. 按一下「**儲存**」。


當您增加這個屬性值時，它有助於您為較大的DITA map產生報表。

**父級主題：**[&#x200B;自訂Web編輯器](conf-web-editor.md)
