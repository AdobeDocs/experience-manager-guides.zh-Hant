---
title: 設定UUID檔案名稱模式
description: 瞭解如何設定UUID檔案名稱模式
feature: Migration
role: Admin
level: Experienced
exl-id: 63d19ec4-1313-4691-b83e-38b67f9d2050
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
    internal-label: Experience Manager Guides
feature_v2:
  - id: 5be0fc8f-1cff-5c3e-bb92-2903a56a3de6
    internal-label: Migration
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 81a0e7f0736ba4970673dd87a888a4c60d3c1b4e
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 1%
---
# 設定UUID檔案名稱模式

匯入內容時，檔案名稱不必以UUID為基礎。 在使用以UUID為基礎的檔案名稱的系統中，所有檔案都必須使用其UUID來參照，而非原始檔案名稱。 如果匯入的檔案沒有以UUID為基礎的檔案名稱，您可以設定系統將UUID新增至其檔案屬性。 然後，會使用此UUID來引用未使用UUID來命名檔案的此類檔案。

## 設定UUID檔案名稱模式的步驟

下列標籤提供根據Experience Manager Guides設定來設定UUID檔案名稱模式的指示： Cloud Service或內部部署。

>[!BEGINTABS]

>[!TAB Cloud Service]

使用[組態覆寫](download-install-config-override.md#)中提供的指示來建立組態檔。 在設定檔案中，提供下列\(property\)詳細資料以設定UUID檔案名稱模式：

| PID | 屬性索引鍵 | 屬性值 |
|---|------------|--------------|
| `com.adobe.fmdita.config.ConfigManager` | `uuid.regex` | 指定UUID檔案名稱模式的規則運算式的字串。<br> 如果檔案未遵循指定的模式，則會將UUID新增至檔案的屬性，而且所有對該檔案的參照都會以指派給該檔案的UUID更新。<br> **預設值**： `"^GUID-(?<id>.*)"` |

>[!TAB 內部部署]

執行以下步驟來根據UUID模式檢查檔案名稱，並將UUID指派給未指派UUID的檔案：

1. 開啟Adobe Experience Manager Web主控台設定頁面。

   存取設定頁面的預設URL為：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜尋並選取&#x200B;*com.adobe.fmdita.config.ConfigManager*&#x200B;套件。

1. 在&#x200B;**UUID檔案名稱模式**&#x200B;屬性中，指定模式以檢查匯入檔案的名稱。

   如果檔案未遵循指定的模式，則會將UUID新增至檔案的屬性，而且所有對該檔案的參照都會以指派給該檔案的UUID更新。

1. 選取「**儲存**」。

>[!ENDTABS]
