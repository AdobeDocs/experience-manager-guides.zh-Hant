---
title: 發行說明 | 已修正Adobe Experience Manager Guides 4.6.0 Service Pack 4版本中的問題
description: 瞭解Adobe Experience Manager Guides 4.6.0 Service Pack 4版中的錯誤修正
role: Leader
source-git-commit: f9a03ae620a362989a36ebaefb264ea28220a4b3
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 1%

---

# 已修正4.6.0 Service Pack 4版本（2025年4月）中的問題


本文章說明4.6.0 Service Pack 4版本Adobe Experience Manager Guides中不同區域所修正的錯誤。

瞭解4.6.0 Service Pack 4版本[&#128279;](upgrade-instructions-4-6-0-sp4.md)的升級指示。

## 製作

- 在&#x200B;**作者**&#x200B;檢視中，拖放主題內的影像會導致影像參考中斷，進而導致資料遺失。 (25769)
- 在&#x200B;**作者**&#x200B;檢視中的地圖中拖放`topicref`無法執行預期的作業，並移除拖曳的`topicref`旁的`topicref`。 (19460)
- 在更新或建立主題時若無法關閉JCR工作階段連線，會導致記憶體洩漏和服務停機時間。 (26282)

## 發佈

- 如果DITA內容具有網路連結，但範圍不是`external`，原生PDF會無限期地繼續發佈。 (26434)
- 建立含有大量標籤的新基準線時，會導致標籤載入器失敗並防止擷取標籤。 (16232)
- 當內容發生錯誤時，原生PDF和AEM網站的發佈會停止並排入佇列。 (26516)

## 已知問題

Adobe已找出此版本的下列已知問題：

- 當DITA內容包含不包含`scope`屬性的外部連結時，Windows上的原生PDF發佈會失敗。
