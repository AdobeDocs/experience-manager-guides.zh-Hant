---
title: 安裝文章式發佈的套件
description: 瞭解如何安裝套件以供文章式發佈之用
feature: Web Editor Configuration
role: Admin
level: Experienced
source-git-commit: 6f3f05419f4f5cdd45ab580cdee6fa869f20f01d
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# 安裝文章式發佈的套件 {#id21BNL02052Z}

AEM Guides提供與Web編輯器整合的強大文章式發佈功能。 使用此功能，您可以同時發佈一個或多個主題。 在地圖編輯器中開啟地圖後，您可以導覽至「輸出」標籤以建立預設集，然後選擇一個或多個主題以產生輸出。 您可以使用以文章為基礎的發佈功能，以遞增方式產生一或多個主題的輸出，或以逐篇文章的方式將您的內容發佈到知識庫平台。 如需更多詳細資料，請參閱使用手冊中的&#x200B;*網頁編輯器區段*&#x200B;的文章式發佈。

下列標籤提供建立AEM網站以根據您的Experience Manager Guides設定發佈文章型輸出的指示： Cloud Service或內部部署。

>[!BEGINTABS]

>[!TAB Cloud Service]

1. 從您的&#x200B;**XML Documentation軟體發佈入口網站**&#x200B;下載Cloud Service的[Adobe元件內容套件](https://experience.adobe.com/#/downloads/content/software-distribution/en/general.html)。
1. 開啟AEM Package Manager。 存取封裝管理程式的預設URL為： `https://<hostname>/crx/packmgr/index.jsp`
1. 上傳適用於Cloud Service的XML Documentation元件內容套件並安裝。
1. 從您的`Knowledge-base-template-for-article-based-publishing-for-cloud-service.zip`Adobe軟體發佈入口網站[下載](https://experience.adobe.com/#/downloads/content/software-distribution/en/general.html)檔案。
1. 從全域導覽中選取&#x200B;**網站**。
1. 在Sites UI內，按一下右上角的&#x200B;**建立**&#x200B;按鈕。
1. 從&#x200B;**建立**&#x200B;下拉式清單中，從範本&#x200B;**選取**&#x200B;網站。
1. 按一下&#x200B;**匯入**&#x200B;按鈕，然後選取在您的系統上下載的`Knowledge-base-template-for-article-based-publishing-for-cloud-service.zip`。 網站範本匯入後，會列在底部。

   >[!NOTE]
   >
   > 您只需要第一次匯入ZIP檔案。 匯入後，網站範本便可在清單中使用。

   選取&#x200B;**文章式發佈的知識庫範本**&#x200B;以建立AEM網站，然後按一下右上角的&#x200B;**下一步**。

1. 輸入&#x200B;**網站標題**&#x200B;和&#x200B;**網站名稱**，然後按一下右上角的&#x200B;**建立**。 AEM網站是使用Tragopan網站範本建立。 \（Tragopan網站是範例知識庫AEM網站，包含類別、區段和文章頁面的範本。\）

   >[!NOTE]
   >
   > 您可以使用相同的範本建立多個AEM網站。


您可以使用AEM網站，透過網頁編輯器的輸出預設集來發佈文章。

>[!TAB 內部部署]

若要啟用文章式發佈，請從Adobe軟體發佈入口網站下載並安裝下列套件。 安裝這些軟體以建立Tragopan網站。 \(Tragopan網站是範例知識庫AEM網站，包含類別、區段和文章頁面的範本。\)更新Tragopan網站，使用網頁編輯器的輸出預設集產生AEM網站輸出。

- 文章式發佈的知識庫範本
- 文章式發佈的元件套件

>[!ENDTABS]


**上層主題：**[&#x200B;自訂Web編輯器](customize-overview.md)
