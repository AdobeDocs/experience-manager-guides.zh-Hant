---
title: 用於輸出管理的REST API
description: 瞭解輸出管理的REST API
exl-id: dab654f5-555d-4a89-bc94-55b1e938f255
feature: Rest API Output Management
role: Developer
level: Experienced
source-git-commit: 0513ecac38840a4cc649758bd1180edff1f8aed1
workflow-type: tm+mt
source-wordcount: '1175'
ht-degree: 0%

---

# 用於輸出管理的REST API {#id175UB30E05Z}

下列REST API可用於管理AEM Guides中的輸出。

## 取得DITA map的所有輸出預設集 {#get-output-presets-dita-map}

一種POST方法，可擷取為DITA map設定的所有輸出預設集。

**要求URL**：
http://*&lt;aem-guides-server\>*： *&lt;連線埠號碼\>*/bin/publishlistener

**引數**：\
|名稱|型別|必要|說明|
---------------------------
|`:operation`|字串|是|要呼叫之作業的名稱。 此引數的值為`getalloutputs`.<br> **注意：**值不區分大小寫。|
|`sourcePath`|字串|是|DITA map檔案的絕對路徑。|

**回應值**：
傳回JSON輸出預設集物件的陣列，每個物件包含下列元素：

| 元素 | 說明 |
|-------|-----------|
| `outputName` | 輸出預設集的名稱。 輸出名稱在其定義的DITA map範圍內是唯一的。 |
| `outputType` | 使用此預設集產生的輸出型別，例如AEM Site、PDF、EPUB或其他。 可用的選項包括：<br>-   AEMSITE <br>-   PDF<br>-   HTML5 <br>-   ePub<br>-   自訂 |
| `outputTitle` | 輸出預設集設定的描述性名稱。 這可用來定義輸出預設集的「設定名稱」屬性值。 |
| `ditaValPathList` | 要用來產生所要輸出的DITAVAL檔案路徑陣列。 |
| `targetPath` | 發佈或儲存輸出的路徑。 |
| `siteName` | *\(針對AEM網站輸出\)* AEM網站的名稱。 |
| `templatePath` | *\(針對AEM網站輸出\)*&#x200B;範本節點的路徑，用來產生所要的輸出。 |
| `searchScope` | 指定搜尋操作的範圍。 此引數的值必須設定為`local`。 |
| `generateTOC` | *\(用於AEM網站輸出\)*&#x200B;指定是否產生\(true\)目錄\(false\)。 |
| `generateBreadcrumbs` | *\(用於AEM網站輸出\)*&#x200B;指定是否產生階層連結\(true\) \(false\)。 |
| `overwriteStrategy` | *\(用於AEM站台輸出\)*&#x200B;指定是否覆寫目的地的檔案\(true\)\(false\)。 |
| `pdfGenerator` | 指定要使用的PDF產生引擎。 可能的值為： <br>-   DITAOT <br>-   FMPS |

>[!NOTE]
>
> 不再支援`DitaValPath`專案。

## 建立輸出預設集

一種為DITA map建立新輸出預設集的POST方法。

**要求URL**：
http://*&lt;aem-guides-server\>*： *&lt;連線埠號碼\>*/bin/publishlistener

**引數**：
|名稱|型別|必要|說明|
---------------------------
|`:operation`|字串|是|要呼叫之作業的名稱。 此引數的值為``createoutput``.<br> **注意：**值不區分大小寫。|
|`sourcePath`|字串|是|DITA map檔案的絕對路徑。|
|`outputTitle`|字串|是|輸出預設集設定的描述性名稱。 這可用來定義輸出預設集之Setting Name屬性的值。<br> **注意：**建立新的輸出預設集時，後端系統從給定的標題為輸出預設集驅動唯一的名稱。|
|`outputType`|字串|是|使用此預設集產生的輸出型別，例如AEM Site、PDF、EPUB或其他。 可用的選項包括：<br>-   AEMSITE <br>-   PDF<br>-   HTML5 <br>-   ePub<br>-   自訂|

**回應值**：
|元素|說明|
-------|-----------|
|`outputName`|新建立的輸出預設集的唯一名稱。 此名稱衍生自`outputTitle`引數的值。|

## 儲存輸出預設集

一種POST方法，可儲存輸出預設集中所做的變更。

**要求URL**：
http://*&lt;aem-guides-server\>*： *&lt;連線埠號碼\>*/bin/publishlistener

