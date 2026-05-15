---
title: 使用條件屬性的REST API
description: 瞭解如何使用條件屬性的REST API
exl-id: 1f0e023a-422c-47b9-917f-b0d80090471c
feature: Rest API Conditional Attributes
role: Developer
level: Experienced
TQID: https://experienceleague.adobe.com/qtmJN6jjCm3xeNYAaHTWr7G3SZFSOodcVqBOKctR3B8
product_v2:
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: a01bfd36-4ab8-4bf8-9dc0-5b45b890552e
  - id: c6d09140-3c91-45d3-b7ed-b681af752f43
subfeature_v2:
  - id: d27d524e-c4e5-4b77-b86b-3db049db0b25
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 154
ht-degree: 5%

---

# 使用條件屬性的REST API {#id175UB30E05Z}

下列REST API可讓您在資料夾設定檔中新增條件屬性。

## 在資料夾層級的設定檔中新增條件屬性

一種POST方法，可將條件屬性新增至指定的資料夾層級設定檔。

**要求URL**：\
http://*<aem-guides-server\>*： *<連線埠號碼\>*/bin/fmdita/folderprofiles

**引數**：

| 名稱 | 類型 | 必要 | 說明 |
|----|----|--------|-----------|
| `:operation` | 字串 | 是 | 要呼叫的作業名稱。 此引數的值為``ADDATTRIBUTEPROFILES``。<br> **注意：**&#x200B;值不區分大小寫。 |
| `profilename` | 字串 | 是 | 必須新增條件屬性的資料夾層級設定檔的顯示名稱。 |
| `conditionalprofiles` | JSON陣列 | 是 | 由條件屬性名稱和值組成的JSON陣列。 下列程式碼片段範例顯示JSON陣列具有兩個屬性 — `platform`和`product`，指派了多個值。 |

```JSON
[  {    name: "platform",    
        values: [       
                {value: "win", label: "Windows"},       
                {value: "mac", label: "Mac OS"}    
                ]},
                {    
                    name: "product",    
                    values: [      
                        {value: "aem_1", label: "AEM 6.1"},     
                        {value: "aem_4,  label: "AEM 6.4"}  
                        ]  
                }]
```

**回應值**：\
傳回HTTP 200 \(Successful\)回應。
