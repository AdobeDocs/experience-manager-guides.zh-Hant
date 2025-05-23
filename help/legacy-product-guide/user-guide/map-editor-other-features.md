---
title: 地圖編輯器中的其他功能
description: 探索基本和進階地圖編輯器中的部分常見功能。 瞭解如何在Map編輯器中解析索引鍵參考。
feature: Authoring, Map Editor
role: User
hide: true
exl-id: d6e00884-e17c-499e-9568-0807a75051ad
source-git-commit: ea597cd14469f21e197c700542b9be7c373aef14
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 0%

---

# 地圖編輯器中的其他功能 {#id1942D0T0HUI}

基本和進階地圖編輯器中的部分常見功能包括：

## 解析關鍵參考 {#id176GD01H05Z}

DITA內容索引鍵參照，或`conkeyref`是將部分內容從一個主題插入另一個主題的機制。 此機制使用索引鍵來找出要重複使用的內容，而非直接內容參考機制。 如需在DITA中直接和間接參考的詳細資訊，請參閱OASIS DITA語言規格中的&#x200B;*DITA定址*。

如果DITA主題有關聯的關鍵參照，則需要先解析這些參照，才能預覽、編輯或檢閱主題。

主要參考會根據根對映集來解析，其優先順序如下：

1. 使用者偏好設定
1. 地圖檢視面板
1. 資料夾設定檔

在「使用者偏好設定」中選取的根目錄對映解析關鍵參照的優先順序最高，其次是「對映檢視」面板和「資料夾設定檔根目錄對映」。 因此，如果在「使用者偏好設定」中未設定對映，則會使用在「對映檢視」面板中開啟的對映。 如果未在「對映檢視」面板中開啟對映，則會使用「資料夾設定檔」中的對映集來解析關鍵參照。

金鑰參照可以儲存在DITA map檔案或單獨的DITA檔案中。 在AEM Guides中，您可以在專案層級或作業階段層級指定關鍵參照。 如果已經為使用者作業階段定義了根對應，則會用來解析金鑰。 否則，會使用該資料夾的預設根對應。 如果未設定預設的根對應，則會向使用者反白缺少的關鍵參照。

透過定義要在下列位置使用的DITA map，有數種方法可解析DITA主題中的關鍵參照：

**專案屬性** — 您可以在[專案屬性]區段中建立專案時，定義根對映以解析索引鍵參考。

此根目錄對應將適用於與該專案關聯的所有資產\（資料夾和子資料夾\）。 對於在多個專案中參考的內容，會維護按字母順序排列的專案清單，並使用與第一個專案關聯的預設根對應。 您也可以從清單中選擇要用於解析關鍵參照的DITA map。

**主題預覽** — 在主題預覽模式中，按一下工具列中的「金鑰解析度」圖示，並選取要用於金鑰參照的DITA檔案。

**主題編輯檢視** — 編輯DITA主題時，按一下「關鍵解析度」圖示，並選取要用於解析關鍵參照的DITA檔案。

**父級主題：**&#x200B;[&#x200B;使用對應編輯器](map-editor.md)
