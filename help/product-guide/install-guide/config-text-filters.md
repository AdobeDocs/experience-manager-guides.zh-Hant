---
title: 設定文字篩選
description: 瞭解如何設定文字篩選器
exl-id: 180e4ab5-5259-4a00-ac3c-bb1d6814ce0d
source-git-commit: 5e0584f1bf0216b8b00f00b9fe46fa682c244e08
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# 設定文字篩選 {#id21BPD0FK0XA}

AEM Guides提供在AEM存放庫的選定路徑中存在的檔案中搜尋文字的功能。 您可以使用篩選器搜尋來搜尋存放庫面板中的檔案或瀏覽檔案。 在Web編輯器中工作時，您需要使用檔案瀏覽對話方塊來插入影像、參照或關鍵參照等元素。

依預設，您可以使用一些增強型篩選器來搜尋AEM存放庫中的檔案。 您可以篩選存在於所選路徑上的所有DITA檔案或非DITA檔案。 您也可以搜尋DITA元素屬性中的特定值。 您也可以尋找由指定使用者出庫的檔案。

>[!NOTE]
>
> 您也可以設定全域設定檔，並新增更多篩選器以供搜尋。

執行以下步驟來設定文字篩選：

1. 以管理員身分登入Adobe Experience Manager。
1. 按一下&#x200B;**Adobe Experience Manager** 在頂端連結，然後選擇 **工具**.
1. 選取 **指南** 從工具清單中，按一下 **資料夾設定檔**.
1. 按一下 **全域設定檔** 圖磚。
1. 按一下 **XML編輯器設定**.
1. 按一下 **編輯** 圖示在頂端。
1. 下載ui\_config.json檔案。
1. 在檔案中設定篩選器。 您也可以新增自訂篩選器，如下列範例所示：

   下列程式碼片段顯示如何新增篩選選項「DITA檔案」、「非DITA」、「DITA元素」和「由檔案出庫」。 它也包含自訂篩選器 — 標籤。

   ```json
   [
     {
       "title": "DITA files",
       "property": "jcr:content/metadata/dita_class",
       "operation": "like",
       "children": [
         {
           "title": "DITA Topics",
           "value": "- topic/topic",
           "checked": true
         },
         {
           "title": "DITA Maps",
           "value": "- map/map",
           "checked": true
         }
       ]
     },
     {
       "title": "DITA elements",
       "property": "jcr:content/ditameta",
       "widgetId": "dita_filter",
       "operation": "like"
     },
     {
       "title": "Checked out by",
       "property": "jcr:content/cq:drivelock",
       "operation": "like",
       "itemConfig": {
         "component": "textfield",
         "placeholder": "Checked out by"
       },
       "children": [
         {
           "title": "Check out"
         }
       ]
     },
     {
       "title": "Tags",
       "property": "jcr:content/metadata/cq:tags",
       "itemConfig": {
         "component": "textfield",
         "placeholder": "Enter Tag"
       },
       "children": [
         {
           "title": "Tags"
         }
       ]
     }
   ]
   ```

   在上述程式碼片段中，第一個篩選器是用於DITA檔案。 篩選定義會採用下列引數：

   - **標題：** 篩選的顯示名稱。 此標題會以篩選選項的形式顯示在檔案瀏覽對話方塊中。

   - **屬性：** 要符合檔案中繼資料的屬性。 例如，如果只允許在屬性中有dita\_class中繼資料的檔案，屬性篩選器會將「jcr：content/metadata/dita\_class」作為其值。

   - **作業** 指定「exists」以符合屬性引數中所指定值的存在

1. 上傳更新的ui\_config.json檔案（其中包含新增的篩選器）。

篩選器面板中提供已設定的篩選器。

**父級主題：**[&#x200B;自訂Web編輯器](conf-web-editor.md)
