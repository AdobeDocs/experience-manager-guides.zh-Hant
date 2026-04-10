---
title: 升級Adobe Experience Manager Guides On Premise舊版
description: 瞭解如何升級Adobe Experience Manager Guides
feature: Installation
role: Admin
level: Experienced
source-git-commit: 6f3f05419f4f5cdd45ab580cdee6fa869f20f01d
workflow-type: tm+mt
source-wordcount: '3159'
ht-degree: 0%

---

# 升級Adobe Experience Manager Guides On Premise （4.4.0版及舊版）

本文提供將&#x200B;**Adobe Experience Manager Guides** 4.6.0 **之前的**&#x200B;版本(最高至（包括）**4.4.0**)升級的說明。

如果您使用3.8.5 **之前的**&#x200B;版本，請參閱&#x200B;**Experience Manager Guides說明PDF封存**&#x200B;上產品特定安裝指南中的[升級Adobe Experience Manager Guides](https://helpx.adobe.com/tw/xml-documentation-for-experience-manager/archive.html)一節。

如需較新版本的升級指示，請參閱[升級Adobe Experience Manager Guides 4.6.0和更高版本](./upgrade-aemg-latest-version.md)。

## 開始之前

>[!NOTE]
>
> 您必須先升級產品授權版本的特定指示，並安裝AEM Service Pack，才能升級Experience Manager Guides版本。

>[!IMPORTANT]
>
> 開始升級之前，請先進行&#x200B;**完整的系統備份**，以避免資料遺失。

## 本文章所述的升級路徑

本文包括下列程式：

