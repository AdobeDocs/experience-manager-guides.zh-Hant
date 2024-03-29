---
title: 發行說明 | Adobe Experience Manager Guides 4.4.0版的升級指示
description: 瞭解如何升級至Adobe Experience Manager Guides 4.4.0版
role: Leader
source-git-commit: 2209fd311ca1ad524db35633b8be22f6d303346d
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 1%

---

# 4.4.0版（2024年1月）的升級指示

本文介紹Adobe Experience Manager Guides 4.4.0版的升級指示和相容性矩陣。

如需新功能和增強功能的詳細資訊，請檢視 [4.4.0版的新增功能](../release-info/whats-new-4-4.md).

如需此版本已修正的問題清單，請檢視 [已修正4.4.0版本中的問題](../release-info/fixed-issues-4-4.md).




## 相容性矩陣

本節列出Experience Manager Guides 4.4.0版本支援之軟體應用程式的相容性矩陣。

### Adobe Experience Manager

**4.4.0非UUID**
6.5版Service Pack 19、18、17

**4.4.0 UUID**
6.5版Service Pack 19、18、17


如需詳細資訊，請檢視 [技術需求](../install-guide/download-install-technical-requirements.md) On-Premise安裝與設定指南中的區段。

### FrameMaker和FrameMaker Publishing Server

| 發行 | FMPS 2022 | FMPS 2020 | Fm 2022 | Fm 2020 |
| --- | --- | --- | --- | --- |
| 4.4.0 （非UUID） | 2022或更高 | 2020.2或更新版本* | 2022或更高 | 2020.3或更高版本 |
| 4.4.0 (UUID) | 2022或更高 | 2020.2或更新版本* | 2022或更高 | 2020.4或更新版本 |
| | | | |

*從2020.2開始的FMPS版本支援AEM中建立的基準和條件。

### 氧氣聯結器

| 發行 | 氧氣聯結器視窗 | 氧氣聯結器Mac | 在氧氣視窗中編輯 | 在氧氣Mac中編輯 |
| --- | --- | --- |--- |--- |
| 4.4.0 （非UUID） | 2.7-regular-1 | 2.7-regular-1 | 1.6 | 1.6 |
| 4.4.0 (UUID) | 3.4-uuid-1 | 3.4-uuid-1 | 2.3 | 2.3 |
|  |  |   |



### 知識庫範本版本

| 元件封裝名稱 | 元件版本 | 範本版本 |
|---|---|---|
| 適用於Cloud Service的Experience Manager指南元件內容套件 | dxml-components.all-1.2.2 | aem-site-template-dxml.all-1.0.15 |



## 升級至Experience Manager指南4.4.0版


您可以輕鬆地將最新版本的Guides升級至4.4.0版。在繼續升級至4.4.0版的Experience Manager指南之前，您必須考慮以下幾點：


- 如果您是使用4.3.1、4.3.0或4.2.1版(Hotfix 4.2.1.3)，則可以直接升級至4.4.0版。
- 如果您是使用4.2、4.1或4.1.x版，則必須先升級至4.3.1、4.3.0或4.2.1版(Hotfix 4.2.1.3)，才能升級至4.4.0版。
- 如果您使用的是4.0版，則必須先升級至4.2版，才能升級至4.3.x版。
- 如果您使用的是3.8.5版，則必須先升級至4.0版，才能升級至4.2版。
- 如果您使用的是3.8.5之前的版本，請參閱上的產品特定安裝指南中的「升級Experience Manager指南」一節。 [Adobe Experience Manager Guides說明PDF封存](https://helpx.adobe.com/xml-documentation-for-experience-manager/archive.html).



>[!NOTE]
>
>您必須先安裝AEM Service Pack，才能升級Experience Manager指南版本。

如需詳細資訊，請檢視 [內部部署版本的升級指示](../install-guide/upgrade-xml-documentation.md) Experience Manager指南。

