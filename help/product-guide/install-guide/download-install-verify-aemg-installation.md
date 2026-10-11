---
title: 驗證AEM Guides安裝
description: 瞭解如何驗證AEM Guides安裝
exl-id: 8e0afe18-5675-4c7e-b216-6de1a752bd01
feature: Installation
role: Admin
level: Experienced
TQID: 'https://experienceleague.adobe.com/sniTYknUIyJH0D1moIL3olj3AeBT08kLH52Gba27sqs'
product_v2:
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
    internal-label: Experience Manager Guides
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
feature_v2:
  - id: e88e74c7-6080-446a-8eb0-496f1ac5f7e6
    internal-label: Administration
subfeature_v2:
  - id: e557051c-ff02-4ff8-9421-cf452af0edd5
    internal-label: Installation
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
topic_v2:
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
    internal-label: Optimization
source-git-commit: 81a0e7f0736ba4970673dd87a888a4c60d3c1b4e
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 0%
---
# 驗證AEM Guides安裝 {#id213BD030FBE}

安裝AEM Guides後，您需要確認安裝是否成功。 執行以下步驟來驗證安裝程式：

1. 登入您的AEM執行個體，並導覽至AEM Web Console套件組合頁面。 存取套件頁面的預設URL為：

   ```http
   http://<server name>:<port>/system/console/bundles
   ```

   隨即顯示套件組合清單。

1. 在篩選文字方塊中輸入fmdita並按&#x200B;**Enter**，以篩選組合清單。

   套件組合清單會經過篩選，以顯示AEM Guides安裝的套件組合。 如果安裝成功，則所有安裝的套件組合都會有&#x200B;**使用中**&#x200B;的&#x200B;**狀態**。

   如果任何套件組合的狀態不是&#x200B;**作用中**，請檢查AEM記錄檔以疑難排解安裝問題。


>[!IMPORTANT]
>
> 您可以考慮許多效能最佳化建議，以提升系統效能。 如需詳細資訊，請參閱[效能最佳化建議](download-install-recommend-perf-optimiz.md#)。

**上層主題：**&#x200B;[&#x200B;下載並安裝](download-install.md)
