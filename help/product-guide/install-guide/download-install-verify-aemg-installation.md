---
title: 驗證AEM Guides安裝
description: 瞭解如何驗證AEM Guides安裝
exl-id: 8e0afe18-5675-4c7e-b216-6de1a752bd01
source-git-commit: 5e0584f1bf0216b8b00f00b9fe46fa682c244e08
workflow-type: tm+mt
source-wordcount: '165'
ht-degree: 0%

---

# 驗證AEM Guides安裝 {#id213BD030FBE}

安裝AEM Guides後，您需要確認安裝是否成功。 執行以下步驟來驗證安裝程式：

1. 登入您的AEM執行個體並導覽至AEM Web Console套件組合頁面。 存取套件頁面的預設URL為：

   ```http
   http://<server name>:<port>/system/console/bundles
   ```

   隨即顯示套件組合清單。

1. 在篩選文字方塊中輸入fmdita並按，以篩選套件組合清單 **輸入**.

   套件組合清單會經過篩選，以顯示AEM Guides安裝的套件組合。 如果安裝成功，則所有已安裝的套件組合都會有 **狀態** 之 **作用中**.

   如果任何套件組合沒有 **作用中** 狀態，然後檢查AEM記錄檔以疑難排解安裝問題。


>[!IMPORTANT]
>
> 您可以考慮許多效能最佳化建議，以提升系統效能。 另請參閱 [Recommendations的效能最佳化](download-install-recommend-perf-optimiz.md#) 以取得詳細資訊。

**父級主題：**[&#x200B;下載並安裝](download-install.md)
