---
title: 發行說明 | Adobe Experience Manager Guides 4.4.0版的升級指示
description: 瞭解如何升級至Adobe Experience Manager Guides 4.4.0版
role: Leader
exl-id: 884178b6-7a72-471a-a6e3-238a543fb227
TQID: https://experienceleague.adobe.com/bich0n61TfwxRPQLCrM-HVSZ8cfjyv6s3SjUf2vIjnQ
product_v2: id: fae5e35a-80c9-4b94-9352-1a060a6aab1did: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: a3bd6397-2eb2-4908-a61c-226e26855dcaid: afb45297-4313-4f67-818e-bc0b03abe086id: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
subfeature_v2: id: cda0baeb-996e-4aaa-92d1-41032e34fd68id: d5ea0417-7932-4688-a3e2-4d3b2e7076a3
role_v2: id: f8a45b24-4be7-4f1b-909b-60d06b483a20
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 454
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

| 發行版本 | FMPS 2022 | FMPS 2020 | Fm 2022 | Fm 2020 |
| --- | --- | --- | --- | --- |
| 4.4.0 （非UUID） | 2022或更高 | 2020.2或更新版本* | 2022或更高 | 2020.3或更高版本 |
| 4.4.0 (UUID) | 2022或更高 | 2020.2或更新版本* | 2022或更高 | 2020.4或更新版本 |
| | | | | |

*從2020.2開始的FMPS版本支援AEM中建立的基準和條件。

### 氧氣聯結器

| 發行版本 | 氧氣聯結器視窗 | 氧氣聯結器Mac | 在氧氣視窗中編輯 | 在氧氣Mac中編輯 |
| --- | --- | --- |--- |--- |
| 4.4.0 （非UUID） | 2.7-regular-1 | 2.7-regular-1 | 1.6 | 1.6 |
| 4.4.0 (UUID) | 3.4-uuid-1 | 3.4-uuid-1 | 2.3 | 2.3 |
|  |  |   | |  |



### 知識庫範本版本

| 元件封裝名稱 | 元件版本 | 範本版本 |
|---|---|---|
| 適用於Cloud Service的Experience Manager Guides元件內容套件 | dxml-components.all-1.2.2 | aem-site-template-dxml.all-1.0.15 |



## 升級至Experience Manager Guides 4.4.0版


您可以輕鬆地將最新版本的Guides升級至4.4.0版。 在繼續升級至Experience Manager Guides 4.4.0版之前，您必須先考量下列幾點：


- 如果您是使用4.3.1、4.3.0或4.2.1版(Hotfix 4.2.1.3)，則可以直接升級至4.4.0版。
- 如果您是使用4.2、4.1或4.1.x版，則必須先升級至4.3.1、4.3.0或4.2.1版(Hotfix 4.2.1.3)，才能升級至4.4.0版。
- 如果您使用的是4.0版，則必須先升級至4.2版，才能升級至4.3.x版。
- 如果您使用的是3.8.5版，則必須先升級至4.0版，才能升級至4.2版。
- 如果您使用的版本早於3.8.5，請參閱[Adobe Experience Manager Guides說明Experience Manager Guides封存](https://helpx.adobe.com/xml-documentation-for-experience-manager/archive.html)中提供的產品特定安裝指南中的「升級PDF」一節。



>[!NOTE]
>
>您必須先安裝AEM Service Pack，才能升級Experience Manager Guides版本。

如需詳細資訊，請檢視Experience Manager Guides內部部署版本](../install-guide/upgrade-xml-documentation.md)的[升級指示。
