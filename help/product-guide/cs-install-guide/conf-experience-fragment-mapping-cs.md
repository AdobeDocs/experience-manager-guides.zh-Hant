---
title: 設定主題和體驗片段範本之間的JSON型對應。
description: 瞭解如何設定主題與體驗片段範本之間的JSON型對應。
feature: Output Generation
role: Admin
level: Experienced
source-git-commit: f252537d15d7e8f8651dddb0ae635905705e4adf
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# 建立主題和體驗片段之間的對應

Adobe Experience Manager Guides提供在主題和體驗片段範本之間建立JSON型對應的功能。 您可以使用此對應，將主題內部分或所有元素中存在的內容發佈到體驗片段。

1. 若要下載 *experienceFragmentMapping.json*，以管理員身分登入Adobe Experience Manager。
1. 選取頂端的Adobe Experience Manager連結，然後選擇 **工具**.
1. 從工具清單中選取「參考線」，然後選取 **資料夾設定檔**.
1. 選取您要設定的設定檔拼貼。 您可以設定全域或資料夾層級設定檔的對應。 例如，選取 **全域設定檔** 圖磚。
1. 選取 **XML編輯器設定** 標籤並選取 **編輯** 圖示在頂端。
1. 選取 **下載** 圖示以下載 *experienceFragmentMapping.json*  檔案。 您可以接著對檔案進行變更，然後上傳相同的檔案。

1. 您需要遵循下列驗證：

   1. 應該是JSON檔案
   2. 其中應包含至少包含一個物件的陣列，且每個物件應包含下列專案：


      `"template": string `

      `"mapping": array`

      每個對應物件都必須包含下列專案：

      `"name": string`

      `"class": string`

      `"resourceType": string`

      `"attributeMap": array`


1. 儲存檔案並上傳。

Experience Manager指南將完整主題轉換為HTML，接著可對映至體驗片段中使用的核心元件。 例如，中的內容 `<p>` 標籤可對應，以在體驗片段中建立文字元件。
* `name`：指定HTML元素。 例如， `<div>`， `<img>`
* `class`：指定與HTML元素相對應的DITA元素標籤。 例如， `<p>` `<image>`
* `resourceType`：指定適用於體驗片段中所使用元件的資源型別。 例如， `wcm/foundation/components/text` 是wcm的resourceType `text` 元件。
* `attributeMap`：為元件提供其他資訊，例如文字元件是否應呈現為 `RichText` 或包含 `fileReference` 影像元件的。




範例檔案：

```
[
  {
    "template": "default",
    "mapping": [
      {
        "name": "#element",
        "resourceType": "wcm/foundation/components/text",
        "attributeMap": [
          {
            "from": "outerHTML",
            "to": "text"
          },
          {
            "value": true,
            "to": "textIsRich"
          }
        ]
      }
    ]
  },
  {
    "template": "/conf/we-retail/settings/wcm/templates/experience-fragment-web-variation",
    "mapping": [
      {
        "name": "div",
        "class": "title",
        "resourceType": "wcm/foundation/components/text",
        "attributeMap": [
          {
            "from": "outerHTML",
            "to": "text"
          },
          {
            "value": true,
            "to": "textIsRich"
          }
        ]
      },
      {
        "name": "h1, h2, h3, h4, h5, h6",
        "resourceType": "wcm/foundation/components/text",
        "attributeMap": [
          {
            "from": "outerHTML",
            "to": "text"
          },
          {
            "value": true,
            "to": "textIsRich"
          }
        ]
      },
      {
        "name": "div",
        "class": "p",
        "resourceType": "wcm/foundation/components/text",
        "attributeMap": [
          {
            "from": "outerHTML",
            "to": "text"
          },
          {
            "value": true,
            "to": "textIsRich"
          }
        ]
      },
      {
        "name": "img",
        "class": "image",
        "resourceType": "wcm/foundation/components/image",
        "attributeMap": [
          {
            "from": "outerHTML",
            "to": "fileReference"
          }
        ]
      },
      {
        "name": "#element",
        "resourceType": "wcm/foundation/components/text",
        "attributeMap": [
          {
            "from": "outerHTML",
            "to": "text"
          },
          {
            "value": true,
            "to": "textIsRich"
          }
        ]
      }
    ]
  }
]
```



從網頁編輯器發佈體驗片段時，選取 `Template` 從的下拉式清單 **產生體驗片段** 對話方塊以檢視範本可用的對應。 **對應** 欄位。 如果範本不存在自訂對應，則會列出預設對應。 您可以使用預設對應，將整個主題發佈為體驗片段。

如需詳細資訊，請檢視 [發佈體驗片段](../user-guide/publish-experience-fragment.md).
