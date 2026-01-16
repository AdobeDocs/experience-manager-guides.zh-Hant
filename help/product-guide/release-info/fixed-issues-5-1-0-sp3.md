---
title: 發行說明 | 已修正Adobe Experience Manager Guides 5.1.0 Service Pack 3版本中的問題
description: 瞭解Adobe Experience Manager Guides 5.1.0 Service Pack 3版的錯誤修正
role: Leader
source-git-commit: 82eb0e18eb285006c66b1fe2b6ecc3ca86fefe61
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 1%

---

# 已修正5.1.0 Service Pack 3版本（2025年12月）中的問題


本文章說明5.1.0 Service Pack 3版本Adobe Experience Manager Guides中不同區域所修正的錯誤。

瞭解5.1.0 Service Pack 3版本[的](upgrade-instructions-5-1-0-sp3.md)升級指示。


## 製作

- 在瀏覽器重新整理時，在主題或地圖的資料夾層級設定檔中套用的自訂CSS將恢復為預覽模式的預設樣式。 (GUIDES-31098)
- 無法從&#x200B;**另存為新版本**&#x200B;對話方塊將多個&#x200B;**版本標籤**&#x200B;新增至主題。 (GUIDES-32716)


## 資產管理

- 無法從Assets UI的&#x200B;**版本記錄**&#x200B;面板中移除版本標籤。 (GUIDES-38276)


## 檢閱

- 當稽核者完成稽核任務或發起者更新稽核任務而未輸入註解時，傳送的通知電子郵件會顯示最近的前一個註解。 (GUIDES-33590)

## 發佈

- 當您使用舊版元件對應產生AEM Sites輸出時，使用`copy-to`屬性的主題會以`copy-from`主題的名稱（而不是`copy-to`屬性中設定的名稱）發佈。 (GUIDES-22155)
- 當使用動態基準產生原生PDF輸出時，字詞&#x200B;**PDFProject**&#x200B;會顯示為PDF標題，而非實際地圖示題。 (GUIDES-31102)

## Platform

- 使用`scope="external"`作為主題或地圖中DAM內容的參照會導致資產的相對路徑被GUID取代。 (GUIDES-35605)

## 已知問題

Adobe已找出下列5.1.0 Service Pack 3版的已知問題：

- 當您從任務詳細資訊頁面將稽核任務標籤為完成時，任務已完成並關閉；但是，其狀態在稽核儀表板上繼續顯示為&#x200B;**進行中**。 (GUIDES-39375)




