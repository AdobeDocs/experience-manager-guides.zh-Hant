---
title: 在網頁編輯器中設定檔案自動儲存
description: 瞭解如何在網頁編輯器中設定檔案自動儲存
feature: Web Editor Configuration
role: Admin
level: Experienced
exl-id: 142a588a-3d26-48ee-a3fe-23882922243c
source-git-commit: 2749c0df3bd5640c9491dce3ab6c96f707625969
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 1%

---

# 在網頁編輯器中設定檔案自動儲存 {#id199CC0J0M5Z}

瀏覽器式編輯器中最常見的功能之一，是特定時段後儲存資料的功能。 AEM Guides Web Editor也支援在指定的時間間隔自動儲存主題和地圖檔案。 觸發此功能時，會儲存主題或地圖的工作副本。 不會建立新版本的主題或地圖。 若要建立新版本，您必須按一下網頁編輯器工具列中的「儲存修訂版本」圖示。

預設不會啟用自動儲存功能，您需要使用Cloud Service的設定檔案和On-Premise的`configMgr`來啟用此功能。

下列標籤會根據您的Experience Manager Guides設定，提供在網頁編輯器中啟用自動儲存功能的指示： Cloud Service或內部部署。

>[!BEGINTABS]

>[!TAB Cloud Service]

使用[組態覆寫](download-install-config-override.md#)中提供的指示來建立組態檔。 在設定檔案中，提供下列\(property\)詳細資訊，以設定檔案自動儲存和自動儲存時間間隔：

| PID | 屬性索引鍵 | 屬性值 |
|---|------------|--------------|
| `com.adobe.fmdita.xmleditor.config.XmlEditorConfig` | `xmleditor.autosave` | 布林值\(true/false\)。<br> **預設值**： false |
| `xmleditor.autosaveinterval` | 指定觸發自動儲存功能的時間間隔（秒）。 |

>[!TAB 內部部署]

1. 開啟Adobe Experience Manager Web主控台設定頁面。

   存取設定頁面的預設URL為：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜尋並按一下&#x200B;**com.adobe.fmdita.xmleditor.config.XmlEditorConfig**&#x200B;套件。

1. 在&#x200B;*XmlEditorConfig*&#x200B;設定中，選取&#x200B;**自動儲存**&#x200B;選項。

1. 在&#x200B;**自動儲存間隔**&#x200B;欄位中，指定觸發自動儲存功能的時間間隔（秒）。

1. 按一下&#x200B;**儲存**。

>[!ENDTABS]
