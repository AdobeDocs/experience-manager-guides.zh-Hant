---
title: 開始大量處理資產的API
description: 瞭解API以開始資產的批次處理
feature: Post-Processing Event Handler
role: Developer
level: Experienced
source-git-commit: e2eca63a5dd56e358aeea047b37f4b0f88dc720b
workflow-type: tm+mt
source-wordcount: '542'
ht-degree: 8%

---

# 開始大量處理資產的API

為指定路徑起始大量資產處理的POST方法。 此API支援JCR型和資料庫型資產處理。 它會啟動非同步作業，處理給定路徑及其子路徑下的所有資產。 啟動後，API會傳回唯一的processingID，可用於追蹤工作狀態。

**要求URL**

`http://<aem-guides-server>:<port-number>/bin/guides/v1/assets/process`

**要求引數**

| 名稱 | 類型 | 必要 | 說明 |
|----|----|--------|-----------|
| `path` | 字串 | 是 | 要處理的AEM存放庫中資料夾或資產的絕對路徑。 |
| `excludedPaths` | 字串 | 否 | 要從處理中排除的路徑清單 |
| `type` | 字串 | 是 | 要執行的處理型別。 例如：ASSET_PROCESSING。 |

**要求範例**

```JSON
{
  "path": "/content/dam/status-fetch1",
  "excludedPaths": [
    "content/dam/status-fetch1/excluded-folder"
  ],
  "type": "ASSET_PROCESSING"
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

一種GET方法，可擷取指定工作ID的記錄檔。 此API會擷取資產處理工作的記錄。 processingid為必要項。 API提供位移和限制引數，以及追蹤策略。

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

GET API可傳回資產後處理的最後一個「N」個執行。

**要求URL**

`http://<aem-guides-server>:<port-number>/bin/guides/v1/assets/process/history`

**要求引數**

無。 此GET請求會擷取工作歷史記錄，不需要輸入引數。

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



