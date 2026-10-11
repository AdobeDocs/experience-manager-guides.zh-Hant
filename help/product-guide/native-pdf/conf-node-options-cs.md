---
title: 原生PDF |設定原生PDF發佈的節點程式
description: 瞭解如何設定原生PDF發佈的節點程式
feature: Output Generation
role: Admin
level: Experienced
exl-id: 5321c785-8259-4ee2-9ada-ee70fb99b4fd
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
    internal-label: Experience Manager Guides
feature_v2:
  - id: a3bd6397-2eb2-4908-a61c-226e26855dca
    internal-label: Publishing
subfeature_v2:
  - id: fd6cc9e1-e5e5-494e-b7b1-a32f2d6cd7c9
    internal-label: Output generation
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 81a0e7f0736ba4970673dd87a888a4c60d3c1b4e
workflow-type: tm+mt
source-wordcount: '122'
ht-degree: 1%
---
# 為Cloud Service的原生PDF發佈設定節點程式

原生PDF發佈會啟動個別的NodeJs程式，將在發佈程式中產生的檔案轉換為最終的PDF。 您可能必須調整此節點程式（執行原生PDF發佈）的設定，以支援不同情境。 例如，若要執行較大的工作負載，您應該增加衍生的NodeJs處理序可用的棧積大小上限。

使用[組態覆寫](../install-conf-guide/download-install-config-override.md)中提供的指示來建立組態檔。在設定檔案中，提供下列（屬性）詳細資訊：

| PID | 屬性索引鍵 | 屬性值 |
|---|---|---|
| `com.adobe.fmdita.config.ConfigManager` | `native.pdf.node.opts` | 要設定任何標準`NODE_OPTIONS`.<BR>的字串值 預設值： &quot;&quot; |
