---
title: 設定Regx以取得有效的檔案名稱字元
description: 瞭解如何設定有效檔案名稱字元的Regx
feature: Filename Configuration
role: Admin
level: Experienced
source-git-commit: 6f3f05419f4f5cdd45ab580cdee6fa869f20f01d
workflow-type: tm+mt
source-wordcount: '506'
ht-degree: 0%

---

# 設定Regx以取得有效的檔案名稱字元 {#id214BD0550E8}

從AEM Guides 3.8版開始，管理員可以定義檔案名稱允許的有效特殊字元清單。 在舊版中，使用者可定義包含特殊字元的檔案名稱，例如`@`、`$`、`>`等。 這些特殊字元在從DITA map儀表板開啟主題或按一下TOC中的主題連結時會導致問題，這通常會導致頁面因URL中的特殊字元而無法開啟。

使用可讓您定義有效檔案名稱字元的regx的設定，您就完全可控制檔案在系統中的內部命名方式。 您可以定義檔案名稱中允許的特殊字元清單。 依預設，有效的檔案名稱組態包含&quot;`a-z A-Z 0-9 - _`&quot;。 建立新檔案時，檔案標題中可以有任何特殊字元，但在內部，檔案名稱中將以「`-`」取代。 例如，檔案標題可以是「Introduction 1」或「Introduction@1」，針對這兩種情況產生的對應檔案名稱都是「Introduction-1」。

定義有效字元清單時，請記住，這些字元&quot;`*/:[\]|#%{}?&<>"/+`&quot;將一律取代為&quot;`-`&quot;。

如果您未設定有效的特殊字元清單，檔案建立程式可能會為您提供一些未預期的結果。 若要避免這類錯誤，強烈建議您變更此設定。

下列標籤會提供根據您的Experience Manager Guides設定，為有效檔案名稱字元設定Regx的說明： Cloud Service或內部部署。


>[!BEGINTABS]

>[!TAB Cloud Service]

使用[組態覆寫](download-install-config-override.md#)中提供的指示來建立組態檔。 在設定檔案中，提供下列\(property\)詳細資訊，以設定有效檔案名稱字元的regex：

| PID | 屬性索引鍵 | 屬性值 |
|---|------------|--------------|
| `com.adobe.fmdita.xmleditor.config.XmlEditorConfig` | `valid.characters` | 該值為規則運算式模式。 它必須有三個基本字元，而且清單必須以連字型大小\(-\)開頭。<br> **預設值**： \[-a-zA-Z0-9\_\] |

>[!NOTE]
>
> 與有效檔案名稱字元清單類似，您也可以為AEM Site輸出指定有效檔案名稱字元清單。 如需詳細資訊，請參閱[為AEM網站輸出設定有效的檔案名稱](conf-file-names-valid-regx-aem-site-output.md#)。

>[!TAB 內部部署]

若要在檔案名稱中設定regx為有效的\（或允許的\）字元，請執行以下步驟：

1. 開啟Adobe Experience Manager Web主控台設定頁面。

   存取設定頁面的預設URL為：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜尋並按一下&#x200B;*com.adobe.fmdita.config.ConfigManager*&#x200B;套件。

1. 在&#x200B;**有效字元的Regex**&#x200B;屬性中，確定屬性已設為\[-a-zA-Z0-9\_\]。 您可以新增更多字元至此清單，但清單必須包含這些基本字元，且清單必須以連字型大小「 — 」開頭。

   >[!NOTE]
   >
   > 此屬性僅適用於檔案名稱，不適用於資料夾名稱。

1. 按一下&#x200B;**儲存**。


>[!NOTE]
>
> 與有效檔案名稱字元清單類似，您也可以為AEM Site輸出指定有效檔案名稱字元清單。 如需詳細資訊，請參閱[為AEM網站輸出設定有效的檔案名稱](conf-file-names-valid-regx-aem-site-output.md#)。

>[!ENDTABS]
