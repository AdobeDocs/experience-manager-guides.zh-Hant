---
title: 設定檔案瀏覽對話方塊的篩選器
description: 瞭解如何設定檔案瀏覽對話方塊的篩選器
exl-id: 1ef09820-3b18-4762-b177-4d40926e21f0
feature: Web Editor Configuration
role: Admin
level: Experienced
TQID: https://experienceleague.adobe.com/7AzojwFiEQkwYtDnwsHhmMOwSCG3vWgsZW5oXZRsTFw
product_v2: id: fae5e35a-80c9-4b94-9352-1a060a6aab1did: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
subfeature_v2: id: b0521e56-a0b2-40b6-bf47-ebc98751f9ba
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2: id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 325
ht-degree: 0%

---

# 設定檔案瀏覽對話方塊的篩選器 {#id20CIL7009GN}

在Web編輯器中工作時，您需要使用檔案瀏覽對話方塊來插入影像、參照或關鍵參照等元素。 預設的檔案瀏覽對話方塊不提供任何檔案篩選選項。 您可以新增自己的篩選器，讓您輕鬆快速地存取所需檔案。

執行以下步驟，將自訂檔案篩選選項新增至檔案瀏覽對話方塊：

1. 登入AEM並開啟CRXDE Lite模式。

1. 導覽至下列位置可用的預設組態檔：

   `/libs/fmdita/clientlibs/clientlibs/xmleditor/ui_config.json`

1. 在下列位置建立預設組態檔案的復本：

   `/apps/fmdita/xmleditor/ui_config.json`

1. 導覽至`apps`節點中的`ui_config.json`檔案，並開啟該檔案以進行編輯。

1. 在`ui_config.json`檔案中，新增您要新增之篩選器的定義。

   下列程式碼片段顯示如何新增兩個篩選選項 — DITA檔案和影像檔案。

   ```json
   "browseFilters": [
       {
         "title": "DITA Files",
         "property": "jcr:content/metadata/dita_class",
         "operation": "exists"
       },
       {
         "title": "Image Files",
         "property": "jcr:content/metadata/dc:format",
         "value": [        
           "image/jpeg",
           "image/gif",
           "image/png"
         ]
       }
   ]
   ```

   在上述程式碼片段中，第一個篩選器是用於DITA檔案。 篩選定義會採用下列引數：

   - **標題：**&#x200B;篩選的顯示名稱。 此標題會以篩選選項的形式顯示在檔案瀏覽對話方塊中。

   - **屬性：**&#x200B;要符合檔案中繼資料的屬性。 例如，若要僅允許屬性中具有`dita_class`中繼資料的檔案，屬性篩選器會將&quot;`jcr:content/metadata/dita_class`&quot;視為其值。

   - **作業：**&#x200B;指定&#39;&#39;`exists`&#39;&#39;以符合屬性引數中所指定值的存在。

   第二個濾鏡是針對影像檔案。 除了`value`引數外，這些引數與第一個篩選器類似。 `value`引數以影像型別的陣列作為其值。 系統會搜尋在value引數中指定的所有檔案型別，並在檔案瀏覽對話方塊中顯示，而會忽略所有其他檔案型別。

1. 儲存&#x200B;*ui\_config.json*&#x200B;檔案並重新載入網頁編輯器。

   當您啟動檔案瀏覽對話方塊時，會顯示在ui\_config.json檔案中設定的篩選選項。

   ![](assets/file-browse-custom-filters.png){width="300"}
