---
title: 發行說明 | 已修正Adobe Experience Manager Guides 5.1.0 Service Pack 1版本中的問題
description: 瞭解Adobe Experience Manager Guides 5.1.0 Service Pack 1版中的錯誤修正
role: Leader
source-git-commit: 575488e1b378c17419add75876a8e7f7423d5116
workflow-type: tm+mt
source-wordcount: '148'
ht-degree: 1%

---

# 已修正5.1.0 Service Pack 1版本（2025年10月）中的問題


本文章說明5.1.0 Service Pack 1版本Adobe Experience Manager Guides中不同區域所修正的錯誤。

瞭解5.1.0 Service Pack 1版本[的](upgrade-instructions-5-1-0-sp1.md)升級指示。


## Platform

- 從非UUID移轉至UUID並升級至最新版本（5.0以上版本）時，如果您在資料夾之間移動參照的影像，然後將DITA檔案（這些影像參照的位置）回覆至先前的版本，則會導致影像參照損毀。 (GUIDES-34315)

## 發佈

- 在AEM Sites上使用基準線（搭配舊版元件對應）發佈DITA map時，也會發佈具有屬性`processing-role = resource-only`的map元素。 (GUIDES-34298)
