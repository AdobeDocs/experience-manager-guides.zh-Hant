---
title: 設定UUID型連結的顯示方式
description: 瞭解如何設定顯示UUID型連結
feature: Web Editor Configuration
role: Admin
level: Experienced
source-git-commit: 6f3f05419f4f5cdd45ab580cdee6fa869f20f01d
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 1%

---

# 設定UUID型連結的顯示方式 {#id2035G20M0QN}

根據預設，當您在編輯器中使用「插入參照」或「插入」「重複使用內容」選項建立連結時，會使用參照內容的UUID來建立連結。 參考內容的&#x200B;**連結**&#x200B;屬性\（在「屬性」面板中\）可設定為顯示參考內容或UUID的相對檔案路徑。 就Cloud Service而言，參照內容的UUID預設會顯示在「屬性」面板中。 針對On-Premise，這個顯示是由&#x200B;**中的**&#x200B;啟用UUID`configMgr`選項所控制。 預設會開啟，這表示參考內容的UUID會顯示在「屬性」面板中。

下列標籤會提供指示，以根據您的Experience Manager Guides設定，在編輯器中顯示參照內容的相對路徑或UUID： Cloud Service或On-Premise。

>[!BEGINTABS]

>[!TAB Cloud Service]

使用[組態覆寫](download-install-config-override.md#)中提供的指示來建立組態檔。 在設定檔案中，提供下列\(property\)詳細資訊，以在編輯器中顯示參照內容的相對路徑或UUID。

| PID | 屬性索引鍵 | 屬性值 |
|---|------------|--------------|
| `com.adobe.fmdita.xmleditor.config.XmlEditorConfig` | `xmleditor.uuid` | 布林值\(true/false\)。 如果要顯示連結內容的相對路徑，則將此屬性設定為false。<br> **預設值**： true |


>[!TAB 內部部署]

1. 開啟Adobe Experience Manager Web主控台設定頁面。

   存取設定頁面的預設URL為：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜尋並按一下&#x200B;**com.adobe.fmdita.xmleditor.config.XmlEditorConfig**&#x200B;套件。

1. 在&#x200B;*XmlEditorConfig*&#x200B;設定中，**啟用UUID**&#x200B;選項預設為啟用。 這表示參考內容的UUID顯示在「屬性」面板的&#x200B;**Link**&#x200B;屬性中。

   如果要顯示連結內容的相對路徑，請取消選取&#x200B;**啟用UUID**&#x200B;選項。

1. 按一下&#x200B;**儲存**。

>[!ENDTABS]

**上層主題：**[&#x200B;自訂Web編輯器](customize-overview.md)
