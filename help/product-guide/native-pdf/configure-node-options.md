---
title: 原生PDF |設定原生PDF發佈的節點程式
description: 瞭解如何設定原生PDF發佈的節點程式
feature: Output Generation
role: Admin
level: Experienced
exl-id: f470939b-a5cb-4d28-92d1-7a0a52c4c637
TQID: https://experienceleague.adobe.com/7i-6SjvI5FuSNsWPy9sX96UsXld9fJjAjHNKDKzo824
product_v2:
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: a3bd6397-2eb2-4908-a61c-226e26855dca
  - id: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
subfeature_v2:
  - id: d6596f3f-92a7-43ec-b444-237db6adad05
  - id: fd6cc9e1-e5e5-494e-b7b1-a32f2d6cd7c9
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 122
ht-degree: 1%

---

# 為Cloud Service的原生PDF發佈設定節點程式

原生PDF發佈會啟動個別的NodeJs程式，將在發佈程式中產生的檔案轉換為最終的PDF。 您可能必須調整此節點程式（執行原生PDF發佈）的設定，以支援不同情境。 例如，若要執行較大的工作負載，您應該增加衍生的NodeJs處理序可用的棧積大小上限。

使用[組態覆寫](../install-conf-guide/download-install-config-override.md)中提供的指示來建立組態檔。在設定檔案中，提供下列（屬性）詳細資訊：

| PID | 屬性索引鍵 | 屬性值 |
|---|---|---|
| `com.adobe.fmdita.config.ConfigManager` | `native.pdf.node.opts` | 要設定任何標準`NODE_OPTIONS`.<BR>的字串值 預設值： &quot;&quot; |
