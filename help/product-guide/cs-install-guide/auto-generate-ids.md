---
title: 自動生成元素ID
description: 瞭解如何自動產生元素ID
exl-id: a651db7f-228e-4de5-b569-3f1b4f86c418
feature: Web Editor Configuration
role: Admin
level: Experienced
source-git-commit: 0513ecac38840a4cc649758bd1180edff1f8aed1
workflow-type: tm+mt
source-wordcount: '284'
ht-degree: 1%

---

# 自動生成元素ID {#id20CIL40016I}

AEM Guides會為您建立的任何新檔案產生檔案ID。 例如，當您建立DITA map時，ID會變成 `map.ditamap_random_digits` 會指派給地圖的ID。 您也可以定義自動產生並指派ID的元素。

AEM Guides提供簡易的組態設定，您需在其中定義ID自動產生的元素及ID的模式。 依預設，某些元素包括 `section`， `table`， `ul`， `ol`，設為自動產生ID。 您可以新增其他元素至此清單，如此一來，當這些元素插入檔案中時，AEM Guides就會根據指定的模式產生並指定ID

使用中提供的指示 [設定覆寫](download-install-additional-config-override.md#) 以建立組態檔。 在設定檔案中，提供下列\(property\)詳細資訊，以設定自動產生的元素ID：

| PID | 屬性索引鍵 | 屬性值 |
|---|------------|--------------|
| `com.adobe.fmdita.xmleditor.config.XmlEditorConfig` | `xmleditor.classes` | 指定以逗號分隔的元素清單。 <br> **預設值**： `"topic, section, table, simpletable, fig, image, ul, ol"` |

若要設定自動產生的ID模式，請建立具有以下屬性的組態檔：

| PID | 屬性索引鍵 | 屬性值 |
|---|------------|--------------|
| `com.adobe.fmdita.xmleditor.config.XmlEditorConfig` | `xmleditor.pattern` | 此欄位的預設值設為 `${elementName}_${id}`. 此 `${elementName}` 值會取代為元素的名稱。 此 `${id}` 變數會產生元素的序號。 例如，如果您將段落元素指派給具有自動產生的ID，則主題或檔案中的第一個段落將取得p\_1之類的ID，而下一個段落將取得p\_2等。 不過，在不同的檔案中，ID產生程式會重新啟動。 這表示在不同的檔案中，可以將p\_1和p\_2等ID指派給段落元素。 **預設值**： ``${elementName}_${id}`` |

**父級主題：**[&#x200B;自訂Web編輯器](conf-web-editor.md)
