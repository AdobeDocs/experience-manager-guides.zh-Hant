---
title: 用於轉換工作流程的Java型API
description: 瞭解用於轉換工作流程的Java型API
exl-id: 807d9ffa-23e3-476c-992d-c1f495233892
feature: Java-Based API Conversion Workflow
role: Developer
level: Experienced
source-git-commit: 8c80a4da8e61909aab0f2db81ef97149774b36c4
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 4%

---

# 用於轉換工作流程的Java型API {#id175UB30E05Z}

>[!NOTE]
>
> 您可以使用Experience Manager Guides中提供的Java式API來建立自訂外掛程式，並擴充現成可用的工作流程。 本文將會在2024年11月封存。
> 檢視[![javadoc](https://javadoc.io/badge2/com.adobe.aem/aem-guides-sdk-api/javadoc.svg)](https://javadoc.io/doc/com.adobe.aem/aem-guides-sdk-api)，以取得有關使用Java型API的最新和詳細檔案。




下列Java型API可讓您將HTML和Word檔案轉換為DITA格式。 這些API以套件組合的形式提供。 您必須在程式碼中包含此套件組合，才能使用這些API。

**套件組合詳細資料**：

- 群組識別碼： **com.adobe.fmdita**

- 成品ID： **api**

- 版本： **3.2**

- 封裝： **com.adobe.fmdita.api.conversion**

- 類別詳細資料：

  ```JAVA
  public class ConversionUtils extends Object
  ```

  **ConversionUtils**&#x200B;類別包含將HTML和Word檔案轉換為DITA格式的方法。


## 轉換HTML檔案

`convertHtmlToDita`方法將HTML檔案轉換為DITA格式。

**語法**：

```JAVA
public static void convertHtmlToDita(Session session, 
                  String inputFile, 
                  String destPath, 
                  boolean createRev) 
                  throws RepositoryException, WorkflowException
```

**引數**：

| 名稱 | 類型 | 說明 |
|----|----|-----------|
| `session` | javax.jcr.Session | 有效的JCR工作階段。 |
| `inputFile` | 字串 | AEM存放庫中來源HTML檔案的絕對路徑。 |
| `destPath` | 字串 | 儲存轉換之DITA檔案的目的地位置的絕對路徑。 |
| `createRev` | 布林值 | 指定是否在指定的目的地建立\(`true`\)檔案的修訂版本\(`false`\)。 僅當目的地位置包含轉換檔案的現有版本時，才會考慮這種情況。 |

**例外狀況**：
擲回`RepositoryException`。

## 轉換Word檔案

``convertWordToDita``方法會將Word檔案轉換為DITA格式。

**語法**：

```JAVA
public static void convertWordToDita(Session session, 
                  String inputFile,
                  String destPath, 
                  String style2tagMap, 
                  boolean createRev) 
                  throws RepositoryException, WorkflowException
```

**引數**：

| 名稱 | 類型 | 說明 |
|----|----|-----------|
| `session` | javax.jcr.Session | 有效的JCR工作階段。 |
| `inputFile` | 字串 | AEM存放庫中來源Word檔案的絕對路徑。 |
| `destPath` | 字串 | 儲存轉換之DITA檔案的目的地位置的絕對路徑。 |
| `style2tagMap` | 字串 | 用於轉換的樣式對應檔案的絕對路徑。 |
| `createRev` | 布林值 | 指定是否在指定的目的地建立\(`true`\)檔案的修訂版本\(`false`\)。 僅當目的地位置包含轉換檔案的現有版本時，才會考慮這種情況。 |

**例外狀況**：
擲回`RepositoryException`。
