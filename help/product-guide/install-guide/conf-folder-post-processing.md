---
title: 設定檔案名稱
description: 瞭解如何針對已上傳至Adobe Experience Manager Assets的資料夾停用後續處理
feature: Filename Configuration
role: Admin
level: Experienced
exl-id: ff6e1322-9655-42aa-b353-199c70c9de49
source-git-commit: d525775afeeb89754762ff514126b1c3a3307b3f
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 0%

---

# 停用資料夾的後處理

依預設，所有上傳的資產都使用DAM更新資產工作流程進行處理。 Experience Manager Guides會在此工作流程中執行稱為後續處理的其他處理。 這也有助於產生UUID

將檔案和資料夾上傳至&#x200B;*Adobe Experience Manager Assets*&#x200B;伺服器時，您也可以停用後處理和UUID的產生。


執行以下步驟來停用指定路徑的後處理，或忽略資料夾的後處理：


1. 開啟Adobe Experience Manager Web主控台設定頁面。

   存取設定頁面的預設URL為：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜尋並按一下&#x200B;**com.adobe.fmdita.config.ConfigManager**&#x200B;套件。

1. 選取&#x200B;**Post處理的已忽略路徑**&#x200B;選項，以忽略後續處理的資料夾。

   用於設定任何標準NODE_OPTIONS的字串值（多值屬性，路徑結尾省略`/`的字串）

   **預設值**： `/content/dam/projects/translation_output`

   >[!NOTE]
   >
   > 此屬性預設為停用，且地圖控制面板上提供翻譯標籤。

1. 選取&#x200B;**啟用Post處理的路徑**&#x200B;選項，以啟用後續處理的路徑。

   用於設定任何標準NODE_OPTIONS的字串值（多值屬性，路徑結尾省略`/`的字串）

   **預設值**： `/content/dam/`

   >[!NOTE]
   >
   > 此屬性預設為停用，且地圖控制面板上提供翻譯標籤。


1. 按一下「**儲存**」。



## 啟用或停用後處理的規則

預設情況下，會對Experience ManagerDAM資料夾下的每個資料夾路徑執行後處理。 設定會根據下列規則套用至任何資料夾：

* 如果忽略父資料夾進行後處理，但子資料夾已啟用，則子資料夾及其所有後續資料夾都會被視為已啟用。
* 如果父項已啟用後處理，但子項被忽略，則子項及其所有後續項都會被忽略。
* 如果ignored.post.processing.paths和enabled.post.processing.paths設定中存在相同的資料夾路徑，則後處理時會將其忽略。
