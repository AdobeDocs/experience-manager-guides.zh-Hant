---
title: 設定在Oxygon中編輯的選項
description: 瞭解如何設定氧聯結器外掛程式中編輯的選項。
feature: Web Editor Configuration
role: Admin
level: Experienced
exl-id: 41ecbbb2-81c3-473d-b48b-7370a74a6474
source-git-commit: cc73b81787a3c3dbe8390d93e558064327e59965
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 1%

---

# 設定在Cloud Service的Oxygon中編輯的選項

AEM Guides也可讓使用者在氧氣聯結器外掛程式中編輯其DITA主題和DITA map。

使用[組態覆寫](download-install-config-override.md#)中提供的指示來建立組態檔。 在組態檔中，提供下列（屬性）詳細資訊，以設定&#x200B;**在Oxyo中編輯**&#x200B;選項：



| PID | 屬性索引鍵 | 屬性值 |
|---|------------|--------------|
| `com.adobe.fmdita.xmleditor.config.XmlEditorConfig` | `xmleditor.editinoxygen` | 布林值\(true/false\)。 **預設值**： false |

>[!NOTE]
>
> 此設定預設為停用，且編輯器中沒有可用選項。

**父級主題：**&#x200B;[&#x200B;自訂編輯器](customize-overview.md)
