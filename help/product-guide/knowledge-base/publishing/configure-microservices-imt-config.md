---
title: 使用AEM Guides的OAuth驗證設定微服務型發佈as a Cloud Service
description: 瞭解如何使用AEM Guides的OAuth驗證來設定微服務型發佈。
feature: Microservice in AEM Guides
role: User, Admin
source-git-commit: 4c7421391922d276ef82515fb4b1cbdc2397e4ce
workflow-type: tm+mt
source-wordcount: '821'
ht-degree: 0%

---

# 使用OAuth驗證設定微服務型發佈

發佈微服務可讓您在Experience Manager Guidesas a Cloud Service上同時執行大型發佈工作負載，並利用業界領先的Adobe I/O Runtime無伺服器平台。

對於每個發佈請求，Experience Manager指南as a Cloud Service會執行單獨的容器，該容器會根據使用者請求水平縮放。 如此一來，您便可執行多個發佈請求，並取得優於其大型內部部署Adobe Experience Manager伺服器的效能。

>[!NOTE]
>
> 「Experience Manager指南」中以微服務為基礎的發佈可支援PDF（原生和DITA-OT型）、HTML5、JSON和CUSTOM型別的輸出預設集。

由於雲端發佈服務受到Adobe IMS OAuth型驗證的保護，請執行以下步驟來整合其環境與Adobe的安全權杖型驗證工作流程，並開始使用雲端型可擴充發佈解決方案。


## 在Adobe Developer Console中建立IMS設定

**建立設定所需的角色**：系統管理員

執行以下步驟，在中建立IMS設定 **Adobe Developer Console**：

>[!NOTE]
>
>如果您已建立OAuth專案以設定AI支援的智慧型建議以進行編寫，您可以略過下列步驟來建立專案。

1. 開啟 **開發人員主控台**： `https://developer.adobe.com/console`.

1. 切換至 **專案** 標籤來顯示。

   <img src="assets/projects-tab.png" alt="專案索引標籤" width="500">

   *選取&#x200B;**專案**標籤上的&#x200B;**Adobe Developer Console***

1. 若要建立新的空白專案，請選取 **空白專案** 從 **建立新專案** 下拉式清單。

   <img src="assets/create-new-project.png" alt="建立新專案" width="500">

   *建立新的空白專案。*

1. 選取 **API** 從 **新增至專案** 下拉式清單，將IO Management API新增至您的專案。

   <img src="assets/add-project.png" alt="新增專案" width="300">

   *從下拉式清單中選取API專案。*

   <img src="assets/io-management-api.png" alt="io管理" width="500">

   *新增I/O Management API至您的專案。*

1. 建立新的OAuth認證並儲存。

   <img src="assets/microservice-api-oauth.png" alt="產生金鑰組" width="500">

   *設定API的OAuth認證。*


1. 返回 **專案** 標籤並選取 **專案概述** 左側。

   <img src="assets/project-overview.png" alt="專案概述" width="500">

   *開始新專案。*

1. 按一下 **下載** 按鈕來下載服務JSON。

   <img src="assets/download-json.png" alt="下載json" width="500">

   *下載JSON服務詳細資料。*

您已設定OAuth驗證詳細資料並下載JSON服務詳細資料。 將此檔案依下一區段的要求保留為方便使用。


## 將IMS設定新增至環境

>[!NOTE]
>
>如果您已針對智慧建議建立OAuth專案，則您可以對微服務重複使用相同的專案，並跳過以下步驟以將IMS設定新增至環境。

### 更新現有設定

如果您已使用微服務來使用JWT發佈（已棄用），請執行以下步驟來更新設定：



1. 開啟 **Experience Manager** 並選取包含要設定之環境的程式。
1. 切換至 **環境** 標籤。
1. 選取要設定的環境名稱。 這應該會將您導覽至 **環境資訊** 頁面。
1. 切換至 **設定** 標籤。

1. 使用您下載的新OAuth JSON檔案更新SERVICE_ACCOUNT_DETAILS JSON欄位。
1. 刪除PRIVATE_KEY欄位。



   <img src="assets/ims-service-account-config.png" alt="ims服務帳戶設定" width="500">

   *更新現有的JWT環境設定。*

### 首次設定

若要第一次使用發佈微服務，請依照下列步驟更新設定：
1. 開啟 **Experience Manager** 並選取包含要設定環境的程式。
1. 切換至 **環境** 標籤。
1. 選取要設定的環境名稱。 這應該會將您導覽至 **環境資訊** 頁面。
1. 切換至 **設定** 標籤。

1. 更新SERVICE_ACCOUNT_DETAILS JSON欄位。 確定您使用與下列熒幕擷取畫面相同的名稱和設定。


<img src="assets/jws-service-account-config.png" alt="ims服務帳戶設定" width="500">

*第一次設定環境。*


### 首次使用微服務型發佈

>[!NOTE]
>
> 如果您已使用以微服務為基礎的發佈，請略過下列步驟：

新增IMS設定至環境後，請使用OSGi執行以下步驟將這些屬性與Experience Manager指南連結：

1. 在您的Cloud Manager Git專案程式碼中，新增以下兩個檔案(針對檔案內容，檢視 [附錄](#appendix))。

   * `com.adobe.aem.guides.eventing.ImsConfiguratorService.cfg.json`
   * `com.adobe.fmdita.publishworkflow.PublishWorkflowConfigurationService.xml`
1. 確保新新增的檔案包含在您的 `filter.xml`.
1. 認可並推送您的Git變更。
1. 執行管道以將變更套用至環境。

完成此操作後，您可以使用微服務型雲端發佈。

## 常見問題


1. 如果啟用使用微服務的OSGi設定，發佈程式是否可以在具有相同程式碼基底的本機Experience Manager伺服器上運作？
   * 否，如果旗標 `dxml.use.publish.microservice` 設為 `true`，會一律尋找微服務設定。 設定 `dxml.use.publish.microservice` 至 `false` 讓發佈功能在本機伺服器上運作。
1. 使用以微服務為基礎的發佈時，為DITA程式分配了多少記憶體？ 這是否透過DITA設定檔和引數驅動？
   * 使用以微服務為基礎的發佈，記憶體配置不會透過DITA設定檔和引數驅動。 服務容器上可用的記憶體總計為8 GB，其中6 GB會配置給DITA-OT處理序。


## 附錄 {#appendix}

**檔案**：
`com.adobe.aem.guides.eventing.ImsConfiguratorService.cfg.json`

**內容**：

```
{
"service.account.details": "$[secret:SERVICE_ACCOUNT_DETAILS]",
}
```

**檔案**： `com.adobe.fmdita.publishworkflow.PublishWorkflowConfigurationService.xml`

**內容**：
* `dxml.use.publish.microservice`：切換以啟用使用DITA-OT的微服務型發佈
* `dxml.use.publish.microservice.native.pdf`：切換以啟用微服務型原生PDF發佈

```
<?xml version="1.0" encoding="UTF-8"?>
<jcr:root xmlns:jcr="http://www.jcp.org/jcr/1.0" xmlns:sling="http://sling.apache.org/jcr/sling/1.0"
          jcr:primaryType="sling:OsgiConfig"
          dxml.publish.microservice.url="https://adobeioruntime.net/api/v1/web/543112-guidespublisher/default/publishercaller.json"
          dxml.use.publish.microservice="{Boolean}true"
          dxml.use.publish.microservice.native.pdf="{Boolean}true"
/>
```