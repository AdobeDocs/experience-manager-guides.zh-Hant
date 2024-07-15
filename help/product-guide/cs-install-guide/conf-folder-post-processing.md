---
title: 設定檔案名稱
description: 瞭解如何針對已上傳至Adobe Experience Manager Assets的資料夾停用後續處理
feature: Filename Configuration
role: Admin
level: Experienced
exl-id: 42722c6f-1b1c-4a7e-89ef-a373623eb774
source-git-commit: 5d99274da8fdacbd255d426fa4913b5773ca45f8
workflow-type: tm+mt
source-wordcount: '258'
ht-degree: 1%

---

# 停用資料夾的後處理

依預設，所有上傳的資產都使用DAM更新資產工作流程進行處理。 Experience Manager Guides會在此工作流程中執行稱為後續處理的其他處理。 這也有助於產生UUID

將檔案和資料夾上傳至&#x200B;*Adobe Experience Manager Assets*&#x200B;伺服器時，您也可以停用後處理和UUID的產生。


使用[組態覆寫](download-install-additional-config-override.md#)中的指示來建立組態檔。 在組態檔中，提供下列（屬性）詳細資訊，以停用指定路徑的後處理，或忽略資料夾的後處理：

| PID | 屬性索引鍵 | 屬性值 |
|---|------------|--------------|
| `com.adobe.fmdita.config.ConfigManager` | `ignored.post.processing.paths` | 用於設定任何標準NODE_OPTIONS的字串值（多值屬性，路徑末尾省略`/`的字串） <br> **預設值**： `/content/dam/projects/translation_output` |


| PID | 屬性索引鍵 | 屬性值 |
|---|------------|--------------|
| `com.adobe.fmdita.config.ConfigManager` | `enabled.post.processing.paths` | 用於設定任何標準NODE_OPTIONS的字串值（多值屬性，路徑末尾省略`/`的字串） <br> **預設值**： `/content/dam` |


## 啟用或停用後處理的規則

預設情況下，會對Experience ManagerDAM資料夾下的每個資料夾路徑執行後處理。 設定會根據下列規則套用至任何資料夾：

* 如果忽略父資料夾進行後處理，但子資料夾已啟用，則子資料夾及其所有後續資料夾都會被視為已啟用。
* 如果父項已啟用後處理，但子項被忽略，則子項及其所有後續項都會被忽略。
* 如果ignored.post.processing.paths和enabled.post.processing.paths設定中存在相同的資料夾路徑，則後處理時會將其忽略。
