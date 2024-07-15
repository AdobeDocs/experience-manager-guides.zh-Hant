---
title: 將自訂樣式新增至「參考線」編輯器
description: 瞭解如何新增自訂樣式以變更「參考線」編輯器的外觀。
exl-id: 03143fb2-d05d-4103-b172-8b91880b7f9e
feature: Web Editor
role: User, Admin
source-git-commit: be06612d832785a91a3b2a89b84e0c2438ba30f2
workflow-type: tm+mt
source-wordcount: '261'
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

[使用此連結來進一步瞭解資料夾設定檔和設定CSS範本配置](https://experienceleague.adobe.com/docs/experience-manager-guides-learn/videos/advanced-user-guide/editor-configuration.html?lang=en#customize-the-css-template-layout)

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


## 參考

您也可能對有關Webeditor組態與Webeditor [Expert講座](https://experienceleague.adobe.com/docs/experience-manager-guides-learn/tutorials/knowledge-base/expert-session/webbased-authoring-jan2023.html?lang=en)中的自訂的專家講座感興趣
