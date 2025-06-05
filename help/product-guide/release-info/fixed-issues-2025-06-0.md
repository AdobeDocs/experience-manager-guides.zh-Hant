---
title: 發行說明 | 已修正2025.06.0版Adobe Experience Manager Guides中的問題
description: 瞭解Adobe Experience Manager Guides as a Cloud Service 2025.06.0版中的錯誤修正。
exl-id: 0f362ab3-0fae-4eba-bbd6-0b64ae1f2599
source-git-commit: c137f18d3cb85ed47547d5523c4dea08c22f9560
workflow-type: tm+mt
source-wordcount: '516'
ht-degree: 4%

---

# 2025.06.0版中的已修正問題

本文介紹2025.06.0版Adobe Experience Manager Guides as a Cloud Service中不同區域修正的錯誤。

如需新功能和增強功能的詳細資訊，請參閱 [2025.06.0 版本中的新增功能](whats-new-2025-06-0.md)。

瞭解2025.06.0版[&#128279;](upgrade-instructions-2025-06-0.md)的升級指示。

## 製作

- 在更新或建立主題時若無法關閉JCR工作階段連線，會導致記憶體洩漏和服務停機時間。 (GUIDES-26282)
- 拖曳欄會將欄寬從百分比變更為畫素值，導致表格扭曲或錯位。(GUIDES-23128)
- 將內容貼到`code block`中或在`code block`中新增空格並切換檢視時，間距會遺失。 (GUIDES-27478)
- 將地圖新增至`bookmap`時，它儲存在`fmditatopicrefs`中，而非`fmditamaprefs`中。 (GUIDES-25480)
- **插入影像**&#x200B;對話方塊無法在高解析度或縮小熒幕上正確轉譯，導致圖示題和替代文字欄位消失。 (GUIDES-26459)


## 發佈

- 如果DITA內容具有網路連結，但範圍不是`external`，原生PDF會無限期地繼續發佈。 (GUIDES-26434)
- 當內容發生錯誤時，原生PDF和AEM網站的發佈會停止並排入佇列。 (GUIDES-26516)
- 建立具有大量標籤的新基準線時，它會防止擷取所有標籤。 (GUIDES-16232)
- 產生標題含有多個以空格分隔的字詞的AEM網站頁面時，地圖示題會顯示連字型大小而非空格。 (GUIDES-27903)
- 對於原生PDF，無效的中繼資料屬性名稱未解析，且在&#x200B;**檔案屬性**&#x200B;中顯示為`unresolved property name`。 (GUIDES-25680)
- `codeblock`內的多行文字會在PDF產生期間造成文字溢位問題。 (GUIDES-15541)
- 將地圖新增至地圖集合時，會顯示地圖以外的資產（例如主題等），且翻譯的地圖語言也不會正確排序。(GUIDES-25085)


## 檢閱

- 檢閱UI中的檔案檢視不會包住某些熒幕大小的內容，因此使用者必須水準捲動才能檢視完整內容。 (GUIDES-25292)


## 已知問題

Adobe發現以下2025.06.0版的已知問題：

- 使用「尋找和取代」選項時，在檔案上套用「取代單一專案」操作後，無法在「尋找和取代」面板中執行進一步的動作。 (GUIDES-28930)

- 在啟用Unified Shell的情況下開啟DITA Map時，編輯器會間歇性地重新整理。 (GUIDES-26919)

- 針對資料夾設定檔底下的AI設定，當從UI中刪除已編制索引的資產時，將不會移除對應的已編制索引路徑，且嘗試重新編制索引會失敗並出現錯誤訊息。 (GUIDES-29147) <br>**因應措施：**&#x200B;您必須先移除已不存在的過時路徑，才能起始重新索引。

- 如果對應包含循環相依性且您開啟了「對應預覽」，則在重新整理瀏覽器之前，將無法存取Source、作者和版面檢視。 (GUIDES-28334) <br>**因應措施：**&#x200B;您必須重新整理瀏覽器，才能還原對這些檢視的存取權。
