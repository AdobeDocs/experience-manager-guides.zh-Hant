---
title: 設定Smart Help以搜尋內容
description: 瞭解如何設定智慧說明以搜尋內容
source-git-commit: 48f7b38448e821a7ad5931a685dedc95303aea95
workflow-type: tm+mt
source-wordcount: '609'
ht-degree: 0%

---


# 設定AI支援的Smart Help以搜尋內容

身為管理員，您可以為作者設定「智慧型說明」功能。 智慧型說明服務受到Adobe IMS驗證型驗證的保護。 將您的環境與Adobe的安全權杖型驗證工作流程整合，並開始使用新的智慧說明功能。 下列設定可協助您將&#x200B;**AI設定**&#x200B;索引標籤新增至資料夾設定檔。 新增後，您便可以在網頁編輯器中使用智慧型說明功能。

## 在Adobe Developer Console中建立IMS設定

執行以下步驟，在Adobe Developer Console中建立IMS設定：

>[!NOTE]
>
>如果您已建立OAuth專案來設定智慧建議功能或微服務型發佈，您可以略過下列步驟來建立專案。 您可以從步驟8開始。

1. 啟動[Adobe Developer Console](https://developer.adobe.com/console)。
1. 成功登入Developer Console後，您將檢視&#x200B;**首頁**&#x200B;畫面。 **首頁**&#x200B;畫面可讓您輕鬆找到資訊和快速連結，包括專案和下載的頂端導覽連結。
1. 若要建立新的空白專案，請從&#x200B;**快速入門**&#x200B;連結中選取&#x200B;**建立新專案**。
   ![快速入門連結](assets/conf-ss-quick-start.png) {width="550" align="left"}
   *建立新專案。*

1. 從&#x200B;**專案**&#x200B;畫面選取&#x200B;**新增API**。  **新增API**&#x200B;畫面會出現。 此畫面會顯示所有可用的API、事件和服務，供您用來開發應用程式的Adobe產品和技術。

1. 選取&#x200B;**I/O管理API**&#x200B;以將其新增至您的專案。
   ![IO管理API](assets/confi-ss-io-management.png)
   *新增I/O Management API至您的專案。*

1. 建立新的&#x200B;**OAuth認證**&#x200B;並儲存。
   設定API中的![OAuth認證磚](assets/conf-ss-OAuth-credential.png) {width="3000" align="left"}
   *將OAuth認證設定到您的API。*

1. 在&#x200B;**專案**&#x200B;索引標籤中，選擇&#x200B;**OAuth伺服器至伺服器**&#x200B;選項，然後選取新建立的認證。

1. 選取&#x200B;**OAuth伺服器對伺服器**&#x200B;連結以檢視專案的認證詳細資料。

   ![已連線的認證](assets/conf-ss-connected-credentials.png) {width="800" align="left"}

   *連線到專案以檢視認證詳細資料。*

1. 返回「**專案**」標籤，並在左側選取「**專案概述**」。

   <img src="assets/project-overview.png" alt="專案概述" width="500">

   *開始新專案。*

1. 按一下頂端的「**下載**」按鈕即可下載服務JSON。

   <img src="assets/download-json.png" alt="下載json" width="500">

   *下載JSON服務詳細資料。*

您已設定OAuth驗證詳細資料並下載JSON服務詳細資料。 將此檔案依下一區段的要求保留為方便使用。

### 將IMS設定新增至環境

執行以下步驟，將IMS設定新增至環境：

1. 開啟Experience Manager，然後選取您的程式，其中包含您要設定的環境。
1. 切換至&#x200B;**環境**&#x200B;標籤。
1. 選取要設定的環境名稱。 這應該會將您導覽至&#x200B;**環境資訊**&#x200B;頁面。
1. 切換至&#x200B;**組態**&#x200B;標籤。
1. 更新SERVICE_ACCOUNT_DETAILS JSON欄位。 確定您使用與下列熒幕擷取畫面相同的名稱和設定。

![ims服務帳戶設定](assets/ims-service-account-config.png){width="800" align="left"}


*新增環境組態詳細資料。*




新增IMS設定至環境後，請使用OSGi執行以下步驟將這些屬性與AEM Guides連結：

1. 在您的Cloud Manager Git專案程式碼中，新增以下指定的兩個檔案（針對檔案內容，請檢視[附錄](#appendix)）。

   * `com.adobe.aem.guides.eventing.ImsConfiguratorService.cfg.json`

1. 確保您的`filter.xml`涵蓋新新增的檔案。
1. 認可並推送您的Git變更。
1. 執行管道以將變更套用至環境。

完成此操作後，您應該能夠使用&#x200B;**智慧說明**&#x200B;功能。



## 附錄 {#appendix}

**檔案**：
`com.adobe.aem.guides.eventing.ImsConfiguratorService.cfg.json`

**內容**：

```
{
 "service.account.details": "$[secret:SERVICE_ACCOUNT_DETAILS]",
}
```


完成設定後，**智慧型說明** ![智慧型說明](assets/smart-help-icon.svg)圖示就會顯示在網頁編輯器的右側面板中。 選取圖示以檢視&#x200B;**智慧說明**&#x200B;面板。
如需更多詳細資料，請檢視Experience Manager使用手冊中的[AI支援的Smart Help以搜尋內容](../user-guide/ai-based-smart-help.md)區段。
