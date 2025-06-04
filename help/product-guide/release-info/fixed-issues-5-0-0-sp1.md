---
title: 發行說明 | 已修正Adobe Experience Manager Guides 5.0.0 Service Pack 1版本中的問題
description: 瞭解Adobe Experience Manager Guides 5.0.0 Service Pack 1版中的錯誤修正
role: Leader
source-git-commit: 083a8e16b9d3cd6c3894d7eaa2fee489b1dc0bb8
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 1%

---


# 已修正5.0.0 Service Pack 1版本（2025年6月）中的問題


本文章說明5.0.0 Service Pack 1版本中不同區域所修正的Adobe Experience Manager Guides錯誤。

瞭解5.0.0 Service Pack 1版本[&#128279;](upgrade-instructions-5-0-0-sp1.md)的升級指示。

## 製作

- 將內容貼到`codeblock`中或在`codeblock`中新增空格並切換檢視時，間距會遺失。 (GUIDES-29347)
- 在&#x200B;**Source**&#x200B;檢視的元素中新增XML註解時，切換檢視時註解周圍的前導和尾端空格會遺失。 (指南 — 28188)

## 資產管理

- 瀏覽器重新整理後，在&#x200B;**作者**&#x200B;檢視中開啟主題時，不會保留&#x200B;**檔案屬性**&#x200B;面板中先前套用的標籤，新增標籤會覆寫現有標籤，尤其是有大量標籤可供選取時。 (GUIDES-29078)
- 為包含大量資產的DITA map產生中繼資料報表時，**管理**&#x200B;按鈕會變得無回應或顯示延遲回應。 (GUIDES-29778)

## 翻譯

- 從Experience Manager Guides傳送要翻譯的資產時，這些資產不會新增到翻譯工作中，這會防止出現&#x200B;**開始**&#x200B;按鈕，並阻止您起始翻譯工作。 (GUIDES-28237)

## 發佈

- 在資料夾設定檔中修改輸出預設集的設定並選取&#x200B;**套用預設集變更**&#x200B;時，變更不會傳播到DITA map中存在的輸出預設集。 (GUIDES-26694)

## 檢閱

- 嘗試透過AEM工作流程建立稽核任務一致地失敗，因為未建立稽核節點。 (GUIDES-28214)
