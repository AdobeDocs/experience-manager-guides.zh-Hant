---
title: 發行說明 |已修正Adobe Experience Manager Guides 5.0.0 Service Pack 1版本中的問題
description: 瞭解Adobe Experience Manager Guides 5.0.0 Service Pack 1版中的錯誤修正
role: Leader
exl-id: 1d0bc3d0-aedf-4f67-b6f7-2208facdee96
TQID: https://experienceleague.adobe.com/0qxye7ZUWt1iixHthjjTNJgtlOQX-C30jGi5zQlRJfA
product_v2:
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: a3bd6397-2eb2-4908-a61c-226e26855dca
  - id: ab01a588-7dea-43f2-a699-0b3f128465d6
role_v2:
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
topic_v2:
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 288
ht-degree: 1%

---

# 已修正5.0.0 Service Pack 1版本（2025年6月）中的問題


本文章說明5.0.0 Service Pack 1版本中不同區域所修正的Adobe Experience Manager Guides錯誤。

瞭解5.0.0 Service Pack 1版本[&#128279;](upgrade-instructions-5-0-0-sp1.md)的升級指示。

## 製作

- 將內容貼到`codeblock`中或在`codeblock`中新增空格並切換檢視時，間距會遺失。 (GUIDES-29347)
- 在&#x200B;**Source**&#x200B;檢視的元素中新增XML註解時，切換檢視時註解周圍的前導和尾端空格會遺失。 （指南 — 28188）

## 資產管理

- 瀏覽器重新整理後，在&#x200B;**作者**&#x200B;檢視中開啟主題時，不會保留&#x200B;**檔案屬性**&#x200B;面板中先前套用的標籤，新增標籤會覆寫現有標籤，尤其是有大量標籤可供選取時。 (GUIDES-29078)
- 為包含大量資產的DITA map產生中繼資料報表時，**管理**&#x200B;按鈕會變得無回應或顯示延遲回應。 (GUIDES-29778)

## 翻譯

- 從Experience Manager Guides傳送要翻譯的資產時，這些資產不會新增到翻譯工作中，這會防止出現&#x200B;**開始**&#x200B;按鈕，並阻止您起始翻譯工作。 (GUIDES-28237)

## 發佈

- 在資料夾設定檔中修改輸出預設集的設定並選取&#x200B;**套用預設集變更**&#x200B;時，變更不會傳播到DITA map中存在的輸出預設集。 (GUIDES-26694)

## 檢閱

- 嘗試透過AEM工作流程建立稽核任務一致地失敗，因為未建立稽核節點。 (GUIDES-28214)
