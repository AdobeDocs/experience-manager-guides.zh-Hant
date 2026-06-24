---
title: 發行說明 | 2026.06.0版Adobe Experience Manager Guides中的升級指示和修正問題
description: 瞭解相容性矩陣，以及如何升級至2026.06.0版的Adobe Experience Manager Guides as a Cloud Service。
source-git-commit: 343fdd0afbab62a2764fcee0a1f8e0f3c08a0033
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 1%

---

# 2026.06.0版的升級指示

本文介紹2026.06.0版Adobe Experience Manager Guides as a Cloud Service的升級指示和相容性矩陣。

如需新功能和增強功能的詳細資訊，請檢視[2026.06.0版的新增功能](whats-new-2026-06-0.md)。

如需此版本中修正的問題清單，請檢視[2026.06.0版本](fixed-issues-2026-06-0.md)中的已修正問題。

## 相容性矩陣

本節說明2026.06.0版Experience Manager Guides as a Cloud Service所支援軟體應用程式的相容性矩陣。

### FrameMaker和FrameMaker Publishing Server

| Experience Manager Guides雲端版 | FMPS | FrameMaker | 氧氣作者 |
| --- | --- | --- | --- |
| 2026.06.0 | 不相容 | 2022或更高 | 26.1 |


### 氧氣聯結器

| Experience Manager Guides雲端版 | 氧氣聯結器視窗 | 氧氣聯結器Mac | 在氧氣視窗中編輯 | 在氧氣Mac中編輯 |
| --- | --- | --- | --- | --- |
| 2026.06.0 | 3.8 -uuid 1 | 3.8 -uuid 1 | 2.3 | 2.3 |


### AEM網站範本版本

| 元件版本 | 網站版本 |
|---|---|
| guides-components.all-1.5.1 | aemg-sites-template-1.3.0 |

### 知識庫範本版本

| 元件封裝名稱 | 元件版本 | 範本版本 |
|---|---|---|
| 適用於Cloud Service的Experience Manager Guides元件內容套件 | guides-components.all-1.4.0 | aem-site-template-dxml-1.0.17 |

## 升級至2026.06.0版

Experience Manager Guides在升級至最新版Experience Manager as a Cloud Service時自動升級。

>[!IMPORTANT]
>
> 此版本包含資料夾設定檔設定(ui_config.json)的更新。 如果您使用自訂設定，升級之前請務必備份這些設定。 更新後，請檢閱並調整您的設定，以符合最新版本中推出的變更。

檢閱及驗證您的設定設定，以確認其已正確實作。 如果您已引進任何自訂組態變更，請檢視[升級Cloud Service的其他組態](../install-conf-guide/additional-config-for-upgrade.md)，以瞭解適用於您升級之版本的任何其他程式。
