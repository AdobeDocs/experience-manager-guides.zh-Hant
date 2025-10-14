---
title: 追蹤資料夾或資產後續處理的API
description: 瞭解API以追蹤資料夾或資產的後續處理
feature: Post-Processing Event Handler
role: Developer
level: Experienced
source-git-commit: 558108650aeeeda440895972e460fa523b804bb2
workflow-type: tm+mt
source-wordcount: '150'
ht-degree: 9%

---

# 追蹤資料夾或資產後處理狀態的API

以下是POST方法，會啟動非同步工作來取得資產的狀態。

## 在指南中尋找資產狀態

**要求URL**

`http://<aem-guides-server>:<port-number>bin/guides/v1/assets/status `

**引數**

| 名稱 | 類型 | 必要 | 說明 |
|----|----|--------|-----------|
| `path` | 字串 | 是 | 需要擷取其狀態的資料夾或資產路徑。 |
| `excludedPaths` | 字串 | 否 | 要從上述清單排除的資料夾路徑。 |

```JSON
{ 

    "paths": [ 

        "/content/dam/status-fetch1", 

        "/content/dam/status-fetch2" 

    ], 

    "excludedPaths": [ 

        "content/dam/status-fetch1/excluded-folder" 

    ] 

} 
```

**回應值**
要輪詢以取得非同步作業狀態的jobId。

```JSON
{ 

  "jobId": "akjhdfalkj1132", 

  "status": "WAITING", 

 

} 
```

## Poller API

取得上述API所執行非同步工作狀態的GET方法。

**要求URL**

`http://<aem-guides-server>:<port-number>bin/guides/v1/assets/status`

**引數**

| 名稱 | 類型 | 必要 | 說明 |
|----|----|--------|-----------|
| `jobId` | 字串 | 是 | 由上述API傳回的工作ID 。 |

**回應值**

資產及其狀態的清單。

```JSON
{ 

  "jobId": " akjhdfalkj1132", 

  "status": "SUCCESS", 

  "assets": [ 

    { 

      "path": "/content/dam/status-fetch1/a.dita", 

      "uuid": "GUID-1293914ansd", 

      "status": "SUCCESS", 

      "exists": true 

    }, 

    { 

      "path": "/content/dam/status-fetch1/b.dita", 

      "uuid": "GUID-1883241", 

      "status": "FAILURE", 

      "exists": true 

    } 

 

  ] 

} 
```

**狀態值：**&#x200B;成功、失敗、處理、擱置
