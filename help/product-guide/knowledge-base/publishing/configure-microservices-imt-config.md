---
title: 使用AEM Guides的OAuth驗證設定微服務型發佈as a Cloud Service
description: 瞭解如何使用AEM Guides的OAuth驗證來設定微服務型發佈。
feature: Microservice in AEM Guides
role: Admin
exl-id: db0c83c7-1ece-4010-b214-f8d806d26bc9
source-git-commit: c51a372dc44921a489219f5ac99e3ad180ccc91d
workflow-type: tm+mt
source-wordcount: '827'
ht-degree: 0%

---

# 使用OAuth驗證設定微服務型發佈

發佈微服務可讓您在Experience Manager Guides as a Cloud Service上同時執行大型發佈工作負載，並利用業界領先的Adobe I/O Runtime無伺服器平台。

對於每個發佈請求，Experience Manager Guides as a Cloud Service會執行單獨的容器，此容器會根據使用者請求水平縮放。 如此一來，您便可執行多個發佈請求，並取得優於其大型內部部署Adobe Experience Manager伺服器的效能。

>[!NOTE]
>
> Experience Manager Guides中基於微服務的發佈支援PDF（原生和DITA-OT型）、HTML5、JSON和CUSTOM型別的輸出預設集。

由於雲端發佈服務受到Adobe IMS OAuth型驗證的保護，請執行以下步驟來整合其環境與Adobe的安全權杖型驗證工作流程，並開始使用雲端型可擴充發佈解決方案。


## 在Adobe Developer Console中建立IMS設定

**建立組態所需的角色**：系統管理員

執行以下步驟，在&#x200B;**Adobe Developer Console**&#x200B;中建立IMS設定：

>[!NOTE]
>
>如果您已建立OAuth專案以設定AI支援的智慧型建議以進行編寫，您可以略過下列步驟來建立專案。

1. 開啟&#x200B;**Developer Console**： `https://developer.adobe.com/console`。

1. 從頂端切換至&#x200B;**專案**&#x200B;索引標籤。

   <img src="assets/projects-tab.png" alt="專案索引標籤" width="500">

   *在&#x200B;**Adobe Developer Console***上選取**&#x200B;專案&#x200B;**標籤

1. 若要建立新的空白專案，請從&#x200B;**建立新專案**&#x200B;下拉式清單中選取&#x200B;**空白專案**。

   <img src="assets/create-new-project.png" alt="建立新專案" width="500">

   *建立新的空白專案。*

1. 從&#x200B;**新增至專案**&#x200B;下拉式清單中選取&#x200B;**API**，將IO管理API新增至您的專案。

   <img src="assets/add-project.png" alt="新增專案" width="300">

   *從下拉式清單中選取API專案。*

   <img src="assets/io-management-api.png" alt="io管理" width="500">

   *新增I/O Management API至您的專案。*

1. 建立新的OAuth認證並儲存。

   <img src="assets/microservice-api-oauth.png" alt="產生金鑰組" width="500">

   *將OAuth認證設定到您的API。*


1. 返回「**專案**」標籤，並在左側選取「**專案概述**」。

   <img src="assets/project-overview.png" alt="專案概述" width="500">

   *開始新專案。*

1. 按一下頂端的「**下載**」按鈕即可下載服務JSON。

   <img src="assets/download-json.png" alt="下載json" width="500">

   *下載JSON服務詳細資料。*

您已設定OAuth驗證詳細資料並下載JSON服務詳細資料。 將此檔案依下一區段的要求保留為方便使用。


## 將IMS設定新增至環境

>[!NOTE]
>
>如果您已針對智慧建議建立OAuth專案，則您可以對微服務重複使用相同的專案，並跳過以下步驟以將IMS設定新增至環境。

### 更新現有設定(JWT)   至OAuth Shift )

如果您已使用微服務來使用JWT發佈（已棄用），請執行以下步驟來更新設定：



1. 開啟&#x200B;**Experience Manager**，並選取包含您要設定之環境的程式。
1. 切換至&#x200B;**環境**&#x200B;標籤。
1. 選取要設定的環境名稱。 這應該會將您導覽至&#x200B;**環境資訊**&#x200B;頁面。
1. 切換至&#x200B;**組態**&#x200B;標籤。

1. 使用您下載的新OAuth JSON檔案更新SERVICE_ACCOUNT_DETAILS JSON欄位。
1. 刪除PRIVATE_KEY欄位。



   <img src="assets/ims-service-account-config.png" alt="ims服務帳戶設定" width="500">

   *更新現有的JWT環境設定。*

### 首次設定

若要第一次使用發佈微服務，請依照下列步驟更新設定：
1. 開啟&#x200B;**Experience Manager**，並選取包含您要設定之環境的程式。
1. 切換至&#x200B;**環境**&#x200B;標籤。
1. 選取要設定的環境名稱。 這應該會將您導覽至&#x200B;**環境資訊**&#x200B;頁面。
1. 切換至&#x200B;**組態**&#x200B;標籤。

1. 建立名稱為SERVICE_ACCOUNT_DETAILS的新設定。 在價值中，新增您從開發人員控制檯下載的OAuth JSON檔案內容。


<img src="assets/jws-service-account-config.png" alt="ims服務帳戶設定" width="500">

*第一次設定環境。*


### 微服務型發佈啟用的第一次程式碼變更

>[!NOTE]
>
> 如果您已使用以微服務為基礎的發佈，請略過下列步驟：

新增IMS設定至環境後，請使用OSGi執行以下步驟將這些屬性與Experience Manager Guides連結：

1. 在您的Cloud Manager Git專案程式碼中，將以下兩個檔案新增到`/apps/fmditaCustom/config`中（針對檔案內容，請檢視[附錄](#appendix)）。

   * `com.adobe.aem.guides.eventing.ImsConfiguratorService.cfg.json`
   * `com.adobe.fmdita.publishworkflow.PublishWorkflowConfigurationService.xml`
1. 確保您的`filter.xml`涵蓋新新增的檔案。
1. 認可並推送您的Git變更。
1. 執行管道以將變更套用至環境。

完成此操作後，您可以使用微服務型雲端發佈。

## 常見問題


1. 如果啟用使用微服務的OSGi設定，發佈程式是否可以在具有相同程式碼基底的本機Experience Manager伺服器上運作？
   * 否，如果旗標`dxml.use.publish.microservice`設為`true`，則一律會尋找微服務組態。 將`dxml.use.publish.microservice`設為`false`，讓發佈在您的本機伺服器上運作。
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
