---
title: 原生PDF |設定原生PDF發佈的節點程式
description: 瞭解如何設定原生PDF發佈的節點程式
feature: Output Generation
role: Admin
level: Experienced
hidefromtoc: true
source-git-commit: 564ee1731be2378744ffd2ed54a2fd423901a0b3
workflow-type: tm+mt
source-wordcount: '121'
ht-degree: 1%

---

# 為Cloud Service的原生PDF發佈設定節點程式

原生PDF發佈會啟動個別的NodeJs程式，將在發佈程式中產生的檔案轉換為最終的PDF。 您可能必須調整此節點程式（執行原生PDF發佈）的設定，以支援不同情境。 例如，若要執行較大的工作負載，您應該增加衍生的NodeJs處理序可用的棧積大小上限。

使用[組態覆寫](../install-conf-guide/download-install-config-override.md)中提供的指示來建立組態檔。在組態檔中，提供下列（屬性）詳細資料：

| PID | 屬性索引鍵 | 屬性值 |
|---|---|---|
| `com.adobe.fmdita.config.ConfigManager` | `native.pdf.node.opts` | 要設定任何標準`NODE_OPTIONS`的字串值。<BR>預設值： &quot;&quot; |
