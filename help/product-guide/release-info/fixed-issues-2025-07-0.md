---
title: 發行說明 | 已修正2025.07.0版Adobe Experience Manager Guides中的問題
description: 瞭解Adobe Experience Manager Guides as a Cloud Service 2025.07.0版中的錯誤修正。
exl-id: 0744e821-5aee-432b-a6c8-7ed6538935db
source-git-commit: c4d3cdd2a0a98b7c9c937c66c5c3130bf4c5c164
workflow-type: tm+mt
source-wordcount: '527'
ht-degree: 4%

---

# 2025.07.0版中的已修正問題

本文介紹2025.07.0版Adobe Experience Manager Guides as a Cloud Service中不同區域修正的錯誤。

如需新功能和增強功能的詳細資訊，請參閱 [2025.07.0 版本中的新增功能](whats-new-2025-07-0.md)。

瞭解2025.07.0版[的](upgrade-instructions-2025-07-0.md)升級指示。

## 製作

- 在Source檢視的元素中新增XML註解時，切換檢視時註解周圍的前導和尾隨空格會遺失。 (GUIDES-29781)
- 當出現在工具列的省略符號圖示（**更多**&#x200B;功能表）中時，多媒體選項無法運作。 (GUIDES-29583)
- 透過Assets UI或編輯器建立新主題時，如果`xmleditor.uniquefilenames`中的`XMLEditorConfig`設定設為true，則不會在編輯器中自動開啟主題。 (GUIDES-28171)
- 切換「編輯器」檢視時，不會保留Source檢視中MathML方程式內新增的空格。 (GUIDES-26111)

## 資產管理

- 在瀏覽器重新整理後，在「作者」檢視中開啟主題時，不會保留先前在「檔案屬性」面板中套用的標籤，新增標籤會覆寫現有標籤，尤其是有大量標籤可供選取時。 (GUIDES-29078)
- 為包含大量資產的DITA map產生中繼資料報表時，**管理**&#x200B;按鈕會停止回應或出現延遲回應。 (GUIDES-28443)

## 檢閱

- 嘗試透過AEM工作流程建立稽核任務總是會失敗，因為並未建立稽核節點。 (GUIDES-28214)

## 發佈

- 透過Cloud Manager部署AEM Sites發佈元件套件`guides-components.all-1.3.0.zip`時發生程式碼品質錯誤。 (GUIDES-28873)
- 發佈具有`chunk=to-content`屬性的DITA map會在新的AEM Sites輸出中建立重複的JCR節點，導致AEM Sites中出現重複的內容結構。 (GUIDES-28104)
- 使用新的AEM Sites輸出發佈DITA map時，如果主題具有`chunk =to-content`屬性，且輸出設定為使用主題標題作為頁面名稱，則產生的頁面名稱會錯誤地顯示單字&#x200B;**區塊**，而不是保留原始主題名稱。 (GUIDES-28102)
- 在新AEM Sites發佈的AEM Guides主題範本中設定的`cq:template`屬性顯示不正確的值，這會影響範本結構和內容呈現。 (GUIDES-27789)


## Platform

- 處理大型集合時，會觀察到載入時間較長及間歇性逾時等效能問題。 (GUIDES-29065， GUIDES-28793)
- 與在Experience Manager Guides上傳之AEM Guides元件中使用的已棄用Guava程式庫相關的漏洞。(GUIDES-27402)

## 已知問題

Adobe已找出下列2025.07.0版的已知問題：

- 使用Markdown主題時，編輯器工具列中會顯示&#x200B;**主題參考**&#x200B;按鈕，但無法運作。 (GUIDES-31038)
- 在編輯器中，資料夾節點名稱無法正確取代資料夾標題。 (GUIDES-30909)
- 在&#x200B;**合併**&#x200B;對話方塊中，下拉式清單錯誤地顯示&#x200B;**主要內容**，而不是顯示所選主題的可用版本。 (GUIDES-30820)
- 在啟用Unified Shell的情況下開啟DITA Map時，編輯器會間歇性地重新整理。(GUIDES-26919)
