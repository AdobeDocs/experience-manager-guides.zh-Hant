---
title: 發行說明 | Adobe Experience Manager Guides as a Cloud Service，2023年3月發行
description: 3月發行的Adobe Experience Manager Guides as a Cloud Service
exl-id: 6a0bba92-7d7d-4b20-ad46-0eacc91268da
feature: Release Notes
role: Leader
source-git-commit: 6e23f52fc9124d0f07f8108da1b5fe574f553469
workflow-type: tm+mt
source-wordcount: '560'
ht-degree: 0%

---

# 2023年3月發行的Adobe Experience Manager Guides as a Cloud Service

此發行說明涵蓋升級指示、相容性矩陣，以及2023年3月Adobe Experience Manager Guides版本(後來稱為&#x200B;*AEM Guides as a Cloud Service*)中修正的問題。

如需新功能和增強功能的詳細資訊，請參閱[AEM Guides as a Cloud Service 2023年3月版本的新增功能](whats-new-2023-3-0.md)。

## 升級至2023年3月版本

請升級您目前的AEM Guides as a Cloud Service設定，方法是執行下列步驟：

1. 請檢視雲端服務的Git程式碼，並切換至雲端服務管道中設定且與您要升級的環境對應的分支。
1. 將雲端服務Git程式碼的`<dox.version>`檔案中的`/dox/dox.installer/pom.xml`屬性更新為2023.3.242。
1. 提交變更並執行雲端服務管道，以升級至2023年3月版本的AEM Guides as a Cloud Service。

## 索引現有內容的步驟(僅限使用9月之前的AEM Guides as a Cloud Service版本時)

執行以下步驟，為現有內容編制索引，並在地圖層級使用新的尋找和取代文字：

* 對伺服器執行POST要求（使用正確的驗證） - `http://<server:port>/bin/guides/map-find/indexing`。
(選用：您可以傳遞地圖的特定路徑來編列索引，預設情況下，所有地圖都會編列索引 || 範例： `https://<Server:port>/bin/guides/map-find/indexing?paths=<map_path_in_repository>`)

* 此API將傳回jobId。 若要檢查工作的狀態，您可以將具有工作識別碼的GET要求傳送至相同的端點 — `http://<server:port>/bin/guides/map-find/indexing?jobId={jobId}`
(例如： http://&lt;_localhost:8080_>/bin/guides/map-find/indexing？jobId=2022/9/15/7/27/7dfa1271-981e-4617-b5a4-c18379f11c42_678)

* 工作完成後，上述GET要求將回應為成功，並提及是否有任何地圖失敗。 可以從伺服器記錄檔確認已成功編制索引的對應。

## 相容性矩陣

本節列出AEM Guides as a Cloud Service 2023年3月版本支援之軟體應用程式的相容性矩陣。

### FrameMaker和FrameMaker Publishing Server

| AEM Guides雲端版 | FMPS | FrameMaker |
| --- | --- | --- |
| 2023.03.0 | 不相容 | 2022或更高 |
| | | |


### 氧氣聯結器

| AEM Guides雲端版 | 氧氣聯結器視窗 | 氧氣聯結器Mac | 在氧氣視窗中編輯 | 在氧氣Mac中編輯 |
| --- | --- | --- | --- | --- |
| 2023.03.0 | 2.9-uuid-2 | 2.9-uuid-2 | 2.3 | 2.3 |
|  |  |  |  |  |

## 已修正的問題

以下列出各種區域中修正的錯誤：

* 下載PDF程式在網頁編輯器中無法正常運作。 (11496)
* JSON輸出 | 屬性值為`"value in spaces and double quotes"`的對應中繼資料會導致發佈錯誤。 (11438)
* 在&#x200B;**插入多媒體**&#x200B;圖示下，無法以YouTube格式插入音訊和視訊多媒體檔案。 (11320)
* 使用具有專門化標題元素的範本建立對應時，會發生驗證錯誤。 (11212)
* 原生PDF | 表格標頭中的註腳會在PDF輸出的對應頁尾中導向粗體和置中對齊文字。 (10610)
>[!NOTE]
>
>若要反映原生PDF變更，請刪除位於/content/dam/dita-templates的PDF資料夾，然後升級至最新組建版本。 (10610)

### 因應措施的已知問題

Adobe已識別AEM Guides as a Cloud Service 2023年3月版本的下列已知問題。

* 使用者無法儲存或建立重複資產的版本。

**因應措施**：對重複資產進行任何變更前，請先從Assets UI重新處理該資產。
