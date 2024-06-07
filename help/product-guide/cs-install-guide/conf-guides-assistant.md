---
title: 設定指南助理以搜尋內容
description: 瞭解如何設定「指南小幫手」以搜尋內容
source-git-commit: 8ac0ed6b867a3efdef750cb19ed4955a67def9ee
workflow-type: tm+mt
source-wordcount: '603'
ht-degree: 0%

---


# 設定AI支援的Guides Assistant以搜尋內容

身為管理員，您可以為作者設定「指南小幫手」功能。 Guides Assistant服務受到Adobe IMS驗證型驗證的保護。 將您的環境與Adobe的安全權杖型驗證工作流程整合，並開始使用新的指南助理功能。 以下設定可協助您新增 **AI設定** 定位字元至資料夾設定檔。 新增後，您便可以使用網頁編輯器中的指南助理功能。

## 在Adobe Developer Console中建立IMS設定

執行以下步驟，在Adobe Developer主控台中建立IMS設定：

>[!NOTE]
>
>如果您已建立OAuth專案來設定智慧建議功能或微服務型發佈，您可以略過下列步驟來建立專案。

1. Launch [Adobe Developer Console](https://developer.adobe.com/console).
1. 成功登入開發人員控制檯後，您將檢視 **首頁** 畫面。 此 **首頁** 畫面可讓您輕鬆找到資訊和快速連結，包括專案和下載的頂端導覽連結。
1. 若要建立新的空白專案，請選取 **建立新專案** 從 **快速入門** 連結。
   ![快速入門連結](assets/conf-ss-quick-start.png) {width="550" align="left"}
   *建立新專案。*

1. 選取 **新增API** 從 **專案** 畫面。  此 **新增API** 畫面隨即顯示。 此畫面會顯示所有可用的API、事件和服務，供您用來開發應用程式的Adobe產品和技術。

1. 選取 **I/O管理API** 以將其新增至您的專案。
   ![IO管理API](assets/confi-ss-io-management.png)
   *新增I/O Management API至您的專案。*

1. 建立新的 **OAuth認證** 並儲存。
   ![設定API中的OAuth認證磚](assets/conf-ss-OAuth-credential.png) {width="3000" align="left"}
   *設定API的OAuth認證。*

1. 在  **專案** 索引標籤，選擇 **OAuth伺服器至伺服器** 選項，然後選取新建立的認證。

1. 選取 **OAuth伺服器對伺服器** 檢視專案認證詳細資料的連結。

   ![連線的認證](assets/conf-ss-connected-credentials.png) {width="800" align="left"}

   *連線至專案以檢視認證詳細資料。*

1. 返回 **專案** 標籤並選取 **專案概述** 左側。

   <img src="assets/project-overview.png" alt="專案概述" width="500">

   *開始新專案。*

1. 按一下 **下載** 按鈕來下載服務JSON。

   <img src="assets/download-json.png" alt="下載json" width="500">

   *下載JSON服務詳細資料。*

您已設定OAuth驗證詳細資料並下載JSON服務詳細資料。 將此檔案依下一區段的要求保留為方便使用。

### 將IMS設定新增至環境

執行以下步驟，將IMS設定新增至環境：

1. 開啟Experience Manager，然後選取您的程式，其中包含您要設定的環境。
1. 切換至 **環境** 標籤。
1. 選取要設定的環境名稱。 這應該會將您導覽至 **環境資訊** 頁面。
1. 切換至 **設定** 標籤。
1. 更新SERVICE_ACCOUNT_DETAILS JSON欄位。 確定您使用與下列熒幕擷取畫面相同的名稱和設定。

![ims服務帳戶設定](assets/ims-service-account-config.png){width="800" align="left"}


*新增環境設定詳細資料。*




新增IMS設定至環境後，請使用OSGi執行以下步驟將這些屬性與AEM Guides連結：

1. 在您的Cloud Manager Git專案程式碼中，新增以下兩個指定的檔案(針對檔案內容，檢視 [附錄](#appendix))。

   * `com.adobe.aem.guides.eventing.ImsConfiguratorService.cfg.json`

1. 確保新新增的檔案包含在您的 `filter.xml`.
1. 認可並推送您的Git變更。
1. 執行管道以將變更套用至環境。

完成後，您應該能夠使用 **指南助理** 功能。



## 附錄 {#appendix}

**檔案**：
`com.adobe.aem.guides.eventing.ImsConfiguratorService.cfg.json`

**內容**：

```
{
 "service.account.details": "$[secret:SERVICE_ACCOUNT_DETAILS]",
}
```


完成設定後， **指南助理** ![指南助理](assets/guides-assistant-icon.svg) 圖示會顯示在網頁編輯器的右側面板中。 選取圖示以檢視 **指南助理** 面板。
如需詳細資訊，請檢視 [AI支援的Guides Assistant可搜尋內容](../user-guide/ai-based-guides-assistant.md) 區段的URL來識別Experience Manager。
