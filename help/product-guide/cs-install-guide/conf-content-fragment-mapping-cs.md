---
title: 設定主題與內容片段模型之間的JSON型對應。
description: 瞭解如何設定主題與內容片段模型之間的JSON型對應。
exl-id: 438e2964-b9c7-462a-a68c-8031bd97911c
feature: Output Generation
role: Admin
level: Experienced
source-git-commit: f8c71e18f5e2e5dbc5a2abdbb92c72fdad3bb233
workflow-type: tm+mt
source-wordcount: '233'
ht-degree: 0%

---

# 建立主題與內容片段之間的對應

AEM Guides提供在主題與內容片段模型之間建立JSON型對應的功能。 您可以使用此對應，將主題內部分或所有元素中存在的內容發佈到內容片段。

1. 若要下載&#x200B;*contentFragmentMapping.json*，請以管理員身分登入Adobe Experience Manager。
1. 選取頂端的Adobe Experience Manager連結，然後選擇&#x200B;**工具**。
1. 從工具清單中選取[參考線]，然後選取&#x200B;**資料夾設定檔**。
1. 選取&#x200B;**全域設定檔**&#x200B;拼貼。
1. 選取&#x200B;**XML編輯器設定**&#x200B;索引標籤，並選取頂端的&#x200B;**編輯**&#x200B;圖示。
1. 選取「**下載**」圖示，在本機系統上下載&#x200B;*contentFragmentMapping.json*&#x200B;檔案。 您可以接著對檔案進行變更，然後上傳相同的檔案。

1. 您需要遵循下列驗證：

   1. 應該是JSON檔案
   2. 其中應包含至少包含一個物件的陣列，且每個物件應包含下列專案：


      `"name": string `

      `"mapping": array`

      每個對應物件都必須包含下列專案：

      `"modelField": string`

      `"xpath": string`

      `"outputType": string`
1. 儲存檔案並上傳。

範例檔案：

```
[
  {
    "mapping": [
      {
        "modelField": "title",
        "xpath": "/topic[1]/title[1]",
        "outputType": "textContent"
      },
      {
        "modelField": "shortdesc",
        "xpath": "/topic[1]/shortdesc[1]",
        "outputType": "textContent"
      },
      {
        "modelField": "topicData",
        "xpath": "/topic[1]/body[1]",
        "outputType": "outerHTML"
      }
    ],
    "name": "Full Topic"
  },
  {
    "mapping": [
      {
        "modelField": "title",
        "xpath": "/topic[1]/title[1]",
        "outputType": "textContent"
      },
      {
        "modelField": "shortdesc",
        "xpath": "/topic[1]/shortdesc[1]",
        "outputType": "textContent"
      },
      {
        "modelField": "heroImage",
        "xpath": "/topic[1]/body[1]/p[1]/image[1]",
        "outputType": "outerHTML"
      },
      {
        "modelField": "dataTable",
        "xpath": "/topic[1]/body[1]/table[1]",
        "outputType": "outerHTML"
      }
    ],
    "name": "Sample Example with XPath"
  }
]
```

您可以使用預設對應來發佈整個主題。 從下拉式清單&#x200B;**產生內容片段**&#x200B;對話方塊中選取`Full Topic`對應，並在內容片段模型中具有「topicData」欄位。
