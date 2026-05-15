---
title: 使用以Java為基礎的API來產生輸出
description: 瞭解用於產生輸出的Java型API
exl-id: e19439df-39ec-47fd-9da5-24f51750a7e5
feature: Java-Based API Publishing
role: Developer
level: Experienced
TQID: https://experienceleague.adobe.com/i5mTM1VtBg3QFUa-sBmF2pH8BITRn9j-efw2dr8VwCU
product_v2: id: fae5e35a-80c9-4b94-9352-1a060a6aab1did: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: a01bfd36-4ab8-4bf8-9dc0-5b45b890552eid: a3bd6397-2eb2-4908-a61c-226e26855dcaid: c6d09140-3c91-45d3-b7ed-b681af752f43
subfeature_v2: id: fd6cc9e1-e5e5-494e-b7b1-a32f2d6cd7c9
role_v2: id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 225
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
| ``sourcePath`` | 字串 | 需要產生輸出的DITA map檔案的路徑\（在AEM存放庫中\）。 |
| ``outputName`` | 字串 | 要用來產生輸出的輸出預設集名稱。 可以使用垂直號\(「\|」\)分隔符號（例如`aemsite\|pdfoutput`）指定多個輸出預設集。 |

**例外狀況**：
擲回``javax.jcr.RepositoryException``、`java.io.IOException`和`java.lang.Exception`。
