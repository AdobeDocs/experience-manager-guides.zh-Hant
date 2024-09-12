---
title: 使用DITA map的REST API
description: 瞭解使用DITA map的REST API
exl-id: 6277e52d-1b05-4dd7-8d2b-4b94f329e2d7
feature: Rest API DITA Map
role: Developer
level: Experienced
source-git-commit: 1843cae11aac38053abc3c50fa2d00c050520470
workflow-type: tm+mt
source-wordcount: '611'
ht-degree: 4%

---

# 使用DITA map的REST API {#id175UB30E05Z}

下列REST API可讓您在AEM Guides中使用DITA map。

## 下載具有相依物件的DITA map

一種GET方法，可下載DITA map及其所有相依專案，例如參照的主題、子地圖、影像以及在地圖和主題中使用的DTD。

**要求URL**：
http://*&lt;aem-guides-server\>*： *&lt;連線埠號碼\>*/bin/fmdita/exportditamap

**引數**：

| 名稱 | 類型 | 必要 | 說明 |
|----|----|--------|-----------|
| `ditamap` | 字串 | 是 | AEM存放庫中DITA map檔案的絕對路徑。 |
| `baseline` | 字串 | 否 | 用來擷取已建立版本之內容的基準標題。<br> **注意：**&#x200B;值區分大小寫。 |

**回應值**：
一個.zip檔案，其內容會寫入回應的輸出資料流中。

## 啟動具有相依物件的DITA map匯出

一種POST方法，會啟動DITA map及其所有相依專案（例如參照的主題、子地圖、影像以及在地圖和主題中使用的DTD）的匯出。 稍後可以查詢狀態，並在完成後擷取下載URL。

**要求URL**：
http：*//&lt;aem-guides-server\>： &lt;port-number\>/bin/dxml/async-export*

**引數**：

| 名稱 | 類型 | 必要 | 說明 |
|----|----|--------|-----------|
| `ditamap` | 字串 | 是 | AEM存放庫中DITA map檔案的絕對路徑。 |
| `baseline` | 字串 | 否 | 用來擷取已建立版本之內容的基準標題。<br> **注意：**&#x200B;值區分大小寫。 |
| `flatFS` | 布林值 | 否 | \(Optional\)如果設為true，則會在ZIP檔案中傳回檔案的平面結構。 例如，如果您的DITA map參照多個資料夾中的內容，則所有參照的檔案都會提取到單一資料夾中。 如果存在同名檔案，則會新增數值尾碼以重新命名這些檔案。 所有參照\（在DITA map和主題中\）都會自動處理，因為它們會根據平面資料夾結構中檔案的新位置進行更新。 如果設為false，則會維持資料夾結構在ZIP檔案中的原樣。 如果DITA map參照來自多個位置的檔案，則所有這些位置也會在ZIP檔案中建立。 還原ZIP檔案時，會在目的地位置建立精確的資料夾結構。 <br>此引數的預設值為false。 |

**回應值**：

| 元素 | 說明 |
|-------|-----------|
| `status` | 已執行作業的傳回狀態。 可能的選項包括：「已啟動」、「失敗」、「進行中」、「成功」、「遺失」、「已刪除」 |
| `jobId` | 工作的唯一ID。 稍後可用於查詢狀態。 |
| errorMessage | 發生失敗時工作的錯誤訊息\（如果狀態為FAILED、MISSING或DELETED\）。 |
| `filePath` | ZIP的檔案路徑。 只有在工作完成且狀態為「成功」時，才會出現此選項。 這可用來下載ZIP檔案。 |

## 查詢匯出DITA map狀態

一種GET方法，可擷取DITA map及其所有相依物件的匯出狀態。 如果狀態為STARTED或INPROGRESS，可以間隔輪詢直到輪詢完成\（成功或有錯誤\）。

**要求URL**：
http：*//&lt;aem-guides-server\>： &lt;port-number\>/bin/dxml/async-export*

**引數**：

| 名稱 | 類型 | 必要 | 說明 |
|----|----|--------|-----------|
| `jobId` | 字串 | 是 | 匯出作業啟動時擷取的作業ID。 |

**回應值**：

| 元素 | 說明 |
|-------|-----------|
| `status` | 匯出工作的狀態。 可能的選項包括：「已啟動」、「失敗」、「進行中」、「成功」、「遺失」、「已刪除」 |
| `jobId` | 工作的唯一ID。 稍後可用於查詢狀態。 |
| `errorMessage` | 發生失敗時工作的錯誤訊息\（如果狀態為FAILED、MISSING或DELETED\）。 |
| `filePath` | ZIP的檔案路徑。 只有在工作完成且狀態為「成功」時，才會出現此選項。 這可用來下載ZIP檔案。 |
