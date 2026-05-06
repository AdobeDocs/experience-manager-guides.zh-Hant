---
title: 關於在Adobe Experience Manager Guides中發佈效能和擴充性的常見問題集
description: 瞭解在Adobe Experience Manager Guides中發佈效能和擴充性的常見問題。
source-git-commit: f188c2827a9e27249d0162c9f9913e090b29672d
workflow-type: tm+mt
source-wordcount: '1666'
ht-degree: 1%

---


# 資產處理

資產處理是一項關鍵的工作流程，負責確保內容資產在平台內結構化、驗證、編制索引及可供存取。 隨著擴充能力需求與雲端原生需求的不斷發展，架構經歷了從單一執行緒、階層式處理模型，到分散式、圖表式多執行緒系統的重大轉變。

## 目前的資產處理工作流程

### 處理概述

將資產匯入Experience Manager Guides時，會依序執行下列處理步驟：

- 唯一索引鍵指派：每個檔案都會指派唯一識別碼，以確保可追蹤性和參考完整性。
- 剖析：內容（例如DITA XML）會剖析為結構化元件，以供系統層級瞭解。
- 驗證：結構和結構描述驗證可確保符合檔案標準。
- 參照解析度：跨資產解析交叉參照（連結、影像、相依性）。
- 中繼資料擷取：會擷取標題、作者和自訂屬性等中繼資料，以進行索引和搜尋。
- 修改時重新處理：增量重新處理可確保內容更新後的一致性。

### 架構特性

- **單一執行緒處理**：防止JCR （Java內容存放庫）結構損毀，這些結構依賴B-Tree實作。這可確保資料完整性，但在大量擷取期間會產生處理瓶頸。

- **Parent-Map相依性**：使用圖表周遊來維護資產之間的階層式關係。 這是一項密集作業，在大規模處理期間具有高延遲性，並增加了運算負荷，以及因大量周遊作業而造成的負擔。

## 新資產處理流程

核心處理步驟在功能上保持一致，但現在會在分散且並行的架構中執行，大幅提升輸送量。

### 架構增強功能

- **圖表資料庫整合**：
   - 從階層式JCR轉換至原生圖表資料庫
   - 有效率地處理關係和相依性
   - 消除在階層式儲存裝置上模擬圖表操作的複雜性
- **多執行緒分散式處理**：
   - 處理作業會在雲端環境中的多個Pod上執行
   - 移除單一導線節點的相依性
   - 啟用水準擴充能力與平行執行
- **父對映相依性已清除：**
   - 移除明確圖表周遊的需求
   - 減少I/O作業與處理延遲
   - 簡化處理管道
- **同步的唯一識別碼配置**
   - 集中協調可確保：
   - 沒有重複的檔案ID
   - 跨分散式節點的一致性
   - 在並行環境中維護參照完整性
- **雲端原生可擴充資料庫（主控的AWS）**
   - 高可用性和彈性的資料庫層
   - 支援根據工作負荷進行彈性調整
   - 提升整體系統可靠性和效能

![](images/workflow.png)

## 新架構的優勢

- 效能改善：
   - 平行執行可大幅縮短處理時間
   - 消除大量周遊作業可縮短延遲
   - 最佳化的圖表處理可提升相依性解析速度
- 擴充性：
   - 橫跨Pod的水平縮放可讓您處理大型擷取磁碟區
   - 雲端原生基礎架構可動態調整以因應工作負載需求
- 可靠性和可用性：
   - 分散式處理可移除單一故障點
   - AWS代管資料庫可確保高可用性和容錯性
- 提升效率：
   - 減少因移除父對映周遊所造成的I/O額外負荷
   - 跨運算節點提高資源使用率
- 資料完整性：
   - 同步的ID配置可維持分散式系統間的一致性
   - 在啟用並行時保持穩健性

## 設定資料庫

Experience Manager Guides可為AEM雲端環境啟用簡化的資料庫設定。 若要設定AEM Cloud執行個體的資料庫，請執行下列步驟：

1. 存取AEM Cloud Manager：使用下列URL導覽至Adobe Experience Cloud Manager，將預留位置取代為您的組織、程式和環境詳細資料： `https://experience.adobe.com/#/${orgName}/cloud-manager/environments.html/program/${programId}/environment/${envId}`

1. 設定環境：透過Cloud Manager開啟環境設定頁面後，您將能調整執行個體特定的設定，包括設定必要的資料庫設定。

這種簡化方法可確保在Adobe雲端基礎結構中輕鬆存取和設定AEM環境。

