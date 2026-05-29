---
title: 追蹤資料夾或資產後續處理的API
description: 瞭解API以追蹤資料夾或資產的後續處理
feature: Post-Processing Event Handler
role: Developer
level: Experienced
exl-id: f902fac1-2717-4696-a835-c4b0bb8add3d
TQID: https://experienceleague.adobe.com/Lyv-S5o-Z40bMqqIHhbxKrsmn9CCqHRnqnpiq91EjGU
product_v2: id: fae5e35a-80c9-4b94-9352-1a060a6aab1did: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2: id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: a13143053c75ab65cbcd20a52c8ca3fb953edecf
workflow-type: tm+mt
source-wordcount: 198
ht-degree: 7%

---

# 追蹤資料夾或資產後處理狀態的API

>[!NOTE]
>
> 如需最新的REST API端點定義和相關詳細資訊，請在`https://<aem-author-url>/libs/fmdita/clientlibs/api-docs/index.html`檢視Swagger檔案（將`<aem-author-url>`取代為AEM伺服器URL）。 由於本文排程在2026年10月封存，我們建議您使用Swagger檔案來取得最新的API資訊。

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
