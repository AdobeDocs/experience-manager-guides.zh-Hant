---
title: 發行說明 |已修正Adobe Experience Manager Guides 5.1.0 Service Pack 1版本中的問題
description: 瞭解Adobe Experience Manager Guides 5.1.0 Service Pack 1版中的錯誤修正
role: Leader
exl-id: 4b51085b-1f71-41e2-b0a9-88a12990fc97
TQID: https://experienceleague.adobe.com/HEWV5RxPUfqUYf6m6kQW-fU-LiAM0UFGbfzKjtOCZxk
product_v2: id: fae5e35a-80c9-4b94-9352-1a060a6aab1did: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: a3bd6397-2eb2-4908-a61c-226e26855dca
role_v2: id: f8a45b24-4be7-4f1b-909b-60d06b483a20
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 144
ht-degree: 1%

---

# 已修正5.1.0 Service Pack 1版本（2025年10月）中的問題


本文章說明5.1.0 Service Pack 1版本Adobe Experience Manager Guides中不同區域所修正的錯誤。

瞭解5.1.0 Service Pack 1版本](upgrade-instructions-5-1-0-sp1.md)的[升級指示。


## Platform

- 從非UUID移轉至UUID並升級至最新版本（5.0以上版本）時，如果您在資料夾之間移動參照的影像，然後將DITA檔案（這些影像參照的位置）回覆至先前的版本，則會導致影像參照損毀。 (GUIDES-34315)

## 發佈

- 在AEM Sites上使用基準線（搭配舊版元件對應）發佈DITA map時，也會發佈具有屬性`processing-role = resource-only`的map元素。 (GUIDES-34298)
