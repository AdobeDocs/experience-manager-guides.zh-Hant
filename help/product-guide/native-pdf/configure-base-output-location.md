---
title: 設定基本輸出位置，以發佈內部部署服務的輸出
description: 設定基本輸出位置，以發佈內部部署服務的輸出
feature: Output Generation
role: Admin
level: Experienced
exl-id: ae1d805a-7b79-4b76-8be2-a19c5552530c
TQID: https://experienceleague.adobe.com/qf1UZh14gvlc7ZHUUBaDlHe1U3zDvzGlGjYavYKITWY
product_v2: id: fae5e35a-80c9-4b94-9352-1a060a6aab1did: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: a3bd6397-2eb2-4908-a61c-226e26855dcaid: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
subfeature_v2: id: d6596f3f-92a7-43ec-b444-237db6adad05id: fd6cc9e1-e5e5-494e-b7b1-a32f2d6cd7c9
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 112
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

1. 按一下&#x200B;**儲存**。
