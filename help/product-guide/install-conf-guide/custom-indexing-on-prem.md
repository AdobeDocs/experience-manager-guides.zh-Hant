---
title: 用於內部部署設定的自訂索引部署
description: 瞭解如何為內部部署設定自訂索引內容
feature: Web Editor Configuration
role: Admin
level: Experienced
exl-id: 87c0519d-120a-4bb7-b70f-7d217bcd7580
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
    internal-label: Experience Manager Guides
feature_v2:
  - id: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
    internal-label: Configuration
subfeature_v2:
  - id: b0521e56-a0b2-40b6-bf47-ebc98751f9ba
    internal-label: Web Editor configuration
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 81a0e7f0736ba4970673dd87a888a4c60d3c1b4e
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 0%
---
# 為內部部署的尋找和取代（Source檢視）功能重新編制索引

需要重新索引才能啟用&#x200B;**尋找和取代（Source檢視）**&#x200B;功能，此功能可讓您掃描在作者檢視中顯示的整個內容，以及搜尋字串的基礎Source內容（XML結構，包括元素、標籤和屬性值）。

## 重新索引

對於內部部署設定，索引定義會包含在套件中。 若要啟用此功能，您必須重新索引內容。

在節點` /oak:index/guidesAssetLucene`上設定屬性`reindex=true (Boolean)`來開始重新索引，以重新索引先前擷取的內容。

重新索引過程將繼續，直到系統自動將此屬性變更回false。 您可以在系統記錄檔中監視重新索引操作的進度。
