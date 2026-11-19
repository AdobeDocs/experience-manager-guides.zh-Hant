---
title: 發行說明 |已修正Adobe Experience Manager Guides 5.2.0 Service Pack 3版本中的問題
description: 瞭解Adobe Experience Manager Guides 5.2.0 Service Pack 3版的錯誤修正
role: Leader
TQID: https://experienceleague.adobe.com/HEWV5RxPUfqUYf6m6kQW-fU-LiAM0UFGbfzKjtOCZxk
product_v2:
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
    internal-label: Experience Manager Guides
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
feature_v2:
  - id: a3bd6397-2eb2-4908-a61c-226e26855dca
    internal-label: Publishing
role_v2:
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
    internal-label: Leader
source-git-commit: 01aae4f8c25d87d2dd0a0255bedab8d7b091e54d
workflow-type: tm+mt
source-wordcount: '814'
ht-degree: 0%
---
# 已修正5.2.0 Service Pack 3版本（2026年11月）中的問題

本文章說明5.2.0 Service Pack 3版本Adobe Experience Manager Guides中不同區域所修正的錯誤。

瞭解5.2.0 Service Pack 3版本](upgrade-instructions-5-2-0-sp3.md)的[升級指示。

## 編輯器2.0

- 從製作模式複製資料表並將其貼到製作模式，會移除`colwidth`等屬性以及在`colspec`上定義的任何其他屬性，導致欄寬設定遺失。 (GUIDES-52916)
- 從Microsoft Word貼上表格時，會建立標題列儲存格，但儲存格內容會遺失。 (GUIDES-49847)
- 當程式碼從Microsoft Word或類似的文字編輯器使用Ctrl+V貼到`codeblock`元素中時，分行符號和前導空格會遺失，程式碼會平面化為單行。 (GUIDES-33247)

## 資產管理

- 資產狀態API不會針對路徑包含逗號的資產傳回正確狀態。 (GUIDES-49065)

## 發佈

- 在AEM Sites上發佈具有`processing-role=resource-only`個元素的DITA map （具有舊版元件對應）時，會在其他情境（例如`topicgroup`元素和特定內容設定）中為這些元素產生孤立網站頁面。 (GUIDES-37650)
- 分支篩選會針對用作`keydef`的不想要的主題產生額外頁面（這些主題已由DITA-OT標籤`resource-only ="true"`）。 (GUIDES-19701)
- 在「地圖」控制面板中，選取不同的預設集時會觸發呼叫以擷取同級連結，導致額外的處理。 (GUIDES-53703)
- 在原生PDF輸出中，以`toc="no"`屬性標籤的主題參考仍會包含在目錄中，導致內容冗長且雜亂。 (GUIDES-20156)
- 在某些情況下，當使用動態基準線產生完整DITA map並發佈至AEM Sites時，某些主題會以較舊或未核准的版本發佈，而不是以目前核准的版本發佈。 (GUIDES-55646)
- 處理大量資產時，`PurgePresetExecutionDataJob`有時會遇到未處理的`RuntimeNodeTraversalException`，導致工作陷入無限回圈並產生過多記錄。 (GUIDES-53897)
- 在原生PDF輸出中，`topichead`或`topicgroup`專案上設定的`outputclass`屬性未套用或轉送至產生的PDF區段。 (GUIDES-22950)
- 在某些情況下，使用原生PDF引擎v1發佈時，具有協助工具`settingsenabled`之內容的讀取順序不正確。 頁尾的頁碼會在主要內容之前閱讀，而非在結尾閱讀。(GUIDES-27790)


## 翻譯

- 將基準線套用至包含許多資產的地圖，會延遲載入所選語言的翻譯報表，有時會在報表轉譯之前導致請求逾時。 (GUIDES-45508)
- 當選取的語言資料夾使用連字地區設定代碼（例如，`da-DK`）而不是底線格式(`da_dk`)時，Workspace設定底下「翻譯」索引標籤中的語言群組不會保留。 (GUIDES-37843)
- 使用XLIFF專案開始翻譯時，會建立永遠不會變成進行中狀態的空白專案。 (GUIDES-51759)
- 當僅具有貢獻者角色的使用者存取編輯器時，全域資料夾設定檔中的`propagateVersionLabel`設定會斷斷續續地重設為`false`。 (GUIDES-51870)

## 基準線

- 刪除基準線後或仍在建立動態基準線時，預設集儲存的基準線選取範圍錯誤地顯示為&#x200B;*無基準線*。 (GUIDES-52690)
- 在某些情況下，動態基準線在失敗重建後仍卡在處理狀態，導致匯出和輸出產生使用過時的主題和對應版本，而不會顯示任何錯誤。 (GUIDES-56739)

## 檢閱

- 在涉及大量稽核任務的情況下，開啟稽核面板或套用專案篩選器需要比預期更長的時間來載入任務清單。 (GUIDES-48893)
- 檢閱UI中的內容窗格在某些熒幕解析度上顯示水準卷軸，包括建議的1600px解析度，當內容延伸超過窗格寬度時，會導致隱藏檢閱評論。 (GUIDES-44082)

## Platform

- 「移動API」、「重新命名API」和Assets UI可防止將檔案名稱為GUID的DITA資產重新命名為人類看得懂的檔案名稱。 Assets現在可重新命名為人類看得懂的檔案名稱，不過仍不允許將GUID型檔案名稱重新命名為其他的GUID型檔案名稱。 (GUIDES-43006， GUIDES-59684)
- 從非UUID設定移轉至UUID設定的非DITA資產（例如影像）恢復或分支至其他版本時，其UUID會變更。 不再解析資產的現有參照，且影像在參照該資產的主題中顯示為已損毀。 (GUIDES-58414)
- 安裝Experience Manager Guides Service Pack會從AEM **工具**&#x200B;區段中移除先前安裝的外部工具，例如ACS Commons。 (GUIDES-60365)

## 已知問題

Adobe已找出下列5.2.0 Service Pack 3版的已知問題：

- 安裝Service Pack後，Schematron驗證可能會因`NoClassDefFoundError`例外狀況而失敗，您無法儲存編輯器中的主題。 <br>**因應措施：**&#x200B;從AEM網頁主控台(`/system/console/bundles`)重新整理`com.adobe.fmdita.schematron-wrapper`套件。
