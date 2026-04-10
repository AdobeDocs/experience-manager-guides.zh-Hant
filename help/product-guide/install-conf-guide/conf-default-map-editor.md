---
title: 將進階地圖編輯器設定為預設值
description: 瞭解如何將進階地圖編輯器設為預設值
feature: Web Editor Configuration
role: Admin
level: Experienced
source-git-commit: 6f3f05419f4f5cdd45ab580cdee6fa869f20f01d
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 0%

---

# 將進階地圖編輯器設定為預設值 {#id181AI0003PN}

>[!NOTE]
>
> Basic Map Editor （先前在Experience Manager Guides中提供）已從4.3版和2307版開始淘汰。 您無法存取「基本對映編輯器」來建立和管理DITA map。
>建議您使用進階地圖編輯器。 進階地圖編輯器提供增強功能和更好的自訂選項。 深入瞭解如何使用[進階地圖編輯器](../user-guide/map-editor-advanced-map-editor.md)。

對於4.3和2307之前的版本，Experience Manager Guides隨附基本地圖編輯器和進階地圖編輯器。 基本地圖編輯器提供您建立地圖檔案所需的所有功能。 進階地圖編輯器功能更豐富，並整合在網頁編輯器中。 「進階對映編輯器」可讓作者使用易用的介面來建立和編輯DITA map檔案。

根據預設，每當建立新的對映檔案時，它都會在「基本對映編輯器」中開啟。 您可以讓設定預設為開啟「進階地圖編輯器」來變更此行為。

下列標籤會提供指示，讓您根據您的Experience Manager Guides設定，將進階對應編輯器設為對應檔案的預設編輯器： Cloud Service或On-Premise。


>[!BEGINTABS]

>[!TAB Cloud Service]

使用[組態覆寫](download-install-config-override.md#)中提供的指示來建立組態檔。 在設定檔中，提供下列\(property\)詳細資訊，以啟用基本地圖編輯器：

| PID | 屬性索引鍵 | 屬性值 |
|---|------------|--------------|
| `com.adobe.fmdita.xmleditor.config.XmlEditorConfig` | ``fmdita.hide.oldmapeditor`` | 布林值\(true/false\)。 如果您預設要使用進階對應編輯器，請將此屬性設定為true。<br> **預設值**： false |

>[!NOTE]
>
> 依預設，當作者建立對應檔案並選擇開啟它以進行編輯時，就會啟動「基本對應編輯器」。 從Assets UI選取地圖檔案的「編輯」選項時，基本地圖編輯器中也會開啟該選項。

>[!TAB 內部部署]

1. 開啟Adobe Experience Manager Web主控台設定頁面。

   存取設定頁面的預設URL為：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜尋並按一下&#x200B;**com.adobe.fmdita.xmleditor.config.XmlEditorConfig**&#x200B;套件。

1. 選取&#x200B;**隱藏基本地圖編輯器**&#x200B;選項。

   選取此選項後，使用者在使用者介面中的任何位置都不會看到「基本地圖編輯器」連結。 依預設，對應檔案會在「進階對應編輯器」中開啟。

>[!ENDTABS]

**上層主題：**[&#x200B;自訂Web編輯器](customize-overview.md)
