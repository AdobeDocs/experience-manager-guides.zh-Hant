---
title: 發行說明 |已修正Adobe Experience Manager Guides 5.1.0 Service Pack 3版本中的問題
description: 瞭解Adobe Experience Manager Guides 5.1.0 Service Pack 3版的錯誤修正
role: Leader
exl-id: faa9a5d7-616f-4692-98d1-23abc78556b6
TQID: https://experienceleague.adobe.com/qiVY-B-D3FcHq2PH7Go2AAFpnstCrPJ2MVLEalQCVn0
product_v2:
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: a3bd6397-2eb2-4908-a61c-226e26855dca
  - id: ab01a588-7dea-43f2-a699-0b3f128465d6
role_v2:
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 297
ht-degree: 1%

---

# 已修正5.1.0 Service Pack 3版本（2025年12月）中的問題


本文章說明5.1.0 Service Pack 3版本Adobe Experience Manager Guides中不同區域所修正的錯誤。

瞭解5.1.0 Service Pack 3版本[&#128279;](upgrade-instructions-5-1-0-sp3.md)的升級指示。


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
