---
title: 使用基線和標籤的Java式API
description: 瞭解如何使用基線和標籤的Java式API
exl-id: 0e2ba1bb-f5bf-44da-848a-a55385460c83
feature: Java-Based API Baseline
role: Developer
level: Experienced
source-git-commit: be06612d832785a91a3b2a89b84e0c2438ba30f2
workflow-type: tm+mt
source-wordcount: '890'
ht-degree: 0%

---

# 使用基線和標籤的Java式API {#id175UB30E05Z}

下列Java式API可讓您建立基準線，並將標籤新增至基準線中的檔案。 這些API以套件組合的形式提供。 您必須在程式碼中包含此套件組合，才能使用這些API。

套件組合詳細資料：

- 群組識別碼： **com.adobe.fmdita**

- 成品ID： **api**

- 版本： **3.5**

- 封裝： **com.adobe.fmdita.api.baselines**

- 類別詳細資料：

  ```JAVA
  public class BaselineUtils extends Object
  ```

  **BaselineUtils**&#x200B;類別包含建立基準線以及將標籤套用至基準線中的檔案的方法。


## 建立基準線

建立基準線方法有兩個版本 — 一個用於XML Documentation解決方案3.5版，另一個用於3.5版之前的版本\（包括3.4、3.3和3.2版\）。 3.5版API允許在對應檔案中使用標籤、直接參照和間接參照來建立基準線。

另一個版本的API會使用日期和時間建立基準。 保留此API是為了與使用XML Documentation解決方案3.4、3.3或3.2的系統保持回溯相容性。

**語法\（適用於3.5版\）**：

```JAVA
public static String createBaseline(Session session, 
String sourcePath, 
String baselineTitle, 
String label, 
LinkedHashMap directContext, 
LinkedHashMap indirectContext) 
throws GuidesApiException
```

**引數**：
|名稱|型別|說明|
--------資-----------
|`session`|javax.jcr.Session|有效的JCR工作階段。 使用者工作階段需要同時擁有DITA map的讀取和寫入許可權，以及基準線中包含之所有參照檔案的讀取許可權。|
|`sourcePath`|字串|AEM存放庫中DITA map檔案的絕對路徑。|
|`baselineTitle`|字串|基準的唯一標題。|
|`label`|字串|選取已套用指定標籤的主題版本。|
|`directContext`|LinkedHashMap&lt;String， Object\>|選取直接參考主題\(content\)所依據的設定，依照對應中提及的順序來解析版本。 <br>如果對映的所有索引鍵執行反複專案後，找不到任何版本，則基準線建立程式會失敗。 <br>如果HashMap是空的\（傳送空白且預設值不是null的對應\），則預設會填入為： <br>`directContext.put("label", label);` <br> `directContext.put("latest", true);` <br>如果您希望基準線建立僅挑選指定標籤的版本，而且如果不存在此類版本，則會失敗，請放入`label`索引鍵和您要建立基準線的標籤。|
|`indirectContext`|LinkedHashMap&lt;String， Object\>|選取間接參考主題\（參考內容\）所依據的設定，依照對應中提及的順序來解析版本。 <br>如果對映的所有索引鍵執行反複專案後，找不到任何版本，則基準線建立程式會失敗。 <br>如果HashMap是空的\（傳送空白且預設值不是null對應\），則預設會填入為： <br>`indirectContext.put("label", label);` <br>`indirectContext.put "pickAutomatically", null);` <br>如果您希望它是最新版本以取代自動擷取版本，則請取代： <br>`indirectContext.put("pickAutomatically", null);` <br> _具有：_ <br>`indirectContext.put("latest", true)`|

**傳回**：
基準線的名稱，是JCR儲存庫中基準線的節點名稱。 新建立之基準線的標題將顯示在DITA map的「基準線」頁面上。

**例外狀況**：
如果已存在具有相同標題的基準線，則擲回``ItemExistExceptiom``。

**語法\（3.4、3.3和3.2\）**

```JAVA
public static String createBaseline
(Session session, 
String sourcePath, 
String baselineTitle, 
Date versionDate) throws GuidesApiException
```

**引數**：
|名稱|型別|說明|
--------資-----------
|`session`|javax.jcr.Session|有效的JCR工作階段。 使用者工作階段需要同時擁有DITA map的讀取和寫入許可權，以及基準線中包含之所有參照檔案的讀取許可權。|
|``sourcePath``|字串|AEM存放庫中DITA map檔案的絕對路徑。|
|`baselineTitle`|字串|基準的唯一標題。|
|`versionDate`|日期|在此日期使用主題版本\（直接從DITA map參照\）建立基準線。 以`d-MM-yyyy H:mm`格式指定日期。|

**傳回**：
基準線的名稱，是JCR儲存庫中基準線的節點名稱。 新建立之基準線的標題將顯示在DITA map的「基準線」頁面上。

**例外狀況**：
擲回``RepositoryException.``

## 套用標籤

``applyLabel``方法會將一或多個標籤套用至基準線中的檔案。

**語法**：

```JAVA
public static void applyLabel(Session session,
                  String sourcePath,
                  String baselineName,
                  String label)
                  throws RepositoryException, WorkflowException, Exception
```

**引數**：
|名稱|型別|說明|
--------資-----------
|`session`|javax.jcr.Session|有效的JCR工作階段。|
|`sourcePath`|字串|AEM存放庫中DITA map檔案的絕對路徑。|
|``baselineName``|字串|必須套用標籤的基準節點名稱。 若要取得基準線節點的名稱，您可以使用[\#id185NFF0085Z](#id185NFF0085Z)方法，或檢查CRXDE中DITA對應的基準線節點。<br> **注意：**標籤已套用至從基線中的對應檔案直接參照的檔案版本。|
|`label`|字串|套用至基準線中檔案的標籤。 確保標籤不含下列字元： &amp;amp；sol； &amp;amp；逗號； &amp;amp；冒號； &amp;amp；逗號； &amp;amp；lbrack； &amp;amp；逗號； &amp;amp；vert； &amp;amp；逗號； &amp;amp； &amp;amp；ast； <br>若您想要設定多個標籤，請以逗號分隔標籤；例如Label1， Label2。|

**例外狀況**：
擲回`RepositoryException`。

## 刪除標籤

``deleteLabel``方法會從基準線中的檔案刪除一或多個標籤。

**語法**：

```JAVA
public static Map
<String, String> deleteLabel(Session session, 
String sourcePath, 
String baselineName, 
String label) throws GuidesApiException
```

**引數**：
|名稱|型別|說明|
--------資-----------
|`session`|javax.jcr.Session|有效的JCR工作階段。|
|`sourcePath`|字串|AEM存放庫中DITA map檔案的絕對路徑。|
|`baselineName`|字串|必須從中刪除標籤的基準名稱。<br> **注意：**標籤會從從基線中的對應檔案直接參照的檔案版本中刪除。|
|`label`|字串|要從基準線中的檔案刪除的標籤。 <br>如果您想要刪除多個標籤，請以逗號分隔標籤；例如Label1、Label2.|

**傳回**：
基準線中所有檔案的對映具有*key：value*&#x200B;對`path:deletedlabels`。

**例外狀況**：
擲回``RepositoryException`, `VersionException`, `Exception``。
