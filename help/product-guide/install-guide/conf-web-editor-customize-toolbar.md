---
title: 自訂工具列
description: 瞭解如何自訂工具列
exl-id: 14a82c7e-5c07-43a8-bd9e-b221d80f6d05
feature: Web Editor Configuration
role: Admin
level: Experienced
source-git-commit: 5778ed2855287d1010728e689abbe6020ad56574
workflow-type: tm+mt
source-wordcount: '951'
ht-degree: 0%

---

# 自訂工具列 {#id172FB00L0V6}

依預設，Web編輯器會隨附任何DITA編輯器所需的最常見編輯功能。 編輯器中有插入型別清單\（編號或專案符號\）、互動參照、內容參照、表格、段落和字元格式等元素的功能。 除了這些基本元素之外，您還可以自訂Web編輯器來插入在編寫環境中使用的元素。

>[!NOTE]
>
> 從舊版UI移轉至新AEM Guides UI (適用於2502和5.0版的AEM Guides)時，`ui_config`的更新必須轉換為更靈活且模組化的UI設定。 此框架可協助您順暢地採用對editor_toolbar和其他目標Widget的變更（如適用）。 如需詳細資訊，請檢視[轉換UI組態](https://experienceleague.adobe.com/en/docs/experience-manager-guides-learn/videos/advanced-user-guide/conver-ui-config)的總覽。

自訂網頁編輯器的工具列有兩種方式：

- 將新功能新增至工具列

- 從工具列移除任何現有功能


## 在工具列中新增功能

將功能新增至網頁編輯器涉及兩個主要工作 — 在&#x200B;*ui\_config.json*&#x200B;檔案中新增該功能的圖示，以及在JavaScript中新增背景功能。

**在工具列中新增圖示**

執行以下步驟，將功能新增至網頁編輯器的工具列：

1. 登入AEM並開啟CRXDE Lite模式。

1. 導覽至下列位置可用的預設組態檔：

   `/libs/fmdita/clientlibs/clientlibs/xmleditor/ui_config.json`

1. 在下列位置建立預設組態檔案的復本：

   `/apps/fmdita/xmleditor/ui_config.json`

1. 導覽至`apps`節點中的`ui_config.json`檔案，並開啟該檔案以進行編輯。

1. 在`ui_config.json`檔案中，在工具列區段中新增新功能的定義。 通常，您可以建立新的工具列按鈕群組，並在其中新增一或多個工具列按鈕。 或者，您可以在現有的工具列群組中新增工具列按鈕。 建立新的工具列群組需要下列詳細資料：

   - **type：**&#x200B;指定`blockGroup`為`type`值。 此值表示您正在建立包含一或多個工具列群組的區塊群組。

   - **解壓縮類別：**&#x200B;以空格分隔的類別名稱。

   - **專案：**&#x200B;指定工具列中所有群組的定義。 每個群組可以包含一或多個工具列圖示。 若要定義工具列群組中的圖示，您必須在`items`中重新定義`type`屬性，並將其值設為`buttonGroup`。 在`extraclass`屬性中指定一或多個類別名稱。 在`label`屬性中指定功能名稱。 `ui_config.json`檔案中的下列程式碼片段顯示主要工具列區塊的定義，後面接著`buttonGroup`定義：

     ```json
     "toolbar": {    
       "type": "blockGroup",    
       "extraclass": 
       "toolbar operations",    
         "items": [      
           {        
             "type": "buttonGroup",        
             "extraclass": "left-controls",        
             "label": "Left Controls",        
             "items": [
     ```

     在`items`集合中，您必須指定一或多個工具列圖示的定義。
您需要定義以下屬性以新增工具列圖示：

   - **型別：**&#x200B;指定`button`為`type`值。 此值表示您正在新增工具列按鈕。

   - **圖示：**&#x200B;指定您要在工具列中使用的Coral圖示名稱。

   - **變體：**&#x200B;指定`quiet`為`variant`值。

   - **標題：**&#x200B;指定圖示的工具提示。

   - **按一下：**&#x200B;指定在JavaScript檔案中為功能定義的命令名稱。 如果您的命令需要輸入引數，則指定命令名稱為：

     ```JavaScript
     "on-click": {"name": "AUTHOR_INSERT_ELEMENT", "args": "simpletable"}
     ```

   - **顯示或隱藏：**&#x200B;如果您正在定義`show`屬性，請指定圖示的顯示模式。 可能的值為 — `@isAuthorMode`、`@isSourceMode`、`@isPreviewMode`、`true` \（在所有模式中顯示\）或`false` \（在所有模式中隱藏\）。

   您也可以定義`hide`屬性，以取代`show`。 可能的值與`show`屬性中的值相同，唯一差異在於指定的模式不會顯示圖示。

1. 建立&#x200B;*clientlib*&#x200B;資料夾，並將您的JavaScript新增至此資料夾。

1. 透過將&#x200B;*apps.fmdita.xml\_editor.page\_overrides*&#x200B;的值指派給&#x200B;*clientlib*&#x200B;資料夾來更新categories屬性。

1. 儲存&#x200B;*ui\_config.json*&#x200B;檔案並重新載入網頁編輯器。


**JavaScript程式碼範例**

本節提供兩個JavaScript程式碼範例，協助您開始新增自訂功能。 以下範例顯示使用者按一下工具列中的「顯示版本」圖示時的AEM Guides版本號碼。

將下列程式碼新增至JavaScript檔案：

```JavaScript
/**
* This file contains an example to show AEM Guides version 
* number when a user clicks on the Show Version icon in the toolbar. 
* Step 1. Create a clientlib folder and add save a file with your *JavaScript code into this folder. A code sample is shared below.
* Step 2: Update the categories property of the clientlib folder by *assigning it the value of 
* "apps.fmdita.xml_editor.page_overrides".
* Step 3: Add the feature in the ui_config.json file as shown after the *sample code. Save the ui_config.json file and reload the Web Editor
 */

(function (window) {
  "use strict";

  window.addEventListener('DOMContentLoaded', function () {
    fmxml.ready(function () {
      fmxml.eventHandler.subscribe({
        key: 'user.alert',
        next: function next() {
          alert("AEM Guides version x.x");
        }
      });
    });
  });
})(window);
```

在ui\_config.json檔案中新增功能，如下所示：

```json
 {
      "type": "button",
      "icon": "alert",
      "title": "About AEM Guides",
      "variant": "quiet",

  "show": "true",
      "on-click": "user.alert"
  } 
```

下列範例說明如何將檔案的使用中檔案狀態變更為「稽核中」。

```JavaScript
/**
* This file contains an example to set the document state of an active *open documen to "In-Review". 
* Step 1. Create a clientlib folder and add save a file with your *JavaScript code into this folder. A code sample is shared below.
* Step 2: Update the categories property of the clientlib folder by *assigning it the value of 
* "apps.fmdita.xml_editor.page_overrides".
* Step 3: Add the feature in the ui_config.json file as shown after the *sample code. Save the ui_config.json file and reload the Web Editor
 */

(function (window) {
  "use strict";

  //Wait for the page has been completely loaded 

  window.addEventListener('DOMContentLoaded', function () {

    //Wait for the xml editor to start
    fmxml.ready(function () {

      //Subscribe to 'user.docstate.to.in-review' event
      fmxml.eventHandler.subscribe({
        key: 'user.docstate.to.in-review',
        next: function next() {
          var docstate = "In-Review"; // New docstate name
          var filePath = fmxml.curEditor.filePath; 
// Get the file path of active open file
          if (filePath) {
            //Call API to change the doc state
            $.ajax({
              type: 'POST',
              url: '/bin/fmdita/states',
              data: {
                paths: filePath,
                operation: "setdocstates",
                docstate: docstate
              }
            }).fail(function (xhr, textStatus, errorThrown) {
              console.error("Cannot update docstate to " + docstate);
            }).success(function (data) {
              console.log('docstate updated to ' + docstate);
            });
          }
        }
      });
    });
  });
})(window);
```

在ui\_config.json檔案中新增功能，如下所示：

```json
 {
      "type": "button",
      "icon": "actions",
      "title": "Change document state to In-Review",
      "variant": "quiet",
      "show": "true",
      "on-click": "user.docstate.to.in-review"
    } 
```

## 從工具列移除功能

有時您可能不想提供網頁編輯器中目前可用的所有功能，在這種情況下，您可以從網頁編輯器的工具列移除不需要的功能。

執行以下步驟，從工具列移除任何不想要的特徵：

1. 登入AEM並開啟CRXDE Lite模式。

1. 瀏覽至下列位置可用的預設組態檔：。

   `/libs/fmdita/clientlibs/clientlibs/xmleditor/ui_config.json`

1. 在下列位置建立預設組態檔案的復本：

   `/apps/fmdita/xmleditor/ui_config.json`

1. 導覽至`apps`節點中的`ui_config.json`檔案，並開啟該檔案以進行編輯。
`ui_config.json`檔案有三個區段：

- **工具列：**   本節包含編輯器工具列中所有可用功能的定義，例如「插入/移除編號清單」、「\(file\)關閉」、「儲存」、「註解」等。

- **捷徑：**   本節包含指定給編輯器中特定功能的鍵盤快速鍵定義。

- **範本：**   本節包含您可在檔案中使用的DITA元素的預先定義結構。 依照預設，「範本」區段包含段落、簡單表格、表格和正文元素的範本定義。 您可以為想要的元素新增有效的XML結構，以建立任何元素的範本定義。 例如，如果您想要新增包含清單中每個新`li`元素的`p`元素，您可以在範本區段的結尾新增下列程式碼，以達成此目的：

```HTML
"li": "<li><p></p></li>"
```

1. 從工具列區段中，移除您不想向使用者公開的功能專案。

1. 儲存&#x200B;*ui\_config.json*&#x200B;檔案並重新載入網頁編輯器。


**上層主題：**&#x200B;[&#x200B;自訂Web編輯器](conf-web-editor.md)
