---
title: 發行說明 |Adobe Experience Manager指南 4.6.0 Service Pack 4 版本的升級指示
description: 瞭解如何升級至 4.6.0 Service Pack 4 版的 Adobe Experience Manager
role: Leader
source-git-commit: f6d5b1abb9e9a50d2564e8199b04129e3bc0f256
workflow-type: tm+mt
source-wordcount: '531'
ht-degree: 1%

---

# 4.6.0 Service Pack 4 版本的升級說明（2025 年 4 月）

本文介紹Adobe Experience Manager Guides 4.6.0 Service Pack 4版的升級指示和相容性矩陣。

有關此版本中已修復的問題清單，視圖 [已修復 4.6.0 Service Pack 4 版本中](fixed-issues-4-6-0-sp4.md)的問題。

## 相容性矩陣

本節列出了Experience Manager指南 4.6.0 Service Pack 4 發行版支持的軟體應用程式的相容性矩陣。

### Adobe Experience Manager

**4.6.0 Service Pack 4 非 UUID**
版本 6.5 Service Pack 21、20 和 19

**4.6.0 Service Pack 4 UUID**
6.5版Service Pack 21、20和19

如需詳細資訊，請檢視On-Premise Installation and Configuration Guide中的[技術需求](../install-guide/download-install-technical-requirements.md)區段。

### FrameMaker和FrameMaker Publishing Server

| 發行 | FMPS 2022 | FMPS 2020 | FM 2022 | FM 2020 |
| --- | --- | --- | --- | --- |
| 4.6.0 Service Pack 4 （非UUID） | 2022或更高 | 2020.2或更新版本* | 2022 年或更高 | 2020.3 或更高版本 |
| 4.6.0 Service Pack 4 （UUID） | 2022 年或更高 | 2020.2或更新版本* | 2022或更高 | 2020.4 或更高版本 |
| | | | |

*從 2020.2 開始的 FMPS 版本中支援AEM中創建的基線和條件。

### 氧氣連接器

| 發行 | 氧氣連接器視窗 | 氧氣聯結器Mac | 在氧氣視窗中編輯 | 在氧氣Mac中編輯 |
| --- | --- | --- |--- |--- |
| 4.6.0 Service Pack 4 （非UUID） | 2.8-regular-10 | 2.8-regular-10 | 1.6 | 1.6 |
| 4.6.0 Service Pack 4 (UUID) | 3.6-uuid.9 | 3.6-uuid.9 | 2.3 | 2.3 |
|  |  |   |

### 知識庫範本版本

| 元件包名稱 | 元件版本 | 範本版本 |
|---|---|---|
| 適用於Cloud Service的Experience Manager Guides元件內容套件 | dxml-components.all-1.2.2 | aem-site-template-dxml.all-1.0.15 |

### 新增AEM網站範本版本

| 元件版本 | 網站版本 |
|---|---|
| guides-components.all-1.0.0 | aemg-docs.all-1.0.0 |

## 升級至Experience Manager Guides的4.6.0 Service Pack 4版本

您可以輕鬆地將最新版本的Guides升級至4.6.0 Service Pack 4。 在繼續升級之前，您必須考慮以下幾點：

- 如果您使用的是版本 4.6.0、4.6.0 Service Pack 1 或 4.6.0 Service Pack 3，則可以直接升級到 4.6.0 Service Pack 4。
- 如果您使用的是版本 4.4、4.3.1 或 4.3.0 ，則需要升級到版本 4.6.0。
- 如果您使用的是版本 4.2、4.2.1（修補程式 4.2.1.3）、4.1 或 4.1.x，則需要先升級到版本 4.4，然後再升級到版本 4.6.0。
- 如果您使用的是 4.0 版，那麼在升級到 4.3.x 版之前需要升級到 4.2 版。
- 如果您使用的是版本 3.8.5，則需要先升級到版本 4.0，然後再升級到版本 4.2。
- 如果您使用的版本早於3.8.5，請參閱[Adobe Experience Manager Guides說明Experience Manager Guides封存](https://helpx.adobe.com/tw/xml-documentation-for-experience-manager/archive.html)中提供的產品特定安裝指南中的「升級PDF」一節。

>[!NOTE]
>
>您必須先安裝 Service Pack AEM 然後才能升級 Experience Manager Guides 版本。

4.6.0 Service Pack 4 版本的升級過程遵循與 4.6.0 版本相同的步驟。 有關詳細說明，請参閱視圖 [Experience Manager 指南內部部署版本的](../install-guide/upgrade-xml-documentation.md) 升級說明。
