---
title: 將進階地圖編輯器設定為預設值
description: 瞭解如何將進階地圖編輯器設為預設值
exl-id: 365264ab-f990-42c1-ab79-61a40ecea42f
feature: Web Editor Configuration
role: Admin
level: Experienced
TQID: 'https://experienceleague.adobe.com/xTRMho5Nhc9KScSAzQIXy5Z6bMAe-ERLjhZMItRyj4k'
product_v2:
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
    internal-label: Experience Manager Guides
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
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
source-wordcount: '296'
ht-degree: 0%
---
# 將進階地圖編輯器設定為預設值 {#id181AI0003PN}

>[!NOTE]
>
> Basic Map Editor （先前在Experience Manager Guides中提供）已從4.3版和2307版開始淘汰。 您無法存取「基本對映編輯器」來建立和管理DITA map。
>建議您使用進階地圖編輯器。 進階地圖編輯器提供增強功能和更好的自訂選項。 深入瞭解如何使用[進階地圖編輯器](../user-guide/map-editor-advanced-map-editor.md)。

對於4.3和2307之前的版本，Experience Manager Guides隨附基本地圖編輯器和進階地圖編輯器。 基本地圖編輯器提供您建立地圖檔案所需的所有功能。 進階地圖編輯器功能更豐富，並整合在網頁編輯器中。 「進階對映編輯器」可讓作者使用易用的介面來建立和編輯DITA map檔案。

根據預設，每當建立新的對映檔案時，它都會在「基本對映編輯器」中開啟。 您可以讓設定預設為開啟「進階地圖編輯器」來變更此行為。

使用[組態覆寫](download-install-additional-config-override.md#)中提供的指示來建立組態檔。 在設定檔中，提供下列\(property\)詳細資訊，以啟用基本地圖編輯器：

| PID | 屬性索引鍵 | 屬性值 |
|---|------------|--------------|
| `com.adobe.fmdita.xmleditor.config.XmlEditorConfig` | ``fmdita.hide.oldmapeditor`` | 布林值\(true/false\)。 如果您預設要使用進階對應編輯器，請將此屬性設定為true。<br> **預設值**： false |

>[!NOTE]
>
> 依預設，當作者建立對應檔案並選擇開啟它以進行編輯時，就會啟動「基本對應編輯器」。 從Assets UI選取地圖檔案的「編輯」選項時，基本地圖編輯器中也會開啟該選項。

**上層主題：**[&#x200B;自訂Web編輯器](conf-web-editor.md)
