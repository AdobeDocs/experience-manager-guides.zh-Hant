---
title: 啟用新的PDF引擎
description: 瞭解如何在Experience Manager Guides中啟用新的PDF引擎
feature: Web Editor Configuration
role: Admin
level: Experienced
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
source-wordcount: '74'
ht-degree: 2%
---

# 設定原生PDF引擎v2

原生PDF的新發佈引擎（即&#x200B;_原生PDF引擎v2_）提供&#x200B;_原生PDF引擎v1_&#x200B;問題的更新PDF演算功能及修正。

使用[組態覆寫](../install-conf-guide/download-install-config-override.md)中提供的指示來建立組態檔。 在設定檔案中，提供下列（屬性）詳細資訊：

| PID | 屬性索引鍵 | 屬性值 |
|-----|--------------|----------------|
| `com.adobe.fmdita.publish.config.GuidesPublishConfiguratorService` | `guides.publish.config` | `{"PDF_ENGINE": "v2"}` <br>預設值： `v1` |

