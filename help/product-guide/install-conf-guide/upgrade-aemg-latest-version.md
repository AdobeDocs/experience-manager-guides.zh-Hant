---
title: 升級Adobe Experience Manager Guides
description: 瞭解如何升級Adobe Experience Manager Guides
feature: Installation
role: Admin
level: Experienced
source-git-commit: 453da51a42984b912547570f2e1de70806b41171
workflow-type: tm+mt
source-wordcount: '1661'
ht-degree: 0%

---

# 升級Adobe Experience Manager Guides 4.6.0版及更新版本

本文提供將Experience Manager Guides 4.6.0及更高版本升級的說明。

>[!NOTE]
>
> 請依照產品的授權版本專屬的升級指示操作。

您可以將目前的Experience Manager Guides版本升級至5.1.0 Service Pack 3版：

- 如果您是使用5.1.0版或5.1.x版，則可以直接升級至5.1.0 Service Pack 3版。
- 如果您使用的是4.6.0、4.6.x、5.0.0或5.0.x版，則需要升級至5.1.0版。
- 如果您使用4.6.0之前的版本，請參閱[升級Adobe Experience Manager Guides 4.4.0和更早版本](./upgrade-aemg-prev-versions.md)的詳細升級指示。

>[!NOTE]
>
> 您必須先安裝AEM Service Pack，才能升級Experience Manager Guides版本。

如需詳細資訊，請參閱下列程式：

