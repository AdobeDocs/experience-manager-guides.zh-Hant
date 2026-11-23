---
title: 發行說明 | Adobe Experience Manager Guides 5.2.0 Service Pack 4版的發行說明
description: 瞭解Adobe Experience Manager Guides 5.2.0 Service Pack 4版的升級程式及錯誤修正
role: Leader
TQID: https://experienceleague.adobe.com/HEWV5RxPUfqUYf6m6kQW-fU-LiAM0UFGbfzKjtOCZxk
product_v2:
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
    internal-label: Experience Manager Guides
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
feature_v2:
  - id: a3bd6397-2eb2-4908-a61c-226e26855dca
    internal-label: Publishing
role_v2:
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
    internal-label: Leader
source-git-commit: ad78587f55ec7190443dbbce80f596821ec41f9f
workflow-type: tm+mt
source-wordcount: '528'
ht-degree: 1%
---
# 5.2.0 Service Pack 4版本（2026年11月）的發行說明

本文提供Adobe Experience Manager Guides 5.2.0 Service Pack 4版本中的升級指示、Java SDK相容性、修正問題和已知問題的相關資訊。

## Java SDK資源

開發自訂Java外掛程式或與Experience Manager Guides的整合時，請使用下列資源。 確保SDK版本符合您安裝的Experience Manager Guides版本。

| 發行版本 | Java SDK版本 | Maven Central | Java API參考 |
|---|---|---|----|
| 5.2.0 Service Pack 4 (UUID) | 5.2.2 | [AEM Guides SDK API 5.2.2](https://central.sonatype.com/artifact/com.adobe.aem/aem-guides-sdk-api/5.2.2/) | [Javadoc 5.2.2](https://javadoc.io/doc/com.adobe.aem/aem-guides-sdk-api/latest/index.html) |

如需更多詳細資料，請檢視[從Maven中央存放庫設定及使用API JAR](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-guides/using/api-reference/introduction)。

## 升級至Experience Manager Guides的5.2.0 Service Pack 4版本

瞭解如何安裝Experience Manager Guides 5.2.0 Service Pack 4版本。

>[!NOTE]
>
>此版本僅適用於AEM 6.5 LTS。 支援的Service Pack為AEM 6.5 LTS Service Pack 2。

### 先決條件

在開始Experience Manager Guides 5.2.0 Service Pack 4升級程式之前，請確定您使用的是5.2.0 Service Pack 1版。

### 升級程式5.2.0 Service Pack 4版本

1. 下載Experience Manager Guides套件5.2.0版Service Pack 4。
1. 使用封裝管理員(`/crx/packmgr`)將封裝上傳到您的執行個體。
1. 安裝套件。 然後確認`fmdita`套件組合已返回&#x200B;**作用中**&#x200B;狀態。 您可以在`/system/console/bundles`檢查套件組合狀態。
1. 清除您的瀏覽器快取。

## 已修正的問題

以下列出各種區域中修正的錯誤：

### 製作

- 將資產從Explorer面板拖放至地圖時，而該面板在另一位作者移動資產後並未重新整理，因此中斷的參照會新增至地圖。 (GUIDES-57869)

### 資產管理

- 當您使用&#x200B;**覆寫現有檔案**&#x200B;選項覆寫現有的非DITA資產（例如影像）時，不會建立已上傳影像的新版本。 因此，使用基準線產生的輸出會包含較舊的資產。 (GUIDES-59287)

- 從非UUID設定移轉至UUID設定的非DITA資產（例如影像）恢復或分支至其他版本時，其UUID會變更。 不再解析資產的現有參照，且影像在參照該資產的主題中顯示為已損毀。 (GUIDES-58414)

### 發佈

- 在匯出其他地圖時發佈地圖時，輸出會斷斷續續地使用較低品質的影像格式，而不是原始向量影像。 (GUIDES-55221)

## 已知問題

Adobe已在5.2.0 Service Pack 4版本中找出下列已知問題：

- 將元素拖放到無效位置時，編輯器會將其移動到最近的有效位置，在此期間，參照可能會保留其存放庫路徑。 同樣地，當您使用拖放來取代DITA map中的現有參照時，新參照可能會保留其存放庫路徑。 (GUIDES-60688)