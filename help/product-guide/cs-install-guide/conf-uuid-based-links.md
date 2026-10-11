---
title: 設定UUID型連結的顯示方式
description: 瞭解如何設定顯示UUID型連結
exl-id: 2ae6a27f-983b-4aa0-be29-166899aeb4ff
feature: Web Editor Configuration
role: Admin
level: Experienced
TQID: 'https://experienceleague.adobe.com/--RdjezGIsplCdBLF8u-3LvR92rVBcgGmPo8a7GbQys'
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
source-wordcount: '162'
ht-degree: 1%
---
# 設定UUID型連結的顯示方式 {#id2035G20M0QN}

根據預設，當您在Web編輯器中使用「插入參照」或「插入重複使用內容」選項建立連結時，會使用參照內容的UUID來建立連結。 參考內容的&#x200B;**連結**&#x200B;屬性\（在「屬性」面板中\）可設定為顯示參考內容或UUID的相對檔案路徑。 根據預設，參考內容的UUID會顯示在「屬性」面板中。

使用[組態覆寫](download-install-additional-config-override.md#)中提供的指示來建立組態檔。 在設定檔中，提供下列\(property\)詳細資訊，以顯示網頁編輯器中參照內容的相對路徑或UUID：

| PID | 屬性索引鍵 | 屬性值 |
|---|------------|--------------|
| `com.adobe.fmdita.xmleditor.config.XmlEditorConfig` | `xmleditor.uuid` | 布林值\(true/false\)。 如果要顯示連結內容的相對路徑，則將此屬性設定為false。<br> **預設值**： true |

**上層主題：**&#x200B;[&#x200B;自訂Web編輯器](conf-web-editor.md)
