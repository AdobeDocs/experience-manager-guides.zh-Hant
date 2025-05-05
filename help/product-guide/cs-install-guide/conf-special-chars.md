---
title: 設定允許的特殊字元
description: 瞭解如何設定允許的特殊字元
exl-id: 7ff4305f-71bb-4155-b8e5-911cea6f0ad9
feature: Web Editor Configuration
role: Admin
level: Experienced
source-git-commit: 0513ecac38840a4cc649758bd1180edff1f8aed1
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 0%

---

# 設定允許的特殊字元 {#id20CIL600035}

網頁編輯器可讓您插入一些現成可用的特殊字元。 不過，您可以自訂作者可在檔案中插入的特殊字元清單。 如果您自訂特殊字元清單，則會覆寫預設的特殊字元集。 作者只能使用您在設定中新增的特殊字元。

執行以下步驟來覆寫預設的特殊字元清單：

1. 在您的Cloud Manager Git存放庫中的下列位置建立`symbols.json`檔案：

   ```
   /apps/fmdita/xmleditor/
   ```

1. 在`symbols.json`檔案中新增特殊字元定義為：

   ```
   {"symbols": [{"label": "Arrows",
      "items": [
      {   "name": "←",   "title": "Left Arrow"   } 
      ,   
      {   "name": "↑",   "title": "Up Arrow"      } 
      ]   
      }   ]   }
   ```


`symbols.json`檔案的結構說明如下：

- `"label": "Arrows"`：這會指定特殊字元的類別。 在程式碼片段中，已定義名稱為`"Arrows"`的類別。
- `"items"`：這會定義類別中特殊字元的集合。
- `"name": "←", "title": "Left Arrow"`：這是特殊字元的定義。 它以`"name"`標籤開始，該標籤不可變更。 名稱后面接著特殊字元。 `"title"`是特殊字元的名稱或標題，會顯示為該特殊字元的工具提示。

  您可以在類別中定義多個特殊字元的定義。


**上層主題：**&#x200B;[&#x200B;自訂Web編輯器](conf-web-editor.md)
