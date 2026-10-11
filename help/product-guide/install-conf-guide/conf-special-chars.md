---
title: 設定允許的特殊字元
description: 瞭解如何設定允許的特殊字元
feature: Web Editor Configuration
role: Admin
level: Experienced
exl-id: e3747a18-b6a1-46fd-a4d1-28a9c087e924
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
    internal-label: Experience Manager Guides
feature_v2:
  - id: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
    internal-label: Configuration
subfeature_v2:
  - id: b0521e56-a0b2-40b6-bf47-ebc98751f9ba
    internal-label: Web Editor configuration
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 81a0e7f0736ba4970673dd87a888a4c60d3c1b4e
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 0%
---
# 設定允許的特殊字元 {#id20CIL600035}

編輯器可讓您插入一些現成可用的特殊字元。 不過，您可以自訂作者可在檔案中插入的特殊字元清單。 如果您自訂特殊字元清單，則會覆寫預設的特殊字元集。 作者只能使用您在設定中新增的特殊字元。

下列標籤會根據您的Experience Manager Guides設定，提供覆寫預設特殊字元清單的指示： Cloud Service或內部部署。

>[!BEGINTABS]

>[!TAB Cloud Service]

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

>[!TAB 內部部署]

1. 登入AEM並開啟CRXDE Lite模式。

1. 在下列位置建立`symbols.json`檔案：

   ```json
   /apps/fmdita/xmleditor/
   ```

1. 在`symbols.json`檔案中新增特殊字元定義為：

   ```json
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

>[!ENDTABS]

**父級主題：**[&#x200B;自訂編輯器](customize-overview.md)
