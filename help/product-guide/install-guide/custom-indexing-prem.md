---
title: 用於內部部署設定的自訂索引部署
description: 瞭解如何為內部部署設定自訂索引內容
feature: Web Editor Configuration
role: Admin
level: Experienced
source-git-commit: 8a9a82e79c757e403141e853aafbc64e1618c30a
workflow-type: tm+mt
source-wordcount: '129'
ht-degree: 0%

---

# 重新索引以尋找和取代(Source檢視)功能

需要重新索引才能啟用&#x200B;**尋找和取代(Source檢視)**&#x200B;功能，此功能可讓您掃描在作者檢視中顯示的整個內容，以及搜尋字串的基礎Source內容（XML結構，包括元素、標籤和屬性值）。

## 重新索引

對於內部部署設定，索引定義會包含在套件中。 若要啟用此功能，您必須重新索引內容。

在節點`reindex=true (Boolean)`上設定屬性` /oak:index/guidesAssetLucene`來開始重新索引，以重新索引先前擷取的內容。

重新索引過程將繼續，直到系統自動將此屬性變更回false。 您可以在系統記錄檔中監視重新索引操作的進度。