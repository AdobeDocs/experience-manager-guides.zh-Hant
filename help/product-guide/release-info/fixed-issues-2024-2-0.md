---
title: 發行說明 | 已修正Adobe Experience Manager Guides 2024.2.0版本中的問題
description: 瞭解Adobe Experience Manager Guides as a Cloud Service 2024.2.0版中的錯誤修正。
exl-id: fae1ff07-6232-4e9a-a89e-5e760e807b9d
source-git-commit: e40ebf4122decc431d0abb2cdf1794ea704e5496
workflow-type: tm+mt
source-wordcount: '509'
ht-degree: 4%

---

# 已修正2024.2.0版本中的問題

本文介紹2024.2.0版Adobe Experience Manager Guides as a Cloud Service中多個區域修正的錯誤。

如需新功能和增強功能的詳細資訊，請參閱 [2024.2.0 版本中的新增功能](whats-new-2024-2-0.md)。

瞭解2024.2.0版](upgrade-instructions-2024-2-0.md)的[升級指示。



## 製作

- 編輯器中的拼字檢查不允許選擇建議。 (15045)
- 全域導覽按鈕無法運作，且儀表板無法載入。 (14968)
- 在網頁編輯器中，下載對應功能在準備下載時無法觸發快顯通知。 (14626)
- 在網頁編輯器中，下載對應功能無法下載包含基準的對應。 (14622)
- 2023年10月發行的Experience Manager Guidesas a Cloud Service中的DTD錯誤無效。 (14482)
- 將字彙表主題從存放庫拖曳到字彙表對應，會建立`topicref`。 (10767)
- 程式碼片段的預覽畫面會凍結。 (14840)
- `labels.json`檔案中的標籤會以隨機順序出現在網頁編輯器中。 (10508)

## 發佈

- 在原生PDF發佈中，條件預設集中的自訂屬性無法用於原生PDF發佈。 (14943)
- 在原生PDF發佈中，無法針對2023年12月版本的Adobe Experience Manager Guides解析關鍵參考資料。 (15085)
- AEM Sites發佈失敗，並造成以「HTTP」開頭的DITA檔案中具有`xref`的檔案範圍錯誤。 (15154)
- 無法從編輯器中的&#x200B;**輸出**&#x200B;索引標籤新增自訂範本。 (14846)
- **AEM Site**&#x200B;預設集因空白範本路徑而無法運作。 (14804)
- 對於主題包含MathML方程式的DITA map，AEM網站重新產生失敗。 (14790)
- 在原生PDF發佈中，產生PDF會導致取得`Node.js`發佈的相依性時發生錯誤。 (14445)
- AEM預設集不允許在網頁編輯器中選取`/content`階層以外的範本。 (14260)
- 在AEM Sites輸出中，具有子元素的`<lines>`元素遺失樣式或分行符號。 (12542)
- 自訂中繼資料無法在最終輸出中使用。 (12116)
- 在原生PDF發佈中，無法使用DITA map中繼資料屬性來填入PDF檔案輸出的中繼資料。 (15159)



## 管理

- **基準篩選**&#x200B;檔案在網頁編輯器中無法使用檔案名稱。 (13486)
- 停用父DITA map的索引以獲得更好的效能可能會影響某些功能的功能。(12213)


## 檢閱

- 右鍵內容功能表無法用於&#x200B;**接受**&#x200B;或&#x200B;**拒絕**&#x200B;追蹤變更。 (14607)
- 在2023年12月版的Adobe Experience Manager Guides中，在檢閱畫面中切換以關閉DITA主題沒有作用。 (14537)
- 自訂稽核工作流程的電子郵件範本不適用於覆蓋。 (13954)

## 已知問題

Adobe發現以下2024.2.0版的已知問題：

- 1.0版不會顯示在重複DITA檔案的UI上。
- 為任何預設集啟用微服務後，資產中繼資料的傳播在2024.2.0版本中無法運作。
