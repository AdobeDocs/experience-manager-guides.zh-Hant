---
title: 自動生成元素ID
description: 瞭解如何自動產生元素ID
exl-id: 8d09ab89-4be5-49f1-9831-9f01c92dc472
feature: Web Editor Configuration
role: Admin
level: Experienced
TQID: https://experienceleague.adobe.com/BD8MStcVS-bjRftYXTtXjUodzuRnaS8D11jKXH-qTs8
product_v2: id: fae5e35a-80c9-4b94-9352-1a060a6aab1did: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
subfeature_v2: id: b0521e56-a0b2-40b6-bf47-ebc98751f9ba
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: cc73b81787a3c3dbe8390d93e558064327e59965
workflow-type: tm+mt
source-wordcount: 342
ht-degree: 0%

---

# 自動生成元素ID {#id20CIL40016I}

AEM Guides會為您建立的任何新檔案產生檔案ID。 例如，當您建立DITA map時，會將`map.ditamap_random_digits`之類的ID指派給該map的ID。 您也可以定義自動產生並指派ID的元素。

AEM Guides提供簡易的組態設定，您需要在其中定義ID自動產生的元素及ID的模式。 根據預設，某些元素（如`section`、`table`、`ul`、`ol`）已設定為自動產生識別碼。 您可以新增其他元素至此清單，以便每當在檔案中插入這些元素時，AEM Guides都會根據指定的模式產生並指派ID

執行以下步驟，將元素設定為具有自動產生的ID：

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


**父級主題：**[&#x200B;自訂編輯器](conf-web-editor.md)
