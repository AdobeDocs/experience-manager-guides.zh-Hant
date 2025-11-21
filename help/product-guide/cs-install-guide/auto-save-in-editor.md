---
title: 在網頁編輯器中設定檔案自動儲存
description: 瞭解如何在網頁編輯器中設定檔案自動儲存
exl-id: 4d99c3d8-cf6a-4cf3-aaec-9009a0376c1e
feature: Web Editor Configuration
role: Admin
level: Experienced
source-git-commit: 6e23f52fc9124d0f07f8108da1b5fe574f553469
workflow-type: tm+mt
source-wordcount: '182'
ht-degree: 1%

---

# 在網頁編輯器中設定檔案自動儲存 {#id199CC0J0M5Z}

瀏覽器式編輯器中最常見的功能之一，是在特定期間後儲存資料的功能。 AEM Guides Web Editor也支援在指定的時間間隔自動儲存主題和地圖檔案。 觸發此功能時，會儲存主題或地圖的工作副本。 不會建立新版本的主題或地圖。 若要建立新版本，您必須按一下網頁編輯器工具列中的「儲存修訂版本」圖示。

預設不會啟用自動儲存功能，您必須使用設定檔案來啟用此功能。

使用[組態覆寫](download-install-additional-config-override.md#)中提供的指示來建立組態檔。 在設定檔案中，提供下列\(property\)詳細資訊，以設定檔案自動儲存和自動儲存時間間隔：

| PID | 屬性索引鍵 | 屬性值 |
|---|------------|--------------|
| `com.adobe.fmdita.xmleditor.config.XmlEditorConfig` | `xmleditor.autosave` | 布林值\(true/false\)。<br> **預設值**： false |
| `xmleditor.autosaveinterval` | 指定觸發自動儲存功能的時間間隔（秒）。 |  |

**上層主題：**[&#x200B;自訂Web編輯器](conf-web-editor.md)
