---
title: 發行說明 | Adobe Experience Manager Guides as a Cloud Service，2022年10月發行版本
description: 10月發行的Adobe Experience Manager Guides as a Cloud Service
exl-id: 38638080-625c-49c3-9e54-56cc23831546
feature: Release Notes
role: Leader
source-git-commit: 6e23f52fc9124d0f07f8108da1b5fe574f553469
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 1%

---

# 10月發行的Adobe Experience Manager Guides as a Cloud Service

## 升級至10月版

請升級您目前的Adobe Experience Manager Guides as a Cloud Service (稍後稱為&#x200B;*AEM Guides as a Cloud Service*)安裝程式，方法是執行下列步驟：
1. 請檢視雲端服務的Git程式碼，並切換至雲端服務管道中設定且與您要升級的環境對應的分支。
1. 將Cloud Services Git程式碼的`<dox.version>`檔案中的`/dox/dox.installer/pom.xml`屬性更新為2022.10.183。
1. 確認變更並執行雲端服務管道，以升級至10月版的AEM Guides as a Cloud Service。

## 相容性矩陣

本節列出AEM Guides as a Cloud Service 2022年10月發行版本支援之軟體應用程式的相容性矩陣。

### FrameMaker和FrameMaker Publishing Server

| FMPS | FrameMaker |
| --- | --- |
| 不相容 | 2020 Update 4及更新版本 |
| | |

*從2020.2開始的FMPS版本支援AEM中建立的基準和條件。

### 氧氣聯結器

| AEM Guides雲端版 | 氧氣聯結器視窗 | 氧氣聯結器Mac | 在氧氣視窗中編輯 | 在氧氣Mac中編輯 |
| --- | --- | --- | --- | --- |
| 2022.10.0 | 2.7.13 | 2.7.13 | 2.3 | 2.3 |
|  |  |  |  |  |


## 新功能和增強功能

AEM Guides as a Cloud Service在10月版本中提供增強功能和新功能：


### 快速產生面板

現在AEM Guides提供&#x200B;**快速產生**&#x200B;面板，可幫助您快速產生並檢視為您的DITA map建立的預設集輸出。

![快速產生圖示](assets/quick-generate-icon.png)

在&#x200B;**快速產生**&#x200B;面板中，您可以看到為您的DITA map建立的所有輸出預設集清單。

![快速產生面板](assets/quick-generate-panel.png)

選取一或多個預設集並快速產生輸出。 您也可以快速檢視針對預設集產生的輸出。 成功訊息會顯示在產生的輸出上。 如果輸出產生失敗，會顯示錯誤訊息。 您也可以檢視錯誤記錄，以檢視產生程式中所發生錯誤的詳細資料。


## 已修正的問題

以下列出各種區域中修正的錯誤：

* 原生PDF | 從PDF輸出移除僅限資源的主題時發生錯誤。 (10554)
* 原生PDF | PDF輸出中出現空白的Keyref。 (10553)
* 原生PDF | 未接受`navtitle`的`topichead`。 (10509)
* 原生PDF | amd64 JDK風格所需的支援。 (10465)
* 原生PDF | 無法從目錄隱藏重要主題。 (10355)
* 原生PDF | 重新啟動章節配置中的頁碼會從上一個章節的結尾開始隨機編號。 (10154)
* Chrome瀏覽器 | 從UI拖放任何元素時，畫面會變成空白。 例如，從「條件」面板拖曳條件時。 (10524)
* 資產執行複製貼上操作後，節點屬性會被移除。 (10053)
* 按一下&#x200B;**關閉**&#x200B;時，系統會將使用者重新導向至資產 — 已更正體驗，將使用者帶至AEM首頁。 (9654)
