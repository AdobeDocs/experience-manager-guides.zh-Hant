---
title: 升級Adobe Experience Manager Guides
description: 瞭解如何升級Adobe Experience Manager Guides
exl-id: f058b39f-7408-4874-942b-693e133886cf
feature: Installation
role: Admin
level: Experienced
source-git-commit: f43d8d01a9c3b29328641680f3ba7d96ce7ecd79
workflow-type: tm+mt
source-wordcount: '8023'
ht-degree: 0%

---

# 升級Adobe Experience Manager Guides {#id224MBE0M0XA}

>[!NOTE]
>
> 請依照產品的授權版本專屬的升級指示操作。

您可以將目前的Experience Manager Guides版本升級至5.0.0版：


- 如果您使用的是版本 4.6.x、4.6 或 4.4，則可以直接升級到版本 5.0.0。
- 如果您是使用4.3.x、4.2、4.2.1 (Hotfix 4.2.1.3)、4.1或4.1.x版，則必須先升級至4.4版，才能升級至5.0.0版。
- 如果您使用的是4.0版，則必須先升級至4.2版，才能升級至4.3.x版。
- 如果您使用的是3.8.5版，則必須先升級至4.0版，才能升級至4.2版。
- 如果您使用的版本早於3.8.5，請參閱[Adobe Experience Manager Guides說明Experience Manager Guides封存](https://helpx.adobe.com/xml-documentation-for-experience-manager/archive.html)中提供的產品特定安裝指南中的「升級PDF」一節。


>[!NOTE]
>
> 您必須先安裝AEM Service Pack，才能升級Experience Manager Guides版本。

有關更多詳細資訊，請參閱以下過程：

- [從 3.8.5 升級至 4.0 版](#upgrade-from-version-385-to-version-40)
- [升級至 4.2 版](#upgrade-to-version-42)
- [升級到版本 4.2.1](#upgrade-to-version-421)
- [升級至 4.3.0 版](#upgrade-to-version-430)
- [升級至4.3.1版](#upgrade-to-version-431)
- [升級至版本4.3.1.5](#upgrade-to-version-4315)
- [升級至4.4.0版](#upgrade-to-version-440)
- [升級至4.6.0版](#upgrade-to-version-460)
- [升級至5.0.0版](#upgrade-to-version-500)



>[!IMPORTANT]
>
> 在開始升級之前，請先進行完整的系統備份，以避免任何資料遺失。

## 從3.8.5版升級至4.0版

如果您使用的是Experience Manager Guides 3.8.5版，則可升級至Experience Manager Guides 4.0版。 使用升級功能，您不必解除安裝舊版Experience Manager Guides。

在執行程式之前，您必須先完成某些工作。 以下小節將逐步引導您瞭解先決條件、報表產生和移轉程式。 此外，安裝Experience Manager Guides 4.0版後，您可以根據客戶設定自訂各種設定。

>[!NOTE]
>
> 此升級程式僅適用於3.8.5版到4.0版。如需從3.4版或更新版本升級至3.8.5的程式，請參閱[Experience Manager Guides說明PDF封存](https://helpx.adobe.com/xml-documentation-for-experience-manager/archive.html)中提供的產品特定安裝指南中的&#x200B;*升級Adobe Experience Manager Guides*&#x200B;一節。



****必備條件****

在開始Experience Manager Guides升級程式之前，請確定您擁有：

1. 已匯入開啟供稽核之主題中的稽核註釋。
1. 已關閉所有進行中的評論。
1. 關閉所有翻譯任務。
1. 解除安裝安裝在Experience Manager Guides舊版\（主要或修補版本\）頂端的Experience Manager Guides Hotfix。

**安裝 4.0 版之前**

在安裝版本 4.0 之前，請執行以下步驟：

1. 確保此時 Experience Manager Guides 使用的是版本 3.8.5。
1. 下載升級腳本包。 為此，搜尋軟體分發門戶](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)上的[“XML 文件解決方案 4.0 升級包”Adobe Systems該包將下載 zip 文件。
1. 透過封裝管理員將此封裝上傳至AEM並安裝此封裝。
1. 安裝升級套件後，請以相同順序執行下列指定指令碼，並依照指定指示執行：

**檢查升級相容性API**

此 API 旨在評估當前系統狀態並報告是否可以升級。 若要運行此腳本，請觸發以下給定終結點：

| 端點 | /bin/dxml/upgrade/3xto4x/report |
| --- | --- |
| 請求型別 | **GET**&#x200B;您可以使用網頁瀏覽器，以管理員身分登入AEM執行個體。 |
| 預期回應 | -   如果可以移動所有必要的節點，您將會獲得通過檢查。 <br>-   如果目標位置出現節點，您會看到相關錯誤。 清理存放庫\（刪除節點/var/dxml\）並重新安裝升級套件，然後再次觸發此端點。 <br>**注意：**&#x200B;這不是常見的錯誤，因為3.x Experience Manager Guides之前未使用目標位置。 <br> -   如果此指令碼失敗，請勿繼續並報告給您的客戶成功團隊。 |

**系統資料移轉API**

此API的設計用途是移轉&#x200B;**移轉對應**&#x200B;區段中提到的系統資料。

1. 如果Check upgrade compatibility API失敗，請勿執行此指令碼\（不要繼續\）。
1. 一旦Check upgrade compatibility API傳回成功，您就可以執行升級指令碼。

| 端點 | /bin/dxml/upgrade/3xto4x |
| --- | --- |
| 請求型別 | **POST**&#x200B;此指令碼為POST要求，因此應透過Postman等代理程式執行。 |
| 預期回應 | -   一旦移轉成功，您就可以安裝XML Documentation解決方案4.0版。<br>-   如果發生錯誤，請還原至最後一個查核點，並與您的客戶成功團隊共用錯誤記錄檔及API輸出。 |

**移轉對應**：上述API會將來源位置下的所有資料移轉到目標位置。

| 來源 | 目標 |
|------|------|
| /content/fmdita | /var/dxml |
| /內容/dxml | /var/dxml |
| /etc/fmdita | /libs/fmdita |

## 安裝4.0版 {#id23598G006XA}

1. 只有在升級步驟成功時才安裝4.0版。
1. 從軟體分發門戶](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)下載 [4.0 版本包Adobe Systems：

   - 如果您使用的是 UUID 版本的軟體，請搜尋“XML 的 4.0 UUID 發行版文件 AEM 6.5 的解決方案”。
   - 如果您使用的是非 UUID 版本的軟體，請搜尋“XML 的 4.0 非 UUID 發行版文件 AEM 6.5 的解決方案”。使用 CRX 封裝管理員將套件上載到現有 AEM 伺服器 執行個體\（s\） 並安裝。

   >[!NOTE]
   >
   > 等待所有系統元件開始。

1. 安裝包后清除瀏覽器快取。
1. 如果在AEM Author例項上設定Dispatcher，請執行以下步驟：
   - 請確定下列專案已在Dispatcher規則中處理：
   - URL模式/home/users/\*/preferences已加入白名單。
   - 不會快取URL模式/libs/cq/security/userinfo.json 。
1. 清除Dispatcher快取\（以清除任何`clientlibs`快取\）。

## 升級至4.2版

升級至版本4.2取決於目前的Experience Manager Guides版本。

如果您是使用4.0、4.1或4.1.x版，則可以直接升級至4.2版。

****必備條件****

在開始Experience Manager Guides 4.2升級程式之前，請確定您擁有：

1. 已升級至Experience Manager Guides 4.0、4.1或4.1.x版。
1. 已關閉所有翻譯任務。
1. 已將`com.adobe.fmdita.translationservices.TranslationMapUpgradeScript`類別的記錄層級變更為&#x200B;**INFO**，並將這些記錄附加至新的記錄檔，例如`logs/translation_upgrade.log.`

>[!NOTE]
>
> 您應該關閉所有作用中的評論。 若在升級至4.2時未關閉稽核任務，則舊版進行中的稽核任務會持續將使用者帶入舊版稽核頁面，且升級後建立的稽核任務會在功能中顯示最新的更新。

## 安裝4.2版 {#id2245IK0E0EV}

1. 從[Adobe軟體發佈入口網站](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)下載4.2版本的套件。
1. 安裝 4.2 版套件。
1. 完成套件安裝後，請等待日誌中的以下消息\（s\）：

   `Completed the post deployment setup script`

   上述消息表示所有安裝步驟均已完成。

   如果您遇到以下任何 ERROR 前綴，請將其報告給您的客戶成功團隊：

   - 貼文部署安裝程式腳本中錯誤
   - 移植翻譯MAP時發生例外狀況
   - 無法將屬性的轉譯對應從v1連線至v2
1. 升級 Oxygen 連接器外掛程式隨版本 4.2 一起發佈\（如果需要\）。
1. 安裝包后清除瀏覽器快取。
1. 繼續升級自定義項，如下一節所述。

## 安裝 4.2 版之後 {#id2326F02004K}

>[!IMPORTANT]
>
> 升級後的伺服器上未顯示高科技範本。 若要在伺服器上加入高科技範本，您可以複製該範本： Source： /libs/fmdita/pdf/Hi-Tech Destination： /content/dam/dita-templates/pdf

安裝Experience Manager Guides後，您可以將適用於新安裝版本的各種設定合併到您的設定中。

>[!NOTE]
>
> 可以自訂dam-update-asset模型。 因此，如果已完成任何自訂，則需要將自訂和Experience Manager Guides同步到模型的工作副本中。

1. **DAM更新資產工作流程\（後續處理變更\）：**

1. 開啟URL：

   ```http
   http://localhost:4502/libs/cq/workflow/admin/console/content/models.html
   ```

1. 選取&#x200B;**DAM更新資產工作流程**。
1. 按一下&#x200B;**編輯**。
1. 如果&#x200B;**DXML後續程式啟動器**&#x200B;元件存在，請確定自訂已同步。
1. 如果&#x200B;**DXML後續處理啟動器**&#x200B;元件不存在，請執行下列步驟以插入它：

1. 按一下「**插入元件**」\(負責Experience Manager Guides後續處理，作為程式的最後一個步驟\)。
1. 使用下列詳細資料設定&#x200B;**處理序步驟**：

   **一般標籤**

   **標題：** DXML後續程式發起人

   **描述**： DXML後續處理啟動器步驟將觸發已修改/建立的資產的DXML後續處理的Sling工作

   **處理標籤**

   - 從&#x200B;**程式**&#x200B;下拉式清單中選取&#x200B;**DXML程式後啟動器**

   - 選取&#x200B;**處理常式進階**

   - 選取&#x200B;**完成**

1. 完成變更後，請按一下右上角的&#x200B;**同步**。 您將會收到成功通知。

   >[!NOTE]
   >
   > 重新整理並確認自訂變更和Experience Manager Guides後處理步驟存在於最終工作流程模型中。

1. 驗證DAM更新資產工作流程&#x200B;**后**，請檢查對應的啟動器配置。為此，請轉到AEM工作流介面並打開啟動器。

   ```http
   http://localhost:4502/libs/cq/workflow/content/console.html
   ```

   尋找下列兩個啟動器\（若有需要\）並進行變更\（應該為作用中\），其對應至&#x200B;**DAM更新資產工作流程**：

1. 已針對&#x200B;**DAM更新資產工作流程**&#x200B;建立「*節點*」的啟動器 — 對於條件`"jcr:content/jcr:mimeType!=video"`，「萬用字元」值應為：

   ```json
   /content/dam(/((?!/subassets|/translation_output).)*/)renditions/original
   ```

   - &#39;excludeList&#39;應該有`"event-user-data:changedByWorkflowProcess"`。
   - 已針對&#x200B;**DAM更新資產工作流程 —** （適用於條件&quot;`jcr:content/jcr:mimeType!=video`&quot;）修改&#x200B;*節點*&#x200B;的啟動器，
   - 「通配符」值應為：

   ```json
   /content/dam(/((?!/subassets|/translation_output).)*/)renditions/original
   ```

   - &#39;excludeList&#39; 應該有 `"event-user-data:changedByWorkflowProcess"`.
1. 升級完成後，請確定所有自訂/覆蓋圖均已驗證並更新，以符合新的應用程式程式碼。 以下提供一些範例：
   - 從/libs/fmditor/libsis覆寫的任何元件都應與新的產品程式碼進行比較，且更新應在/apps下方的覆寫檔案中完成。
   - 應檢視產品中使用的任何 clientlib 類別是否有變更。 任何被覆蓋的配置\（下面的示例\）應與最新版本進行比較，以獲得最新功能：
   - elementmapping.xml
   - ui\_config.json\（可能已在資料夾設定檔中設定\）
   - 已修改`com.adobe.fmdita.config.ConfigManager`
   - 檢查是否有任何自訂程式碼使用任何舊路徑\（如[移轉對應](#id2244LE040XA)區段中所述\） — 應更新為新路徑，讓自訂功能也能如預期運作。
1. 閱讀最新版本中的任何新設定\（請參閱[發行說明](../release-info/release-notes-4-3.md)\），檢視是否有任何功能受到影響，然後採取適當的動作。 例如使用4.0版中引進的「改善檔案和版本處理」，您需要為此啟用設定。

## 為現有內容建立索引以使用新尋找和取代的步驟：

執行以下步驟來索引現有內容，並在地圖層級使用新的尋找和取代文字：

- 對伺服器執行POST要求\（使用正確的驗證\） - `http://<server:port\>/bin/guides/map-find/indexing`。 \(可選：您可以傳遞地圖的特定路徑來為其建立索引，預設情況下，所有地圖都會建立索引\|\| 例如： `https://<Server:port\>/bin/guides/map-find/indexing?paths=<map\_path\_in\_repository\>`\)

- 此API將傳回jobId。 若要檢查作業的狀態，您可以將具有作業ID的GET請求傳送至相同的端點 — 

`http://<server:port\>/bin/guides/map-find/indexing?jobId=\{jobId\}`\（例如： `http://localhost:8080/bin/guides/map-find/indexing?jobId=2022/9/15/7/27/7dfa1271-981e-4617-b5a4-c18379f11c42`\）

- 工作完成後，上述GET要求將回應為成功，並提及是否有任何地圖失敗。 可以從伺服器記錄檔確認已成功編制索引的對應。

如果升級作業失敗，錯誤記錄會顯示下列錯誤：

「*查詢*&#x200B;讀取或周遊超過&#x200B;*100000個節點*。 為了避免影響其他工作，已停止處理。」

因為未針對升級中使用的查詢正確設定索引，所以可能發生這種情況。 您可以嘗試以下解決方法：

1. 在damAssetLucene橡木指數中，添加布爾屬性 `indexNodeName` ，如 `true` 節點。
   `/oak:index/damAssetLucene/indexRules/dam:Asset`
1. 在節點下添加名稱為摘錄的新節點。

   `/oak:index/damAssetLucene/indexRules/dam:Asset/properties`並在 節點 中設置以下屬性：

   ```
   name - rep:excerpt
   propertyIndex - {Boolean}true
   notNullCheckEnabled - {Boolean}true
   ```

   的結構 `damAssetLucene` 應該看起來像按讚：

   ```
   <damAssetLucene compatVersion="{Long}2" async="async, nrt" jcr:primaryType="oak:QueryIndexDefinition" evaluatePathRestrictions="{Boolean}true" type="lucene">
   <indexRules jcr:primaryType="nt:unstructured">
     <dam:Asset indexNodeName="{Boolean}true" jcr:primaryType="nt:unstructured">
       <properties jcr:primaryType="nt:unstructured">
         <excerpt name="rep:excerpt" propertyIndex="{Boolean}true" jcr:primaryType="nt:unstructured" notNullCheckEnabled="{Boolean}true"/>
       </properties>
       </dam:Asset>
     </indexRules>
   </damAssetLucene>    
   ```


   （以及其他現有節點和屬性）

1. 重新索引`damAssetLucene`索引(透過將重新索引旗標設定為`true`，在
並等待它重新`false` （這表示重新索引已完成）。 請注意，視索引大小而定，這可能需要幾個小時。
1. 通過執行前面的步驟再次運行索引腳本。


## 升級到版本 4.2.1

>[!TIP]
>
>建議在版本 4.2.1 之上安裝修補程式 4.2.1.3 。

是否升級至 4.2.1 版取決於 Experience Manager 指南的當前版本。 如果您是使用4.1版、4.1.x版或4.2版，則可以直接升級至4.2.1版。

>[!NOTE]
>
>後期處理和索引可能需要幾個小時。 我們建議您在非尖峰時段開始升級程式。

****必備條件****

在開始Experience Manager Guides 4.2.1升級程式之前，請確定您擁有：

1. 升級至Experience Manager Guides 4.1、4.1.x或4.2版。
1. 已關閉所有翻譯任務。
1. 已將`com.adobe.fmdita.translationservices.TranslationMapUpgradeScript`類別的記錄層級變更為&#x200B;**INFO**，並將這些記錄附加至新的記錄檔，例如`logs/translation_upgrade.log.`

>[!NOTE]
>
> 您應該關閉所有作用中的評論。 若在升級至4.2時未關閉稽核任務，則舊版進行中的稽核任務會持續將使用者帶入舊版稽核頁面，且升級後建立的稽核任務會在功能中顯示最新的更新。

## 安裝4.2.1版

1. 從[Adobe軟體發佈入口網站](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)下載4.2.1版套件。
1. 安裝4.2.1版本的套件。
1. 您可以選擇點選觸發器，以啟動翻譯對應升級工作。 如需詳細資訊，請參閱[透過Servlet啟用指令碼的觸發程式](#enable-trigger-of-script-via-a-servlet-for-421)。


1. 完成套件安裝後，請等候記錄中的下列訊息：

   `Completed the post deployment setup script`

   上述訊息表示安裝的所有步驟均已完成。

   如果您遇到以下任何錯誤首碼，請向您的客戶成功團隊報告：

   - 部署後安裝指令碼發生錯誤
   - 移植翻譯MAP時發生例外狀況
   - 無法將屬性的轉譯對應從v1連線至v2
1. 升級氧氣聯結器外掛程式，隨版本4.2發行\（如有需要\）。
1. 安裝套件後清除瀏覽器快取。
1. 繼續升級自訂，如下一節所述。

### 透過Servlet啟用指令碼觸發（適用於4.2.1）

發佈：

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

在上述回應 JSON 中，鍵 `lockNodePath` 保存指向提交的作業的存放庫中創建的節點的路徑。 作業完成後，它將自動刪除，在此之前，您可以參考此節點了解作業的當前狀態。

紀錄範例：
以下為觸發指令碼後，記錄檔中顯示的記錄範例。

```
04.05.2023 14:17:12.876 *INFO* [[0:0:0:0:0:0:0:1] [1683190032736] POST /bin/guides/script/start HTTP/1.1] com.adobe.dxml.common.executor.RunnableSynchronizedOTS Acquiring lock for job : translation-map-upgrade
04.05.2023 14:17:12.897 *INFO* [pool-59-thread-1] com.adobe.fmdita.xmltranslation.ots.TranslationMapUpgradeOTS Starting the thread to upgrade translation map from V1 to V2
04.05.2023 14:17:12.899 *INFO* [pool-59-thread-1] com.adobe.dxml.common.executor.RunnableSynchronizedOTS Initiating lock for node : /var/dxml/executor-locks/translation-map-upgrade/1683190032886
04.05.2023 14:17:12.901 *INFO* [pool-59-thread-1] com.adobe.fmdita.translationservices.TranslationMapUpgradeScript Starting porting of translation map from V1 to V2
04.05.2023 14:17:12.904 *INFO* [pool-59-thread-1] com.adobe.fmdita.translationservices.TranslationMapUpgradeScript Memory increase is of : 764 kB
04.05.2023 14:17:12.906 *INFO* [pool-59-thread-1] com.adobe.fmdita.translationservices.TranslationMapUpgradeScript Completed porting of translation map from V1 to V2
04.05.2023 14:17:12.907 *INFO* [pool-59-thread-1] com.adobe.dxml.common.executor.RunnableSynchronizedOTS Releasing lock for node : /var/dxml/executor-locks/translation-map-upgrade/1683190032886
04.05.2023 14:17:12.909 *INFO* [pool-59-thread-1] com.adobe.fmdita.xmltranslation.ots.TranslationMapUpgradeOTS Completed the thread to upgrade translation map from V1 to V2
```

繼續後續步驟前，請尋找`com.adobe.fmdita.translationservices.TranslationMapUpgradeScript Completed porting of translation map from V1 to V2`和`com.adobe.fmdita.xmltranslation.ots.TranslationMapUpgradeOTS Completed the thread to upgrade translation map from V1 to V2`。



## 安裝4.2.1版之後

>[!IMPORTANT]
>
> 升級後的伺服器上未顯示高科技範本。 要在伺服器上包含高科技範本，您可以複製它： 來源： /libs/fmdita/pdf/Hi-Tech 目的地： /內容/dam/dita-templates/pdf

安裝 Experience Manager 指南後，您可以將適用於新安裝版本的各種配置合併到您的設置中。

>[!NOTE]
>
> 可以自定義 dam-update-資產 模型。 因此，如果已完成任何自定義，則需要將自定義和Experience Manager指南同步到模型的工作副本中。

1. **DAM更新資產工作流程\（後續處理變更\）：**

1. 開啟URL：

   ```http
   http://localhost:4502/libs/cq/workflow/admin/console/content/models.html
   ```

1. 選取&#x200B;**DAM更新資產工作流程**。
1. 按一下&#x200B;**編輯**。
1. 如果&#x200B;**DXML後續程式啟動器**&#x200B;元件存在，請確定自訂已同步。
1. 如果&#x200B;**DXML後續處理啟動器**&#x200B;元件不存在，請執行下列步驟以插入它：

1. 按一下「**插入元件**」\(負責Experience Manager Guides後續處理，作為程式的最後一個步驟\)。
1. 使用下列詳細資料設定&#x200B;**處理序步驟**：

   **一般標籤**

   **標題：** DXML後續程式發起人

   **描述**： DXML後續處理啟動器步驟將觸發已修改/建立的資產的DXML後續處理的Sling工作

   **處理標籤**

   - 從&#x200B;**程式**&#x200B;下拉式清單中選取&#x200B;**DXML程式後啟動器**

   - 選取&#x200B;**處理常式進階**

   - 選取&#x200B;**完成**

1. 完成變更後，請按一下右上角的&#x200B;**同步**。 您將收到成功通知。

   >[!NOTE]
   >
   > 重新整理並驗證最終工作流程模型中是否存在自定義更改和Experience Manager指南貼文處理步驟。

1. 驗證DAM更新資產工作流程&#x200B;**后**，請檢查對應的啟動器配置。為此，請轉到AEM工作流介面並打開啟動器。

   ```http
   http://localhost:4502/libs/cq/workflow/content/console.html
   ```

   查找並更改與「更新資產」工作流程對應的以下 **兩個啟動器 \（應處於活動狀態DAM**）：

1. 用於 DAM 更新資產 工作流程&#x200B;**- 的「*節點已建立*」**&#x200B;啟動器 ，「`"jcr:content/jcr:mimeType!=video"`通配符」值應為：

   ```json
   /content/dam(/((?!/subassets|/translation_output).)*/)renditions/original
   ```

   - &#39;excludeList&#39;應該有`"event-user-data:changedByWorkflowProcess"`。
   - 針對&#x200B;**DAM更新資產工作流程 —**&#x200B;的「*節點已修改*」的啟動器（條件「`jcr:content/jcr:mimeType!=video`」），「萬用字元」值應為：

   ```json
   /content/dam(/((?!/subassets|/translation_output).)*/)renditions/original
   ```

   - `excludeList` 應該有 `"event-user-data:changedByWorkflowProcess"`.

1. 升級完成後，請確保驗證並更新任何自定義/疊加以匹配新的應用程式代碼。 下面給出了一些範例：
   - 任何覆蓋自/libs/fmditaor/libs的元件都應與新產品代碼進行比較，並且更新應在/apps下的疊加檔中完成。
   - 產品中使用的任何clientlib類別都應檢閱是否有變更。 任何覆寫的設定\（範例如下\）都應與最新的設定進行比較，以取得最新的功能：
   - elementmapping.xml
   - ui\_config.json\（可能已在資料夾設定檔中設定\）
   - 已修改`com.adobe.fmdita.config.ConfigManager`
   - 檢查是否有任何自訂程式碼使用任何舊路徑\（如[移轉對應](#id2244LE040XA)區段中所述\） — 應更新為新路徑，讓自訂功能也能如預期運作。
1. 閱讀最新版本中的任何新設定\（請參閱[發行說明](../release-info/release-notes-4-2-1.md)\），檢視是否有任何功能受到影響，然後採取適當的動作。 例如使用4.0版中引進的「改善檔案和版本處理」，您需要為此啟用設定。

## 為現有內容建立索引以使用新尋找和取代的步驟：

執行以下步驟來索引現有內容，並在地圖層級使用新的尋找和取代文字：

- 請確定`damAssetLucene`索引已完成。 視伺服器上呈現的資料量而定，最多可能需要幾個小時。 您可以透過檢查中重新索引欄位是否設定為false來確認重新索引已完成
  `http://<server:port>/oak:index/damAssetLucene`。  此外，如果您已在`damAssetLucene`中新增任何自訂，您可能需要再次套用它們。

- 對伺服器執行POST要求\（使用正確的驗證\） - `http://<server:port\>/bin/guides/map-find/indexing`。 (選用：您可以傳遞地圖的特定路徑來編列索引，預設情況下，所有地圖都會編列索引\|\| 例如： `https://<Server:port\>/bin/guides/map-find/indexing?paths=<map\_path\_in\_repository\>`)

- 您也可以傳遞根資料夾，為特定資料夾（及其子資料夾）的DITA map建立索引。 例如 `http://<server:port\>/bin/guides/map-find/indexing?root=/content/dam/test`。請注意，如果同時傳遞路徑引數和根引數，則只會考慮路徑引數。

- 此API將傳回jobId。 若要檢查工作的狀態，您可以將具有工作識別碼的GET要求傳送至相同的端點 — `http://<server:port\>/bin/guides/map-find/indexing?jobId=\{jobId\}`\（例如： `http://localhost:8080/bin/guides/map-find/indexing?jobId=2022/9/15/7/27/7dfa1271-981e-4617-b5a4-c18379f11c42`\）


- 工作完成後，上述GET要求將回應為成功，並提及是否有任何地圖失敗。 可以從伺服器記錄檔確認已成功編制索引的對應。


## 升級至4.3.0版

升級至4.3.0版須視目前的Experience Manager Guides版本而定。 如果您是使用4.2或4.2.x版，則可以直接升級至4.3.0版。

>[!NOTE]
>
>後期處理和索引可能需要幾個小時。 我們建議您在非尖峰時段開始升級程式。

****必備條件****

在開始 Experience Manager指南 4.3.0 升級過程之前，請確保您已：

1. 已升級至 Experience Manager Guides 4.2 或 4.2.x 版，並完成各自的安裝步驟。
1. 關閉所有翻譯任務。



## 安裝4.3.0版

1. 從[Adobe軟體發佈入口網站](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)下載4.3.0版本的套件。
1. 安裝4.3.0版本的套件。
1. 安裝套件後清除瀏覽器快取。
1. 從資料夾設定檔中的&#x200B;**XML編輯器組態**&#x200B;索引標籤升級`ui_config.json`檔案。


## 安裝 4.3.0 版之後

安裝Experience Manager Guides後，您可以將適用於新安裝版本的各種設定合併到您的設定中。

## 後續處理現有內容以使用中斷連結報告的步驟


執行以下步驟後續處理現有內容並使用新的中斷連結報表：

1. （選擇性）如果系統中有超過100,000個dita檔案，請將`org.apache.jackrabbit.oak.query.QueryEngineSettingsService`下的`queryLimitReads`更新為較大的值（任何大於現有資產數的值，例如200,000），然後重新部署。

   | PID | 屬性索引鍵 | 屬性值 |
   |---|---|---|
   | org.apache.jackrabbit.oak.query.QueryEngineSettingsService | querylimitereads | 值： 200000 <br>預設值： 100000 |

1. 執行下列API以對所有檔案執行後續處理：

   | 端點 | /bin/guides/reports/upgrade |
   |---|---|
   | 請求型別 | **POST**&#x200B;此指令碼為POST要求，因此應透過Postman等代理程式執行。 |
   | 預期回應 | 此API將傳回jobId。 要檢查作業的狀態，可以將具有作業 ID 的GET 要求發送到同一端點。<br> 樣本URL： `http://<server:port>/bin/guides/reports/upgrade` |

   | 端點 | /bin/guides/reports/upgrade |
   |---|---|
   | 請求類型 | **獲取** |
   | 引數 | jobId：傳遞從上一個post請求收到的jobId。 |
   | 預期回應 |  — 工作完成後，GET要求會成功回應。 <br> — 如果發生錯誤，請和您的客戶成功團隊共用錯誤記錄檔以及API輸出。  <br>範例URL： `http://<server:port>/bin/guides/reports/upgrade?jobId=2022/9/15/7/27/7dfa1271-981e-4617-b5a4-c18379f11c42_678` |


1. 如果您在步驟1中變更了`queryLimitReads`的值，請恢復為預設值或先前的現有值。



## 升級至4.3.1版

升級至4.3.1版須視目前的Experience Manager Guides版本而定。 如果您是使用4.3.0、4.2或4.2.1版，則可以直接升級至4.3.1版。

>[!NOTE]
>
>後期處理和索引可能需要幾個小時。 我們建議您在非尖峰時段開始升級程式。

****必備條件****

在開始Experience Manager Guides 4.3.1升級程式之前，請確定您擁有：

1. 已升級至Experience Manager Guides 4.3.0、4.2或4.2.1版，並完成各自的安裝步驟。
1. （選用）已關閉所有翻譯工作。
1. 已將`com.adobe.fmdita.translationservices.TranslationMapUpgradeScript`類別的記錄層級變更為&#x200B;**INFO**，並將這些記錄附加至新的記錄檔，例如`logs/translation_upgrade.log`。


## 安裝4.3.1版

1. 從[Adobe軟體發佈入口網站](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)下載4.3.1版本的套件。
1. 安裝4.3.1版本的套件。
1. 您可以選擇點選觸發器，以啟動翻譯對應升級工作。 如需詳細資訊，請參閱[透過Servlet啟用指令碼的觸發程式](#enable-trigger-of-script-via-a-servlet-for-431)。


1. 完成套件安裝後，請等候記錄中的下列訊息：

   `Completed the post deployment setup script`

   上述訊息表示安裝的所有步驟均已完成。

   如果您遇到以下任何錯誤首碼，請向您的客戶成功團隊報告：

   - 部署後安裝指令碼發生錯誤
   - 移植翻譯MAP時發生例外狀況
   - 無法將屬性的轉譯對應從v1連線至v2
1. 升級氧氣聯結器外掛程式，隨版本4.2發行\（如有需要\）。
1. 安裝套件後清除瀏覽器快取。
1. 繼續升級自訂，如下一節所述。

### 透過 Servlet 啟用指令觸發 （適用於 4.3.1）

發佈：

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

在上述回應 JSON 中，鍵 `lockNodePath` 保存指向提交的作業的存放庫中創建的節點的路徑。 作業完成後，它將自動刪除，在此之前，您可以參考此節點了解作業的當前狀態。

紀錄範例：
以下為觸發指令碼後，記錄檔中顯示的記錄範例。

```
04.05.2023 14:17:12.876 *INFO* [[0:0:0:0:0:0:0:1] [1683190032736] POST /bin/guides/script/start HTTP/1.1] com.adobe.dxml.common.executor.RunnableSynchronizedOTS Acquiring lock for job : translation-map-upgrade
04.05.2023 14:17:12.897 *INFO* [pool-59-thread-1] com.adobe.fmdita.xmltranslation.ots.TranslationMapUpgradeOTS Starting the thread to upgrade translation map from V1 to V2
04.05.2023 14:17:12.899 *INFO* [pool-59-thread-1] com.adobe.dxml.common.executor.RunnableSynchronizedOTS Initiating lock for node : /var/dxml/executor-locks/translation-map-upgrade/1683190032886
04.05.2023 14:17:12.901 *INFO* [pool-59-thread-1] com.adobe.fmdita.translationservices.TranslationMapUpgradeScript Starting porting of translation map from V1 to V2
04.05.2023 14:17:12.904 *INFO* [pool-59-thread-1] com.adobe.fmdita.translationservices.TranslationMapUpgradeScript Memory increase is of : 764 kB
04.05.2023 14:17:12.906 *INFO* [pool-59-thread-1] com.adobe.fmdita.translationservices.TranslationMapUpgradeScript Completed porting of translation map from V1 to V2
04.05.2023 14:17:12.907 *INFO* [pool-59-thread-1] com.adobe.dxml.common.executor.RunnableSynchronizedOTS Releasing lock for node : /var/dxml/executor-locks/translation-map-upgrade/1683190032886
04.05.2023 14:17:12.909 *INFO* [pool-59-thread-1] com.adobe.fmdita.xmltranslation.ots.TranslationMapUpgradeOTS Completed the thread to upgrade translation map from V1 to V2
```

繼續後續步驟前，請尋找`com.adobe.fmdita.translationservices.TranslationMapUpgradeScript Completed porting of translation map from V1 to V2`和`com.adobe.fmdita.xmltranslation.ots.TranslationMapUpgradeOTS Completed the thread to upgrade translation map from V1 to V2`。

## 安裝4.3.1版之後



安裝 Experience Manager 指南後，您可以將適用於新安裝版本的各種配置合併到您的設置中。

>[!NOTE]
>
> 可以自定義 dam-update-資產 模型。 因此，如果已完成任何自定義，則需要將自定義和Experience Manager指南同步到模型的工作副本中。

1. **DAM更新資產工作流程\（後續處理變更\）：**

1. 開啟URL：

   ```
   http://localhost:4502/libs/cq/workflow/admin/console/content/models.html 
   ```

1. 選取&#x200B;**DAM更新資產工作流程**。
1. 按一下&#x200B;**編輯**。
1. 如果&#x200B;**DXML後續程式啟動器**&#x200B;元件存在，請確定自訂已同步。
1. 如果&#x200B;**DXML後續處理啟動器**&#x200B;元件不存在，請執行下列步驟以插入它：

1. 按一下「**插入元件**」\(負責Experience Manager Guides後續處理，作為程式的最後一個步驟\)。
1. 使用下列詳細資料設定&#x200B;**處理序步驟**：

   **一般標籤**

   **標題：** DXML後續程式發起人

   **描述**： DXML後續處理啟動器步驟將觸發已修改/建立的資產的DXML後續處理的Sling工作

   **處理標籤**

   - 從&#x200B;**程式**&#x200B;下拉式清單中選取&#x200B;**DXML程式後啟動器**

   - 選取&#x200B;**處理常式進階**

   - 選取&#x200B;**完成**

1. 完成變更後，請按一下右上角的&#x200B;**同步**。 您將會收到成功通知。

   >[!NOTE]
   >
   > 重新整理並確認自訂變更和Experience Manager Guides後處理步驟存在於最終工作流程模型中。

1. 驗證&#x200B;**DAM更新資產工作流程**&#x200B;後，請檢查對應的啟動器設定。 若要這麼做，請前往AEM工作流程介面並開啟啟動器。

   ```http
   http://localhost:4502/libs/cq/workflow/content/console.html
   ```

   尋找下列兩個啟動器\（若有需要\）並進行變更\（應該為作用中\），其對應至&#x200B;**DAM更新資產工作流程**：

1. 已針對&#x200B;**DAM更新資產工作流程**&#x200B;建立「*節點*」的啟動器 — 對於條件`"jcr:content/jcr:mimeType!=video"`，「萬用字元」值應為：

   ```json
   /content/dam(/((?!/subassets|/translation_output).)*/)renditions/original
   ```

   - &#39;excludeList&#39;應該有`"event-user-data:changedByWorkflowProcess"`。
   - 針對&#x200B;**DAM更新資產工作流程 —**&#x200B;的「*節點已修改*」的啟動器（條件「`jcr:content/jcr:mimeType!=video`」），「萬用字元」值應為：

   ```json
   /content/dam(/((?!/subassets|/translation_output).)*/)renditions/original
   ```

   - `excludeList`應該有`"event-user-data:changedByWorkflowProcess"`。

1. 升級完成後，請確定所有自訂/覆蓋圖均已驗證並更新，以符合新的應用程式程式碼。 以下提供一些範例：
   - 從/libs/fmditor/libsis覆寫的任何元件都應與新的產品程式碼進行比較，且更新應在/apps下方的覆寫檔案中完成。
   - 產品中使用的任何clientlib類別都應檢閱是否有變更。 任何覆寫的設定\（範例如下\）都應與最新的設定進行比較，以取得最新的功能：
   - elementmapping.xml
   - ui\_config.json\（可能已在資料夾設定檔中設定\）
   - 已修改`com.adobe.fmdita.config.ConfigManager`


## 索引現有內容的步驟

>[!NOTE]
>
> 如果您從4.3.0或4.2.1升級，則不需要執行這些步驟。

執行以下步驟來索引現有內容，並在地圖層級使用新的尋找和取代文字：


- 對伺服器執行POST要求\（使用正確的驗證\） - `http://<server:port\>/bin/guides/map-find/indexing`。 (選用：您可以傳遞地圖的特定路徑來編列索引，預設情況下，所有地圖都會編列索引\|\| 例如： `https://<Server:port\>/bin/guides/map-find/indexing?paths=<map\_path\_in\_repository\>`)


- 此API將傳回jobId。 若要檢查工作的狀態，您可以將具有工作識別碼的GET要求傳送至相同的端點 — `http://<server:port\>/bin/guides/map-find/indexing?jobId=\{jobId\}`\（例如： `http://localhost:8080/bin/guides/map-find/indexing?jobId=2022/9/15/7/27/7dfa1271-981e-4617-b5a4-c18379f11c42`\）


- 工作完成後，上述GET要求將回應為成功，並提及是否有任何地圖失敗。 可以從伺服器記錄檔確認已成功編制索引的對應。

## 後續處理現有內容以使用中斷連結報告的步驟

>[!NOTE]
>
> 如果您從4.3.0升級，則不需要執行這些步驟

執行以下步驟後續處理現有內容並使用新的中斷連結報表：

1. （選擇性）如果系統中有超過100,000個dita檔案，請將`org.apache.jackrabbit.oak.query.QueryEngineSettingsService`下的`queryLimitReads`更新為較大的值（任何大於現有資產數的值，例如200,000），然後重新部署。

   | PID | 屬性索引鍵 | 屬性值 |
   |---|---|---|
   | org.apache.jackrabbit.oak.query.QueryEngineSettingsService | querylimitereads | 值： 200000 <br>預設值： 100000 |

1. 執行下列API以對所有檔案執行後續處理：

   | 端點 | /bin/guides/reports/upgrade |
   |---|---|
   | 請求類型 | **** POST 此腳本是POST 要求因此應通過Postman按讚代理執行。 |
   | 預期回應 | 此API將傳回jobId。 若要檢查作業的狀態，您可以將具有作業ID的GET請求傳送至相同的端點。<br>範例URL： `http://<server:port>/bin/guides/reports/upgrade` |

   | 端點 | /bin/guides/reports/upgrade |
   |---|---|
   | 請求型別 | **獲取** |
   | 引數 | jobId：傳遞從上一個post請求收到的jobId。 |
   | 預期回應 |  — 工作完成後，GET要求會成功回應。 <br> — 如果發生錯誤，請和您的客戶成功團隊共用錯誤記錄檔以及API輸出。  <br>範例URL： `http://<server:port>/bin/guides/reports/upgrade?jobId=2022/9/15/7/27/7dfa1271-981e-4617-b5a4-c18379f11c42_678` |


1. 如果您在步驟1中變更了`queryLimitReads`的值，請恢復為預設值或先前的現有值。



## 升級至版本4.3.1.5

升級至版本4.3.1.5取決於目前版本的Experience Manager Guides。 如果您使用的是4.3.1版，則可以直接升級至4.3.1.5版。



## 安裝版本4.3.1.5

1. 從[Adobe軟體發佈入口網站](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)下載4.3.1.5版本套件。
1. 安裝版本4.3.1.5封裝。

1. 請等候安裝程式順利完成。
1. 繼續升級自訂，如下一節所述。


## 安裝版本4.3.1.5之後


>[!NOTE]
>
>如果您想使用org.apache.velocity套件組合，請於上傳套件組合前執行下列步驟：
> 1. 前往 `<server>:<port>/system/console/bundles`。
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

升級至4.4.0版須視目前的Experience Manager Guides版本而定。 如果您是使用4.3.1、4.3.0、4.2或4.2.1版(Hotfix 4.2.1.3)，則可以直接升級至4.4.0版

>[!NOTE]
>
>後期處理和索引可能需要幾個小時。 我們建議您在非尖峰時段開始升級程式。

****必備條件****

在開始Experience Manager Guides 4.4.0升級程式之前，請確定您擁有：

1. 已升級至Experience Manager Guides 4.3.1、4.3.0或4.2.1版(Hotfix 4.2.1.3)，並已完成各自的安裝步驟。
1. （選用）已關閉所有翻譯工作。
1. 已將`com.adobe.fmdita.translationservices.TranslationMapUpgradeScript`類別的記錄層級變更為&#x200B;**INFO**，並將這些記錄附加至新的記錄檔，例如`logs/translation_upgrade.log`。


## 安裝4.4.0版

1. 從[Adobe軟體發佈入口網站](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)下載4.4.0版套件。
1. 安裝4.4.0版本的套件。
1. 您可以選擇點選觸發器，以啟動翻譯對應升級工作。 如需詳細資訊，請參閱[透過Servlet啟用指令碼的觸發程式](#enable-trigger-of-script-via-a-servlet)。

1. 完成套件安裝後，請等候記錄中的下列訊息：

   `Completed the post deployment setup script`

   上述訊息表示安裝的所有步驟均已完成。

   如果您遇到以下任何錯誤首碼，請向您的客戶成功團隊報告：

   - 部署後安裝指令碼發生錯誤
   - 移植翻譯MAP時發生例外狀況
   - 無法將屬性的轉譯對應從v1連線至v2
1. 升級氧氣聯結器外掛程式4.4.0版\（如有需要\）。
1. 安裝套件後清除瀏覽器快取。
1. 繼續升級自訂，如下一節所述。


## 安裝4.4.0版之後

安裝Experience Manager Guides後，您可以將適用於新安裝版本的各種設定合併到您的設定中。

>[!NOTE]
>
> 可以自定義 dam-update-資產 模型。 因此，如果已完成任何自定義，則需要將自定義和Experience Manager指南同步到模型的工作副本中。

1. **DAM更新資產工作流程\（Post-處理變更\）：**

1. 開啟URL：

   ```
   http://localhost:4502/libs/cq/workflow/admin/console/content/models.html 
   ```

1. 選取&#x200B;**DAM更新資產工作流程**。
1. 按一下&#x200B;**編輯**。
1. 如果&#x200B;**DXML後續程式啟動器**&#x200B;元件存在，請確定自訂已同步。
1. 如果&#x200B;**DXML後續處理啟動器**&#x200B;元件不存在，請執行下列步驟以插入它：

1. 按一下「**插入元件**」\(負責Experience Manager Guides後續處理，作為程式的最後一個步驟\)。
1. 使用下列詳細資料設定&#x200B;**處理序步驟**：

   **一般標籤**

   **標題：** DXML後續程式發起人

   **描述**： DXML後續處理啟動器步驟將觸發已修改/建立的資產的DXML後續處理的Sling工作

   **處理標籤**

   - 從&#x200B;**程式**&#x200B;下拉式清單中選取&#x200B;**DXML程式後啟動器**

   - 選取&#x200B;**處理常式進階**

   - 選取&#x200B;**完成**

1. 完成變更後，請按一下右上角的&#x200B;**同步**。 您將會收到成功通知。

   >[!NOTE]
   >
   > 重新整理並確認自訂變更和Experience Manager Guides後處理步驟存在於最終工作流程模型中。

1. 驗證&#x200B;**DAM更新資產工作流程**&#x200B;後，請檢查對應的啟動器設定。 若要這麼做，請前往AEM工作流程介面並開啟啟動器。

   ```http
   http://localhost:4502/libs/cq/workflow/content/console.html
   ```

   尋找下列兩個啟動器\（若有需要\）並進行變更\（應該為作用中\），其對應至&#x200B;**DAM更新資產工作流程**：

1. 已針對&#x200B;**DAM更新資產工作流程**&#x200B;建立「*節點*」的啟動器 — 對於條件`"jcr:content/jcr:mimeType!=video"`，「萬用字元」值應為：

   ```json
   /content/dam(/((?!/subassets|/translation_output).)*/)renditions/original
   ```

   - &#39;excludeList&#39;應該有`"event-user-data:changedByWorkflowProcess"`。
   - 針對&#x200B;**DAM更新資產工作流程 —**&#x200B;的「*節點已修改*」的啟動器（條件「`jcr:content/jcr:mimeType!=video`」），「萬用字元」值應為：

   ```json
   /content/dam(/((?!/subassets|/translation_output).)*/)renditions/original
   ```

   - `excludeList`應該有`"event-user-data:changedByWorkflowProcess"`。

1. 升級完成後，請確定所有自訂/覆蓋圖均已驗證並更新，以符合新的應用程式程式碼。 以下提供一些範例：
   - 從/libs/fmditor/libsis覆寫的任何元件都應與新的產品程式碼進行比較，且更新應在/apps下方的覆寫檔案中完成。
   - 產品中使用的任何clientlib類別都應檢閱是否有變更。 任何覆寫的設定\（範例如下\）都應與最新的設定進行比較，以取得最新的功能：
   - elementmapping.xml
   - ui\_config.json\（可能已在資料夾設定檔中設定\）
   - 已修改`com.adobe.fmdita.config.ConfigManager`

1. 如果您已在damAssetLucene中新增任何自訂，您可能需要再次套用它們。 進行這些變更後，將重新索引設定為true。 這會使用自訂重新索引所有現有節點。 完成後，重新索引標幟將再次設定為false。 視系統中的資產數量而定，這可能需要幾個小時的時間。

## 索引現有內容的步驟

>[!NOTE]
>
> 如果您從4.3.0或4.3.1升級，則不需要執行這些步驟。

執行以下步驟來索引現有內容，並在地圖層級使用新的尋找和取代文字：

- 對伺服器執行POST要求\（使用正確的驗證\） - `http://<server:port\>/bin/guides/map-find/indexing`。 (選用：您可以傳遞地圖的特定路徑來編列索引，預設情況下，所有地圖都會編列索引\|\| 例如： `https://<Server:port\>/bin/guides/map-find/indexing?paths=<map\_path\_in\_repository\>`)

- 此API將傳回jobId。 若要檢查工作的狀態，您可以將具有工作識別碼的GET要求傳送至相同的端點 — `http://<server:port\>/bin/guides/map-find/indexing?jobId=\{jobId\}`\（例如： `http://localhost:8080/bin/guides/map-find/indexing?jobId=2022/9/15/7/27/7dfa1271-981e-4617-b5a4-c18379f11c42`\）

- 工作完成後，上述GET要求將回應為成功，並提及是否有任何地圖失敗。 可以從伺服器記錄檔確認已成功編制索引的對應。

## 後續處理現有內容以使用中斷連結報告的步驟

>[!NOTE]
>
> 如果您從4.3.0或4.3.1升級，則不需要執行這些步驟。

執行以下步驟後續處理現有內容並使用新的中斷連結報表：

1. （選擇性）如果系統中有超過100,000個dita檔案，請將`org.apache.jackrabbit.oak.query.QueryEngineSettingsService`下的`queryLimitReads`更新為較大的值（任何大於現有資產數的值，例如200,000），然後重新部署。

   | PID | 屬性索引鍵 | 屬性值 |
   |---|---|---|
   | org.apache.jackrabbit.oak.query.QueryEngineSettingsService | querylimitereads | 值： 200000 <br>預設值： 100000 |

1. 執行下列API以對所有檔案執行後續處理：

   | 端點 | /bin/guides/reports/upgrade |
   |---|---|
   | 請求型別 | **POST**&#x200B;此指令碼為POST要求，因此應透過Postman等代理程式執行。 |
   | 預期回應 | 此API將傳回jobId。 若要檢查作業的狀態，您可以將具有作業ID的GET請求傳送至相同的端點。<br> 樣本URL： `http://<server:port>/bin/guides/reports/upgrade` |

   | 端點 | /bin/guides/reports/upgrade |
   |---|---|
   | 請求型別 | **GET** |
   | 引數 | jobId： 傳遞從上一個貼文請求收到的 jobId。 |
   | 預期回應 | - 一旦作業完成，GET 要求會成功回應。 <br> - 如果出現錯誤，請與客戶成功團隊共享錯誤日誌以及 API 輸出。  <br>樣本URL： `http://<server:port>/bin/guides/reports/upgrade?jobId=2022/9/15/7/27/7dfa1271-981e-4617-b5a4-c18379f11c42_678` |

1. 如果已在步驟 1 中更改了預設值或以前的現有值，請恢復為該值 `queryLimitReads` 。

### 透過Servlet啟用指令碼的觸發

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



## 處理`'fmdita rewriter'`衝突的步驟

Experience Manager Guides有&#x200B;[**自訂sling重寫程式**](../cs-install-guide/conf-output-generation.md#custom-rewriter)&#x200B;模組，可處理交叉對映時產生的連結（兩個不同對映之主題之間的連結）。

如果您的程式碼基底中有另一個自訂Sling重寫程式，請使用大於50的`'order'`值，因為Experience Manager Guides Sling重寫程式使用`'order'` 50。  若要覆寫此值，您需要大於50的值。 如需詳細資訊，請檢視[輸出重寫管道](https://sling.apache.org/documentation/bundles/output-rewriting-pipelines-org-apache-sling-rewriter.html)。

在此升級期間，由於`'order'`值從1000變更為50，因此您必須將現有的自訂重寫程式（若有的話）與`'fmdita-rewriter'`合併。


**上層主題：**[&#x200B;下載並安裝](download-install.md)


## 升級至4.6.0版

>[!TIP]
>
> 建議在版本 4.6.0 、4.6.0 Service Pack 1 或 4.6.0 Service Pack 3 之上安裝 4.6.0 Service Pack 4。 4.6.0 Service Pack 4版本的升級程式遵循與4.6.0版本相同的步驟。

升級至4.6.0版須視目前的Experience Manager Guides版本而定。 如果您是使用4.4.0、4.3.1、4.3.0、4.2或4.2.1版(Hotfix 4.2.1.3)，可以直接升級至4.6.0版。

>[!NOTE]
>
> 後期處理和索引可能需要幾個小時。 我們建議您在非尖峰時段開始升級程式。

****必備條件****

在開始Experience Manager Guides 4.6.0升級程式之前，請確定您擁有：

1. 已升級到 Experience Manager 指南版本 4.3.1、4.3.0 或 4.2.1（修補程式 4.2.1.3），並完成了各自的安裝步驟。
1. （選擇）關閉所有翻譯任務。
1. 將類的日誌級別&#x200B;**更改為 INFO**，並將這些日誌附加到新記錄檔中，例如 `logs/translation_upgrade.log`。`com.adobe.fmdita.translationservices.TranslationMapUpgradeScript`


## 安裝 4.6.0 版

1. 從軟體分發門戶](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)下載 [4.6.0 版本包Adobe Systems。
1. 安裝 4.6.0 版套件。
1. 您可以選擇點擊觸發器以開始翻譯地圖升級工作。 有關詳細資訊，請參閱 [通過 Servlet](#enable-trigger-of-script-via-a-servlet) 啟用腳本觸發器。

1. 完成套件安裝後，請等待日誌中的以下消息\（s\）：

   `Completed the post deployment setup script`

   上述消息表示所有安裝步驟均已完成。

   如果您遇到以下任何 ERROR 前綴，請將其報告給您的客戶成功團隊：

   - 貼文部署安裝程式腳本中錯誤
   - 移植翻譯MAP時發生例外狀況
   - 無法將屬性的轉譯對應從v1連線至v2
1. 升級氧氣聯結器外掛程式4.6.0版\（如有需要\）。
1. 安裝套件後清除瀏覽器快取。

## 安裝4.6.0版之後

安裝Experience Manager Guides後，您可以將適用於新安裝版本的各種設定合併到您的設定中。

>[!NOTE]
>
> 可以自訂dam-update-asset模型。 因此，如果已完成任何自訂，則需要將自訂和Experience Manager Guides同步到模型的工作副本中。

1. **DAM更新資產工作流程\（後續處理變更\）：**

1. 開啟URL：

   ```
   http://localhost:4502/libs/cq/workflow/admin/console/content/models.html 
   ```

1. 選取&#x200B;**DAM更新資產工作流程**。
1. 按一下&#x200B;**編輯**。
1. 如果&#x200B;**DXML後續程式啟動器**&#x200B;元件存在，請確定自訂已同步。
1. 如果&#x200B;**DXML後續處理啟動器**&#x200B;元件不存在，請執行下列步驟以插入它：

1. 按一下「**插入元件**」\(負責Experience Manager Guides後續處理，作為程式的最後一個步驟\)。
1. 使用下列詳細資料設定&#x200B;**處理序步驟**：

   **一般標籤**

   **標題：** DXML Post進程贊助者

   **描述**： DXML後續處理啟動器步驟將觸發已修改/建立的資產的DXML後續處理的Sling工作

   **處理標籤**

   - 從&#x200B;**程式**&#x200B;下拉式清單中選取&#x200B;**DXML程式後啟動器**

   - 選取&#x200B;**處理常式進階**

   - 選擇 **完成**

1. 完成更改后，按兩下 **右上角的同步** 。 您將收到成功通知。

   >[!NOTE]
   >
   > 重新整理並驗證最終工作流程模型中是否存在自定義更改和Experience Manager指南貼文處理步驟。

1. 驗證DAM更新資產工作流程&#x200B;**后**，請檢查對應的啟動器配置。為此，請轉到AEM工作流介面並打開啟動器。

   ```http
   http://localhost:4502/libs/cq/workflow/content/console.html
   ```

   查找並更改與「更新資產」工作流程對應的以下 **兩個啟動器 \（應處於活動狀態DAM**）：

1. 已針對&#x200B;**DAM更新資產工作流程**&#x200B;建立「*節點*」的啟動器 — 對於條件`"jcr:content/jcr:mimeType!=video"`，「萬用字元」值應為：

   ```json
   /content/dam(/((?!/subassets|/translation_output).)*/)renditions/original
   ```

   - &#39;excludeList&#39;應該有`"event-user-data:changedByWorkflowProcess"`。
   - 針對&#x200B;**DAM更新資產工作流程 —**&#x200B;的「*節點已修改*」的啟動器（條件「`jcr:content/jcr:mimeType!=video`」），「萬用字元」值應為：

   ```json
   /content/dam(/((?!/subassets|/translation_output).)*/)renditions/original
   ```

   - `excludeList`應該有`"event-user-data:changedByWorkflowProcess"`。

1. 升級完成後，請確定所有自訂/覆蓋圖均已驗證並更新，以符合新的應用程式程式碼。 以下提供一些範例：
   - 從/libs/fmditor/libsis覆寫的任何元件都應與新的產品程式碼進行比較，且更新應在/apps下方的覆寫檔案中完成。
   - 產品中使用的任何clientlib類別都應檢閱是否有變更。 任何覆寫的設定\（範例如下\）都應與最新的設定進行比較，以取得最新的功能：
   - elementmapping.xml
   - ui\_config.json\（可能已在資料夾設定檔中設定\）
   - 已修改`com.adobe.fmdita.config.ConfigManager`

1. 如果您已在damAssetLucene中新增任何自訂，您可能需要再次套用它們。 進行這些變更後，將重新索引設定為true。 這會使用自訂重新索引所有現有節點。 完成後，重新索引標幟將再次設定為false。 視系統中的資產數量而定，這可能需要幾個小時的時間。

## 重新索引Experience Manager Guides索引的步驟

1. 開啟 `crx/de` 並瀏覽到索引路徑：  `/oak:index/guidesAssetProperties`
2. 將重新索引屬性設定為`true` （預設為`false`），然後按一下&#x200B;**全部儲存**。
3. 重新索引完成後，重新索引屬性會再次設定為`false`，而重新索引計數會增加1。

   >[!NOTE]
   >
   > 視資料數量而定，這可能需要幾分鐘的時間。
4. 對其他新增或修改的索引執行相同的步驟： `guidesBulkActivation`、`guidesPeerLinkIndex`和`guidesKonnectTemplateIndex`。

## 索引現有內容的步驟



執行以下步驟來索引現有內容：

- 對伺服器執行POST要求\（使用正確的驗證\） - `http://<server:port\>/bin/guides/map-find/indexing`。 (選用：您可以傳遞地圖的特定路徑來編列索引，預設情況下，所有地圖都會編列索引 || 範例： `https://<Server:port\>/bin/guides/map-find/indexing?paths=<map\_path\_in\_repository\>`)

- API 將傳回 jobId。 若要檢查工作的狀態，您可以將具有工作識別碼的GET要求傳送至相同的端點 — `http://<server:port\>/bin/guides/map-find/indexing?jobId=\{jobId\}`\（例如： ` http://localhost:8080/bin/guides/map-find/indexing?jobId=2022/9/15/7/27/7dfa1271-981e-4617-b5a4-c18379f11c42_678`）

- 作業完成後，上述GET 要求將成功回應，並提及是否有任何地圖失敗。 可以從伺服器日誌中確認成功索引的映射。


>[!NOTE]
>
> 如果使用自定義綱要，則必須在「集成目錄&#x200B;**」選項的** AEM存放庫中定義自定義 DTD 和 XSD catalog.xml文件的路徑。




## 處理`'fmdita rewriter'`衝突的步驟

Experience Manager Guides有&#x200B;[**自訂sling重寫程式**](../cs-install-guide/conf-output-generation.md#custom-rewriter)&#x200B;模組，可處理交叉對映時產生的連結（兩個不同對映之主題之間的連結）。

如果您的程式碼基底中有另一個自訂Sling重寫程式，請使用大於50的`'order'`值，因為Experience Manager Guides Sling重寫程式使用`'order'` 50。  若要覆寫此值，您需要大於50的值。 如需詳細資訊，請檢視[輸出重寫管道](https://sling.apache.org/documentation/bundles/output-rewriting-pipelines-org-apache-sling-rewriter.html)。

在此升級期間，由於`'order'`值從1000變更為50，因此您必須將現有的自訂重寫程式（若有的話）與`'fmdita-rewriter'`合併。


## 升級至5.0.0版

>[!TIP]
>
> 升級至5.0.0版須視目前的Experience Manager Guides版本而定。 如果您是使用4.6.3、4.6.1、4.6.0或4.4版，則可以直接升級至5.0.0版。

>[!NOTE]
>
> 後期處理和索引可能需要幾個小時。 我們建議您在非尖峰時段開始升級程式。

****必備條件****

在開始Experience Manager Guides 5.0.0升級程式之前，請確定您擁有：

1. 已升級至Experience Manager Guides 4.6.3、4.6.1、4.6.0或4.4版，並完成各自的安裝步驟。
1. （選用）已關閉所有翻譯工作。
1. 已將`com.adobe.fmdita.translationservices.TranslationMapUpgradeScript`類別的記錄層級變更為&#x200B;**INFO**，並將這些記錄附加至新的記錄檔，例如`logs/translation_upgrade.log`。


## 安裝5.0.0版

1. 從[Adobe軟體發佈入口網站](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)下載5.0.0版本的套件。
1. 安裝5.0.0版本的套件。
1. 您可以選擇點選觸發器，以啟動翻譯對應升級工作。 如需詳細資訊，請參閱[透過Servlet啟用指令碼的觸發程式](#enable-trigger-of-script-via-a-servlet)。

1. 完成套件安裝後，請等候記錄中的下列訊息：

   `Completed the post deployment setup script`

   上述訊息表示安裝的所有步驟均已完成。

   如果您遇到以下任何錯誤首碼，請向您的客戶成功團隊報告：

   - 部署後安裝指令碼發生錯誤
   - 移植翻譯MAP時發生例外狀況
   - 無法將屬性的轉譯對應從v1連線至v2
1. 升級氧氣聯結器外掛程式5.0.0版\（如有需要\）。
1. 安裝套件後清除瀏覽器快取。

## 安裝5.0.0版之後

安裝 Experience Manager 指南後，您可以將適用於新安裝版本的各種配置合併到您的設置中。

>[!NOTE]
>
> 可以自定義 dam-update-資產 模型。 因此，如果已完成任何自定義，則需要將自定義和Experience Manager指南同步到模型的工作副本中。

1. **DAM更新資產工作流程\（Post-處理變更\）：**

1. 開啟URL：

   ```
   http://localhost:4502/libs/cq/workflow/admin/console/content/models.html 
   ```

1. 選取 **DAM更新資產工作流程**。
1. 按一下&#x200B;**編輯**。
1. 如果&#x200B;**DXML後續程式啟動器**&#x200B;元件存在，請確定自訂已同步。
1. 如果&#x200B;**DXML後續處理啟動器**&#x200B;元件不存在，請執行下列步驟以插入它：

1. 按一下「**插入元件**」\(負責Experience Manager Guides後續處理，作為程式的最後一個步驟\)。
1. 使用下列詳細資料設定&#x200B;**處理序步驟**：

   **一般標籤**

   **標題：** DXML後續程式發起人

   **描述**： DXML後續處理啟動器步驟將觸發已修改/建立的資產的DXML後續處理的Sling工作

   **處理標籤**

   - 從&#x200B;**程式**&#x200B;下拉式清單中選取&#x200B;**DXML程式後啟動器**

   - 選取&#x200B;**處理常式進階**

   - 選取&#x200B;**完成**

1. 完成變更後，請按一下右上角的&#x200B;**同步**。 您將會收到成功通知。

   >[!NOTE]
   >
   > 重新整理並確認自訂變更和Experience Manager Guides後處理步驟存在於最終工作流程模型中。

1. 驗證&#x200B;**DAM更新資產工作流程**&#x200B;後，請檢查對應的啟動器設定。 若要這麼做，請前往AEM工作流程介面並開啟啟動器。

   ```http
   http://localhost:4502/libs/cq/workflow/content/console.html
   ```

   尋找下列兩個啟動器\（若有需要\）並進行變更\（應該為作用中\），其對應至&#x200B;**DAM更新資產工作流程**：

1. 用於 DAM 更新資產 工作流程&#x200B;**- 的「*節點已建立*」**&#x200B;啟動器 ，「`"jcr:content/jcr:mimeType!=video"`通配符」值應為：

   ```json
   /content/dam(/((?!/subassets|/translation_output).)*/)renditions/original
   ```

   - &#39;excludeList&#39; 應該有 `"event-user-data:changedByWorkflowProcess"`.
   - 適用於「*節點已修改*」 **的啟動器 DAM更新資產 工作流程 -** 對於條件 “`jcr:content/jcr:mimeType!=video`”，「通配符」值應為：

   ```json
   /content/dam(/((?!/subassets|/translation_output).)*/)renditions/original
   ```

   - `excludeList` 應該有 `"event-user-data:changedByWorkflowProcess"`.

1. 升級完成後，請確保驗證並更新任何自定義/疊加以匹配新的應用程式代碼。 以下提供一些範例：
   - 從/libs/fmditor/libsis覆寫的任何元件都應與新的產品程式碼進行比較，且更新應在/apps下方的覆寫檔案中完成。
   - 應檢視產品中使用的任何 clientlib 類別是否有變更。 任何覆寫的設定\（範例如下\）都應與最新的設定進行比較，以取得最新的功能：
   - elementmapping.xml
   - UI\_config.json\（可能已在資料夾描述檔中設定）
   - 已修改`com.adobe.fmdita.config.ConfigManager`

1. 如果您已在damAssetLucene中新增任何自訂，您可能需要再次套用它們。 進行這些變更後，將重新索引設定為true。 這會使用自訂重新索引所有現有節點。 完成後，重新索引標幟將再次設定為false。 視系統中的資產數量而定，這可能需要幾個小時的時間。

## 重新索引Experience Manager Guides索引的步驟

1. 開啟`crx/de`並導覽至索引路徑： `/oak:index/guidesAssetProperties`
2. 將重新索引屬性設定為`true` （預設為`false`），然後按一下&#x200B;**全部儲存**。
3. 重新索引完成後，重新索引屬性會再次設定為`false`，而重新索引計數會增加1。

   >[!NOTE]
   >
   > 視資料數量而定，這可能需要幾分鐘的時間。
4. 對其他新增或修改的索引執行相同的步驟： `guidesBulkActivation`、`guidesPeerLinkIndex`和`guidesKonnectTemplateIndex`。

## 索引現有內容的步驟



執行以下步驟來索引現有內容：

- 對伺服器執行POST要求\（使用正確的驗證\） - `http://<server:port\>/bin/guides/map-find/indexing`。 (選用：您可以傳遞地圖的特定路徑來編列索引，預設情況下，所有地圖都會編列索引 || 範例： `https://<Server:port\>/bin/guides/map-find/indexing?paths=<map\_path\_in\_repository\>`)

- 此API將傳回jobId。 若要檢查工作的狀態，您可以將具有工作識別碼的GET要求傳送至相同的端點 — `http://<server:port\>/bin/guides/map-find/indexing?jobId=\{jobId\}`\（例如： ` http://localhost:8080/bin/guides/map-find/indexing?jobId=2022/9/15/7/27/7dfa1271-981e-4617-b5a4-c18379f11c42_678`）

- 工作完成後，上述GET要求將回應為成功，並提及是否有任何地圖失敗。 可以從伺服器記錄檔確認已成功編制索引的對應。


>[!NOTE]
>
> 如果您使用自訂結構描述，您必須在&#x200B;**整合目錄**&#x200B;選項中，定義AEM儲存庫中自訂DTD和XSD catalog.xml檔案的路徑。




## 處理`'fmdita rewriter'`衝突的步驟

Experience Manager Guides有&#x200B;[**自訂sling重寫程式**](../cs-install-guide/conf-output-generation.md#custom-rewriter)&#x200B;模組，可處理交叉對映時產生的連結（兩個不同對映之主題之間的連結）。

如果您的程式碼基底中有另一個自訂Sling重寫程式，請使用大於50的`'order'`值，因為Experience Manager Guides Sling重寫程式使用`'order'` 50。  若要覆寫此值，您需要大於50的值。 如需詳細資訊，請檢視[輸出重寫管道](https://sling.apache.org/documentation/bundles/output-rewriting-pipelines-org-apache-sling-rewriter.html)。

在此升級期間，由於`'order'`值從1000變更為50，因此您必須將現有的自訂重寫程式（若有的話）與`'fmdita-rewriter'`合併。



## 將 damAssetLucene 重新索引的步驟

已更新包含Guides的damAssetLucene的索引定義。 請參閱[本文](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-16460)，瞭解在升級至5.0.0版後如何重新索引damAssetLucene。

>[!NOTE]
>
> 在依照檔案指示進行時，請確定兩個屬性（對於/oak：index/damAssetLucene而言，reindex=true和reindex-async=true）同時透過儲存作業更新。


**父級主題：** [下載並安裝](download-install.md)
