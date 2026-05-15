---
title: 發行說明 |修正2024.2.0版Adobe Experience Manager Guides中的問題
description: 瞭解Adobe Experience Manager Guides as a Cloud Service 2024.2.0版中的錯誤修正。
exl-id: fae1ff07-6232-4e9a-a89e-5e760e807b9d
TQID: https://experienceleague.adobe.com/z-L0sZ2HH720nI3LyDjiIqujxSBP-QLdPqvEInNNRnE
product_v2:
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: a3bd6397-2eb2-4908-a61c-226e26855dca
  - id: ab01a588-7dea-43f2-a699-0b3f128465d6
subfeature_v2:
  - id: ad602516-aca3-4247-9ae8-f393d958efa9
  - id: d6596f3f-92a7-43ec-b444-237db6adad05
  - id: f89f75b0-cf2e-4e96-aec8-fe8c39cbd0ef
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2:
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 504
ht-degree: 8%

---

# 已修正2024.2.0版本中的問題

本文介紹2024.2.0版Adobe Experience Manager Guides as a Cloud Service中多個區域修正的錯誤。

如需新功能和增強功能的詳細資訊，請參閱 [2024.2.0 版本中的新增功能](whats-new-2024-2-0.md)。

瞭解2024.2.0版[&#128279;](upgrade-instructions-2024-2-0.md)的升級指示。



## 製作

- 編輯器中的拼字檢查不允許選擇建議。 (15045)
- 全域導覽按鈕無法運作，且儀表板無法載入。 (14968)
- 在網頁編輯器中，下載對應功能在準備下載時無法觸發快顯通知。 (14626)
- 在網頁編輯器中，下載對應功能無法下載包含基準的對應。 (14622)
- 2023年10月發行的Experience Manager Guides as a Cloud Service中出現無效的DTD錯誤。 (14482)
- 將字彙表主題從存放庫拖曳到字彙表對應，會建立`topicref`。 (10767)
- 程式碼片段的預覽畫面會凍結。 (14840)
- `labels.json`檔案中的標籤會以隨機順序出現在網頁編輯器中。 (10508)

## 發佈

- 在原生PDF發佈中，條件預設集中的自訂屬性無法用於原生PDF發佈。 (14943)
- 在原生PDF發佈中，系統無法解析2023年12月版Adobe Experience Manager Guides的重要參考資料。 (15085)
- AEM Sites發佈失敗，並造成以「HTTP」開頭的DITA檔案中具有`xref`的檔案範圍錯誤。 (15154)
- 無法從編輯器中的&#x200B;**輸出**&#x200B;索引標籤新增自訂範本。 (14846)
- **AEM網站**&#x200B;預設集因範本路徑空白而無法運作。 (14804)
- 主題包含AEM方程式的DITA map的MathML網站重新產生失敗。 (14790)
- 在原生PDF發佈中，PDF產生會在取得`Node.js`發佈的相依性時擲回錯誤。 (14445)
- AEM預設集不允許在網頁編輯器中選取`/content`階層以外的範本。 (14260)
- 在AEM Sites輸出中，具有子元素的`<lines>`元素遺失樣式或分行符號。 (12542)
- 自訂中繼資料無法在最終輸出中使用。 (12116)
- 在原生PDF發佈中，DITA map中繼資料屬性無法用來填入PDF檔案輸出的中繼資料。 (15159)



## 管理

- **基準篩選**&#x200B;檔案在網頁編輯器中無法使用檔案名稱。 (13486)
- 停用編制父DITA map的索引以獲得更好的效能可能會影響某些功能的功能。(12213)


## 檢閱

- 右鍵內容功能表無法用於&#x200B;**接受**&#x200B;或&#x200B;**拒絕**&#x200B;追蹤變更。 (14607)
- 在2023年12月版的Adobe Experience Manager Guides中，在檢閱畫面中切換以關閉DITA主題沒有作用。 (14537)
- 自訂稽核工作流程的電子郵件範本不適用於覆蓋。 (13954)

## 已知問題

Adobe發現了2024.2.0版的以下已知問題：

- 1.0版不會顯示在重複DITA檔案的UI上。
- 為任何預設集啟用微服務後，資產中繼資料的傳播在2024.2.0版本中無法運作。
