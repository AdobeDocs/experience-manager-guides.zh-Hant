---
title: 重設轉換工作流程的API
description: 了解轉換工作流程的REST API
exl-id: f091782e-ab54-4db4-9018-9bcbff9da7b2
feature: Rest API Conversion Workflow
role: Developer
level: Experienced
source-git-commit: 45ae1471fe0f0586764ede9dd96530b7f75f69ee
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 9%

---

# 重設轉換工作流程的API {#id175UB30E05Z}

下列REST API可讓您將Word、HTML和InDesign檔案轉換為DITA格式。

## 轉換Word檔案

將Word檔案轉換為DITA格式的GET方法。

**要求URL**：
http://*&lt;aem-guides-server\>*： *&lt;連線埠號碼\>*/bin/fmdita/conversion

| 名稱 | 類型 | 必要 | 說明 |
|----|----|--------|-----------|
| ``operation`` | 字串 | 是 | 要呼叫的作業名稱。 此引數的值為``word2dita``。<br> **注意：**&#x200B;值不區分大小寫。 |
| `inputFile` | 字串 | 是 | AEM存放庫中來源Word檔案的絕對路徑。 |
| `destPath` | 字串 | 是 | 儲存轉換之DITA檔案的目的地位置的絕對路徑。 |
| `createRev` | 布林值 | 是 | 指定是否在指定的目的地建立\(`true`\)檔案的修訂版本\(`false`\)。 僅當目的地位置包含轉換檔案的現有版本時，才會考慮這種情況。 |
| `style2tagMap` | 字串 | 是 | 用於轉換的樣式對應檔案的絕對路徑。 |

**回應值**：
傳回HTTP 200 \(Successful\)回應。

## 轉換HTML檔案

將HTML檔案轉換為DITA格式的GET方法。

**要求URL**：

http://*&lt;aem-guides-server\>*： *&lt;連線埠號碼\>*/bin/fmdita/conversion

**引數**：

| 名稱 | 類型 | 必要 | 說明 |
|----|----|--------|-----------|
| `operation` | 字串 | 是 | 要呼叫的作業名稱。 此引數的值為``html2dita``。<br> **注意：**&#x200B;值不區分大小寫。 |
| `inputFile` | 字串 | 是 | AEM存放庫中來源HTML檔案的絕對路徑。 |
| `destPath` | 字串 | 是 | 儲存轉換之DITA檔案的目的地位置的絕對路徑。 |
| `createRev` | 布林值 | 是 | 指定是否在指定的目的地建立\(`true`\)檔案的修訂版本\(`false`\)。 僅當目的地位置包含轉換檔案的現有版本時，才會考慮這種情況。 |

**回應值**：

傳回HTTP 200 \(Successful\)回應。

## 轉換InDesign檔案

將InDesign檔案轉換為DITA格式的GET方法。

**要求URL**：
http://*&lt;aem-guides-server\>*： *&lt;連線埠號碼\>*/bin/fmdita/conversion

**引數**：

| 名稱 | 類型 | 必要 | 說明 |
|----|----|--------|-----------|
| ``operation`` | 字串 | 是 | 要呼叫的作業名稱。 此引數的值為``idml2dita``。<br> **注意：**&#x200B;值不區分大小寫。 |
| `inputFile` | 字串 | 是 | AEM存放庫中來源InDesign檔案的絕對路徑。 |
| `destPath` | 字串 | 是 | 儲存轉換之DITA檔案的目的地位置的絕對路徑。 |
| `createRev` | 布林值 | 是 | 指定是否在指定的目的地建立\(`true`\)檔案的修訂版本\(`false`\)。 僅當目的地位置包含轉換檔案的現有版本時，才會考慮這種情況。 |

**回應值**：
傳回HTTP 200 \(Successful\)回應。
