---
title: 下載並安裝適用於內部部署服務的AEM Sites範本
description: 瞭解如何在Prem Services上下載和安裝適用的AEM Sites範本
feature: Installation
role: Admin
level: Experienced
exl-id: aa843a72-ff0d-4c9a-a87d-48d099087b5e
source-git-commit: 4c564a0ffaa8f287bcaf012634d49dbf1e0682b4
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---

# 下載及安裝AEM Sites範本（內部部署服務）

本指南提供逐步指示，說明如何設定最新的AEM Guides範本，以產生AEM Sites。 請依照下列步驟安裝所需的套件、建立和設定預設集，以及產生AEM Sites。

## 先決條件

繼續安裝之前，請先確定符合下列必要條件：

- **Adobe Experience Manager (AEM)：**&#x200B;已安裝&#x200B;**Service Pack** 21、20和19及&#x200B;**AEM 4.6.0**&#x200B;或更新版本的&#x200B;**AEM Guides 6.5**&#x200B;的執行中執行個體。

- **必要的許可權**：請確定擁有下列許可權：

   - 存取&#x200B;**軟體發佈入口網站**&#x200B;以下載必要的封裝
   - 存取&#x200B;**CRX封裝管理員**&#x200B;以在AEM中安裝封裝。
   - 在AEM Guides中建立和修改預設集的許可權。

- **下載封裝**：從&#x200B;**軟體發佈入口網站**&#x200B;下載下列封裝：

   - 元件套件： on-prem-guides-components.all-1.x.0.zip
   - Sites套件： aemg-docs.all-1.x.0.zip

## 使用CRX Package Manager安裝套件

1. **安裝元件封裝：**
   1. 瀏覽至&#x200B;[**CRX封裝管理員**](http://&lt;your-aem-instance>/crx/packmgr)。
   2. 上傳並安裝on-prem-guides-components.all-1.x.0.zip套件。

2. **安裝Sites封裝：**&#x200B;使用CRX封裝管理員上傳並安裝aemg-docs.all-1.x.0.zip封裝。


## 建立及設定AEM網站預設集

1. **建立新的預設集：**
   1. 在AEM Guides中開啟DITA map並導覽至&#x200B;**輸出**&#x200B;面板。
   2. 選取&#x200B;**建立預設集**。
   3. 選取型別為&#x200B;**AEM Sites**。
   4. 輸入預設集名稱。
   5. 取消勾選&#x200B;**使用舊版元件對應**&#x200B;設定。
   6. 選取&#x200B;**新增**&#x200B;以建立預設集。

      ![新的輸出預設集對話方塊](/help/product-guide/knowledge-base/kb-articles/assets/publishing/new-output-preset.png){width="350" align="left"}


2. **設定AEM網站預設集：**&#x200B;有兩個選項可設定現成可用的網站(OOTB)：

   **選項1：使用網站下拉式清單**

   1. 選取&#x200B;**網站**&#x200B;作為&#x200B;**AEMG檔案**。
   2. 確認&#x200B;**發佈路徑**&#x200B;和&#x200B;**主題頁面範本**&#x200B;已自動設定為：
      - 發佈路徑： `aemg-docs/en/docs/product1`
      - 主題頁面範本：主題頁面。

      ![使用網站下拉式清單](/help/product-guide/knowledge-base/kb-articles/assets/publishing/use-site-dropdown.png){width="350" align="left"}

   **選項2：使用網站路徑**

   1. 手動將&#x200B;**網站路徑**&#x200B;設定為`/content/aemg-docs/en/docs/product1`。
   2. 確認&#x200B;**主題頁面範本**&#x200B;已自動設定為主題頁面。

      ![使用網站路徑](/help/product-guide/knowledge-base/kb-articles/assets/publishing/use-site-path.png){width="350" align="left"}

3. **儲存預設集：**&#x200B;儲存對預設集所做的變更。

## 產生AEM Sites

1. **產生網站：**
   1. 設定預設集後，您現在可以為對應的DITA map產生AEM網站。
   2. 產生的網站將可在以下路徑使用： `/content/aemg-docs/en/docs/product1`。
2. **變更預設產生路徑（選用）：**&#x200B;若要變更網站產生的預設路徑，請執行下列步驟：

   1. 導覽至&#x200B;**AEM Sites**。
   2. 在OOTB網站結構下建立新產品頁面。
   3. 導覽至&#x200B;**AEMG檔案** > **英文** > **檔案**。

      ![在AEM網站結構](/help/product-guide/knowledge-base/kb-articles/assets/publishing/create-new-page.png){width="350" align="left"}中建立頁面

   4. 選取&#x200B;**首頁**&#x200B;圖磚，然後選取&#x200B;**下一步**。

      ![選取首頁拼貼](/help/product-guide/knowledge-base/kb-articles/assets/publishing/home-page-tile.png){width="350" align="left"}

   5. 輸入頁面的&#x200B;**標題**&#x200B;和&#x200B;**名稱**。
   6. 選取「**建立**」。
