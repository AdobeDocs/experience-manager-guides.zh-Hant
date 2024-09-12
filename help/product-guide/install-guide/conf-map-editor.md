---
title: 將進階地圖編輯器設定為預設值
description: 瞭解如何將進階地圖編輯器設為預設值
exl-id: ecc023f6-48eb-4afd-97a2-4b3cdd5a8991
feature: Web Editor Configuration
role: Admin
level: Experienced
source-git-commit: 126cecdaa481b9da1add4ba3664c26c2bc5da068
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---

# 將進階地圖編輯器設定為預設值 {#id181AI0003PN}

>[!NOTE]
>
> Basic Map Editor (先前在Experience Manager Guides中提供)已從4.3版和2307版開始淘汰。 您無法存取「基本對映編輯器」來建立和管理DITA map。
>建議您使用進階地圖編輯器。 進階地圖編輯器提供增強功能和更好的自訂選項。 深入瞭解如何使用[進階地圖編輯器](../user-guide/map-editor-advanced-map-editor.md)。

對於4.3和2307之前的版本，Experience Manager Guides隨附基本地圖編輯器和進階地圖編輯器。 基本地圖編輯器提供您建立地圖檔案所需的所有功能。 進階地圖編輯器功能更豐富，並整合在網頁編輯器中。 「進階對映編輯器」可讓作者使用易用的介面來建立和編輯DITA map檔案。

根據預設，每當建立新的對映檔案時，它都會在「基本對映編輯器」中開啟。 您可以讓設定預設為開啟「進階地圖編輯器」來變更此行為。

執行以下步驟，讓「進階對映編輯器」成為對映檔案的預設編輯器：

1. 開啟Adobe Experience Manager Web主控台設定頁面。

   存取設定頁面的預設URL為：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜尋並按一下&#x200B;**com.adobe.fmdita.xmleditor.config.XmlEditorConfig**&#x200B;套件。

1. 選取&#x200B;**隱藏基本地圖編輯器**&#x200B;選項。

   選取此選項後，使用者在使用者介面中的任何位置都不會看到「基本地圖編輯器」連結。 依預設，對應檔案會在「進階對應編輯器」中開啟。
