---
title: 設定檔案名稱
description: 瞭解如何針對已上傳至Adobe Experience Manager Assets的資料夾停用後續處理
feature: Filename Configuration
role: Admin
level: Experienced
exl-id: 42722c6f-1b1c-4a7e-89ef-a373623eb774
hidefromtoc: true
source-git-commit: 564ee1731be2378744ffd2ed54a2fd423901a0b3
workflow-type: tm+mt
source-wordcount: '574'
ht-degree: 0%

---

# 停用資料夾的後處理

依預設，所有上傳的資產都使用DAM更新資產工作流程進行處理。 Experience Manager Guides會在此工作流程中執行稱為後續處理的其他處理。 這也有助於產生UUID

將檔案和資料夾上傳至&#x200B;*Adobe Experience Manager Assets*&#x200B;伺服器時，您也可以停用後處理和UUID的產生。

使用[組態覆寫](download-install-additional-config-override.md#)中的指示來建立組態檔。 在組態檔中，提供下列（屬性）詳細資訊，以停用指定路徑的後處理，或忽略資料夾的後處理：

>[!NOTE]
>
> 您也可以使用規則運算式（規則運算式）來定義適用於多個資料夾或整個資料夾階層的規則。 如需詳細資訊，請檢視[使用Regex啟用或停用後處理](#use-regex-to-enable-or-disable-post-processing)區段。

| PID | 屬性索引鍵 | 屬性值 |
|---|------------|--------------|
| `com.adobe.fmdita.config.ConfigManager` | `ignored.post.processing.paths` | 字串值，用來設定任何標準NODE_OPTIONS （多值屬性，路徑在結尾或regex省略`/`的字串） <br> **預設值**： `/content/dam/projects/translation_output` |

| PID | 屬性索引鍵 | 屬性值 |
|---|------------|--------------|
| `com.adobe.fmdita.config.ConfigManager` | `enabled.post.processing.paths` | 字串值，用來設定任何標準NODE_OPTIONS （多值屬性，路徑在結尾或regex省略`/`的字串） <br> **預設值**： `/content/dam` |

## 啟用或停用後處理的規則

依預設，Experience Manager DAM資料夾下的每個資料夾路徑都會完成後續處理。 設定會根據下列規則套用至任何資料夾：

* 如果忽略父資料夾進行後處理，但子資料夾已啟用，則子資料夾及其所有後續資料夾都會被視為已啟用。
* 如果父項已啟用後處理，但子項被忽略，則子項及其所有後續項都會被忽略。
* 如果`ignored.post.processing.paths`和`enabled.post.processing.paths`設定中存在相同的資料夾路徑，則會將其視為忽略以便進行後處理。

## 使用Regex來啟用或停用後續處理

您可以使用規則運算式（規則運算式）來定義適用於多個資料夾或整個資料夾階層的規則，而不需指定個別的資料夾路徑。

在後置處理期間，會根據完整資產路徑評估Regex模式。

使用規則運算式（規則運算式）設定忽略和啟用的後續處理路徑時，AEM Guides會根據資產路徑評估兩個設定。 如果路徑同時符合忽略規則和啟用規則，則忽略規則一律優先。

下列範例說明如何評估規則運算式式式忽略和啟用規則。

## 後處理的規則運算式評估案例

### 忽略父階層，啟用特定資料夾

**忽略regex**

`regex:/content/dam/lang-test/.*`

**啟用Regex**

`regex:/content/dam/lang-test/.*/parent1`

在上述範例中，`/content/dam/lang-test/en/parent1`的後置處理將會停用。

雖然路徑符合啟用Regex，但它已與ignore Regex相符。 忽略規則優先，因此不會啟用後續處理。

### 忽略特定資料夾，啟用更廣泛的階層

**忽略regex**

`regex:/content/dam/lang-test/.*/parent1`

**啟用Regex**

`regex:/content/dam/lang-test/.*`

在上述範例中，`/content/dam/lang-test/en/parent1`的後置處理將會停用，而`/content/dam/lang-test/en/parent2`則會啟用。

已明確忽略`parent1`路徑且保持停用狀態。 只符合啟用Regex的其他資料夾會被處理。

### 忽略父資料夾，啟用子資料夾

**忽略regex**

`regex:/content/dam/lang-test/.*/parent1`

**啟用Regex**

`regex:/content/dam/lang-test/.*/parent1/child1`

在上述範例中，`/content/dam/lang-test/en/parent1`和`/content/dam/lang-test/en/parent1/child2`的後置處理將會停用，而`/content/dam/lang-test/en/parent1/child1`則會啟用。

會處理由regex明確啟用的子資料夾。 其他子資料夾仍為停用狀態，因為其父路徑與忽略規則運算式相符。

### 忽略特定子資料夾，啟用父階層

**忽略regex**

`regex:/content/dam/lang-test/.*/parent1/child1`

**啟用Regex**

`regex:/content/dam/lang-test/.*/parent1`

在上述範例中，`/content/dam/lang-test/en/parent1/child1`的後置處理將停用，`/content/dam/lang-test/en/parent1`和`/content/dam/lang-test/en/parent1/child2`將啟用。

僅略過明確忽略的子資料夾。 系統會處理父資料夾和其他子資料夾，因為它們與啟用規則運算式相符，與忽略規則運算式不相符。

