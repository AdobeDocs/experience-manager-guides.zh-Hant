---
title: 發行說明 | 已修正2024.12.0版Adobe Experience Manager Guides中的問題
description: 瞭解Adobe Experience Manager Guides as a Cloud Service 2024.12.0版中的錯誤修正。
source-git-commit: f643a4a22151af2ff14288ab3885c1a6657a80ca
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 1%

---

# 已修正2024.12.0版本中的問題

本文介紹2024.12.0版Adobe Experience Manager Guides as a Cloud Service中多個區域修正的錯誤。

瞭解2024.12.0版](./upgrade-instructions-2024-12-0.md)的[升級指示。

## 製作

- 在`XMLEditorConfig`中啟用`xmleditor.uniquefilenames`時，無法在UUID執行個體上建立DITA map。 (21201)
- 關閉檔案時，**儲存變更及解除鎖定檔案**&#x200B;對話方塊中新增的註解和標籤沒有以新版本儲存在「版本記錄」中。 這是特定使用案例，其在`XMLEditorConfig`中啟用了&#x200B;**Ask for Check in Close**&#x200B;或&#x200B;**Ask for New Version on Close**。 (20065)
- 儲存新版本之前，標籤為&#x200B;**完成**&#x200B;的檔案狀態會回覆成&#x200B;**草稿**，導致&#x200B;**完成**&#x200B;狀態不會持續存在於任何檔案版本中。 (20006)
- 無法在網頁編輯器的主題中新增PDF檔案作為影像參考。 (21206)
- 在Assets UI中選取DITA檔案會顯示&#x200B;**在FrameMaker中開啟**&#x200B;選項，即使在組態中停用亦然。 (20082)

## 發佈

- 在原生PDF輸出中，目錄中有章節標題遺失，導致不正確的階層。 (21840)


## 管理

- 因為記錄檔中有&#x200B;**個未關閉的ResourceResolver**&#x200B;錯誤，所以發生資源洩漏。 (18488)
- 建立新的或重複的基準線時，標籤會以隨機順序顯示。 (19307)


## 基準線

- 如果基線具有大量主題或地圖，請在1分鐘後編輯並在雲端設定上儲存基線並逾時。 (19558)

## 翻譯

- 使用基線的地圖轉譯會變得緩慢，最終無法載入所有關聯主題和地圖檔案的清單。 (19733)
