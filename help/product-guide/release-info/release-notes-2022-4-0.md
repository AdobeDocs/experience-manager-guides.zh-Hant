---
title: 發行說明 | Adobe Experience Manager Guides as a Cloud Service，2022年4月發行
description: 4月發行的Adobe Experience Manager Guides as a Cloud Service
exl-id: c735ba24-a803-454b-8723-57dacf90061b
feature: Release Notes
role: Leader
source-git-commit: 6e23f52fc9124d0f07f8108da1b5fe574f553469
workflow-type: tm+mt
source-wordcount: '809'
ht-degree: 0%

---

# 4月發行的Adobe Experience Manager Guides as a Cloud Service

## 升級至4月發行

請升級您目前的[!DNL Adobe Experience Manager Guides] as a Cloud Service (後來稱為&#x200B;*[!DNL AEM Guides]as a Cloud Service*)安裝程式，方法是執行下列步驟：
1. 請檢視雲端服務的Git程式碼，並切換至雲端服務管道中設定且與您要升級的環境對應的分支。
1. 將Cloud Services Git程式碼的`<dox.version>`檔案中的`/dox/dox.installer/pom.xml`屬性更新為2022.4.133。
1. 認可變更並執行雲端服務管道，以升級至[!DNL AEM Guides] as a Cloud Service的4月版本。

## 相容性矩陣

本節列出[!DNL AEM Guides] as a Cloud Service 2022年4月發行版本支援之軟體應用程式的相容性矩陣。

### FrameMaker和FrameMaker Publishing Server

| FMPS | FrameMaker |
| --- | --- |
| 不相容 | 2020 Update 4及更新版本 |
| | |


### 氧氣聯結器

| AEM Guides Cloud版本 | 氧氣聯結器視窗 | 氧氣聯結器Mac |
| --- | --- | --- |
| 2022.4.0 | 2.5.6 | 2.5.6 |
|  |  |  |

*從2020.2開始的FMPS版本支援AEM中建立的基準和條件。

## 新功能和增強功能

網頁編輯器中新增了許多增強功能和新功能：

### 改善金鑰解析度

DITA內容索引鍵參照會將部分內容從一個主題插入另一個主題。 它會使用索引鍵來尋找內容。 需要解析與DITA主題相關聯的關鍵參照。 選取的根對映解析關鍵參照的優先順序最高。

![使用者偏好設定對話方塊](assets/user-preferences.png)

現在，主要參考會根據根對映集來解析，其優先順序如下：

1. 使用者偏好設定
1. 地圖檢視面板
1. 資料夾設定檔

如需詳細資訊，請參閱使用手冊中的&#x200B;*解析金鑰參考*&#x200B;區段。

### 在左側面板中新增自訂面板

現在您可以在網頁編輯器的左側面板中新增自訂面板。 您可以將自訂面板用於各種用途，例如提供說明或針對專案進行測試。 如果已設定自訂面板，則它也會出現在&#x200B;**編輯器設定**&#x200B;內的面板清單中。 您可以切換開關，以顯示或隱藏自訂面板。

### 能夠變更DITA map中主題的檔案狀態

現在您可以輕鬆地變更DITA map中選取主題的檔案狀態。 您也可以從「對映檢視」面板底部的&#x200B;**更多選項**&#x200B;功能表，開啟並編輯DITA map中選取主題的屬性。

![選取的主題屬性](assets/map-view-properties.png)

### 預覽模式中顯示的版本資訊

網頁編輯器可協助您管理版本。 現在您也可以在主題的「預覽」模式中，在主題之檔案標籤的右上角，看到使用中主題或DITA map的版本。

![預覽版本](assets/preview-version.png)

## 已修正的問題

以下列出各種區域中修正的錯誤：

* 新標籤不會自動反映在新增/移除標籤下拉式清單中，而是需要基線重新整理。 (9249)
* 如果基準是由標籤條件所建立，則無法編輯基準標題。 (9171)
* 如果基準線狀態變更為「失敗」，使用基準線的發佈工作會卡在「等待中」狀態。 (9194)
* 移除直接參照上的標籤也會從間接參照中移除標籤。 (9257)
* 當您輸入時進行搜尋，會在「存放庫」檢視中造成不必要的搜尋請求。 (9307)
* 在索引標籤的標題中使用任何關鍵字時會發生問題。 (9318)
* 基線無法新增含有空格的標籤。 (9362)
* AEM網站輸出未正確顯示glosusage元素。 (8936)
* 在網頁編輯器中開啟&#x200B;**輸出**&#x200B;索引標籤時發生主控台錯誤。 (8715)
* 透過Salesforce發佈手動記錄型別時顯示的錯誤訊息並非直覺。 (8952)
* 使用條件屬性設定進行驗證不會立即開啟，而是使用者需要重新開啟檔案才能檢視驗證。 (9300)
* 使用中繼資料發佈DITA map後，就無法移除中繼資料。  (9178)
* 即使在Map編輯器中開啟DITA map，也可看到翻譯面板。 (9053)
* 使用者定義的自訂DTD不會優先於內嵌於DITA-OT中的標準DITA DTD。 (9104)
* 在原生PDF功能中，上傳範本中的非DITA和非影像檔案會失敗。 (9070)
* 在某些特殊情況下，授權機制會執行兩個查詢而不是一個查詢。 (9221)
* 使用自訂DTD發佈AEM網站輸出時失敗。 (9243)
* 參考使用註腳不會捲動至AEM網站輸出中的註腳區段。 (9234)

## 已知問題

Adobe已在[!DNL AEM Guides] as a Cloud Service 4月版本中找出下列已知問題。

* 當以相同名稱建立兩個或多個基準線，但兩者有空格或大小寫差異時，Web編輯器不會報告錯誤。 例如，「adobe」和「Adobe」或「Adobe」。
* 執行頻繁登入或登出，或在不同驗證型別之間切換時，氧氣聯結器會斷斷續續地掛起。
