---
title: 驗證AEM Guides安裝
description: 瞭解如何驗證AEM Guides安裝
feature: Installation
role: Admin
level: Experienced
source-git-commit: 6f3f05419f4f5cdd45ab580cdee6fa869f20f01d
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 0%

---

# 驗證AEM Guides安裝 {#id213BD030FBE}

安裝AEM Guides後，您需要確認安裝是否成功。

下列標籤提供根據Experience Manager Guides設定驗證AEM Guides安裝的指示： Cloud Service或內部部署。

>[!BEGINTABS]

>[!TAB Cloud Service]

執行以下步驟來驗證安裝：

1. 存取Cloud Service的Developer Console。

   如需存取Developer Console的詳細資訊，請參閱AEM檔案中的[Developer Console存取](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/developer-console.html)。

1. 存取AEM中的OSGi套件組合清單。

   如需存取套裝的詳細資訊，請參閱AEM檔案中的[套裝](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/developer-console.html?lang=en#bundles)。

1. 在套件組合清單中搜尋fmdita並檢查其狀態。

   已成功部署的套件組合的狀態應該會顯示&#x200B;*作用中*。 如果任何套件組合的狀態不是「作用中」，請檢查AEM記錄檔以疑難排解安裝問題。

>[!TAB 內部部署]

執行以下步驟來驗證安裝：

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
> 您可以考慮許多效能最佳化建議，以提升系統效能。 如需詳細資訊，請參閱[效能最佳化建議](perf-optimization-on-prem.md#)。

>[!ENDTABS]


