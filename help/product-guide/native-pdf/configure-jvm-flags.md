---
title: 原生PDF | 為原生PDF發佈設定JVM標幟
description: 為原生PDF發佈設定JVM標幟
exl-id: d5432913-4b5a-48e7-9467-7f6c6e0adbe4
feature: Output Generation
role: Admin
level: Experienced
source-git-commit: 0513ecac38840a4cc649758bd1180edff1f8aed1
workflow-type: tm+mt
source-wordcount: '125'
ht-degree: 1%

---

# 為原生PDF發佈設定JVM標幟

原生PDF發佈會啟動單獨的JVM流程來產生PDF。 您可能需要調整此JVM的設定，以支援不同情境。 例如，若要執行較大的工作負載，您應該增加衍生的JVM程式可用的棧積大小上限。

執行以下步驟來設定AEM Guides原生PDF發佈JVM標幟：

1. 開啟Adobe Experience Manager Web主控台設定頁面。

   存取設定頁面的預設URL為：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜尋並選取 *com.adobe.fmdita.config.ConfigManager* 套件組合。

1. 更新屬性 **原生pdf的Java命令列選項** (*native.pdf.java.opts*)，以傳遞任何標準JVM標幟。



1. 按一下「**儲存**」。
