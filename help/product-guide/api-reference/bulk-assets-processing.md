---
title: 開始大量處理資產的API
description: 瞭解API以開始資產的批次處理
feature: Post-Processing Event Handler
role: Developer
level: Experienced
exl-id: feba6d8e-c363-4360-af33-92a01dcf6672
TQID: https://experienceleague.adobe.com/rGPpMIf5X5lfZZy2ZWk9lizd2E7UyRT8BLkSBb0o320
product_v2: id: fae5e35a-80c9-4b94-9352-1a060a6aab1did: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2: id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: a13143053c75ab65cbcd20a52c8ca3fb953edecf
workflow-type: tm+mt
source-wordcount: 639
ht-degree: 8%

---

# 開始大量處理資產的API

>[!NOTE]
>
> 如需最新的REST API端點定義和相關詳細資訊，請在`https://<aem-author-url>/libs/fmdita/clientlibs/api-docs/index.html`檢視Swagger檔案（將`<aem-author-url>`取代為AEM伺服器URL）。 由於本文排程在2026年10月封存，我們建議您使用Swagger檔案來取得最新的API資訊。

為指定路徑起始大量資產處理的POST方法。 此API支援JCR型和資料庫型資產處理。 它會啟動非同步作業，處理給定路徑及其子路徑下的所有資產。 啟動後，API會傳回唯一的processingID，可用於追蹤工作狀態。

**要求URL**

`http://<aem-guides-server>:<port-number>/bin/guides/v1/assets/process`

**要求引數**

| 名稱 | 類型 | 必要 | 說明 |
|----|----|--------|-----------|
| `path` | 字串 | 是 | 要處理的AEM存放庫中資料夾或資產的絕對路徑。 |
| `excludedPaths` | 字串 | 否 | 要從處理中排除的路徑清單 |
| `type` | 字串 | 是 | 要執行的處理型別。 例如：ASSET_PROCESSING。 |
| `filter` | 物件 | 否 | 套用至所選資產的篩選器 |

**篩選物件欄位**

| 名稱 | 類型 | 說明 |
|----|----|-----------|
| 檔案型別 | 字串 | 要處理的資產型別。 允許的值： DITATOPIC、DITAMAP、MARKDOWN、HTML/CSS、DITAVAL、其他。 |
| startTime | 整數 | 資產建立時間的下限 |
| endTime | 整數 | 資產建立時間上限 |

**要求範例**

```JSON
{
  "path": "/content/dam/status-fetch1",
  "excludedPaths": [
    "content/dam/status-fetch1/excluded-folder"
  ],
  "type": "ASSET_PROCESSING",
  "filter": {
        "fileTypes": ["DITAMAP", "DITATOPIC"],
        "startTime": 1758876933000
        "endTime": 1764932039000
    }
}
```

**回應值**

processingId可輪詢以取得非同步作業的狀態。

```JSON
{
  "processingId": "akjhdfalkj1132"
}
```

**回應代碼**

- 200項成功
- 400無效的輸入
- 401未經授權的存取
- 500內部伺服器錯誤

## 檢查工作狀態

一種GET方法，可擷取先前已啟動資產處理工作的目前狀態。

**要求URL**

`http://<aem-guides-server>:<port-number>/bin/guides/v1/assets/process/status`

**要求引數**

| 名稱 | 類型 | 必要 | 說明 |
|----|----|--------|-----------|
| `processingId` | 字串 | 是 | 其狀態被查詢之作業的唯一ID。 |

**回應範例**

```JSON
{
  "processingId": "string",
  "path": "string",
  "excludedPaths": ["string"],
  "status": "WAITING",
  "triggeredCount": 0,
  "startedAt": 0,
  "completedAt": 0,
  "hasLogs": true,
  "createdBy": "string",
  "type": "ASSET_PROCESSING",
  "migrationSet": {
    "totalFiles": 0,
    "calculationStatus": "WAITING"
  },
  "eta": {
    "value": 0,
    "unit": "string"
  },
  "comments": "string",
  "restartable": true,
  "resumable": true,
  "cancellable": true
}
```

**回應代碼**