- [升級至5.1.0版](#upgrade-to-version-510)
- [升級至5.0.0版](#upgrade-to-version-500)
- [升級至4.6.0版](#upgrade-to-version-460)

>[!IMPORTANT]
>
> 在開始升級之前，請先進行完整的系統備份，以避免任何資料遺失。


## 升級至5.1.0版


>[!IMPORTANT]
>
> 如果您目前使用AEM 6.5，並計畫改用AEM 6.5 LTS，在繼續升級AEM 5.1.0之前，請務必先完成Experience Manager Guides升級。 如需詳細資訊，請檢視[升級至Adobe Experience Manager (AEM) 6.5 LTS](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-65-lts/content/implementing/deploying/upgrading/upgrade)。

**先決條件**

>[!NOTE]
>
>如果您升級至5.1.0 Service Pack 3，則需使用5.1.0或5.1.x版的Experience Manager Guides。 5.1.0 Service Pack 3版本的升級程式遵循與5.1.0版本相同的步驟。

在開始Experience Manager Guides 5.1.0升級程式之前，請確定您擁有：

1. 已升級至Experience Manager Guides 4.6.3、4.6.4、5.0.0或5.0.0 Service Pack 1版。
1. （選用）已關閉所有翻譯工作。
1. 已將&#x200B;**類別的記錄層級變更為** INFO`com.adobe.fmdita.translationservices.TranslationMapUpgradeScript`，並將這些記錄附加至新的記錄檔，例如`logs/translation_upgrade.log`。

>[!NOTE]
>
> 後期處理和索引可能需要幾個小時。 我們建議您在非尖峰時段開始升級程式。

**安裝5.1.0**&#x200B;版

從[Adobe軟體發佈入口網站](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)下載5.1.0版套件，並按照[安裝與後續安裝升級工作流程](#installation-and-post-installation-upgrade-workflow)中提供的指示完成升級程式。


## 升級至5.0.0版

>[!TIP]
>
> 升級至5.0.0 Service Pack 3版須視目前Experience Manager Guides的版本而定。 如果您是使用5.0.0 Service Pack 2、5.0.0 Service Pack 1或5.0.0版，則可以直接升級至5.0.0 Service Pack 3版。 升級步驟與5.0.0版的相同。

>[!NOTE]
>
> 後期處理和索引可能需要幾個小時。 我們建議您在非尖峰時段開始升級程式。

**先決條件**

在開始Experience Manager Guides 5.0.0升級程式之前，請確定您擁有：

1. 升級至Experience Manager Guides 4.6.3、4.6.1、4.6.0或4.4版。
1. （選用）已關閉所有翻譯工作。
1. 已將&#x200B;**類別的記錄層級變更為** INFO`com.adobe.fmdita.translationservices.TranslationMapUpgradeScript`，並將這些記錄附加至新的記錄檔，例如`logs/translation_upgrade.log`。


**安裝5.0.0**&#x200B;版

從[Adobe軟體發佈入口網站](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)下載5.0.0版套件，並按照[安裝與後續安裝升級工作流程](#installation-and-post-installation-upgrade-workflow)中提供的指示完成升級程式。

## 升級至4.6.0版

>[!TIP]
>
> 建議您在4.6.0、4.6.0 Service Pack 1或4.6.0 Service Pack 3版之上安裝4.6.0 Service Pack 4。 4.6.0 Service Pack 4版本的升級程式遵循與4.6.0版本相同的步驟。

升級至4.6.0版須視目前的Experience Manager Guides版本而定。 如果您是使用4.4.0、4.3.1、4.3.0、4.2或4.2.1版(Hotfix 4.2.1.3)，可以直接升級至4.6.0版。

>[!NOTE]
>
> 後期處理和索引可能需要幾個小時。 我們建議您在非尖峰時段開始升級程式。

**先決條件**

在開始Experience Manager Guides 4.6.0升級程式之前，請確定您擁有：

1. 已升級至Experience Manager Guides 4.3.1、4.3.0或4.2.1版(Hotfix 4.2.1.3)。
1. （選用）已關閉所有翻譯工作。
1. 已將&#x200B;**類別的記錄層級變更為** INFO`com.adobe.fmdita.translationservices.TranslationMapUpgradeScript`，並將這些記錄附加至新的記錄檔，例如`logs/translation_upgrade.log`。

**安裝4.6.0**&#x200B;版

從[Adobe軟體發佈入口網站](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)下載4.6.0版套件，並按照[安裝與後續安裝升級工作流程](#installation-and-post-installation-upgrade-workflow)中提供的指示完成升級程式。

## 安裝和安裝後升級工作流程

### 安裝版本套件

執行以下步驟來安裝版本套件：

1. 安裝您要升級的版本套件。
1. 您可以選擇點選觸發器，以開始翻譯對應升級工作。 如需詳細資訊，請參閱[透過Servlet啟用指令碼的觸發程式](#enable-trigger-of-script-via-a-servlet)。

1. 完成套件安裝後，請等候記錄中的下列訊息：

   `Completed the post deployment setup script`

   上述訊息表示安裝的所有步驟均已完成。

   如果您遇到下列任何錯誤，請向客戶成功團隊報告：

   - 部署後安裝指令碼發生錯誤
   - 移植翻譯MAP時發生例外狀況
   - 無法將屬性的轉譯對應從v1連線至v2
1. （選用）升級氧氣聯結器外掛程式，隨要升級至的版本發行。
1. 安裝套件後清除瀏覽器快取。

### 安裝後程式

安裝Experience Manager Guides後，您可以將適用於新安裝版本的各種設定合併到您的設定中。

>[!NOTE]
>
> 可以自訂dam-update-asset模型。 因此，如果已完成任何自訂，則需要將自訂和Experience Manager Guides同步到模型的工作副本中。

**DAM更新資產工作流程\（後續處理變更\）：**

1. 開啟URL：

   ```
   http://localhost:4502/libs/cq/workflow/admin/console/content/models.html 
   ```

1. 選取&#x200B;**DAM更新資產工作流程**。
1. 選取&#x200B;**編輯**。
1. 如果&#x200B;**DXML後續程式啟動器**&#x200B;元件存在，請確定自訂已同步。
1. 如果&#x200B;**DXML後續處理啟動器**&#x200B;元件不存在，請執行下列步驟以插入它：

   - 選取&#x200B;**插入元件** \（負責Experience Manager Guides後續處理，作為程式的最後步驟\）。
   - 使用下列詳細資料設定&#x200B;**處理序步驟**：

     **一般標籤：**

      - **標題：** DXML後續程式發起人

      - **描述**： DXML後續處理啟動器步驟將觸發已修改/建立的資產的DXML後續處理的Sling工作

     **處理標籤**

      - 從&#x200B;**程式**&#x200B;下拉式清單中選取&#x200B;**DXML程式後啟動器**
      - 選取&#x200B;**處理常式進階**
      - 選取&#x200B;**完成**

1. 完成變更後，在右上角選取&#x200B;**同步**。 您將會收到成功通知。

   >[!NOTE]
   >
   > 重新整理並確認自訂變更和Experience Manager Guides後處理步驟存在於最終工作流程模型中。

1. 驗證&#x200B;**DAM更新資產工作流程**&#x200B;後，請檢查對應的啟動器設定。 若要這麼做，請前往AEM工作流程介面並開啟啟動器。

   ```http
   http://localhost:4502/libs/cq/workflow/content/console.html
   ```

   尋找下列兩個啟動器\（若有需要\）並進行變更\（應該為作用中\），其對應至&#x200B;**DAM更新資產工作流程**：

1. 已針對&#x200B;*DAM更新資產工作流程*&#x200B;建立「**節點**」的啟動器 — 對於條件`"jcr:content/jcr:mimeType!=video"`，「萬用字元」值應為：

   ```json
   /content/dam(/((?!/subassets|/translation_output).)*/)renditions/original
   ```

   - &#39;excludeList&#39;應該有`"event-user-data:changedByWorkflowProcess"`。
   - 針對&#x200B;*DAM更新資產工作流程 —*&#x200B;的「**節點已修改**」的啟動器（條件「`jcr:content/jcr:mimeType!=video`」），「萬用字元」值應為：

   ```json
   /content/dam(/((?!/subassets|/translation_output).)*/)renditions/original
   ```

   - `excludeList`應該有`"event-user-data:changedByWorkflowProcess"`。

1. 升級完成後，請確定所有自訂/覆蓋圖均已驗證並更新，以符合新的應用程式程式碼。 以下提供一些範例：
   - 從`/libs/fmditaor/libsshould`重疊的所有元件都會與新的產品程式碼進行比較，而且更新應該在/apps下的重疊檔案中完成。
   - 任何從產品中使用的`clientlib`類別都應該檢閱是否有變更。 任何覆寫的設定`\(examples below\)`應該與最新的設定比較，以取得最新的功能：
   - elementmapping.xml
   - `ui\_config.json\(may have been set in folder profiles\)`
   - 已修改`com.adobe.fmdita.config.ConfigManager`

1. 如果您已在damAssetLucene中新增任何自訂，您可能需要再次套用它們。 進行這些變更後，將重新索引設定為true。 這會使用自訂重新索引所有現有節點。 完成後，重新索引標幟將再次設定為false。 視系統中的資產數量而定，這可能需要幾個小時的時間。

### 重新索引Experience Manager Guides索引的步驟

1. 開啟`crx/de`並導覽至索引路徑： `/oak:index/guidesAssetProperties`
2. 將重新索引屬性設定為`true` （預設為`false`），然後按一下&#x200B;**全部儲存**。
3. 重新索引完成後，重新索引屬性會再次設定為`false`，而重新索引計數會增加1。

   >[!NOTE]
   >
   > 視資料數量而定，這可能需要幾分鐘的時間。
4. 對其他新增或修改的索引執行相同的步驟： `guidesBulkActivation`、`guidesPeerLinkIndex`和`guidesKonnectTemplateIndex`。

### 索引現有內容的步驟

執行以下步驟來索引現有內容：

- 對伺服器執行POST要求\（使用正確的驗證\） - `http://<server:port\>/bin/guides/map-find/indexing`。 （選用：您可以傳遞地圖的特定路徑來編列索引，預設情況下，所有地圖都會編列索引||範例： `https://<Server:port\>/bin/guides/map-find/indexing?paths=<map\_path\_in\_repository\>`）

- API將傳回`jobId`。 若要檢查工作的狀態，您可以將具有工作識別碼的GET要求傳送至相同的端點 — `http://<server:port\>/bin/guides/map-find/indexing?jobId=\{jobId\}`\（例如： ` http://localhost:8080/bin/guides/map-find/indexing?jobId=2022/9/15/7/27/7dfa1271-981e-4617-b5a4-c18379f11c42_678`）

- 工作完成後，上述GET要求將回應為成功，並提及是否有任何地圖失敗。 可以從伺服器記錄檔確認已成功編制索引的對應。


>[!NOTE]
>
> 如果您使用自訂結構描述，您必須在&#x200B;**整合目錄**&#x200B;選項中，定義AEM儲存庫中自訂DTD和XSD catalog.xml檔案的路徑。

### 處理`'fmdita rewriter'`衝突的步驟

Experience Manager Guides有&#x200B;[**自訂sling重寫程式**](../install-conf-guide/conf-output-generation.md#custom-rewriter)&#x200B;模組，可處理交叉對映時產生的連結（兩個不同對映之主題之間的連結）。

如果您的程式碼基底中有另一個自訂Sling重寫程式，請使用大於50的`'order'`值，因為Experience Manager Guides Sling重寫程式使用`'order'` 50。  若要覆寫此值，您需要大於50的值。 如需詳細資訊，請檢視[輸出重寫管道](https://sling.apache.org/documentation/bundles/output-rewriting-pipelines-org-apache-sling-rewriter.html)。

在此升級期間，由於`'order'`值從1000變更為50，因此您必須將現有的自訂重寫程式（若有的話）與`'fmdita-rewriter'`合併。


### 重新索引damAssetLucene的步驟

已使用AEM Guides更新damAssetLucene的索引定義。 升級至所需版本後，請參閱[本文章](https://experienceleague.adobe.com/zh-hant/docs/experience-cloud-kcs/kbarticles/ka-16460)以重新索引damAssetLucene。

>[!NOTE]
>
> 在依照檔案操作時，請確定透過儲存作業同時更新兩個屬性（`reindex=true`的`reindex-async=true`和`/oak:index/damAssetLucene`）。

