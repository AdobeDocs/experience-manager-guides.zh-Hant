---
title: 設定檔案名稱
description: 瞭解如何針對已上傳至Adobe Experience Manager Assets的資料夾停用後續處理
feature: Filename Configuration
role: Admin
level: Experienced
source-git-commit: fedd04f4a261ec199f86cb38ecd57e76b9393ae5
workflow-type: tm+mt
source-wordcount: '258'
ht-degree: 1%

---


# 停用資料夾的後處理

依預設，所有上傳的資產都使用DAM更新資產工作流程進行處理。 Experience Manager指南會執行額外的處理（稱為後處理），作為此工作流程的一部分。 這也有助於產生UUID

將檔案和資料夾上傳至 *Adobe Experience Manager Assets* 伺服器，您也可以停用後處理和UUID的產生。


使用中的指示 [設定覆寫](download-install-additional-config-override.md#) 以建立組態檔。 在組態檔中，提供下列（屬性）詳細資訊，以停用指定路徑的後處理，或忽略資料夾的後處理：

| PID | 屬性索引鍵 | 屬性值 |
|---|------------|--------------|
| `com.adobe.fmdita.config.ConfigManager` | `ignored.post.processing.paths` | 字串值，用來設定任何標準NODE_OPTIONS（多值屬性，帶有忽略路徑的字串） `/` 在結尾) <br> **預設值**： `/content/dam/projects/translation_output` |


| PID | 屬性索引鍵 | 屬性值 |
|---|------------|--------------|
| `com.adobe.fmdita.config.ConfigManager` | `enabled.post.processing.paths` | 字串值，用來設定任何標準NODE_OPTIONS（多值屬性，帶有忽略路徑的字串） `/` 在結尾) <br> **預設值**： `/content/dam` |


## 啟用或停用後處理的規則

預設情況下，會對Experience ManagerDAM資料夾下的每個資料夾路徑執行後處理。 設定會根據下列規則套用至任何資料夾：

* 如果忽略父資料夾進行後處理，但子資料夾已啟用，則子資料夾及其所有後續資料夾都會被視為已啟用。
* 如果父項已啟用後處理，但子項被忽略，則子項及其所有後續項都會被忽略。
* 如果ignored.post.processing.paths和enabled.post.processing.paths設定中存在相同的資料夾路徑，則後處理時會將其忽略。
