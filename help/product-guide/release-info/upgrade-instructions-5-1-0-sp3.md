---
title: 發行說明 | Adobe Experience Manager Guides 5.1.0 Service Pack 3版本的升級指示
description: 瞭解相容性矩陣，以及如何升級至Adobe Experience Manager Guides的5.1.0 Service Pack 3版本。
source-git-commit: 172599c2bd99f1779b04255aac5e7d505614b463
workflow-type: tm+mt
source-wordcount: '521'
ht-degree: 1%

---

# 5.1.0 Service Pack 3版本（2025年12月）的升級指示

本文介紹Adobe Experience Manager Guides 5.1.0 Service Pack 3版的升級指示和相容性矩陣。

如需此版本中已修正的問題清單，請檢視5.1.0 Service Pack 3版本[中的](../release-info/fixed-issues-5-1-0-sp3.md)已修正問題。

## 相容性矩陣

本節列出Experience Manager Guides 5.1.0版支援之軟體應用程式的相容性矩陣。

### Adobe Experience Manager

**5.1.0 Service Pack 3 UUID**

6.5版Service Pack 23、Service Pack 22和Service Pack 21

如需詳細資訊，請檢視On-Premise Installation and Configuration Guide中的[技術需求](../install-guide/download-install-technical-requirements.md)區段。

### FrameMaker和FrameMaker Publishing Server

| 發行版本 | FMPS | FM |
| --- | --- | --- |
| 5.1.0 Service Pack 3 (UUID) | 支援 | 2022或更高 |

### 氧氣聯結器

| 發行版本 | 氧氣聯結器視窗 | 氧氣聯結器Mac | 在氧氣視窗中編輯 | 在氧氣Mac中編輯 |
| --- | --- | --- |--- |--- |
| 5.1.0 Service Pack 3 (UUID) | 3.8-uuid.1 | 3.8-uuid.1 | 2.3 | 2.3 |

### 知識庫範本版本

| 元件封裝名稱 | 元件版本 | 範本版本 |
|---|---|---|
| 適用於Cloud Service的Experience Manager Guides元件內容套件 | dxml-components.all-1.3.0 | aem-site-template-dxml.all-1.0.4 |

### 新增AEM網站範本版本


| 元件版本 | 網站版本 |
|---|---|
| guides-components.all-1.4.0 | aemg-docs.all-1.2.0 |

## 先決條件

根據標準DITA行為，scope=`external`屬性不可套用至內部連結，因為它僅適用於外部資源的參考。 將此屬性套用至內部連結可能會中斷工作流程。 對於Experience Manager Guides中管理的內容，請改用預設範圍=`local`或索引鍵型參考。

## 升級至Experience Manager Guides的5.1.0 Service Pack 3版本

您可以輕鬆地將目前版本的Guides升級至5.1.0 Service Pack 3版。 在繼續升級至Experience Manager Guides 5.1.0 Service Pack 3版之前，您必須先考量下列幾點：

- 如果您是使用5.1.0版或5.1.x版，則可以直接升級至5.1.0 Service Pack 3版。
- 如果您使用的是4.6.0、4.6.x、5.0.0或5.0.x版，則需要升級至5.1.0版。
- 如果您是使用4.6.3、4.6.1、4.6或4.4版，則需升級至5.0.0版。
- 如果您是使用4.3.x、4.2、4.2.1 (Hotfix 4.2.1.3)、4.1或4.1.x版，則必須先升級至4.4版，才能升級至5.0.0版。
- 如果您使用的是4.0版，則必須先升級至4.2版，才能升級至4.3.x版。
- 如果您使用的是3.8.5版，則必須先升級至4.0版，才能升級至4.2版。
- 如果您使用的版本早於3.8.5，請參閱[Adobe Experience Manager Guides說明Experience Manager Guides封存](https://helpx.adobe.com/tw/xml-documentation-for-experience-manager/archive.html)中提供的產品特定安裝指南中的「升級PDF」一節。

>[!NOTE]
>
> 您必須先安裝AEM Service Pack，才能升級Experience Manager Guides版本。

如需詳細資訊，請檢視Experience Manager Guides內部部署版本[的](../install-guide/upgrade-xml-documentation.md)升級指示。
