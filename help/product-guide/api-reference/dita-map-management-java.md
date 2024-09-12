---
title: 使用DITA map的Java型API
description: 瞭解搭配DITA map使用的Java型API
exl-id: bd91fc90-75f8-487c-99d1-2637e9cf9924
feature: Java-Based API Dita Map
role: Developer
level: Experienced
source-git-commit: 8c80a4da8e61909aab0f2db81ef97149774b36c4
workflow-type: tm+mt
source-wordcount: '1068'
ht-degree: 2%

---

# 使用DITA map的Java型API {#id175UB30E05Z}

>[!NOTE]
>
> 您可以使用Experience Manager Guides中提供的Java式API來建立自訂外掛程式，並擴充現成可用的工作流程。 本文將會在2024年11月封存。
> 檢視[![javadoc](https://javadoc.io/badge2/com.adobe.aem/aem-guides-sdk-api/javadoc.svg)](https://javadoc.io/doc/com.adobe.aem/aem-guides-sdk-api)，以取得有關使用Java型API的最新和詳細檔案。



下列Java型API可讓您在AEM Guides中使用DITA map。 這些API以套件組合的形式提供。 您必須在程式碼中包含此套件組合，才能使用這些API。

套件組合詳細資料：

- 群組識別碼： **com.adobe.fmdita**

- 成品ID： **api**

- 版本： **3.2**

- 封裝： **com.adobe.fmdita.api.maps**

- 類別詳細資料：

  ```JAVA
  public class MapUtilities extends Object
  ```

  MapUtilities類別包含從DITA map檔案擷取中繼資料資訊的方法。


## 下載具有相依物件的DITA map

`zipMapWithDependents`方法會建立包含DITA map及其所有相依專案（例如參照的主題、子地圖、影像和DTD）的.zip檔案。 DITA map的.zip檔案是根據指定的基準線建立的。

它也可讓您維持相同的結構\（父資料夾和子資料夾\），或在單一資料夾內為所有相依檔案建立平面檔案結構。

>[!IMPORTANT]
>
> 如果遺失任何相依檔案，API會擲回例外狀況，且無法建立.zip檔案。

**語法**：

```JAVA
public static void zipMapWithDependents(Session session, 
                     String sourcePath, 
                     String baseline, 
                     OutputStream outputStream,
                     boolean flatFS) 
                     throws RepositoryException, IOException
```

**引數**：

| 名稱 | 類型 | 說明 |
|----|----|-----------|
| `session` | javax.jcr.Session | 有效的JCR工作階段。 |
| `sourcePath` | 字串 | 需要下載之DITA map檔案的路徑\(在AEM存放庫中\)。 |
| `outputStream` | java.io.OutputStream | 要將ZIP寫入的資料流。 |
| `baseline` | 字串 | 用來擷取已建立版本之內容的基準標題。<br> **注意：**&#x200B;值區分大小寫。 |
| flatFS | 布林值 | \(Optional\)如果設為true，則會在ZIP檔案中傳回檔案的平面結構。 例如，如果您的DITA map參照多個資料夾中的內容，則所有參照的檔案都會提取到單一資料夾中。 如果存在同名檔案，則會新增數值尾碼以重新命名這些檔案。 所有參照\（在DITA map和主題中\）都會自動處理，因為它們會根據平面資料夾結構中檔案的新位置進行更新。 如果設為false，則會維持資料夾結構在ZIP檔案中的原樣。 如果DITA map參照來自多個位置的檔案，則所有這些位置也會在ZIP檔案中建立。 還原ZIP檔案時，會在目的地位置建立精確的資料夾結構。 <br>此引數的預設值為false。 |

**傳回**：
ZIP的內容會寫入`outputStream`。

**例外狀況**：
擲回``javax.jcr.RepositoryException``、`java.io.IOException`。

## 下載含有相依項的DITA map \（非同步\）

或者，您可以以非同步模式下載具有相依物件的DITA map。 此方法對於較大的DITA map比較實用。

`zipMapWithDependents`方法會建立包含DITA map及其所有相依專案（例如參照的主題、子地圖、影像和DTD）的.zip檔案。 DITA map的.zip檔案是根據指定的基準線建立的。

它也可讓您維持相同的結構\（父資料夾和子資料夾\），或在單一資料夾內為所有相依檔案建立平面檔案結構。

>[!NOTE]
>
> 一段時間後，系統會根據output.history.purgetime設定（若已定義）或預設為5天，自動刪除此節點。

**語法**：

```JAVA
public static CompletableFuture<Node> zipMapWithDependencies(Session session,
                     String sourcePath, 
                     String baseline, 
                     boolean flatFS) 
```

**引數**：

| 名稱 | 類型 | 說明 |
|----|----|-----------|
| `session` | javax.jcr.Session | 有效的JCR工作階段。 |
| `sourcePath` | 字串 | 需要下載之DITA map檔案的路徑\(在AEM存放庫中\)。 |
| `baseline` | 字串 | 用來擷取已建立版本之內容的基準標題。<br> **注意：**&#x200B;值區分大小寫。 |
| flatFS | 布林值 | \(Optional\)如果設為true，則會在ZIP檔案中傳回檔案的平面結構。 例如，如果您的DITA map參照多個資料夾中的內容，則所有參照的檔案都會提取到單一資料夾中。 如果存在同名檔案，則會新增數值尾碼以重新命名這些檔案。 所有參照\（在DITA map和主題中\）都會自動處理，因為它們會根據平面資料夾結構中檔案的新位置進行更新。 如果設為false，則會維持資料夾結構在ZIP檔案中的原樣。 如果DITA map參照來自多個位置的檔案，則所有這些位置也會在ZIP檔案中建立。 還原ZIP檔案時，會在目的地位置建立精確的資料夾結構。<br>此引數的預設值為false。 |

**傳回**：
Zip檔案的Node已包裝在`CompletableFuture`類別中。 使用者可以繼續以非同步方式處理它，並且可以在需要節點時使用未來的`.get()`方法來封鎖執行緒。 傳回的值也可能以錯誤結束，而且可以使用`.exceptionally()`方法處理。

## 取得基準線清單

``getBaselineList``方法會擷取特定DITA map存在的所有基準清單。

**語法**：

```JAVA
public static List<HashMap<String,String>> getBaselineList( 
                  javax.jcr.Session session, 
                  String sourcePath)
                  throws javax.jcr.RepositoryException
```

**引數**：

| 名稱 | 類型 | 說明 |
|----|----|-----------|
| `session` | javax.jcr.Session | 有效的JCR工作階段。 |
| `sourcePath` | 字串 | 要擷取基準線資訊之DITA map檔案的路徑\(在AEM存放庫中\)。 |

**傳回**：
`HashMap`物件的清單。 每個`HashMap`物件代表一個基準線，並包含基準線的名稱和標題。

**例外狀況**：
擲回``javax.jcr.RepositoryException``。

## 取得條件預設集清單

``getConditionalPresetList``方法會擷取特定DITA map存在的所有條件預設集清單。

**語法**：

```JAVA
public static List<HashMap<String,String>> getConditionalPresetList (
                  javax.jcr.Session session,
                  String sourcePath)
                  throws javax.jcr.RepositoryException
```

**引數**：

| 名稱 | 類型 | 說明 |
|----|----|-----------|
| `session` | javax.jcr.Session | 有效的JCR工作階段。 |
| `sourcePath` | 字串 | 要擷取條件預設集資訊之DITA map檔案的路徑\(在AEM存放庫中\)。 |

**傳回**：
`HashMap`物件的清單。 每個`HashMap`物件代表一個條件式預設集，並包含條件式預設集的名稱和標題。

**例外狀況**：
擲回``javax.jcr.RepositoryException``。

## 取得條件預設集的DITAVAL檔案資訊

``getDitavalFromConditionalPreset``方法會擷取與指定DITA map的條件預設集相對應的DITAVAL檔案路徑。

**語法**：

```JAVA
public static String getDitavalFromConditionalPreset
    (Session session,
    String sourcePath, 
    String cpName) throws RepositoryException
```

**引數**：

| 名稱 | 類型 | 說明 |
|----|----|-----------|
| `session` | javax.jcr.Session | 有效的JCR工作階段。 |
| `sourcePath` | 字串 | 要擷取DITAVAL檔案之DITA map檔案的路徑\(在AEM存放庫中\)。 |
| `cpName` | 字串 | DITA map中要擷取DITAVAL檔案的條件預設集名稱。 |

**傳回**：
與DITA map檔案中定義的條件預設集相對應的DITAVAL檔案路徑。

## 取得節點的所有相依性

``getAllDependencies``方法會傳回指定節點的所有相依性。

**語法**：

```JAVA
public static List
<Node> getAllDependencies 
(Node rootNode) throws GuidesApiException
```

**引數**：

| 名稱 | 類型 | 說明 |
|----|----|-----------|
| `rootNode` | javax.jcr.Node | 要擷取其所有相依性的根節點。 |

**傳回**：
包含根節點所有相依性的節點清單。
