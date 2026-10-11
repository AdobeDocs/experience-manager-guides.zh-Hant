---
title: Cloud Service的設定覆寫
description: 瞭解如何設定覆寫
feature: Installation
role: Admin
level: Experienced
exl-id: baf48913-ced7-444f-a125-661c0213d847
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
    internal-label: Experience Manager Guides
feature_v2:
  - id: e88e74c7-6080-446a-8eb0-496f1ac5f7e6
    internal-label: Administration
subfeature_v2:
  - id: e557051c-ff02-4ff8-9421-cf452af0edd5
    internal-label: Installation
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 81a0e7f0736ba4970673dd87a888a4c60d3c1b4e
workflow-type: tm+mt
source-wordcount: '91'
ht-degree: 0%
---
# Cloud Service的設定覆寫 {#id216IFC003XA}

若要在Experience Manager Guides as a Cloud Service中進行任何設定更新，應使用下列通用方法：

1. 存取您的Cloud Manager Git存放庫。

1. 在下列位置建立新的JSON檔案：

   `src/main/content/jcr\_root/apps/fmditaCustom/config/`

1. 以下列格式命名檔案：

   `$\{PID\}.cfg.json`

   在此，PID是設定的處理序ID。

1. 使用以下格式在JSON檔案中新增屬性：

   ```
   {
      "aem.adminuname": "updatedUserjson",
      "valid.characters": "[-a-zA-Z0-9_@$]",
      "dita.serialization": true
   }
   ```

1. 認可變更並執行Cloud Manager管道以部署更新的設定。
