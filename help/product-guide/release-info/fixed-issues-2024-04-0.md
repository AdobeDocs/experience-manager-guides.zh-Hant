---
title: 發行說明 | 已修正2024.4.0版Adobe Experience Manager Guides中的問題
description: 瞭解Adobe Experience Manager Guidesas a Cloud Service版2024.04.0中的錯誤修正。
source-git-commit: 4c7421391922d276ef82515fb4b1cbdc2397e4ce
workflow-type: tm+mt
source-wordcount: '578'
ht-degree: 0%

---


# 已修正2024.04.0版本中的問題

本文介紹2024.04.0版Adobe Experience Manager Guidesas a Cloud Service中不同區域所修正的錯誤。

如需新功能和增強功能的詳細資訊，請檢視 [2024.04.0版的新增功能](whats-new-2024-04-0.md).

瞭解 [2024.04.0版的升級指示](upgrade-instructions-2024-04-0.md).

## 製作

- 此 **複製** 函式無法在Adobe Experience Manager as a Cloud Service中複製空白資料夾。 (15353)
- 網頁編輯器無法上傳.pptx檔案。 (14837)
- 在Web編輯器中尋找文字時，按下Enter鍵時，游標會回到搜尋文字的第一個專案。 (14820)
- 自動儲存會造成多個問題，它會重新定位游標，並需要手動點選檔案。 (14253)
- 開啟透過全域找到的檔案後，搜尋結果會停用 **尋找和取代**. (12142)
- 在來源檢視中， `</conbody>` 有時會插入不正確的位置。 (11305)
- 在XML編輯器中，工具提示功能無法更新來源欄位。 (15847)
- 此 **共用UUID連結** 功能無法用於Adobe Experience Manager中的影像。 (15598)
- 中發生重疊文字問題 `<reltable>` 和 `<fig>` 標籤之間。 (15238)
- 發生忽隱忽現問題的位置 **屬性** 面板。 (15237)
- 刪除內容中的字元或文字時，游標會在區塊元素之間跳躍。 (15224)
- 此 **屬性** 面板不會顯示在網頁編輯器的來源檢視中。 (14387)
- 在網頁編輯器中的標籤結尾編輯時，會新增不想要的不間斷空格。 (11786)
- 修正DITA檔案中的拼字錯誤時會刪除內容。 (11610)


## 發佈

- AEM網站輸出產生失敗的原因為 **刪除孤立網站** 選項已啟用。 (15896)
- 將檔案新增至地圖集合時，編輯功能無法運作。 (15813)
- 在JSON輸出中，來自DITA map或主題的中繼資料無法傳播至JSON輸出檔案。 (15713)
- 重新命名預設集時，原生PDF發佈失敗。 (15662)
- 此 **來源路徑** 發佈的AEM網站輸出上的屬性不正確。 (15502)
- 語言變數選取和自訂在原生PDF輸出預設集中無法正常運作。 (15399)
- 使用具有大型樣式表或版面的範本時，原生PDF產生會失敗。 (15344)
- 如果發生下列情況，發佈輸出中的內容便無法正確轉譯： `<conref>` 與絕對路徑搭配使用。
- AEM Sites URL縮短無法運作，因為 `fmdita rewriter` 和 `ResourceResolver`. (14793)
- 此 **processing-role=&quot;resource-only&quot;**， **search=&quot;no&quot;**、和 **chunk=&quot;to-content&quot;** 屬性在AEM Sites輸出中不會分別出現。 (14442)
- 如果在任何資料夾設定檔內的資料夾路徑中設定了包含2k個地圖的資料夾，則套用至輸出預設集的變更會失敗。(14852)

## 管理

- 未關閉 **資源解析器** 導致2023年10月發行的Experience Manager指南as a Cloud Service出現工作階段計數增加和PathNotFoundException錯誤。 (15604)
- 功能標幟 **fmdita.useapproval** 未按預期運作。 (15310)
- 使用Java API建立基準線在2023年6月版本的Experience Manager指南as a Cloud Service中無法運作。 (14787)
- 此 `/bin/fmdita/import` 當上傳的資產超過500 MB時，API會無限期停滯在待處理請求中。 (14743)

## 檢閱

- 刪除檢閱節點會中斷在Adobe Experience Manager Guides中開啟和檢視評論的功能。 (15366)
- 在Web編輯器中，「稽核」面板載入緩慢。 (14680)

## 轉換

- **接受翻譯** 無法完成暫存檔的翻譯。 (14665)


