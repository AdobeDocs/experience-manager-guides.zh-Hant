---
title: 根據UUID設定自動檔案名稱
description: 瞭解如何根據UUID設定自動檔案名稱
feature: Filename Configuration
role: Admin
level: Experienced
source-git-commit: 6f3f05419f4f5cdd45ab580cdee6fa869f20f01d
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 1%

---

# 根據UUID設定自動檔案名稱 {#id205QG070D5Z}

依預設，建立主題或地圖檔案時，作者也可以選擇指定檔案名稱。 作者可自由依需求指派檔案名稱。 不過，這可能會導致不一致，在大型檔案系統中可以看到各種檔案名稱。 身為管理員，您可以限製作者為他們在系統中建立的檔案指定檔案名稱。 對於每個新主題或對應檔案，您可以選擇自動指派以UUID為基礎的檔案名稱。

下列標籤會提供根據您的Experience Manager Guides設定根據UUID設定自動檔案名稱的指示： Cloud Service或On-Premise。


>[!BEGINTABS]

>[!TAB Cloud Service]

使用[組態覆寫](download-install-config-override.md#)中提供的指示來建立組態檔。 在設定檔案中，提供下列\(property\)詳細資訊，以根據UUID設定自動檔案名稱：

| PID | 屬性索引鍵 | 屬性值 |
|---|------------|--------------|
| `com.adobe.fmdita.xmleditor.config.XmlEditorConfig` | `xmleditor.uniquefilenames` | 布林值\(true/false\)。<br> **預設值**： false |

>[!NOTE]
>
> 開啟此選項後，作者在建立新主題或對應檔案時，看不到指定檔案名稱的選項。 您可以從Assets UI和Web編輯器建立新的主題或地圖檔案。

>[!TAB 內部部署]

執行以下步驟，自動為系統中建立的所有新檔案指派以UUID為基礎的檔案名稱：

1. 開啟Adobe Experience Manager Web主控台設定頁面。

   存取設定頁面的預設URL為：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜尋並按一下&#x200B;*com.adobe.fmdita.xmleditor.config.XmlEditorConfig*&#x200B;套件。

1. 選取&#x200B;**使用UUID系統檔案名稱**&#x200B;選項。

1. 按一下&#x200B;**儲存**。


>[!NOTE]
>
> 依預設，此選項是關閉的。 開啟此選項後，作者在建立新主題或對應檔案時，看不到指定檔案名稱的選項。 您可以從Assets UI和Web編輯器建立新的主題或地圖檔案。

>[!ENDTABS]

