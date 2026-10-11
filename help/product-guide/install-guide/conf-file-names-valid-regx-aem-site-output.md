---
title: 設定AEM網站輸出的有效檔案名稱
description: 瞭解如何為AEM網站輸出設定有效的檔案名稱
exl-id: 1e69d6f8-7baf-4189-bbbd-34cd0fec6634
feature: Filename Configuration
role: Admin
level: Experienced
TQID: 'https://experienceleague.adobe.com/vGe4--XJ9VL5q74J7hVFCmD0vrBRnUkBAdZDCFcUxeU'
product_v2:
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
    internal-label: Experience Manager Guides
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
feature_v2:
  - id: a3bd6397-2eb2-4908-a61c-226e26855dca
    internal-label: Publishing
  - id: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
    internal-label: Configuration
subfeature_v2:
  - id: ccd46b93-df7f-4458-ba4c-90a3562d9ab0
    internal-label: Filename configuration
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 81a0e7f0736ba4970673dd87a888a4c60d3c1b4e
workflow-type: tm+mt
source-wordcount: '139'
ht-degree: 0%
---
# 設定AEM網站輸出的有效檔案名稱 {#id214GK0X0KXA}

與DITA主題允許的有效檔案名稱字元清單類似，您也可以為AEM網站輸出設定有效檔案名稱字元清單。 URL中不允許使用的部分已知字元為： `<>``@$`。 這些字元已設定為在產生AEM網站輸出檔案名稱時，找到時自動轉換為底線「_」。 允許您在AEM站台輸出中設定有效字元的設定存在於`com.adobe.fmdita.common.SanitizeNodeNameImpl`套件組合中。 **設定發佈至AEM Sites時不允許的字元集**&#x200B;設定，在AEM網站輸出檔案名稱中包含要以底線取代的字元。

**父級主題：**[&#x200B;設定檔名](conf-file-names.md)
