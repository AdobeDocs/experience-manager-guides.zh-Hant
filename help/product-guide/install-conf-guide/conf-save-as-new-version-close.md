---
title: 設定關閉時儲存為新版本的提示
description: 瞭解如何設定關閉時儲存為新版本的提示
feature: Web Editor Configuration
role: Admin
level: Experienced
exl-id: da41044a-bab0-456b-9543-effc88d1a2ae
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
    internal-label: Experience Manager Guides
feature_v2:
  - id: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
    internal-label: Configuration
subfeature_v2:
  - id: b0521e56-a0b2-40b6-bf47-ebc98751f9ba
    internal-label: Web Editor configuration
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 81a0e7f0736ba4970673dd87a888a4c60d3c1b4e
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 1%
---
# 設定關閉時儲存為新版本的提示 {#id222HBI00XXA}

當使用者嘗試使用檔案索引標籤上的&#x200B;**關閉**&#x200B;按鈕或「選項」選單中的&#x200B;**關閉**&#x200B;選項關閉在編輯器中開啟的檔案時，如果檔案有未儲存的資料或未儲存的版本，則會出現一個對話方塊。 如果未儲存版本，則會提示使用者將檔案另存為新版本。

下列標籤會根據您的Experience Manager Guides設定提供指示： Cloud Service或內部部署。

>[!BEGINTABS]

>[!TAB Cloud Service]

使用[組態覆寫](download-install-config-override.md#)中提供的指示來建立組態檔。 在設定檔案中，提供下列\(property\)詳細資訊，以設定關閉時另存為新版本的提示：

| PID | 屬性索引鍵 | 屬性值 |
|---|------------|--------------|
| `com.adobe.fmdita.xmleditor.config.XmlEditorConfig` | `xmleditor.savenewversion` | 布林值\( true/ false\)。<br>  **預設值**： true |

啟用此設定時，對話方塊中預設會選取&#x200B;**另存為新版本**&#x200B;核取方塊。

如需詳細資訊，請參閱「使用Adobe Experience Manager Guides as a Cloud Service」指南中的&#x200B;*檔案關閉和儲存案例*&#x200B;一節。

>[!TAB 內部部署]

1. 開啟Adobe Experience Manager Web主控台設定頁面。

   存取設定頁面的預設URL為：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜尋並按一下&#x200B;**com.adobe.fmdita.xmleditor.config.XmlEditorConfig**&#x200B;套件。

1. 選取&#x200B;**關閉**&#x200B;時詢問新版本選項。

1. 按一下&#x200B;**儲存**。


預設不會啟用&#x200B;**另存為新版本**&#x200B;核取方塊，您必須從configMgr啟用此專案。

選取此選項時，預設會在對話方塊中選取&#x200B;**另存為新版本**&#x200B;核取方塊。

如需詳細資訊，請參閱「使用Adobe Experience Manager Guides as a Cloud Service」指南中的&#x200B;*檔案關閉和儲存案例*&#x200B;一節。

>[!ENDTABS]
