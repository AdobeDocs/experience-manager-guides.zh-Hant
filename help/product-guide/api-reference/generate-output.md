---
title: 使用以Java為基礎的API來產生輸出
description: 瞭解用於產生輸出的Java型API
exl-id: e19439df-39ec-47fd-9da5-24f51750a7e5
feature: Java-Based API Publishing
role: Developer
level: Experienced
source-git-commit: ee4eb829ebe215315b05cd1f376e934c02a73b1e
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 2%

---

# 使用以Java為基礎的API來產生輸出 {#id175UB30E05Z}

>[!NOTE]
>
> 您可以使用Experience Manager Guides中提供的Java式API來建立自訂外掛程式，並擴充現成可用的工作流程。 本文將會在2024年11月封存。
> 檢視[![javadoc](https://javadoc.io/badge2/com.adobe.aem/aem-guides-sdk-api/javadoc.svg)](https://javadoc.io/doc/com.adobe.aem/aem-guides-sdk-api)，以取得有關使用Java型API的最新和詳細檔案。

下列Java型API可讓您產生DITA map的輸出。 此API可以套件形式提供。 您必須在程式碼中包含此套件組合才能使用此API。

套件組合詳細資料：

- 群組識別碼： **com.adobe.fmdita**

- 成品ID： **api**

- 版本： **3.4**

- 封裝： ****com.adobe.fmdita.api.maps****

- 類別詳細資料：

  ```JAVA
  public class **PublishUtils** extends Object
  ```

  **`PublishUtils`**&#x200B;類別包含產生一或多個輸出預設集輸出的方法。


## 產生輸出

``generateOutput``方法使用指定的輸出預設集產生DITA map檔案的輸出。

**語法**：

```JAVA
public static void generateOutput(Session session,
String sourcePath,
String outputName)
throws GuidesApiException
```

**引數**：

| 名稱 | 類型 | 說明 |
|----|----|-----------|
| `session` | javax.jcr.Session | 有效的JCR工作階段。 |
| ``sourcePath`` | 字串 | 需要產生輸出的DITA map檔案的路徑\(在AEM存放庫中\)。 |
| ``outputName`` | 字串 | 要用來產生輸出的輸出預設集名稱。 可以使用垂直號\(「\|」\)分隔符號（例如`aemsite\|pdfoutput`）指定多個輸出預設集。 |

**例外狀況**：
擲回``javax.jcr.RepositoryException``、`java.io.IOException`和`java.lang.Exception`。
