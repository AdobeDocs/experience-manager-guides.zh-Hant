---
title: 發行說明 | 已修正Adobe Experience Manager Guides 4.6.1版本中的問題
description: 瞭解Adobe Experience Manager Guides 4.6.1版中的錯誤修正
role: Leader
source-git-commit: 3547eb43977f31dae297ca5cb1f1ab53f7f2b067
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 0%

---


# 已修正4.6.1版（2024年10月）中的問題


本文章說明4.6.1版Adobe Experience Manager Guides中不同區域所修正的錯誤。

瞭解4.6.1版](upgrade-instructions-4-6-1.md)的[升級指示。

## 製作

- 在`XMLEditorConfig`中啟用`xmleditor.uniquefilenames`時，無法在UUID執行個體上建立DITA map。 (21201)
- 關閉檔案時，**儲存變更及解除鎖定檔案**&#x200B;對話方塊中新增的註解和標籤沒有以新版本儲存在「版本記錄」中。 這是特定使用案例，其在`XMLEditorConfig`中啟用了&#x200B;**Ask for Check in Close**&#x200B;或&#x200B;**Ask for New Version on Close**。 (20065)
- 儲存新版本之前，標籤為&#x200B;**完成**&#x200B;的檔案狀態會回覆為&#x200B;**草稿**，導致&#x200B;**完成**&#x200B;狀態不會持續存在於任何檔案版本中。 (20006)
- 無法在網頁編輯器的主題中新增PDF檔案作為影像參考。 (21206)
- 在Assets UI中選取DITA檔案會顯示&#x200B;**在FrameMaker中開啟**&#x200B;選項，即使在組態中停用亦然。 (20082)


## 發佈

- 如果附件路徑超過允許的長度，則將附件上傳到Salesforce會失敗。 (19420)
- 將主題發佈至Salesforce時，PDF檔案連結無法解析。 (19304)
- 嘗試在Salesforce中重新發佈現有文章時，`DUPLICATE_VALUE`錯誤間歇性地發生。 (17932)
- 在原生PDF輸出中，目錄中有章節標題遺失，導致不正確的階層。 (21840)
- 發佈AEM Sites時，目錄中可包含的屬性數量有限。 (7483)

## 管理

- 因為記錄檔中發生未關閉的&#x200B;**ResourceResolver**&#x200B;錯誤，所以發生資源洩漏。 (18488)
- 建立新的或重複的基準線時，標籤會以隨機順序顯示。 (19307)









