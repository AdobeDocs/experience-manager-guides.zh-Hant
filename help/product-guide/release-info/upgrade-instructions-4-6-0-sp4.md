---
title: 發行說明 | Adobe Experience Manager Guides 4.6.0 Service Pack 4版本的升級指示
description: 瞭解如何升級至Adobe Experience Manager Guides的4.6.0 Service Pack 4版本
role: Leader
exl-id: d0914e8a-7c7f-47da-9655-697f95f7d4ff
source-git-commit: 6e23f52fc9124d0f07f8108da1b5fe574f553469
workflow-type: tm+mt
source-wordcount: '531'
ht-degree: 1%

---

# 4.6.0 Service Pack 4版本（2025年4月）的升級指示

本文介紹Adobe Experience Manager Guides 4.6.0 Service Pack 4版的升級指示和相容性矩陣。

如需此版本中已修正的問題清單，請檢視4.6.0 Service Pack 4版本[中的](fixed-issues-4-6-0-sp4.md)已修正問題。

## 相容性矩陣

本節列出Experience Manager Guides 4.6.0 Service Pack 4版本支援之軟體應用程式的相容性矩陣。

### Adobe Experience Manager

**4.6.0 Service Pack 4非UUID**
6.5版Service Pack 21、20和19

**4.6.0 Service Pack 4 UUID**
6.5版Service Pack 21、20和19

如需詳細資訊，請檢視On-Premise Installation and Configuration Guide中的[技術需求](../install-guide/download-install-technical-requirements.md)區段。

### FrameMaker和FrameMaker Publishing Server

| 發行版本 | FMPS 2022 | FMPS 2020 | FM 2022 | FM 2020 |
| --- | --- | --- | --- | --- |
| 4.6.0 Service Pack 4 （非UUID） | 2022或更高 | 2020.2或更新版本* | 2022或更高 | 2020.3或更高版本 |
| 4.6.0 Service Pack 4 (UUID) | 2022或更高 | 2020.2或更新版本* | 2022或更高 | 2020.4或更新版本 |
| | | | | |

*從2020.2開始的FMPS版本支援AEM中建立的基準和條件。

### 氧氣聯結器

| 發行版本 | 氧氣聯結器視窗 | 氧氣聯結器Mac | 在氧氣視窗中編輯 | 在氧氣Mac中編輯 |
| --- | --- | --- |--- |--- |
| 4.6.0 Service Pack 4 （非UUID） | 2.8-regular-10 | 2.8-regular-10 | 1.6 | 1.6 |
| 4.6.0 Service Pack 4 (UUID) | 3.6-uuid.9 | 3.6-uuid.9 | 2.3 | 2.3 |
|  |  |   |  |  |

### 知識庫範本版本

| 元件封裝名稱 | 元件版本 | 範本版本 |
|---|---|---|
| 適用於Cloud Service的Experience Manager Guides元件內容套件 | dxml-components.all-1.2.2 | aem-site-template-dxml.all-1.0.15 |

### 新增AEM網站範本版本

| 元件版本 | 網站版本 |
|---|---|
| guides-components.all-1.0.0 | aemg-docs.all-1.0.0 |

## 升級至Experience Manager Guides的4.6.0 Service Pack 4版本

您可以輕鬆地將最新版本的Guides升級至4.6.0 Service Pack 4。 在繼續升級之前，您必須考慮以下幾點：

- 如果您是使用4.6.0、4.6.0 Service Pack 1或4.6.0 Service Pack 3版，則可以直接升級至4.6.0 Service Pack 4。
- 如果您是使用4.4、4.3.1或4.3.0版，則需升級至4.6.0版。
- 如果您是使用4.2、4.2.1 (Hotfix 4.2.1.3)、4.1或4.1.x版，則必須先升級至4.4版，才能升級至4.6.0版。
- 如果您使用的是4.0版，則必須先升級至4.2版，才能升級至4.3.x版。
- 如果您使用的是3.8.5版，則必須先升級至4.0版，才能升級至4.2版。
- 如果您使用的版本早於3.8.5，請參閱[Adobe Experience Manager Guides說明Experience Manager Guides封存](https://helpx.adobe.com/xml-documentation-for-experience-manager/archive.html)中提供的產品特定安裝指南中的「升級PDF」一節。

>[!NOTE]
>
>您必須先安裝AEM Service Pack，才能升級Experience Manager Guides版本。

4.6.0 Service Pack 4版本的升級程式遵循與4.6.0版本相同的步驟。 如需詳細指示，請檢視Experience Manager Guides內部部署版本[的](../install-guide/upgrade-xml-documentation.md)升級指示。
