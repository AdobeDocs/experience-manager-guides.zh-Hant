---
title: 設定關閉時簽入檔案的提示
description: 瞭解如何設定關閉時簽入檔案的提示
exl-id: 5b09ec46-aea4-4a3f-8bab-42414e31e37d
feature: Web Editor Configuration
role: Admin
level: Experienced
source-git-commit: 0513ecac38840a4cc649758bd1180edff1f8aed1
workflow-type: tm+mt
source-wordcount: '174'
ht-degree: 1%

---

# 設定關閉時簽入檔案的提示 {#id222HC040PE8}

當使用者嘗試使用檔案索引標籤上的&#x200B;**關閉**&#x200B;按鈕或「選項」功能表中的&#x200B;**關閉**&#x200B;選項關閉在Web編輯器中開啟的檔案時，如果檔案有未儲存的資料或未儲存的版本，則會出現一個對話方塊。 如果檔案已鎖定，系統會提示使用者解除鎖定。

使用[組態覆寫](download-install-additional-config-override.md#)中提供的指示來建立組態檔。 在設定檔案中，提供下列\(property\)詳細資訊，以設定關閉時簽入檔案的提示：

| PID | 屬性索引鍵 | 屬性值 |
|---|------------|--------------|
| `com.adobe.fmdita.xmleditor.config.XmlEditorConfig` | `xmleditor.checkin` | 布林值\( true/ false\)。<br> **預設值**： false |

啟用此組態時，對話方塊中預設會選取&#x200B;**解除鎖定檔案**&#x200B;核取方塊。

如需詳細資訊，請參閱「使用Adobe Experience Manager Guides」as a Cloud Service指南中的&#x200B;*檔案關閉和儲存案例*&#x200B;一節。

**上層主題：**[&#x200B;自訂Web編輯器](conf-web-editor.md)
