---
title: 發行說明 |已修正Adobe Experience Manager Guides 4.6.0 Service Pack 1版本中的問題
description: 瞭解Adobe Experience Manager Guides 4.6.0 Service Pack 1版的錯誤修正
role: Leader
exl-id: ab45ac10-8a97-4ade-accc-2b884da0e973
TQID: https://experienceleague.adobe.com/-PGxudGeachzaYoru1fHTObZcwRuXzle5s7KRRJlfBA
product_v2:
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: a3bd6397-2eb2-4908-a61c-226e26855dca
  - id: ab01a588-7dea-43f2-a699-0b3f128465d6
  - id: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
subfeature_v2:
  - id: ad602516-aca3-4247-9ae8-f393d958efa9
  - id: d4f22c6d-7923-41e5-9da3-527ff8df4bc8
  - id: f89f75b0-cf2e-4e96-aec8-fe8c39cbd0ef
role_v2:
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
source-git-commit: cc73b81787a3c3dbe8390d93e558064327e59965
workflow-type: tm+mt
source-wordcount: 311
ht-degree: 4%

---

# 已修正4.6.0 Service Pack 1版本（2024年10月）中的問題


本文章說明4.6.0 Service Pack 1版本Adobe Experience Manager Guides中不同區域所修正的錯誤。

瞭解4.6.0 Service Pack 1版本[&#128279;](upgrade-instructions-4-6-0-sp1.md)的升級指示。

## 製作

- 在`XMLEditorConfig`中啟用`xmleditor.uniquefilenames`時，無法在UUID執行個體上建立DITA map。 (21201)
- 關閉檔案時，**儲存變更及解除鎖定檔案**&#x200B;對話方塊中新增的註解和標籤沒有以新版本儲存在「版本記錄」中。 這是特定使用案例，其在`XMLEditorConfig`中啟用了&#x200B;**Ask for Check in Close**&#x200B;或&#x200B;**Ask for New Version on Close**。 (20065)
- 儲存新版本之前，標籤為&#x200B;**完成**&#x200B;的檔案狀態會回覆為&#x200B;**草稿**，導致&#x200B;**完成**&#x200B;狀態不會持續存在於任何檔案版本中。 (20006)
- 無法將PDF檔案新增為編輯器主題中的影像參考。 (21206)
- 在Assets UI中選取DITA檔案會顯示&#x200B;**在FrameMaker中開啟**&#x200B;選項，即使在設定中停用亦然。 (20082)


## 發佈

- 如果附件路徑超過允許的長度，則將附件上傳到Salesforce會失敗。 (19420)
- 將主題發佈至Salesforce時，PDF檔案連結無法解析。 (19304)
- 嘗試在Salesforce中重新發佈現有文章時，`DUPLICATE_VALUE`錯誤間歇性地發生。 (17932)
- 在原生PDF輸出中，目錄中有章節標題遺失，導致不正確的階層。 (21840)
- 發佈AEM Sites時，目錄中可包含的屬性數量有限。 (7483)

## 管理

- 因為記錄檔中發生未關閉的&#x200B;**ResourceResolver**&#x200B;錯誤，所以發生資源洩漏。 (18488)
- 建立新的或重複的基準線時，標籤會以隨機順序顯示。 (19307)
