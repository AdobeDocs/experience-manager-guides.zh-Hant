---
title: 驗證AEM Guides安裝
description: 瞭解如何驗證AEM Guides安裝
exl-id: 4e566c57-a522-4605-bc70-47155f20b429
feature: Installation
role: Admin
level: Experienced
source-git-commit: 0513ecac38840a4cc649758bd1180edff1f8aed1
workflow-type: tm+mt
source-wordcount: '128'
ht-degree: 0%

---

# 驗證AEM Guides安裝 {#id213BD030FBE}

安裝AEM Guides後，您需要確認安裝是否成功。 執行以下步驟來驗證安裝：

1. 存取您Cloud Service的Developer Console。

   如需存取Developer Console的詳細資訊，請參閱AEM檔案中的[Developer Console存取](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/developer-console.html)。

1. 存取AEM中的OSGi套件組合清單。

   如需存取套裝的詳細資訊，請參閱AEM檔案中的[套裝](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/developer-console.html?lang=en#bundles)。

1. 在套件組合清單中搜尋fmdita並檢查其狀態。

   已成功部署的套件組合的狀態應該會顯示&#x200B;*作用中*。 如果任何套件組合的狀態不是「作用中」，請檢查AEM記錄檔以疑難排解安裝問題。


**上層主題：**&#x200B;[&#x200B;下載並安裝](download-install.md)
