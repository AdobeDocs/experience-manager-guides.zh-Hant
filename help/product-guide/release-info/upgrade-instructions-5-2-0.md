---
title: 發行說明 | Adobe Experience Manager Guides 5.2.0版的升級指示
description: 瞭解相容性矩陣，以及如何升級至Adobe Experience Manager Guides 5.2.0版。
source-git-commit: 1dc529ba8913c30fba876f101c3b52474e8a71dd
workflow-type: tm+mt
source-wordcount: '859'
ht-degree: 4%

---

# 5.2.0版（2026年5月）的升級指示

本文介紹Adobe Experience Manager Guides 5.2.0版的升級指示和相容性矩陣。

如需新功能和增強功能的詳細資訊，請檢視[&#x200B; 5.2.0版的新功能](../release-info/whats-new-5-2-0.md)。

如需此版本中已修正的問題清單，請檢視5.2.0版本[&#128279;](../release-info/fixed-issues-5-2-0.md)中的已修正問題。

## 相容性矩陣

本節列出Experience Manager Guides 5.2.0版本支援之軟體應用程式的相容性矩陣。

| AEM Guides | AEM 版本 | Service Pack |
| --- | --- | --- |
| 5.2.0 (UUID) | 6.5 LTS | 2 |
| 5.2.0 (UUID) | 6.5 | 24, 23, 22 |

如需詳細資訊，請檢視On-Premise Installation and Configuration Guide中的[技術需求](../install-guide/download-install-technical-requirements.md)區段。

### FrameMaker和FrameMaker Publishing Server

| 發行版本 | FMPS | FM |
| --- | --- | --- |
| 5.2.0 (UUID) | 支援 | 2026或更高版本 |

### 氧氣聯結器

| 發行版本 | 氧氣聯結器視窗 | 氧氣聯結器Mac | 在氧氣視窗中編輯 | 在氧氣Mac中編輯 |
| --- | --- | --- |--- |--- |
| 5.2.0 (UUID) | 3.8-uuid.1 | 3.8-uuid.1 | 2.3 | 2.3 |

### 知識庫範本版本

| 元件封裝名稱 | 元件版本 | 範本版本 |
|---|---|---|
| 適用於Cloud Service的Experience Manager Guides元件內容套件 | guides-components.all-1.4.0 | aem-site-template-dxml-1.0.17 |

### 新增AEM網站範本版本


| AEM Guides | AEM 版本 | 元件版本 | 網站版本 |
|---|---|---| ---|
| 5.2.0 UUID | 6.5 LTS | guides-components.all-1.4.1 | 不適用 |
| 5.2.0 UUID | 6.5 | guides-components.all-1.4.0 | aemg-sites-template-1.3.0 |

## 先決條件

在開始Experience Manager Guides 5.2.0升級程式之前，請確定您擁有：

1. 已升級至Experience Manager Guides 5.0.0、5.0.3、5.1.0、5.1.3或5.1.4版。
1. （選用）已關閉所有翻譯工作。
1. 已將`com.adobe.fmdita.translationservices.TranslationMapUpgradeScript`類別的記錄層級變更為&#x200B;**INFO**，並將這些記錄附加至新的記錄檔，例如`logs/translation_upgrade.log`。

## Experience Manager Guides 5.2.0的升級路徑

您可以在&#x200B;**Experience Manager Guides 6.5**&#x200B;或&#x200B;**AEM 6.5 LTS**&#x200B;上，輕鬆地將您目前的AEM版本升級至5.2.0版。

>[!IMPORTANT]
>
> - **對於AEM 6.5 LTS**：只有Experience Manager Guides 6.5 LTS Service Pack 2才支援AEM 5.2.0。
> - **適用於AEM 6.5**： Experience Manager Guides 5.2.0僅支援AEM 6.5 Service Pack 24、23和22。
> - 如果您目前使用AEM 6.5，並計畫改用AEM 6.5 LTS，在繼續升級AEM 5.2.0之前，請務必先完成Experience Manager Guides升級。 如需詳細資訊，請檢視[升級至Adobe Experience Manager (AEM) 6.5 LTS](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-65-lts/content/implementing/deploying/upgrading/upgrade)。

在繼續升級至5.2.0版的Experience Manager Guides之前，您必須先考量下列幾點：

- 如果您是使用5.0.0、5.0.3、5.1.0、5.1.3或5.1.4版，則可直接升級至5.2.0版。
- 如果您是使用4.6.3、4.6.4、5.0.x版，則可以直接升級至5.1.0版。
- 如果您是使用4.6.0、4.6.1版，則必須先升級至4.6.3、4.6.4或5.0.0版，才能升級至5.1.0版。
- 如果您是使用4.3.x、4.2、4.2.1 (Hotfix 4.2.1.3)、4.1或4.1.x版，則必須先升級至4.4版，才能升級至5.1.0版。
- 如果您使用的是4.0版，則必須先升級至4.2版，才能升級至4.3.x版。
- 如果您使用的是3.8.5版，則必須先升級至4.0版，才能升級至4.2版。
- 如果您使用的版本早於3.8.5，請參閱[Adobe Experience Manager Guides說明Experience Manager Guides封存](https://helpx.adobe.com/tw/xml-documentation-for-experience-manager/archive.html)中提供的產品特定安裝指南中的「升級PDF」一節。

## Experience Manager Guides 5.2.0的升級程式

>[!IMPORTANT]
>
> 後期處理和索引可能需要幾個小時。 我們建議您在非尖峰時段開始升級程式。

1. 從[Adobe軟體發佈入口網站](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)下載5.2.0版本的套件。
1. 安裝您要升級的版本套件，然後等到安裝套件組合為止。
1. *（選用）*&#x200B;升級氧氣聯結器外掛程式，隨您要升級至的版本發行。
1. 安裝套件後清除瀏覽器快取。
1. 如果您已啟用設定`Enable markup find and replace`來存取來源檢視中先前擷取內容的「尋找和取代」功能，您必須重新索引`guidesAssetLucene`索引。 如需詳細資訊，請檢視[重新索引以尋找和取代](../install-conf-guide/custom-indexing-on-prem.md)。
1. 更新系統組態以納入5.2.0版中推出的新設定，確保支援下列增強功能：


| 已新增設定 | 組態檔 | 顯示設定的標籤 | 設定的名稱 |
|-----|-----|------|-----|
| 啟用或停用新編輯器 | `com.adobe.fmdita.config.ConfigManager` | 啟用編輯器2.0 | `enable.markup.editor` |
| 啟用或停用「新建基準線」 | `com.adobe.fmdita.config.ConfigManager` | 啟用較快的基準線(v2) | `enable.baseline.v2` |
| 忽略將版本標示為已變更的中繼資料屬性 | `com.adobe.fmdita.xmleditor.config.XmlEditorConfig` | 忽略已變更版本的中繼資料屬性 | `xmleditor.dirtychecker.ignoremetadata` |
| Source檢視中的尋找和取代功能 | `com.adobe.fmdita.config.ConfigManager` | 啟用標籤尋找和取代 | `enable.markup.findreplace` |
| 啟用或停用略過舊基準的對等連結 | `com.adobe.fmdita.config.ConfigManager` | 略過基準V1的對等連結 | `guides.baseline.v1.skip.peer.links` |
| 啟用或停用翻譯工作流程中目標復本與來源內容的初始化。這僅適用於停用舊版翻譯工作流程時。  | `com.adobe.fmdita.config.ConfigManager` | 使用來源內容初始化目的地語言副本 | `translation.workflow.propagate.source.content` |
| 引用存放區清理 | `com.adobe.fmdita.config.ConfigManager` | 已啟用指南樹狀結構刪除 | `btree.deletion.enabled` |
| DITA資產復寫 | `com.adobe.fmdita.config.ConfigManager` | 復寫DITA資產 | `publish.replicate` |
| 資產處理 | `com.adobe.fmdita.config.ConfigManager` | 啟用Guides資產處理排程工作 | `enable.asset.processing.scheduler` |

如需這些組態設定的詳細資訊，請檢視[組態更新](../install-conf-guide/configuration-on-prem.md)。







