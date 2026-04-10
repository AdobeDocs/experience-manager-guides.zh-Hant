---
title: 設定檔案名稱
description: 瞭解如何針對已上傳至Adobe Experience Manager Assets的資料夾停用後續處理
feature: Filename Configuration
role: Admin
level: Experienced
source-git-commit: 6f3f05419f4f5cdd45ab580cdee6fa869f20f01d
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---

# 停用資料夾的後處理

依預設，所有上傳的資產都使用DAM更新資產工作流程進行處理。 Experience Manager Guides會在此工作流程中執行稱為後續處理的其他處理。 這也有助於產生UUID

將檔案和資料夾上傳至&#x200B;*Adobe Experience Manager Assets*&#x200B;伺服器時，您也可以停用後處理和UUID的產生。

下列標籤會根據您的Experience Manager Guides設定，提供停用資料夾後續處理的指示： Cloud Service或內部部署。

>[!BEGINTABS]

>[!TAB Cloud Service]

使用[組態覆寫](download-install-config-override.md#)中的指示來建立組態檔。 在組態檔中，提供下列（屬性）詳細資訊，以停用指定路徑的後處理，或忽略資料夾的後處理：

| PID | 屬性索引鍵 | 屬性值 |
|---|------------|--------------|
| `com.adobe.fmdita.config.ConfigManager` | `ignored.post.processing.paths` | 用於設定任何標準NODE_OPTIONS的字串值（多值屬性，路徑在結尾省略`/`的字串） <br> **預設值**： `/content/dam/projects/translation_output` |
| `com.adobe.fmdita.config.ConfigManager` | `enabled.post.processing.paths` | 用於設定任何標準NODE_OPTIONS的字串值（多值屬性，路徑在結尾省略`/`的字串） <br> **預設值**： `/content/dam` |

>[!TAB 內部部署]

執行以下步驟來停用指定路徑的後處理，或忽略資料夾的後處理：


1. 開啟Adobe Experience Manager Web主控台設定頁面。

   存取設定頁面的預設URL為：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜尋並按一下&#x200B;**com.adobe.fmdita.config.ConfigManager**&#x200B;套件。

1. 選取&#x200B;**忽略後續處理的路徑**&#x200B;選項，忽略後續處理的資料夾。

   用於設定任何標準NODE_OPTIONS的字串值（多值屬性，路徑在結尾省略`/`的字串）

   **預設值**： `/content/dam/projects/translation_output`

   >[!NOTE]
   >
   > 此屬性預設為停用，且地圖控制面板上提供翻譯標籤。

1. 選取&#x200B;**啟用後續處理的路徑**&#x200B;選項，以啟用後續處理的路徑。

   用於設定任何標準NODE_OPTIONS的字串值（多值屬性，路徑在結尾省略`/`的字串）

   **預設值**： `/content/dam/`

   >[!NOTE]
   >
   > 此屬性預設為停用，且地圖控制面板上提供翻譯標籤。


1. 按一下&#x200B;**儲存**。

>[!ENDTABS]

## 啟用或停用後處理的規則

依預設，Experience Manager DAM資料夾下的每個資料夾路徑都會完成後續處理。 設定會根據下列規則套用至任何資料夾：

* 如果忽略父資料夾進行後處理，但子資料夾已啟用，則子資料夾及其所有後續資料夾都會被視為已啟用。
* 如果父項已啟用後處理，但子項被忽略，則子項及其所有後續項都會被忽略。
* 如果ignored.post.processing.paths和enabled.post.processing.paths設定中存在相同的資料夾路徑，則後處理時會將其忽略。

