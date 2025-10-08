---
title: 設定檔案名稱
description: 瞭解如何針對已上傳至Adobe Experience Manager Assets的資料夾停用後續處理
feature: Filename Configuration
role: Admin
level: Experienced
exl-id: ff6e1322-9655-42aa-b353-199c70c9de49
source-git-commit: e84a00237e61275c6cd1ddd312883ac4f66b65ff
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---

# 停用資料夾的後處理

依預設，所有上傳的資產都使用DAM更新資產工作流程進行處理。 Experience Manager Guides會在此工作流程中執行稱為後續處理的其他處理。 這也有助於產生UUID。

將檔案和資料夾上傳至&#x200B;*Adobe Experience Manager Assets*&#x200B;伺服器時，您也可以停用後處理和UUID的產生。


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

>[!NOTE]
>
> 除了透過OSGi設定設定的已忽略和已啟用的路徑外，位於`/var/dxml/postprocess/ignoredPaths`的存放庫層級節點也會影響後續處理行為。 <br>如果資料夾意外地從後續處理中排除，而且未列在OSGi設定中，則建議檢查此存放庫節點。 如果路徑出現在那裡並且設定為`true`，則會忽略它。 若要重新啟用處理，您可以從節點手動移除對應的屬性。

## 啟用或停用後處理的規則

依預設，Experience Manager DAM資料夾下的每個資料夾路徑都會完成後續處理。 設定會根據下列規則套用至任何資料夾：

* 如果忽略父資料夾進行後處理，但子資料夾已啟用，則子資料夾及其所有後續資料夾都會被視為已啟用。
* 如果父項已啟用後處理，但子項被忽略，則子項及其所有後續項都會被忽略。
* 如果ignored.post.processing.paths和enabled.post.processing.paths設定中存在相同的資料夾路徑，則後處理時會將其忽略。
