---
title: 原生PDF |為原生PDF發佈設定JVM標幟
description: 為原生PDF發佈設定JVM標幟
feature: Output Generation
role: Admin
level: Experienced
exl-id: d5432913-4b5a-48e7-9467-7f6c6e0adbe4
TQID: https://experienceleague.adobe.com/UvDTutOu-rfQ7tNTMZ6f1dNYJ90dwSGCtTJvWWFm638
product_v2: id: fae5e35a-80c9-4b94-9352-1a060a6aab1did: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: a3bd6397-2eb2-4908-a61c-226e26855dcaid: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
subfeature_v2: id: d6596f3f-92a7-43ec-b444-237db6adad05id: fd6cc9e1-e5e5-494e-b7b1-a32f2d6cd7c9
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 128
ht-degree: 1%

---

# 為內部部署的原生PDF發佈設定JVM標幟

原生PDF發佈會啟動個別的JVM程式，以產生PDF。 您可能需要調整此JVM的設定，以支援不同情境。 例如，若要執行較大的工作負載，您應該增加衍生的JVM程式可用的棧積大小上限。

執行以下步驟來設定AEM Guides原生PDF發佈JVM標幟：

1. 開啟Adobe Experience Manager Web主控台設定頁面。

   存取設定頁面的預設URL為：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜尋並選取&#x200B;*com.adobe.fmdita.config.ConfigManager*&#x200B;套件。

1. 更新原生pdf **(*native.pdf.java.opts*)的屬性** Java命令列選項，以傳遞任何標準JVM標幟。



1. 按一下&#x200B;**儲存**。
