---
title: 設定自訂DITA主題範本
description: 瞭解如何設定自訂DITA主題範本
exl-id: 5a2f4897-9697-4c5c-b5be-8fdb3a211948
feature: Template Configuration
role: Admin
level: Experienced
source-git-commit: 0513ecac38840a4cc649758bd1180edff1f8aed1
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 2%

---

# 設定自訂DITA主題範本 {#id16A7G0O02TD}

AEM Guides隨附下列DITA主題範本：

- 主題

- 任務

- 概念

- 參考

- 字彙表

- 疑難排解

- 空白


您可以使用任何這些範本，根據您的編寫需求來建立主題範本。 「空白DITA」範本不包含其他範本的任何結構或元素。 如果您的範本是高度自訂的，且不是以任何一般DITA主題範本為基礎，則可以使用「空白」範本作為基礎。

若要自訂DITA主題範本並用於撰寫，您必須執行下列三個主要工作：

1. *\（可選\）* [設定自訂DITA範本資料夾路徑](#id191LCF0095Z)

1. [建立自訂編寫範本](conf-folder-level.md#id1917D0EG0HJ)

1. 將自訂範本新增到全域或資料夾層級的設定檔中，如 [設定編寫範本](conf-folder-level.md#id1889D0IL0Y4) 區段


## 設定自訂DITA範本資料夾路徑 {#id191LCF0095Z}

AEM Guides可讓您設定資料夾以儲存自訂的DITA map和範本。 依預設，範本檔案儲存在DAM的以下資料夾中：

`/content/dam/dita-templates/`

為了管理主題和對應範本檔案，有專用的資料夾來儲存主題和對應範本。 依預設，所有主題範本都儲存在 `/content/dam/dita-templates/topics`

資料夾。 所有地圖範本都儲存在 `/content/dam/dita-templates/maps` 資料夾。

作為管理員，您可以選擇在預設資料夾中建立自訂地圖或主題範本，或建立您自己的資料夾以儲存自訂範本。 如果您計畫使用預設資料夾，則可以略過此程式。

使用中提供的指示 [設定覆寫](download-install-additional-config-override.md#) 以建立組態檔。 在組態檔案中，提供下列\(property\)詳細資訊，以設定自訂DITA主題範本的資料夾：

>[!IMPORTANT]
>
> 如果您想要使用預設資料夾來儲存自訂範本，可以略過此程式。

| PID | 屬性索引鍵 | 屬性值 |
|---|------------|--------------|
| `com.adobe.fmdita.config.ConfigManager` | `topic.templates` | 指定儲存自訂範本的位置。<br> 如果DAM中存在指定的位置，則所有預設地圖和主題範本都會複製到該資料夾中。 如果該位置不存在，則會使用所有預設地圖和主題範本建立該資料夾。 |

**父級主題：**[&#x200B;設定主題和對應範本](conf-template-tags.md)
