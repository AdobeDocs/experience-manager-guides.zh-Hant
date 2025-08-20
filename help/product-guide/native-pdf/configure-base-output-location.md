---
title: 設定基本輸出位置，以發佈內部部署服務的輸出
description: 設定基本輸出位置，以發佈內部部署服務的輸出
feature: Output Generation
role: Admin
level: Experienced
source-git-commit: ab6f1f09de2ef758d7f05ba0a49194ac9f387dea
workflow-type: tm+mt
source-wordcount: '108'
ht-degree: 1%

---

# 設定基本輸出位置，以發佈內部部署服務的輸出

執行以下步驟來設定基本輸出位置：

1. 開啟Adobe Experience Manager Web主控台設定頁面。

   存取設定頁面的預設URL為：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜尋並選取&#x200B;*com.adobe.fmdita.config.ConfigManager*&#x200B;套件。

1. 更新屬性&#x200B;**基本輸出位置**&#x200B;以指定AEM存放庫中的預設路徑，在發佈後會在此儲存PDF。 此外，如果輸入了無效的路徑，則會自動還原為預設路徑： /content/dam/fmdita-outputs。

1. 按一下「**儲存**」。


