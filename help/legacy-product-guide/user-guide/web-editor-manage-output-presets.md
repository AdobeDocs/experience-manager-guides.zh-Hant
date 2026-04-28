---
title: 管理全域和資料夾設定檔輸出預設集
description: Learn how to create, edit, rename, duplicate, and delete global and folder profile output presets as administrative users in AEM Guides.
feature: Authoring, Features of Web Editor, Publishing
role: User
hide: true
exl-id: 4e9cd1d5-1c28-4363-917d-f58511c4f809
source-git-commit: a70b3ce942b3e69445ad1d7ba6c8f7542e0ff176
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 0%

---

# 管理全域和資料夾設定檔輸出預設集 {#id22BLJ0D0V1U}

The Global and Folder Profile presets are only available to folder-level administrative users.

As an administrator, AEM Guides allows you to create and manage output presets for the Global and Folder Profiles. Then you can easily use these output presets to generate output for all maps that are related to that Global or Folder Profile.

Perform the following steps to create an output preset for the Global and Folder Profiles:

1. Select the DITA map for which you want to create an output preset.
1. Select the **Edit Topics** option from the **Options** menu of the map file. 會開啟對應檔案，以便在Web編輯器中編輯。
1. 在&#x200B;**輸出**&#x200B;標籤中，選取+圖示以建立DITA map的輸出預設集。

   ![](images/add-global-output-preset.png){width="350" align="left"}

1. Enter the following details in the **Add preset** dialog:
   - 類型
   - 名稱
   - Target \(for Knowledgebase preset\)
1. Select the **Add to folder profile** check box to create an output preset for the related folder profile and then click **Add**. The preset is created, and it appears under the **Output** tab of all related maps. \( ![](images/global-preset-icon.svg)\) icon indicates a folder profile level preset.
1. Enter the configuration details. For more details on output presets, view [Understanding the output presets](./generate-output-understand-presets.md).

   >[!NOTE]
   >
   > These presets added to the folder profile are independent of the maps, so the map specific configurations are not present for these presets.

1. You can select the **Generate Preset** icon at the top to generate the output for the maps related to the created output preset. 您將會看到輸出產生程式的狀態。 To view the output, hover the mouse pointer over the topic and click **View Output**.

>[!NOTE]
>
> AEM Guides also provides an out-of-box PDF output preset to generate the output for your DITA maps.

**Other operations from the Options menu**

You can also perform the following operations on the preset from the Options menu:

- Select the preset as default pdf preset. Then the selected preset would be used as the default preset to generate the PDF output using the **Download as PDF** option for a map.
- **Edit**, **Rename**, **Duplicate**, or **Delete** an existing output preset from the **Options** menu.

>[!NOTE]
>
> When an output preset in Global and Folder Profiles is deleted, it will reflect in all related maps and will not appear under the **Output** tab.

**上層主題：**[&#x200B;使用網頁編輯器](web-editor.md)
