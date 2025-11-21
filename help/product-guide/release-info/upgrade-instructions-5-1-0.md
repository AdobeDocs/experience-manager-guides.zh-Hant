---
title: 發行說明 | Adobe Experience Manager Guides 5.1.0版的升級指示
description: 瞭解相容性矩陣，以及如何升級至Adobe Experience Manager Guides 5.1.0版。
exl-id: 4b7b6756-d260-4baf-a9cb-d99fc02f020f
source-git-commit: 6e23f52fc9124d0f07f8108da1b5fe574f553469
workflow-type: tm+mt
source-wordcount: '520'
ht-degree: 7%

---

# 5.1.0版（2025年9月）的升級指示

本文介紹Adobe Experience Manager Guides 5.1.0版的升級指示和相容性矩陣。

如需新功能和增強功能的詳細資訊，請參閱 [5.1.0 版本中的新增功能](../release-info/whats-new-5-1-0.md)。

如需此版本中已修正的問題清單，請檢視5.1.0版本[中的](../release-info/fixed-issues-5-1-0.md)已修正問題。

## 相容性矩陣

本節列出Experience Manager Guides 5.1.0版支援之軟體應用程式的相容性矩陣。

| AEM Guides | AEM 版本 | Service Pack |
| --- | --- | --- |
| 5.1.0 (UUID) | 6.5 LTS | 1 |
| 5.1.0 (UUID) | 6.5 | 23， 22， 21 |

如需詳細資訊，請檢視On-Premise Installation and Configuration Guide中的[技術需求](../install-guide/download-install-technical-requirements.md)區段。

### FrameMaker和FrameMaker Publishing Server

| 發行版本 | FMPS | FM |
| --- | --- | --- |
| 5.1.0 (UUID) | 支援 | 2022或更高 |

### 氧氣聯結器

| 發行版本 | 氧氣聯結器視窗 | 氧氣聯結器Mac | 在氧氣視窗中編輯 | 在氧氣Mac中編輯 |
| --- | --- | --- |--- |--- |
| 5.1.0 (UUID) | 3.8-uuid.1 | 3.8-uuid.1 | 2.3 | 2.3 |

### 知識庫範本版本

| 元件封裝名稱 | 元件版本 | 範本版本 |
|---|---|---|
| 適用於Cloud Service的Experience Manager Guides元件內容套件 | dxml-components.all-1.3.0 | aem-site-template-dxml.all-1.0.4 |

### 新增AEM網站範本版本


| AEM Guides | AEM 版本 | 元件版本 | 網站版本 |
|---|---|---| ---|
| 5.1.0 UUID | 6.5 LTS | guides-components.all-1.4.1 | aemg-docs.all-1.2.0 |
| 5.1.0 UUID | 6.5 | guides-components.all-1.4.0 | aemg-docs.all-1.2.0 |

## 升級至Experience Manager Guides 5.1.0

您可以在&#x200B;**Experience Manager Guides 6.5**&#x200B;或&#x200B;**AEM 6.5 LTS**&#x200B;上，輕鬆地將您目前的AEM版本升級至5.1.0版。

>[!NOTE]
>
> 如果您目前使用AEM 6.5，並計畫改用AEM 6.5 LTS，在繼續升級AEM 5.1.0之前，請務必先完成Experience Manager Guides升級。 如需詳細資訊，請檢視[升級至Adobe Experience Manager (AEM) 6.5 LTS](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-65-lts/content/implementing/deploying/upgrading/upgrade)。

在繼續升級至5.1.0版的Experience Manager Guides之前，您必須先考量下列幾點：

- 如果您是使用4.6.3、4.6.4、5.0.0或5.0.0 Service Pack 1版，則可以直接升級至5.1.0版。
- 如果您是使用4.6.0、4.6.1版，則必須先升級至4.6.3、4.6.4或5.0.0版，才能升級至5.1.0版。
- 如果您是使用4.3.x、4.2、4.2.1 (Hotfix 4.2.1.3)、4.1或4.1.x版，則必須先升級至4.4版，才能升級至5.1.0版。
- 如果您使用的是4.0版，則必須先升級至4.2版，才能升級至4.3.x版。
- 如果您使用的是3.8.5版，則必須先升級至4.0版，才能升級至4.2版。
- 如果您使用的版本早於3.8.5，請參閱[Adobe Experience Manager Guides說明Experience Manager Guides封存](https://helpx.adobe.com/tw/xml-documentation-for-experience-manager/archive.html)中提供的產品特定安裝指南中的「升級PDF」一節。

>[!NOTE]
>
>您必須先安裝AEM Service Pack，才能升級Experience Manager Guides版本。

如需詳細資訊，請檢視Experience Manager Guides內部部署版本[的](../install-guide/upgrade-xml-documentation.md)升級指示。