1. 設定以下屬性：


| 屬性名稱 | 值 | 套用的服務 | 類型 |
|----------------------------------|--------------------------------|-----------------|----------|
| DATABASE_URL | `<host>:<port>/<db_name>` | 作者 | 變數 |
| GUIDES_ENABLE_DATABASE | `true` | 作者 | 變數 |
| DATABASE_PASSWORD | `password` | 作者 | 密碼 |
| 資料庫使用者名稱 | `username` | 作者 | 變數 |
| RUN_POSTPROCESS_IN_PHODS | `true` | 作者 | 變數 |
| DATABASE_CONNECTION_POOL_SIZE | `10` | 作者 | 變數 |


![](images/environment-config.png){width="350"}

1. 儲存變更：進行組態變更後，請確定您在Cloud Manager介面中&#x200B;**儲存**&#x200B;變更。

1. 系統可用性：完全套用組態後，請開啟GET `http://host/bin/guides/v1/system/status`並檢查以下屬性：
   - `<isDatabase>`：必須為true
   - `<databaseConnectionCheck>`：必須通過

   如果上述值在回應中正確無誤，則系統可搭配新設定的資料庫使用。

依照此程式，您將可正確設定且隨時可用的AEM雲端環境。

>[!NOTE]
>
> 如果您要移轉至具有既有內容的現有環境，則必須先執行階段2 （移轉現有內容），才能內嵌任何新內容。 這是為了確保為新內容正確指派暫時GUID。

## 在AEM DAM （雲端環境）中擷取資料（第1階段）

若要在AEM DAM (Digital Asset Manager)中設定新資料夾、擷取資料，並將其與JCR型環境進行比較，請遵循以下步驟。

1. 在DAM中建立新資料夾。

2. 使用資料上傳工具擷取資料：如需詳細資料，請檢視&#x200B;**將Assets上傳至AEM Cloud**。

3. 驗證系統
   - 上傳完成後，請確認資產存在於DAM中。
   - 確保已擷取中繼資料（例如檔案型別、說明和標籤）並將其與資產相關聯。
   - 檢查Experience Manager Guides處理（多執行緒），確認所有參考、中繼資料擷取和驗證都成功。
   - 測試存取和編輯檔案以確認系統完整性。

4. 與JCR式環境比較
   - 比較各種測試案例的結果。
   - 評估擷取速度。


若要移轉在將Experience Manager Guides切換至資料庫式設定之前已上傳和處理的內容，可以使用移轉指令碼。 指令碼會運用一組API來起始及監控移轉程式。 下列步驟概述建議的方法。

## 將內容從JCR移轉至資料庫（階段2）

若要在將Experience Manager Guides切換至資料庫式設定之前移轉已上傳和處理的內容，您必須使用移轉指令碼。 指令碼會運用一組API來起始及監控移轉程式。 下列步驟概述建議的方法。

1. 使用任何REST使用者端觸發移轉API。
2. 檢查移轉進度。
3. 監視移轉直到完成：繼續監視，直到進度API報告100%完成。 完成後，先前從JCR存放庫上傳和處理的所有內容都會移轉至資料庫。

   >[!NOTE]
   >
   > - 確保包含必要的授權標頭（例如OAuth權杖、API金鑰或來自開發人員控制檯的存取權杖），以使用AEM驗證請求。
   > - 移轉持續時間取決於內容存放庫的大小。 建議定期檢查進度，並監控錯誤或中斷情況。
   > - 檢閱移轉記錄（若有），以評估移轉效能並找出任何問題。

4. 若要支援大型存放庫大小的移轉，請遵循以下設定

   >[!NOTE]
   >
   > 只有在移轉期間發生存放庫周遊錯誤時，才套用此設定。

   `file name: `org.apache.jackrabbit.oak.query.QueryEngineSettingsService.xml&quot;

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:jcr="http://www.jcp.org/jcr/1.0"
         xmlns:sling="http://sling.apache.org/jcr/sling/1.0"
         jcr:primaryType="sling:OsgiConfig"
         queryLimitInMemory="5000000"
         queryLimitReads="1000000"
   />
   ```


## 移轉API

### 開始移轉

- 端點： `POST /bin/guides/v1/assets/process`
- 要求內文： (`application/json`)：

```json
  {
    "path": "/content/dam/dita-templates",
    "excludedPaths": [
      "/content/dam/demo",
      "/content/dam/demo1"
    ],
    "type": "ASSET_PROCESSING"
  }
