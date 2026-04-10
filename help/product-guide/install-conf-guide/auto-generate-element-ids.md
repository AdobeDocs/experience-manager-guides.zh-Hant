---
title: 自動生成元素ID
description: 瞭解如何自動產生元素ID
feature: Web Editor Configuration
role: Admin
level: Experienced
source-git-commit: 6f3f05419f4f5cdd45ab580cdee6fa869f20f01d
workflow-type: tm+mt
source-wordcount: '509'
ht-degree: 1%

---

# 自動生成元素ID {#id20CIL40016I}

AEM Guides會為您建立的任何新檔案產生檔案ID。 例如，當您建立DITA map時，會將`map.ditamap_random_digits`之類的ID指派給該map的ID。 您也可以定義自動產生並指派ID的元素。

AEM Guides提供簡易的組態設定，您需要在其中定義ID自動產生的元素及ID的模式。 根據預設，某些元素（如`section`、`table`、`ul`、`ol`）已設定為自動產生識別碼。 您可以新增其他元素至此清單，如此一來，每當在檔案中插入這些元素時，AEM Guides就會根據指定的模式產生並指定ID。

下列標籤提供根據您的Experience Manager Guides設定，將元素設定為具有自動產生的ID的說明： Cloud Service或On-Premise。

>[!BEGINTABS]

>[!TAB Cloud Service]

使用[組態覆寫](download-install-config-override.md#)中提供的指示來建立組態檔。 在設定檔案中，提供下列\(property\)詳細資訊，以設定自動產生的元素ID：

| PID | 屬性索引鍵 | 屬性值 |
|---|------------|--------------|
| `com.adobe.fmdita.xmleditor.config.XmlEditorConfig` | `xmleditor.classes` | 指定以逗號分隔的元素清單。<br> **預設值**： `"topic, section, table, simpletable, fig, image, ul, ol"` |

若要設定自動產生的ID模式，請建立具有以下屬性的組態檔：

| PID | 屬性索引鍵 | 屬性值 |
|---|------------|--------------|
| `com.adobe.fmdita.xmleditor.config.XmlEditorConfig` | `xmleditor.pattern` | 此欄位的預設值設定為`${elementName}_${id}`。 `${elementName}`值會取代為專案名稱。 `${id}`變數會產生專案的連續數字。 例如，如果您將段落元素指派給具有自動產生的ID，則主題或檔案中的第一個段落將取得p\_1之類的ID，而下一個段落將取得p\_2等。 不過，在不同的檔案中，ID產生程式會重新啟動。 這表示在不同的檔案中，可以將p\_1和p\_2等ID指派給段落元素。 **預設值**： ``${elementName}_${id}`` |

>[!TAB 內部部署]

1. 開啟Adobe Experience Manager Web主控台設定頁面。

   存取設定頁面的預設URL為：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜尋並按一下&#x200B;**com.adobe.fmdita.xmleditor.config.XmlEditorConfig**&#x200B;套件。

1. 在&#x200B;*XmlEditorConfig*&#x200B;設定中，請在&#x200B;**自動產生專案標籤**&#x200B;欄位中指定一或多個專案。

   >[!NOTE]
   >
   > 元素標籤是DITA元素名稱，例如`body`、`title`、`codeblock`等。 若要指定多個元素，請以逗號分隔元素名稱。

1. 在&#x200B;**產生ID的模式**&#x200B;欄位中，指定產生ID的模式。

   此欄位的預設值設定為`${elementName}_${id}`。 `${elementName}`值會取代為專案名稱。 `${id}`變數會產生專案的連續數字。 例如，如果您將段落元素指派給具有自動產生的ID，則主題或檔案中的第一個段落將取得p\_1之類的ID，而下一個段落將取得p\_2等。 不過，在不同的檔案中，ID產生程式會重新啟動。 這表示在不同的檔案中，可以將p\_1和p\_2等ID指派給段落元素。

   如果您的檔案已包含指定模式的ID，則自動產生程式不會將這些ID指派給新元素。

1. 按一下&#x200B;**儲存**。

>[!ENDTABS]

**上層主題：**[&#x200B;自訂Web編輯器](customize-overview.md)