- 200項成功
- 400無效的輸入
- 401未經授權的存取
- 500內部伺服器錯誤

## 檢視工作記錄檔

GET方法，可擷取指定工作ID的記錄檔。 此API會擷取資產處理工作的記錄。 processingid為必要項。 API提供位移和限制引數，以及追蹤策略。

**要求URL**

`http://<aem-guides-server>:<port-number>/bin/guides/v1/assets/process/logs`

**要求引數**

| 名稱 | 類型 | 必要 | 說明 |
|----|----|--------|-----------|
| `processingId` | 字串 | 是 | 要檢視其記錄檔之工作的唯一ID。 |
| `offset` | 整數 | 否 | 應從中讀取記錄的起點（行號）。 用於分頁，以略過前N行。 |
| `limit` | 整數 | 否 | 要擷取的記錄行數上限。 |
| `tail` | 整數 | 否 | 要從結尾擷取的記錄行數。 |


**回應範例**

```JSON
{
  "lines": [
    "string"
  ],
  "limit": 0,
  "offset": 0,
  "hasMore": true
}
```

**回應代碼**

- 200項成功
- 400無效的輸入
- 401未經授權的存取
- 500內部伺服器錯誤


## 下載工作記錄檔

一種GET方法，可將指定工作的記錄檔下載為ZIP檔。

**要求URL**

`http://<aem-guides-server>:<port-number>/bin/guides/v1/assets/process/logs/download`

**要求引數**

| 名稱 | 類型 | 必要 | 說明 |
|----|----|--------|-----------|
| `processingId` | 字串 | 是 | 需要下載其記錄檔之作業的唯一ID。 |


**回應範例**

```JSON
{
  "logFilePaths": [
    "string"
  ]
}
 
```

**回應代碼**

- 400無效的輸入
- 401未經授權的存取
- 500內部伺服器錯誤

## 取消工作

取消進行中的大量資產處理請求的POST API。 如果找不到工作，API會傳回錯誤。

**要求URL**

`http://<aem-guides-server>:<port-number>/bin/guides/v1/assets/process/cancel`

**要求引數**

| 名稱 | 類型 | 必要 | 說明 |
|----|----|--------|-----------|
| `processingId` | 字串 | 是 | 其狀態被查詢之作業的唯一ID。 |


**回應代碼**

- 200項成功
- 400無效的輸入
- 401未經授權的存取
- 500內部伺服器錯誤


## 繼續工作

POST API可重新啟動先前已取消或失敗的批次資產處理請求。 它會從最後一個查核點繼續處理。 如果找不到工作或工作目前正在執行，API會傳回錯誤。

**要求URL**

`http://<aem-guides-server>:<port-number>/bin/guides/v1/assets/process/resume`

**要求引數**

| 名稱 | 類型 | 必要 | 說明 |
|----|----|--------|-----------|
| `processingId` | 字串 | 是 | 其狀態被查詢之作業的唯一ID。 |


**回應代碼**

- 200項成功
- 400無效的輸入
- 401未經授權的存取
- 500內部伺服器錯誤

## 檢視工作歷史記錄

傳回資產後續處理最後「N」個執行專案的GET API。

**要求URL**

`http://<aem-guides-server>:<port-number>/bin/guides/v1/assets/process/history`

**要求引數**

無。 此GET要求會擷取工作歷史記錄，而不需要輸入引數。

**回應範例**

```JSON
{
  "executionHistory": [
    {
      "processingId": "165f1de6-68c4-4dcd-9223-2b7242b62306",
      "path": "/content/dam/22858",
      "status": "SUCCESS",
      "triggeredCount": 6,
      "startedAt": 1761291362776,
      "completedAt": 1761291364026,
      "hasLogs": true,
      "createdBy": "user",
      "type": "ASSET_PROCESSING",
      "migrationSet": {
        "totalFiles": 6,
        "calculationStatus": "SUCCESS"
      },
      "eta": {
        "value": 0,
        "unit": "SECONDS"
      },
      "comments": "",
      "filter": {
        "fileTypes": [],
        "filterProcessedAssets": false
      },
      "cancellable": false,
      "resumable": false,
      "restartable": true
    }
  ]
}
```
