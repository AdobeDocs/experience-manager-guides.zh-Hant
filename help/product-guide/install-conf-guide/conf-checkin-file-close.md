---
title: 設定關閉時簽入檔案的提示
description: 瞭解如何設定關閉時簽入檔案的提示
feature: Web Editor Configuration
role: Admin
level: Experienced
source-git-commit: 6f3f05419f4f5cdd45ab580cdee6fa869f20f01d
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 1%

---

# 設定關閉時簽入檔案的提示 {#id222HC040PE8}

當使用者嘗試使用檔案索引標籤上的&#x200B;**關閉**&#x200B;按鈕或[選項]功能表中的&#x200B;**關閉**&#x200B;選項關閉在Web編輯器中開啟的檔案時，如果檔案有未儲存的資料或未儲存的版本，就會出現一個對話方塊。 如果檔案已鎖定，系統會提示使用者解除鎖定。

下列標籤會提供相關指示，說明如何根據您的Experience Manager Guides設定，設定在網頁編輯器中提示在關閉時簽入檔案選項： Cloud Service或內部部署。

>[!BEGINTABS]

>[!TAB Cloud Service]

使用[組態覆寫](download-install-config-override.md#)中提供的指示來建立組態檔。 在設定檔案中，提供下列\(property\)詳細資訊，以設定關閉時簽入檔案的提示：

| PID | 屬性索引鍵 | 屬性值 |
|---|------------|--------------|
| `com.adobe.fmdita.xmleditor.config.XmlEditorConfig` | `xmleditor.checkin` | 布林值\( true/ false\)。<br> **預設值**： false |

啟用此組態時，對話方塊中預設會選取&#x200B;**解除鎖定檔案**&#x200B;核取方塊。

如需詳細資訊，請參閱「使用Adobe Experience Manager Guides as a Cloud Service」指南中的&#x200B;*檔案關閉和儲存案例*&#x200B;一節。

>[!TAB 內部部署]

>[!NOTE]
>
>預設不會啟用&#x200B;**解除鎖定檔案**&#x200B;核取方塊，您必須從configMgr啟用此核取方塊。 執行以下步驟，在Web編輯器中啟用預設選項：

1. 開啟Adobe Experience Manager Web主控台設定頁面。

   存取設定頁面的預設URL為：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜尋並按一下&#x200B;**com.adobe.fmdita.xmleditor.config.XmlEditorConfig**&#x200B;套件。

1. 選取&#x200B;**關閉時要求籤入**&#x200B;選項。

1. 按一下&#x200B;**儲存**。


啟用此組態時，對話方塊中預設會選取&#x200B;**解除鎖定檔案**&#x200B;核取方塊。

如需詳細資訊，請參閱「使用Adobe Experience Manager Guides as a Cloud Service」指南中的&#x200B;*檔案關閉和儲存案例*&#x200B;一節。

>[!ENDTABS]

**上層主題：**&#x200B;[&#x200B;自訂Web編輯器](customize-overview.md)
