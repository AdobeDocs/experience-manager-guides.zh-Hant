---
title: 發行說明 | Adobe Experience Manager Guides 4.4.0版的升級指示
description: 瞭解如何升級至Adobe Experience Manager Guides 4.4.0版
role: Leader
exl-id: 884178b6-7a72-471a-a6e3-238a543fb227
source-git-commit: 47c06dcc30b34780cbd26ded1ca400a5056a59ba
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 5%

---

# 4.4.0版（2024年1月）的升級指示

本文介紹Adobe Experience Manager Guides 4.4.0版的升級指示和相容性矩陣。

如需新功能和增強功能的詳細資訊，請參閱 [4.4.0 版本中的新增功能](../release-info/whats-new-4-4.md)。

如需此版本中已修正的問題清單，請檢視[4.4.0版本](../release-info/fixed-issues-4-4.md)中已修正的問題。




## 相容性矩陣

本節列出Experience Manager Guides 4.4.0版本支援之軟體應用程式的相容性矩陣。

### Adobe Experience Manager

**4.4.0非UUID**
版本6.5 Service Pack 20、19、18或17

**4.4.0 UUID**
版本6.5 Service Pack 20、19、18或17


如需詳細資訊，請檢視On-Premise Installation and Configuration Guide中的[技術需求](../install-guide/download-install-technical-requirements.md)區段。

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
| 適用於Cloud Service的Experience Manager Guides元件內容套件 | dxml-components.all-1.2.2 | aem-site-template-dxml.all-1.0.15 |



## 升級至Experience Manager Guides 4.4.0版


您可以輕鬆地將最新版本的Guides升級至4.4.0版。在繼續升級至Experience Manager Guides 4.4.0版之前，您必須先考量下列幾點：


- 如果您是使用4.3.1、4.3.0或4.2.1版(Hotfix 4.2.1.3)，則可以直接升級至4.4.0版。
- 如果您是使用4.2、4.1或4.1.x版，則必須先升級至4.3.1、4.3.0或4.2.1版(Hotfix 4.2.1.3)，才能升級至4.4.0版。
- 如果您使用的是4.0版，則必須先升級至4.2版，才能升級至4.3.x版。
- 如果您使用的是3.8.5版，則必須先升級至4.0版，才能升級至4.2版。
- 如果您使用3.8.5之前的版本，請參閱[Experience Manager Guides說明PDF封存](https://helpx.adobe.com/xml-documentation-for-experience-manager/archive.html)上產品特定安裝指南中的「升級Adobe Experience Manager Guides」一節。



>[!NOTE]
>
>升級Experience Manager Guides版本前，您必須先安裝AEM Service Pack。

如需詳細資訊，請檢視Experience Manager Guides內部部署版本](../install-guide/upgrade-xml-documentation.md)的[升級指示。