**引數**：
|名稱|型別|必要|說明|
---------------------------
|`:operation`|字串|是|要呼叫之作業的名稱。 此引數的值為``saveoutput``.<br> **注意：**值不區分大小寫。|
|`sourcePath`|字串|是|DITA map檔案的絕對路徑。|
|`outputObj`|字串|是|包含正在更新的輸出預設集屬性的JSON物件。 `outputObj.outputName`屬性包含要更新的輸出預設集名稱。 如需JSON物件的格式，請參閱[取得DITA map的所有輸出預設集](#get-output-presets-dita-map)中的&#x200B;**回應值**&#x200B;表格。|

**回應值**：
傳回HTTP 200 \(Successful\)回應。

## 取得特定的輸出預設集

一種POST方法，可擷取現有的輸出預設集。

**要求URL**：
http://*&lt;aem-guides-server\>*： *&lt;連線埠號碼\>*/bin/publishlistener

**引數**：
|名稱|型別|必要|說明|
---------------------------
|`:operation`|字串|是|要呼叫之作業的名稱。 此引數的值為`getoutput`。 <br>**注意：**值不區分大小寫。|
|`sourcePath`|字串|是|DITA map檔案的絕對路徑。|
|`outputName`|字串|是|必須擷取其詳細資訊的輸出預設集名稱。|

**回應值**：
|元素|說明|
-------|-----------|
|`outputName`|輸出預設集名稱。 輸出名稱在其定義的DITA map範圍內是唯一的。|
|`outputType`|使用此預設集產生的輸出型別，例如AEM Site、PDF、EPUB或其他。 可用的選項包括：<br>-   AEMSITE <br>-   PDF<br>-   HTML5 <br>-   ePub<br>-   自訂<br>|
|`outputTitle`|輸出預設集設定的描述性名稱。 這可用來定義輸出預設集的「設定名稱」屬性值。|
|`ditaValPathList`|要用來產生所要輸出的DITAVAL檔案路徑陣列。|
|`targetPath`|發佈或儲存輸出的路徑。|
|`siteName`|\(針對AEM網站輸出\)AEM網站的名稱。|
|`siteTitle`|\(針對AEM網站輸出\) AEM網站的標題。|
|`templatePath`|\(針對AEM網站輸出\)要用來產生所要輸出的範本節點路徑。|
|`searchScope`|指定搜尋操作的範圍。 此引數的值必須設定為`local`。|
|`generateTOC`|\(用於AEM網站輸出\)指定是否產生\(true\)目錄\(false\)。|
|`generateBreadcrumbs`|\(用於AEM網站輸出\)指定是否產生階層連結\(true\) \(false\)。|
|`overwriteFiles`|\(用於AEM網站輸出\)指定是否覆寫目的地的檔案\(true\) \(false\)。|
|`pdfGenerator`|指定要使用的PDF產生引擎。 可能的值為： <br>-   DITAOT <br>-   FMPS|

>[!NOTE]
>
> 不再支援`DitaValPath`專案。

## 產生輸出

使用一或多個輸出預設集產生輸出的GET方法。

**要求URL**：
http://*&lt;aem-guides-server\>*： *&lt;連線埠號碼\>*/bin/publishlistener

**引數**：
|名稱|型別|必要|說明|
---------------------------
|`operation`|字串|是|要呼叫之作業的名稱。 此引數的值為`GENERATEOUTPUT`.<br> **注意：**值區分大小寫。|
|`source`|字串|是|DITA map檔案的絕對路徑。|
|`outputName`|字串|是|要用來產生輸出的輸出預設集名稱。 可使用垂直號\(「\|」\)分隔符號（例如`aemsite|pdfoutput`）指定多個輸出預設集。|

**回應值**：
傳回HTTP 200 \(Successful\)回應。

## 產生增量輸出

使用一或多個輸出預設集為AEM Site產生增量輸出的GET方法。

**要求URL**：
http://*&lt;aem-guides-server\>*： *&lt;連線埠號碼\>*/bin/publishlistener

**引數**：
|名稱|型別|必要|說明|
---------------------------
|`operation`|字串|是|要呼叫之作業的名稱。 此引數的值為`INCREMENTALPUBLISH`。 <br>**注意：**值區分大小寫。|
|`contentPath`|JSON|是|DITA map檔案和主題檔案的絕對路徑，以及輸出預設集的名稱。 使用下列範例作為建置區塊：|

```XML
{
   {   
   "ditamap": 
      "/content/dam/sample/sample.ditamap",   
   "topics": [     
      "/content/dam/sample/topic1.xml",     
      "/content/dam/sample/topic2.xml"   
         ],   
   "fullMaps": [     
      "/content/dam/sample/submap.ditamap"   
      ],   
   "maps": [     
      "/content/dam/sample/keyspace.ditamap"   
      ],   
   "outputs": [     
      "aemsite"   
      ] 
   }
}
```

- `ditamap`屬性採用用來產生輸出的DITA map的絕對路徑。
- `topics`屬性需要一系列已更新且需要重新發佈的主題。
- `fullMaps`屬性包含增量輸出產生所需對應檔案\（如區塊子對應\）的路徑及其主題。
- `maps`屬性包含擷取到磁碟上的對應檔案\（用於解析鍵區參考\）的路徑（不含主題）。
- `outputs`屬性採用用來產生輸出的輸出預設集名稱陣列。

**回應值**：
傳回HTTP 200 \(Successful\)回應。

## 刪除輸出預設集

刪除輸出預設集的POST方法。

**要求URL**：
http://*&lt;aem-guides-server\>*： *&lt;連線埠號碼\>*/bin/publishlistener

**引數**：
|名稱|型別|必要|說明|
---------------------------
|`:operation`|字串|是|要呼叫之作業的名稱。 此引數的值為`deleteoutput`.<br> **注意：**值不區分大小寫。|
|`sourcePath`|字串|是|DITA map檔案的絕對路徑。|
|`outputName`|字串|是|要刪除的輸出預設集名稱。|

**回應值**：
傳回HTTP 200 \(Successful\)回應。