```

- 傳回移轉的processingId。
- 觸發內建在產品中的資產處理工作流程。

### 檢查移轉狀態

端點： `GET /bin/guides/v1/assets/process/status?processingId=<processingId>`

### 取消正在執行的移轉

- 端點： `POST /bin/guides/v1/assets/process/cancel`
- 要求內文(application/json)：

  ```
  {
   "processingId": "processingId"
  }
  ```

### 繼續失敗或已取消的移轉

- 端點： `POST /bin/guides/v1/assets/process/resume`
- 要求內文(application/json)：

  ```
  {
   "processingId": "processingId"
  }
  ```

## 將資產上傳至AEM cloud

Adobe Experience Manager (AEM) as a Cloud Service提供多種大量內容擷取方法。 為了確保最佳效能（尤其是Experience Manager Guides後續處理），採用支援且可擴充的擷取策略至關重要。

### 使用雲端儲存空間整合進行大量內嵌

AEM透過支援的雲端儲存空間提供者支援大量內容擷取，讓組織可連線其偏好的儲存空間解決方案，並將內容直接匯入AEM。 由於具備下列優點，因此建議將此方法用於大規模且對效能敏感的內嵌：

- 可擴充的基礎架構：擷取程式會在Adobe管理的雲端基礎結構上執行，可根據負載和內容量自動擴充。 這確保即使是大型資料集也能有一致的擷取效能。

- 可預測的擷取計畫：使用者可以提前估計擷取持續時間，這有助於發行計畫、排程以及與相依團隊的協調。

  ![](images/ingestion-time.png){width="350"}

- 全方位的記錄與追蹤：擷取工作流程包含詳細的記錄與追蹤功能，可讓您在整個匯入程式中檢視進度、成功狀態和潛在問題。

  ![](images/bulk-import-job.png){width="350"}

- 排程擷取：可排程在預先定義的時間範圍內進行內容擷取，確保對一般使用者和持續作業影響最小或沒有。

如需詳細資訊，請檢視[使用大量匯入](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/migration/bulk-import)。

## 使用AEM上傳進行大量擷取

AEM也提供[AEM upload](https://github.com/adobe/aem-uploa)、程式庫和命令列介面(CLI)，讓使用者可直接從本機檔案系統擷取內容。 此選項可整合至自訂解決方案，或作為上傳內容的獨立CLI工具使用。

由於此方法會在使用者的本機電腦上執行，因此需要有穩定且無中斷的網路連線，以確保可靠且順暢的擷取體驗。


## Experience Manager Guides資料庫連線的健康狀態檢查

設定為使用資料庫的Experience Manager Guides部署需要穩定且一致的資料庫連線能力，才能可靠運作。 驗證資料庫連線狀態是重要的健康狀態檢查步驟，可排除可能影響系統功能的連線相關問題。

此健康狀態檢查可讓使用者確認資料庫是否已設定、可連線及是否如預期運作。 若要檢查DB連線狀態，請遵循下列步驟。

1. 開啟任何瀏覽器或REST使用者端
2. 使用此[URL](https://host:port/bin/guides/v1/system/status)觸發GET呼叫
3. 以下欄位可用於判斷系統設定和健康狀態
   1. isDatabase：
      - true：環境已使用資料庫設定。
      - false：環境未使用資料庫

   2. databaseConnectionCheck：
      - 通過： Experience Manager Guides將檢查連線狀態，如果Guides能夠連線資料庫，其狀態將傳回「通過」。
      - 失敗：環境無法連線到資料庫。 客戶應立即停止使用系統，並聯絡Adobe支援團隊。

## 記錄檔監視

Experience Manager Guides與資料庫可以有效地記錄詳細資訊，讓insight進入系統狀態。
在Splunk中使用以下查詢來取得不同案例的記錄。

1. 移轉記錄：
   - `index IN ("dx_aem_engineering") aem_service=cm-${programid}-${environmentId} sourcetype=aemerror "AssetProcessingJob" OR "AssetJobProducerDb" NOT "ServiceEvent"`
2. 後處理記錄：
   - `index IN ("dx_aem_engineering") aem_service= cm-${programid}-${environmentId} sourcetype=aemerror com.adobe.fmdita.uuid.concrete.Cor*`


>[!NOTE]
>
> 深入瞭解[Splunk查詢功能](https://www.splunk.com/en_us/blog/learn/splunk-cheat-sheet-query-spl-regex-commands.html)，以根據持續時間、記錄層級或搜尋某些特定模式來篩選這些記錄。










