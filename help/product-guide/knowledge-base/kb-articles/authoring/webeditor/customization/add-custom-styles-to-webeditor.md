---
title: 將自訂樣式新增至「參考線」編輯器
description: 瞭解如何新增自訂樣式以變更「參考線」編輯器的外觀。
exl-id: 03143fb2-d05d-4103-b172-8b91880b7f9e
feature: Web Editor
role: User, Admin
TQID: https://experienceleague.adobe.com/uQc8TTz7dHxbN6-zbin-esQevLoJR-IMR1hchrwEs8M
product_v2: id: fae5e35a-80c9-4b94-9352-1a060a6aab1did: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: ab01a588-7dea-43f2-a699-0b3f128465d6id: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
subfeature_v2: id: ad602516-aca3-4247-9ae8-f393d958efa9id: b1ef4d86-3917-4b76-a0bc-4a4771f9b3b0id: f89f75b0-cf2e-4e96-aec8-fe8c39cbd0ef
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 300
ht-degree: 0%

---

# 將自訂樣式新增至「參考線」編輯器

在本文中，我們將瞭解如何新增自訂樣式以變更webitor預設外觀。

這將涉及以下步驟：
- 透過資料夾設定檔XML編輯器設定新增自訂樣式
- 在Webeditor中選擇個別資料夾設定檔並測試變更


## 以範例來實施

以一個範例讓我們瞭解這一點，我們想要將簡短說明和標題以個別區塊的形式顯示在編輯器中，包含一些樣式方面。

![使用自訂樣式預覽Webeditor](../../../assets/authoring/webeditor-customstyles-preview.png)


## 實作此


### 將自訂CSS新增至資料夾設定檔

使用資料夾設定檔來檢查「XML編輯器設定」索引標籤下的&#x200B;*css_layout.css*，並新增具有自訂樣式的CSS

[使用此連結來進一步瞭解資料夾設定檔和設定CSS範本版面](https://experienceleague.adobe.com/docs/experience-manager-guides-learn/videos/advanced-user-guide/editor-configuration.html?lang=en#customize-the-css-template-layout)

使用下列專案在編輯器中設定上述樣式：
- 使用[css_layout.css](../../../assets/authoring/webeditor-customstyles-css_layout.css)並將其上傳至您選擇的資料夾設定檔
- 使用AEM封裝管理員安裝附加的封裝[webeditor-styles-resources.zip](../../../assets/authoring/webeditor-styles-resources.zip)，以安裝上述CSS檔案中使用的資源

```
This will install the resources at path "/content/dam/resources" which will include sub-folders "fonts" and "images"
```


### 測試

- 開啟Web編輯器
- 從使用者偏好設定中選擇您新增自訂樣式的資料夾設定檔。 如果您將其新增至全域設定檔，表示您可能已經在使用它。
- 開啟主題，您會注意到編輯區域應具有自訂UI

```
Please note this is compatible to AEM Guides version 4.2 and AEM Guides cloud version 2303 (March)
```


## 參照

您也可能對有關Webeditor組態與Webeditor [Expert講座](https://experienceleague.adobe.com/docs/experience-manager-guides-learn/tutorials/knowledge-base/expert-session/webbased-authoring-jan2023.html?lang=en)中的自訂的專家講座感興趣