- [升級至4.4.0版](#upgrade-to-version-440)
- [升級至版本4.3.1.5](#upgrade-to-version-4315)
- [升級至4.3.1版](#upgrade-to-version-431)
- [升級至4.3.0版](#upgrade-to-version-430)
- [升級至4.2.1版](#upgrade-to-version-421)
- [升級至4.2版](#upgrade-to-version-42)
- [從3.8.5升級至4.0版](#upgrade-from-version-385-to-version-40)


## 全域先決條件（除非程式另有說明，否則適用於所有升級）

在執行升級程式之前，請先完成下列工作：

1. 在開放供稽核的主題中匯入稽核註釋。
2. 關閉所有作用中的評論。
3. 關閉所有翻譯任務。
4. 解除安裝先前版本（主要或修補程式版本）上安裝的所有Experience Manager Guides Hotfix。

部分升級還需要將翻譯升級類別的記錄層級設定為`INFO`，並記錄至個別檔案；這些要求會在相關升級程式中列出。

## 從3.8.5版升級至4.0版

>[!NOTE]
>
> 此升級程式只適用於&#x200B;**從** 3.8.5 **到** 4.0 **的**。 如需從&#x200B;**3.4或更新版本**&#x200B;升級至&#x200B;**3.8.5**，請參閱[Adobe Experience Manager Guides說明PDF封存](https://helpx.adobe.com/tw/xml-documentation-for-experience-manager/archive.html)中提供的產品特定安裝指南。

如果您使用Experience Manager Guides版本&#x200B;**3.8.5**，您可以升級至版本&#x200B;**4.0**，而不需要解除安裝先前的版本。

### 安裝4.0版之前

1. 請確定Experience Manager Guides的版本為&#x200B;**3.8.5**。
2. 下載升級指令碼套件：在XML Documentation軟體發佈入口網站上搜尋&#x200B;**&quot;Adobe解決方案4.0升級套件&quot;** （下載`.zip`）。
3. 透過&#x200B;**封裝管理員**&#x200B;將封裝上傳至AEM並進行安裝。
4. 安裝升級套件後，請依照下列順序執行指令碼。

**檢查升級相容性API**

此API的設計目的是評估目前的系統狀態，並報告升級是否可行。 若要執行此指令碼，請觸發以下指定的端點：

| 端點 | /bin/dxml/upgrade/3xto4x/report |
| --- | --- |
| 請求型別 | **GET** <br> **注意**：您可以使用網頁瀏覽器，以管理員身分登入AEM執行個體。 |
| 預期回應 | -   如果可以移動所有必要的節點，您將會獲得通過檢查。 <br>-   如果目標位置出現節點，您會看到相關錯誤。 清理存放庫\（刪除節點/var/dxml\）並重新安裝升級套件，然後再次觸發此端點。 <br>**注意：**&#x200B;這不是常見的錯誤，因為3.x Experience Manager Guides之前未使用目標位置。 <br> -   如果此指令碼失敗，請勿繼續並報告給您的客戶成功團隊。 |

**系統資料移轉API**

此API的設計用途是移轉&#x200B;**移轉對應**&#x200B;區段中提到的系統資料。

1. 如果Check upgrade compatibility API失敗，請勿執行此指令碼\（不要繼續\）。
1. 一旦Check upgrade compatibility API傳回成功，您就可以執行升級指令碼。

| 端點 | /bin/dxml/upgrade/3xto4x |
| --- | --- |
| 請求型別 | **POST** <br>**注意**：此指令碼為POST要求，因此應透過Postman之類的代理程式執行。 |
| 預期回應 | -   一旦移轉成功，您就可以安裝XML Documentation解決方案4.0版。<br>-   如果發生錯誤，請還原至最後一個查核點，並與您的客戶成功團隊共用錯誤記錄檔及API輸出。 |


**移轉對應**

此API會將來源位置下的所有資料移轉至目標位置。

| 來源 | 目標 |
|------|------|
| /content/fmdita | /var/dxml |
| /content/dxml | /var/dxml |
| /etc/fmdita | /libs/fmdita |

### 安裝4.0版

1. 只有在升級步驟成功時才安裝4.0版。
1. 從[Adobe軟體發佈入口網站](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)下載4.0版套件：

   - 如果您使用UUID版本的軟體，請搜尋「適用於AEM 6.5的XML Documentation解決方案的4.0 UUID版本」。
   - 如果您使用非UUID版本的軟體，請搜尋「適用於AEM 6.5的XML Documentation解決方案非UUID版本4.0」。
使用AEM封裝管理員將封裝上傳到現有的CRX伺服器執行個體並進行安裝。

     >[!NOTE]
     >
     > 等待所有系統元件啟動。

1. 安裝套件後清除瀏覽器快取。
1. 如果在AEM Author例項上設定Dispatcher，請執行以下步驟：
   - 請確定下列專案已在Dispatcher規則中處理：
   - URL模式/home/users/\*/preferences已加入白名單。
   - 不會快取URL模式/libs/cq/security/userinfo.json 。
1. 清除Dispatcher快取\（以清除任何`clientlibs`快取\）。

## 升級至4.2版

如果您使用版本&#x200B;**4.0**、**4.1**&#x200B;或&#x200B;**4.1.x**，可以直接升級為版本&#x200B;**4.2**。

### 安裝4.2版之前

在開始Experience Manager Guides 4.2升級程式之前，請確定您擁有：

1. 已升級至Experience Manager Guides **4.0**、**4.1**&#x200B;或&#x200B;**4.1.x**。
2. 已關閉所有翻譯任務。
3. 將`INFO`的記錄層級設定為`com.adobe.fmdita.translationservices.TranslationMapUpgradeScript`，並記錄至新的記錄檔（例如，`logs/translation_upgrade.log`）。

   >[!NOTE]
   > 
   > 您應該關閉所有作用中的評論。 若在升級至4.2時檢閱並未關閉，較舊的進行中檢閱任務可以繼續開啟較舊的檢閱頁面；升級後建立的新檢閱任務會顯示最新的功能更新。

### 安裝4.2版

1. 從&#x200B;**Adobe軟體發佈入口網站**&#x200B;下載[4.2](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)套件。
2. 安裝4.2套件。
3. 安裝後，請等待記錄檔中的下列訊息：

   `Completed the post deployment setup script`

   上述訊息指出所有安裝步驟均已完成。

   如果您遇到下列任何錯誤，請向客戶成功回報：

   - `Error in post deployment setup script`
   - `Exception while porting the translation MAP`
   - `Unable to port translation map from v1 to v2 for property`

4. （選用）升級氧氣聯結器外掛程式隨版本4.2發行。
5. 安裝套件後清除瀏覽器快取。
6. 繼續升級自訂，如下一節所述。

### 安裝版本4.2之後

>[!IMPORTANT]
>
> 升級後的伺服器上未顯示高科技範本。 若要在伺服器上加入高科技範本，您可以複製它： Source： `/libs/fmdita/pdf/Hi-Tech`目的地： `/content/dam/dita-templates/pdf`。

然後繼續進行[常見的升級後工作（所有版本）](#common-postupgrade-tasks-all-versions)中的共用升級後工作。

## 升級至4.2.1版

>[!TIP]
>
> 建議在版本&#x200B;**4.2.14.2.1.3**&#x200B;之上安裝&#x200B;**Hotfix**。

如果您使用&#x200B;**4.1**、**4.1.x**&#x200B;或&#x200B;**4.2**，可以直接升級為&#x200B;**4.2.1**&#x200B;版。

>[!NOTE]
>
> 後期處理和索引可能需要幾個小時。 在非尖峰時段開始升級。

### 安裝4.2.1版之前

1. 升級至Experience Manager Guides **4.1**、**4.1.x**&#x200B;或&#x200B;**4.2**。
2. 關閉所有翻譯任務。
3. 將`INFO`的記錄層級設定為`com.adobe.fmdita.translationservices.TranslationMapUpgradeScript`，並記錄至新檔案（例如，`logs/translation_upgrade.log`）。

>[!NOTE]
>
> 您應該關閉所有作用中的評論（與4.2的行為相同）。

### 安裝4.2.1版

1. 從&#x200B;**Adobe軟體發佈入口網站**&#x200B;下載[4.2.1](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)套件。
2. 安裝4.2.1套件。
3. 選擇性地觸發翻譯對應升級工作。 如需詳細資訊，請參閱[透過Servlet啟用指令碼的觸發程式](#enable-trigger-of-script-via-a-servlet)。

4. 安裝之後，在記錄中等候： `Completed the post deployment setup script`。

   向客戶成功報告這些錯誤：

   - `Error in post deployment setup script`
   - `Exception while porting the translation MAP`
   - `Unable to port translation map from v1 to v2 for property`
5. （選用）升級氧氣聯結器外掛程式隨版本&#x200B;**4.2**&#x200B;發行
6. 清除瀏覽器快取。
7. 繼續執行[常見的升級後工作（所有版本）](#common-postupgrade-tasks-all-versions)。

### 安裝版本4.2.1之後

>[!IMPORTANT]
>
> 升級後的伺服器上未顯示高科技範本。 若要在伺服器上加入高科技範本，您可以複製它： Source： `/libs/fmdita/pdf/Hi-Tech`目的地： `/content/dam/dita-templates/pdf`。

繼續進行[常見的升級後工作（所有版本）](#common-postupgrade-tasks-all-versions)及（如果需要）[為現有內容編制索引，以尋找及取代](#index-existing-content-for-map-find-and-replace)。


## 升級至4.3.0版

升級至4.3.0版須視目前的Experience Manager Guides版本而定。 如果您是使用4.2或4.2.x版，則可以直接升級至4.3.0版。

>[!NOTE]
>
>後期處理和索引可能需要幾個小時。 我們建議您在非尖峰時段開始升級程式。

### 安裝4.3.0版之前

在開始Experience Manager Guides 4.3.0升級程式之前，請確定您擁有：

1. 已升級至Experience Manager Guides 4.2或4.2.x版，並完成各自的安裝步驟。
1. 已關閉所有翻譯任務。

### 安裝4.3.0版

1. 從[Adobe軟體發佈入口網站](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)下載4.3.0版本的套件。
1. 安裝4.3.0版本的套件。
1. 安裝套件後清除瀏覽器快取。
1. 從資料夾設定檔中的`ui_config.json`XML編輯器組態&#x200B;**索引標籤升級**&#x200B;檔案。

### 安裝4.3.0版之後

繼續進行：

- [常見的升級後工作（所有版本）](#common-postupgrade-tasks-all-versions)
- 如果適用： [針對中斷的連結報告後處理現有內容](#post-process-existing-content-for-broken-link-report)

## 升級至4.3.1版

升級至4.3.1版須視目前的Experience Manager Guides版本而定。 如果您是使用4.3.0、4.2或4.2.1版，則可以直接升級至4.3.1版。

>[!NOTE]
>
>後期處理和索引可能需要幾個小時。 我們建議您在非尖峰時段開始升級程式。

### 安裝4.3.1版之前

在開始Experience Manager Guides 4.3.1升級程式之前，請確定您擁有：

1. 已升級至Experience Manager Guides 4.3.0、4.2或4.2.1版，並完成各自的安裝步驟。
1. （選用）已關閉所有翻譯工作。
1. 已將&#x200B;**類別的記錄層級變更為** INFO`com.adobe.fmdita.translationservices.TranslationMapUpgradeScript`，並將這些記錄附加至新的記錄檔，例如`logs/translation_upgrade.log`。

### 安裝4.3.1版

1. 從[Adobe軟體發佈入口網站](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)下載4.3.1版本的套件。
1. 安裝4.3.1版本的套件。
1. 選擇性地觸發翻譯對應升級工作。 如需詳細資訊，請參閱[透過Servlet啟用指令碼的觸發程式](#enable-trigger-of-script-via-a-servlet)。
1. 安裝之後，在記錄中等候： `Completed the post deployment setup script`。
向客戶成功報告這些錯誤：\
   `Error in post deployment setup script`、`Exception while porting the translation MAP`、`Unable to port translation map from v1 to v2 for property`
1. （選用）升級氧氣聯結器外掛程式隨版本&#x200B;**4.2**&#x200B;發行。
1. 清除瀏覽器快取。

### 安裝4.3.1版之後

繼續進行：

- [常見的升級後工作（所有版本）](#common-postupgrade-tasks-all-versions)
- 如果適用： [為地圖尋找與取代的現有內容編制索引](#index-existing-content-for-map-find-and-replace)
- 如果適用： [針對中斷的連結報告後處理現有內容](#post-process-existing-content-for-broken-link-report)


## 升級至版本4.3.1.5

如果您使用版本&#x200B;**4.3.1.5** 4.3.1 **，可以直接升級至**。

### 安裝版本4.3.1.5

1. 從&#x200B;**4.3.1.5** Adobe軟體發佈入口網站[下載](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)套件。
2. 安裝4.3.1.5封裝。
3. 請等候安裝程式順利完成。
4. 繼續升級自訂，如下一節所述。

## 安裝版本4.3.1.5之後

>[!NOTE]
>
>如果您想使用org.apache.velocity套件組合，請於上傳套件組合前執行下列步驟：
> 1. 前往`<server>:<port>/system/console/bundles`
> 1. 搜尋org.apache.velocity。
> 1. 解除安裝搜尋的套件組合。
> 1. 安裝所需的Velocity套件。

1. 升級完成後，請確定所有自訂/覆蓋圖均已驗證並更新，以符合新的應用程式程式碼。 以下提供一些範例：
   - 任何從`/libs/fmdita`或` /libs`覆寫的元件都應與新的產品程式碼進行比較，且更新應在`/apps`下的覆寫檔案中完成。
   - 產品中使用的任何clientlib類別都應檢閱是否有變更。 任何覆寫的設定\（範例如下\）都應與最新的設定進行比較，以取得最新的功能：
   - `elementmapping.xml`
   - `ui\_config.json\` （可能已在資料夾設定檔中設定\）
   - 已修改`com.adobe.fmdita.config.ConfigManager`


## 升級至4.4.0版

如果您使用： **4.3.1**、**4.3.0**、**4.2**&#x200B;或&#x200B;**4.2.1 (Hotfix**)**，可以直接升級至4.2.1.34.4.0**。

>[!NOTE]
>
>後期處理和索引可能需要幾個小時。 我們建議您在非尖峰時段開始升級程式。

### 安裝4.4.0版之前

在開始Experience Manager Guides 4.4.0升級程式之前，請確定您擁有：

1. 已升級至Experience Manager Guides 4.3.1、4.3.0或4.2.1版(Hotfix 4.2.1.3)，並已完成各自的安裝步驟。
1. （選用）已關閉所有翻譯工作。
1. 已將&#x200B;**類別的記錄層級變更為** INFO`com.adobe.fmdita.translationservices.TranslationMapUpgradeScript`，並將這些記錄附加至新的記錄檔，例如`logs/translation_upgrade.log`。

### 安裝4.4.0版

1. 從[Adobe軟體發佈入口網站](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)下載4.4.0版套件。
2. 安裝4.4.0套件。
3. 選擇性地觸發翻譯對應升級工作。 如需詳細資訊，請參閱[透過Servlet啟用指令碼的觸發程式](#enable-trigger-of-script-via-a-servlet)。
4. 完成套件安裝後，請等候記錄中的下列訊息：

   `Completed the post deployment setup script`

   上述訊息表示安裝的所有步驟均已完成。

   如果您遇到以下任何錯誤首碼，請向您的客戶成功團隊報告：

   - `Error in post deployment setup script`
   - `Exception while porting the translation MAP`
   - `Unable to port translation map from v1 to v2 for property`
5. （選用）升級氧氣聯結器外掛程式隨版本&#x200B;**4.4.0**&#x200B;發行。
6. 清除瀏覽器快取。
7. 繼續使用：

   - [常見的升級後工作（所有版本）](#common-ppostupgrade-tasks-all-versions)
   - [為地圖尋找和取代的現有內容編制索引](#index-existing-content-for-map-find-and-replace) （適用時適用）
   - [針對中斷的連結報告](#post-process-existing-content-for-broken-link-report)後續處理現有內容（僅適用時）
   - [翻譯對應升級（servlet觸發程式）](#translation-map-upgrade-servlet-trigger) （適用時）


## 常見的升級後工作（所有版本）

安裝Experience Manager Guides後，您可能需要將適用於新安裝版本的設定合併到您的設定中。

>[!NOTE]
>
> 可自訂&#x200B;**DAM更新資產**&#x200B;工作流程模型。 如果您有自訂，請將其與模型工作副本中的Experience Manager Guides變更同步。

### 驗證DAM更新資產工作流程（後處理變更）

1. 開啟AEM工作流程模型UI （來源中顯示的範例）：\
   `http://<host>:4502/libs/cq/workflow/admin/console/content/models.html`
2. 選取&#x200B;**DAM更新資產工作流程**。
3. 選取&#x200B;**編輯**。
4. 如果&#x200B;**DXML後續程式啟動器**&#x200B;元件存在，請確定自訂已同步。
5. 如果元件不存在，請插入它：
   1. 按一下&#x200B;**插入元件** （負責指南後續處理作為最後步驟）。
   2. 設定&#x200B;**處理序步驟**：
      **一般標籤**
 — 標題： `DXML Post Process Initiator`
 — 描述： `DXML post process initiator step which will trigger a sling job for DXML post-processing of the modified/created asset`
      **處理標籤**
 — 處理序：選取`DXML Post Process Initiator`
 — 選取`Handler Advance`
 — 選取`Done`
   3. 完成變更後，請按一下右上角的&#x200B;**同步**。 您將會收到成功通知。

>[!NOTE]
>
> 重新整理並確認自訂變更和Experience Manager Guides後處理步驟存在於最終工作流程模型中。

### 驗證啟動器設定

1. 前往AEM工作流程介面並開啟&#x200B;**啟動器**。

```http
    http://localhost:4502/libs/cq/workflow/content/console.html
```

1. 尋找下列兩個啟動器\（若有需要\）並進行變更\（應該為作用中\），其對應至&#x200B;**DAM更新資產工作流程**：

1. 已針對&#x200B;*DAM更新資產工作流程*&#x200B;建立「**節點**」的啟動器 — 對於條件`"jcr:content/jcr:mimeType!=video"`，「萬用字元」值應為：

   ```json
   /content/dam(/((?!/subassets|/translation_output).)*/)renditions/original
   ```

   - `excludeList`應該有`"event-user-data:changedByWorkflowProcess"`。
   - 已針對&#x200B;*DAM更新資產工作流程 —* （條件&quot;**&quot;）修改**&#x200B;節點`jcr:content/jcr:mimeType!=video`的啟動器，「萬用字元」值應為：

   ```json
   /content/dam(/((?!/subassets|/translation_output).)*/)renditions/original
   ```

   - `excludeList`應該有`"event-user-data:changedByWorkflowProcess"`。

### 驗證覆蓋圖與自訂

升級完成後：

1. 升級完成後，請確定所有自訂/覆蓋圖均已驗證並更新，以符合新的應用程式程式碼。 以下提供一些範例：
   - 從/libs/fmditor/libsis覆寫的任何元件都應與新的產品程式碼進行比較，且更新應在/apps下方的覆寫檔案中完成。
   - 產品中使用的任何clientlib類別都應檢閱是否有變更。 任何覆寫的設定\（範例如下\）都應與最新的設定進行比較，以取得最新的功能：
   - elementmapping.xml
   - ui\_config.json\（可能已在資料夾設定檔中設定\）
   - 已修改`com.adobe.fmdita.config.ConfigManager`

1. 如果您已在damAssetLucene中新增任何自訂，您可能需要再次套用它們。 進行這些變更後，將重新索引設定為true。 這會使用自訂重新索引所有現有節點。 完成後，重新索引標幟將再次設定為false。 視系統中的資產數量而定，這可能需要幾個小時的時間。

## 為地圖尋找和取代的現有內容編制索引

此區段整合用於啟用新&#x200B;**地圖層級尋找和取代**&#x200B;功能的重複&#x200B;**索引**&#x200B;程式。

**當您可以略過索引時**

根據您的升級路徑，來源包含「略過」備註（例如「如果您從4.3.0或4.3.1升級，則不需要執行這些步驟」以及類似的備註）。 請依照升級一節中所述的略過說明操作。

執行以下步驟來索引現有內容，並在地圖層級使用新的尋找和取代文字：

1. 執行POST要求（使用驗證）：

```http
POST http://<server:port>/bin/guides/map-find/indexing
```

來源支援的選用引數：

- 索引特定對應路徑（預設為索引所有對應）：

  ```http
  POST http://<server:port>/bin/guides/map-find/indexing?paths=<map_path_in_repository>
  ```

- 在根資料夾（及其子資料夾）下編制索引DITA map：

  ```http
  POST http://<server:port>/bin/guides/map-find/indexing?root=/content/dam/test
  ```

  >[!NOTE]
  >
  > 如果同時傳遞`paths`和`root`，則只會考慮`paths`。

1. api傳回`jobId`。 若要檢查狀態，請傳送GET要求：

   ```http
   GET http://<server:port>/bin/guides/map-find/indexing?jobId={jobId}
   ```

   預期完成行為：

   - 完成後，GET會回應成功，並指出是否有任何地圖失敗。
   - 在伺服器記錄檔中確認已成功建立對應索引。

### 確保damAssetLucene索引完整（如適用）

來源備註指出，根據資料大小，damAssetLucene索引可能需要數小時，而且您可以在`reindex`位於以下位置時`false`確認完成：

`http://<server:port>/oak:index/damAssetLucene`

如果您在`damAssetLucene`中新增自訂，則可能需要在重新索引完成後再次套用它們。

### 「查詢讀取或周遊超過100000個節點」（如果作業失敗）的因應措施

如果索引工作失敗且錯誤顯示：

「查詢讀取或周遊了超過100000個節點。 為了避免影響其他工作，已停止處理。」

從來源嘗試此因應措施：

1. 在`damAssetLucene` Oak索引中，在`indexNodeName=true`中新增布林值屬性`/oak:index/damAssetLucene/indexRules/dam:Asset`。
2. 在`excerpt`下新增名為`/oak:index/damAssetLucene/indexRules/dam:Asset/properties`的新節點，並設定如來源中所示的屬性：
   - `name=rep:excerpt`
   - `propertyIndex=true`
   - `notNullCheckEnabled=true`
3. 透過設定`damAssetLucene`重新索引`reindex=true`並等候它再次變成`false` （可能需要數小時）。
4. 再次重新執行索引指令碼（重複POST和工作追蹤）。

## 針對失效連結報告後續處理現有內容

此區段整合用於啟用&#x200B;**中斷連結報告**&#x200B;的重複&#x200B;**後處理**&#x200B;程式。

**何時可以略過後處理**

根據您的升級路徑，來源包含「略過」備註（例如「如果您從4.3.0升級」、「從4.3.0或4.3.1」升級，則不需要執行這些步驟）。 請依照升級一節中所述的略過說明操作。

執行以下步驟來啟用中斷連結報表：

1. （選用）為大型存放庫增加Oak queryLimitReads

   如果有超過&#x200B;**100,000個DITA檔案**，請將`queryLimitReads`下的`org.apache.jackrabbit.oak.query.QueryEngineSettingsService`更新為大於資產數的值（範例： `200000`）、重新部署並繼續。

   | PID | 屬性索引鍵 | 屬性值 |
   |---|---|---|
   | org.apache.jackrabbit.oak.query.QueryEngineSettingsService | querylimitereads | 值： 200000 <br>預設值： 100000 |

1. 執行下列API以對所有檔案執行後續處理：

   | 端點 | /bin/guides/reports/upgrade |
   |---|---|
   | 請求型別 | **POST**&#x200B;此指令碼為POST要求，因此應透過Postman等代理程式執行。 |
   | 預期回應 | 此API將傳回jobId。 若要檢查作業的狀態，您可以將具有作業ID的GET請求傳送至相同的端點。<br>範例URL： `http://<server:port>/bin/guides/reports/upgrade` |

   | 端點 | /bin/guides/reports/upgrade |
   |---|---|
   | 請求型別 | **GET** |
   | 引數 | jobId：傳遞從上一個post請求收到的jobId。 |
   | 預期回應 |  — 工作完成後，GET要求會成功回應。 <br> — 如果發生錯誤，請和您的客戶成功團隊共用錯誤記錄檔以及API輸出。  <br>範例URL： `http://<server:port>/bin/guides/reports/upgrade?jobId=2022/9/15/7/27/7dfa1271-981e-4617-b5a4-c18379f11c42_678` |

1. 如果您在步驟1中變更了`queryLimitReads`的值，請恢復為預設值或先前的現有值。

## 透過Servlet啟用指令碼的觸發

數個版本包含可選步驟，可透過servlet觸發翻譯對應升級工作。 本節整合重複程式，並包含來源中提供的所有詳細資訊。


>[!NOTE]
>
> 如果您從4.3.0或4.3.1升級，則不需要執行這些步驟。

張貼：

```
http://localhost:4503/bin/guides/script/start?jobType=translation-map-upgrade
```

回應：

```
{
"msg": "Job is successfully submitted and lock node is created for future reference",
"lockNodePath": "/var/dxml/executor-locks/translation-map-upgrade/1683190032886",
"status": "SCHEDULED"
}
```

在上述回應JSON中，索引鍵`lockNodePath`保留在存放庫中建立之節點的路徑，指向已提交的工作。 它會在作業完成後自動刪除，在此之前，您可以參照此節點來瞭解作業的目前狀態。

繼續後續步驟前，請尋找`com.adobe.fmdita.translationservices.TranslationMapUpgradeScript Completed porting of translation map from V1 to V2`和`com.adobe.fmdita.xmltranslation.ots.TranslationMapUpgradeOTS Completed the thread to upgrade translation map from V1 to V2`。

>[!NOTE]
>
> 您應該檢查節點是否仍然存在以及工作的狀態。

**GET**： `http://<aem_domain>/var/dxml/executor-locks/translation-map-upgrade/1683190032886.json`


### 處理「fmdita重寫程式」衝突的步驟

Experience Manager Guides包含自訂Sling重寫程式模組(`fmditarewriter`)，用於處理針對跨對應連結產生的連結。

如果您的程式碼基底中有另一個自訂Sling重寫程式：

- 使用大於50`order`的&#x200B;**值**，因為參考線使用`order=50`。
- 在此升級期間，`order`值會從`1000`變更為`50`，因此您必須將現有的自訂重寫程式（如果有的話）與`fmditarewriter`合併。

