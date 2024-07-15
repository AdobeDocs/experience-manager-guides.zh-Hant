---
title: 發行說明 | 已修正Adobe Experience Manager Guides 2024.4.0版本中的問題
description: 瞭解Adobe Experience Manager Guides as a Cloud Service 2024.04.0版中的錯誤修正。
exl-id: 35351d71-7739-4ad3-a063-67adf64906bf
source-git-commit: 5d99274da8fdacbd255d426fa4913b5773ca45f8
workflow-type: tm+mt
source-wordcount: '578'
ht-degree: 3%

---

# 已修正2024.04.0版本中的問題

本文介紹2024.04.0版Adobe Experience Manager Guides as a Cloud Service中多個區域修正的錯誤。

如需新功能和增強功能的詳細資訊，請參閱 [2024.04.0 版本中的新增功能](whats-new-2024-04-0.md)。

瞭解2024.04.0版](upgrade-instructions-2024-04-0.md)的[升級指示。

## 製作

- **複製**&#x200B;函式無法複製Adobe Experience Manager as a Cloud Service中的空白資料夾。 (15353)
- 網頁編輯器無法上傳.pptx檔案。 (14837)
- 在Web編輯器中尋找文字時，按下Enter鍵時，游標會回到搜尋文字的第一個專案。 (14820)
- 自動儲存會造成多個問題，它會重新定位游標，並需要手動點選檔案。 (14253)
- 開啟透過全域&#x200B;**尋找和取代**&#x200B;找到的檔案後，搜尋結果會停用。 (12142)
- 在來源檢視中，`</conbody>`偶爾會插入不正確的位置。 (11305)
- 在XML編輯器中，工具提示功能無法更新Source欄位。 (15847)
- **共用UUID連結**&#x200B;功能無法用於Adobe Experience Manager中的影像。 (15598)
- `<reltable>`和`<fig>`標籤中出現重疊文字問題。 (15238)
- **屬性**&#x200B;面板中發生忽隱忽現的問題。 (15237)
- 刪除內容中的字元或文字時，游標會在區塊元素之間跳躍。 (15224)
- **屬性**&#x200B;面板未顯示在網頁編輯器的Source檢視中。 (14387)
- 在網頁編輯器中的標籤結尾編輯時，會新增不想要的不間斷空格。 (11786)
- 修正DITA檔案中的拼字錯誤時會刪除內容。 (11610)


## 發佈

- 啟用&#x200B;**刪除孤立網站**&#x200B;選項時，AEM網站輸出產生失敗。 (15896)
- 將檔案新增至地圖集合時，編輯功能無法運作。 (15813)
- 在JSON輸出中，來自DITA map或主題的中繼資料無法傳播至JSON輸出檔案。 (15713)
- 重新命名預設集時，原生PDF發佈失敗。 (15662)
- 發佈的AEM網站輸出中的&#x200B;**sourcePath**&#x200B;屬性不正確。 (15502)
- 語言變數選取和自訂在原生PDF輸出預設集中無法正常運作。 (15399)
- 使用具有大型樣式表或版面的範本時，原生PDF產生會失敗。 (15344)
- 如果`<conref>`與絕對路徑一起使用，則發佈輸出中的內容無法正確轉譯。
- 由於`fmdita rewriter`和`ResourceResolver`之間發生衝突，AEM Sites URL縮短無法運作。 (14793)
- **processing-role=&quot;resource-only&quot;**、**search=&quot;no&quot;**&#x200B;和&#x200B;**chunk=&quot;to-content&quot;**&#x200B;屬性在AEM Sites輸出中分別出現不正。 (14442)
- 如果在任何資料夾設定檔內的資料夾路徑中設定了包含2k個地圖的資料夾，則套用至輸出預設集的變更會失敗。(14852)

## 管理

- 未關閉的&#x200B;**資源解析器**&#x200B;會造成工作階段計數增加，且2023年10月發行的Experience Manager Guidesas a Cloud Service中出現PathNotFoundException錯誤。 (15604)
- 功能標幟&#x200B;**fmdita.useapproval**&#x200B;未如預期運作。 (15310)
- 使用Java API建立基準線在2023年6月版本的Experience Manager Guidesas a Cloud Service中無法運作。 (14787)
- 當上傳的資產超過500 MB時，`/bin/fmdita/import` API會無限期地停滯在待處理要求中。 (14743)

## 檢閱

- 刪除檢閱節點會中斷在Adobe Experience Manager Guides中開啟和檢視註解的能力。 (15366)
- 在Web編輯器中，「稽核」面板載入緩慢。 (14680)

## 轉換

- **接受翻譯**&#x200B;無法完成暫存檔的翻譯。 (14665)
