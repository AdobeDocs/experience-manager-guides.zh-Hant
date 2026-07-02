---
title: 設定SCORM預覽篩選器
description: 瞭解如何設定SCORM預覽篩選器
feature: Configuration
role: Admin
level: Experienced
source-git-commit: f5b7ae41fe63b31a3b45b38fc73976987a2a5ebe
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 3%

---

# 設定SCORM預覽

本文說明如何設定Experience Manager Guides SCORM預覽，以管理哪些外部網域允許在SCORM預覽輸出中提供樣式表、影像、字型、媒體及內嵌內容。 下列步驟說明如何根據您使用的設定，為SCORM預覽設定各種篩選器：

>[!BEGINTABS]

>[!TAB Cloud Service]

1. 使用[組態覆寫](../install-conf-guide/download-install-config-override.md)中提供的指示來建立組態檔。

1. 在設定檔案中，提供下列屬性詳細資訊：

   | PID | 屬性索引鍵 | 預設值 |
   |---|---|---|
   | `com.adobe.fmdita.publishworkflow.ScormPreviewResponseFilter` | `additional.style.src` | `https://fonts.googleapis.com` |
   | `com.adobe.fmdita.publishworkflow.ScormPreviewResponseFilter` | `additional.img.src` | - |
   | `com.adobe.fmdita.publishworkflow.ScormPreviewResponseFilter` | `additional.font.src` | `https://fonts.gstatic.com` |
   | `com.adobe.fmdita.publishworkflow.ScormPreviewResponseFilter` | `additional.media.src` | - |
   | `com.adobe.fmdita.publishworkflow.ScormPreviewResponseFilter` | `additional.frame.src` | `https://www.youtube-nocookie.com`, `https://www.youtube.com` |


1. 儲存設定檔案並將其部署至您的Cloud Service環境。

儲存後，SCORM預覽會開始套用更新的網域允許清單。 來自未新增到此設定的網域的外部資源在預覽中將無法使用。

>[!NOTE]
>
> 這僅適用於預覽環境；可下載的SCORM套件會繼續如預期提供所有編寫的內容。


>[!TAB 內部部署]

1. 開啟Adobe Experience Manager Web主控台設定頁面。

   存取設定頁面的預設URL為：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜尋並選取&#x200B;**指南SCORM預覽篩選器(com.adobe.fmdita.publishworkflow.ScormPreviewResponseFilter)**&#x200B;套件。

   ![](assets/scorm-preview-filters.png){width="600"}


1. 在套件設定中，視需要新增每個資源型別的允許網域URL：

   | 欄位 | 說明 |
   |---|---|
   | **其他style-src主機** | 授權載入外部CSS樣式表的網域（預設為`https://fonts.googleapis.com`）。 |
   | **其他image-src主機** | 授權載入外部影像的網域。 |
   | **其他font-src主機** | 授權載入外部字型檔案（OTF、WOFF等）的網域（預設為`https://fonts.gstatic.com`）。 |
   | **其他media-src主機** | 授權載入外部媒體檔案的網域。 |
   | **其他frame-src主機** | 授權內嵌iframe內容的網域（預設為`https://www.youtube.com`，以允許YouTube視訊內嵌）。 |

1. 選取「**儲存**」。

儲存後，SCORM預覽會開始套用更新的網域允許清單。 來自未新增到此設定的網域的外部資源在預覽中將無法使用。

>[!NOTE]
>
> 這僅適用於預覽環境；可下載的SCORM套件會繼續如預期提供所有編寫的內容。

>[!ENDTABS]