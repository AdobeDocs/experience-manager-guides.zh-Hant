---
title: 設定關閉時簽入檔案的提示
description: 瞭解如何設定關閉時簽入檔案的提示
exl-id: 5b09ec46-aea4-4a3f-8bab-42414e31e37d
source-git-commit: 5e0584f1bf0216b8b00f00b9fe46fa682c244e08
workflow-type: tm+mt
source-wordcount: '174'
ht-degree: 1%

---

# 設定關閉時簽入檔案的提示 {#id222HC040PE8}

當使用者嘗試關閉在網頁編輯器中開啟的檔案(使用 **關閉** 按鈕或 **關閉**&#x200B;選項，如果檔案有未儲存的資料或未儲存的版本，則會出現一個對話方塊。 如果檔案已鎖定，系統會提示使用者解除鎖定。

使用中提供的指示 [設定覆寫](download-install-additional-config-override.md#) 以建立組態檔。 在設定檔案中，提供下列\(property\)詳細資訊，以設定關閉時簽入檔案的提示：

| PID | 屬性索引鍵 | 屬性值 |
|---|------------|--------------|
| `com.adobe.fmdita.xmleditor.config.XmlEditorConfig` | `xmleditor.checkin` | 布林值\( true/ false\)。<br> **預設值**： false |

啟用此設定時， **解鎖檔案** 對話方塊中的核取方塊預設為選取。

如需詳細資訊，請參閱 *檔案關閉並儲存案例* 使用Adobe Experience Manager指南as a Cloud Service指南中的區段。

**父級主題：**[&#x200B;自訂Web編輯器](conf-web-editor.md)
