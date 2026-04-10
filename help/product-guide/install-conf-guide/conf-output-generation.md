---
title: 設定輸出產生設定
description: 瞭解如何設定輸出產生設定
feature: Output Generation
role: Admin
level: Experienced
source-git-commit: 6f3f05419f4f5cdd45ab580cdee6fa869f20f01d
workflow-type: tm+mt
source-wordcount: '3314'
ht-degree: 1%

---

# 設定輸出產生設定 {#id181AI0B0E30}

AEM Guides提供許多設定選項，供您自訂輸出產生流程。 本主題涵蓋可協助您設定輸出產生程式的所有設定和自訂。

## 在DITA map圖示板上設定基準線標籤 {#id223MD0D0YRM}

下列標籤會提供根據您的Experience Manager Guides設定在DITA Map控制面板上隱藏「基線」標籤的指示： Cloud Service或On-Premise。

>[!BEGINTABS]

>[!TAB Cloud Service]

1. 使用[組態覆寫](download-install-config-override.md#)中提供的指示來建立組態檔。
1. 在組態檔中，提供下列\(property\)詳細資訊，以設定地圖圖示板上的基準線標籤。

| PID | 屬性索引鍵 | 屬性值 |
|---|------------|--------------|
| `com.adobe.fmdita.config.ConfigManager` | `hide.tabs.baseline` | 布林值\(`true/false`\)。**預設值**： `true` |

>[!NOTE]
>
> 預設會啟用此設定，且地圖控制面板上無法使用「基準線」標籤。

>[!TAB 內部部署]

1. 開啟Adobe Experience Manager Web主控台設定頁面。

   存取設定頁面的預設URL為：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜尋並按一下&#x200B;**com.adobe.fmdita.config.ConfigManager**&#x200B;套件。

1. 選取&#x200B;**隱藏基準線索引標籤**&#x200B;選項。

1. 按一下&#x200B;**儲存**。

>[!NOTE]
>
> 此設定預設為停用，且可在地圖控制面板上使用「基準」標籤。

>[!ENDTABS]


## 在現有AEM網站中設定混合發佈 {#id1691I0V0MGR}

如果您有包含DITA內容的AEM網站，您可以設定AEM網站輸出，將DITA內容發佈至網站內預先定義的位置。 例如，在以下AEM網站頁面熒幕擷圖中，`ditacontent`節點已保留以儲存DITA內容：

![](assets/publish-in-aem-site.png)

頁面中的其餘節點會直接從AEM網站編輯器撰寫。 將發佈設定設為發佈DITA內容至預先定義的位置，可確保AEM Guides發佈程式不會修改任何現有的非DITA內容。

您需要在現有網站上執行下列設定，以允許將DITA內容發佈到預先定義的節點：

- 設定網站的範本屬性

- 在您的網站中新增節點以發佈DITA內容


下列標籤提供根據您的Experience Manager Guides設定來設定現有網站的範本屬性的指示： Cloud Service或內部部署。

>[!BEGINTABS]

>[!TAB Cloud Service]

1. 使用封裝管理員來下載/libs/fmdita/config/templates/default檔案。

   >[!NOTE]
   >
   > 請勿在`libs`節點中使用預設組態檔中的任何自訂專案。 您必須在`libs`節點中建立`apps`節點的覆蓋，並僅更新`apps`節點中的必要檔案。

1. 新增下列屬性：

   | 屬性名稱 | 類型 | 值 |
   |-------------|----|-----|
   | `topicContentNode` | 字串 | 指定要發佈DITA內容的節點名稱。 例如，AEM Guides發佈DITA內容的預設節點為： <br> `jcr:content/contentnode` |
   | `topicHeadNode` | 字串 | 指定要儲存DITA內容的中繼資料資訊的節點名稱。 例如，AEM Guides儲存中繼資料資訊的預設節點為： <br> `jcr:content/headnode` |


下次當您使用網站的範本設定發佈任何DITA內容時，該內容會發佈到`topicContentNode`和`topicHeadNode`屬性中指定的節點。

>[!TAB 內部部署]

1. 登入AEM並開啟CRXDE Lite模式。

1. 導覽至您網站的範本設定節點。 例如，AEM Guides會將預設範本設定儲存在下列節點中：

   `/libs/fmdita/config/templates/default`

   >[!NOTE]
   >
   > 請勿在`libs`節點中使用預設組態檔中的任何自訂專案。 您必須在`libs`節點中建立`apps`節點的覆蓋，並僅更新`apps`節點中的必要檔案。

1. 新增下列屬性：

   | 屬性名稱 | 類型 | 值 |
   |-------------|----|-----|
   | `topicContentNode` | 字串 | 指定要發佈DITA內容的節點名稱。 例如，AEM Guides發佈DITA內容的預設節點為： <br>`jcr:content/contentnode` |
   | `topicHeadNode` | 字串 | 指定要儲存DITA內容的中繼資料資訊的節點名稱。 例如，AEM Guides儲存中繼資料資訊的預設節點為： <br>`jcr:content/headnode` |


下列熒幕擷圖顯示新增到AEM Guides預設範本節點中的屬性：

![](assets/add-content-node.png){width="800" align="left"}

下次當您使用網站的範本設定發佈任何DITA內容時，該內容會發佈到`topicContentNode`和`topicHeadNode`屬性中指定的節點。

不過，針對現有站台，您必須手動新增`topicContentNode`和`topicHeadNode`節點。

執行以下步驟，將所需節點新增至現有站台：

1. 登入AEM並開啟CRXDE Lite模式。

1. 在您的網站節點中找到`jcr:content`。

1. 新增與您在網站的範本設定中指定的名稱相同的`topicContentNode`和`topicHeadNode`節點。

>[!ENDTABS]

## 設定基本輸出位置以進行發佈

下列標籤提供根據Experience Manager Guides設定設定來設定基本輸出位置的指示： Cloud Service或內部部署。

>[!BEGINTABS]

>[!TAB Cloud Service]

1. 使用[組態覆寫](download-install-config-override.md)中提供的指示來建立組態檔。

1. 在組態檔中，提供下列（屬性）詳細資訊，以設定基礎輸出位置：

   | PID | 屬性索引鍵 | 屬性值 |
   |---|---|---|
   | `com.adobe.fmdita.config.ConfigManager` | `base.output.path` | **預設值：** &quot;/content/dam/fmdita-outputs&quot; |

>[!TAB 內部部署]

1. 開啟Adobe Experience Manager Web主控台設定頁面。

   存取設定頁面的預設URL為：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜尋並選取&#x200B;*com.adobe.fmdita.config.ConfigManager*&#x200B;套件。

1. 更新屬性&#x200B;**基本輸出位置**&#x200B;以指定AEM存放庫中的預設路徑，在發佈後會在此儲存PDF。 此外，如果輸入的路徑無效，它會自動還原為預設路徑： `/content/dam/fmdita-outputs`。

1. 按一下&#x200B;**儲存**。

>[!ENDTABS]

## 透過DITA-OT在發佈輸出中使用中繼資料 {#id191LF0U0TY4}

AEM Guides提供在使用DITA-OT發佈輸出時傳遞自訂中繼資料的方法。 作為管理員和發佈者，您需要執行以下任務以在發佈輸出中設定和使用自訂中繼資料：

- 以管理員身分，在系統中新增必要的中繼資料，使其可在DITA map的「屬性」頁面上使用。

- 作為管理員，在中繼資料清單中新增自訂中繼資料，使其顯示在DITA map主控台中。

- 作為發行者，使用DITA map設定並新增自訂中繼資料，並產生所需的輸出。


若要在系統中新增必要的中繼資料，請執行下列步驟：

1. 以管理員身分登入Adobe Experience Manager。

1. 按一下頂端的Adobe Experience Manager連結，然後選擇&#x200B;**工具**。

1. 從工具清單中選取&#x200B;**Assets**。

1. 按一下&#x200B;**中繼資料結構**&#x200B;圖磚。

   此時會顯示「中繼資料結構Forms」頁面。

1. 從清單中選取&#x200B;**預設**&#x200B;表單。

   >[!NOTE]
   >
   > DITA map的「屬性」頁面上顯示的屬性取自此表單。

1. 按一下「**編輯**」。

1. 新增您要在發佈的輸出中使用的自訂中繼資料。 例如，我們將使用下列步驟新增對象中繼資料：

   1. 從&#x200B;**建置表單**&#x200B;元件清單中，將&#x200B;**單行文字**&#x200B;元件拖放至表單上。

   2. 選取新欄位以開啟欄位的&#x200B;**設定**。

   3. 在&#x200B;**欄位標籤**&#x200B;中，輸入中繼資料名稱 — Audience。

   4. 在&#x200B;**對應至屬性**&#x200B;設定中，指定。/jcr:content/metadata/&lt;中繼資料的名稱\>。 例如我們的範例，我們將其設為。/jcr:content/metadata/audience。

   使用這些步驟，新增所有必要的中繼資料引數。

1. 按一下&#x200B;**儲存**。


現在，所有DITA map的「屬性」頁面中都會顯示新引數。

![](assets/properties-page-custom-metadata.PNG)

接下來，您需要在DITA map主控台中提供自訂中繼資料。 下列標籤會提供指示，讓您根據您的Experience Manager Guides設定，在DITA map虛板上提供自訂中繼資料：Cloud Service或內部部署。

>[!BEGINTABS]

>[!TAB Cloud Service]

1. 使用套件管理器來存取metadataList檔案，該檔案可在您的Cloud Manager Git存放庫中的下列位置取得：

   /libs/fmdita/config/metadataList

   >[!NOTE]
   >
   > metadataList檔案包含顯示在地圖儀表板中DITA map的&#x200B;**屬性**&#x200B;下拉式清單中的屬性清單。 依預設，此檔案中列出四個屬性：docstate、dc:language、dc:description和dc:title。

1. 新增您在中繼資料結構Forms頁面中新增的自訂中繼資料。 例如，將對象引數新增至預設清單的結尾。

>[!TAB 內部部署]

1. 登入AEM並開啟CRXDE Lite模式。

1. 存取以下位置可用的metadataList檔案：

   /libs/fmdita/config/metadataList

   >[!NOTE]
   >
   > metadataList檔案包含顯示在地圖儀表板中DITA map的&#x200B;**屬性**&#x200B;下拉式清單中的屬性清單。 依預設，此檔案中列出四個屬性：docstate、dc:language、dc:description和dc:title。

1. 新增您在中繼資料結構Forms頁面中新增的自訂中繼資料。 例如，將對象引數新增至預設清單的結尾。

1. 按一下&#x200B;**「儲存全部」**。

>[!ENDTABS]

現在，自訂中繼資料會顯示在DITA map主控台的&#x200B;**屬性**&#x200B;下拉式清單中。

最後，身為「發佈者」，您需要在發佈的輸出中包含自訂中繼資料。 若要在產生輸出時處理自訂中繼資料，請執行下列步驟：

1. 在Assets UI中，導覽至您要發佈的DITA map。

1. 選取DITA map檔案並開啟其屬性頁面。

1. 在「屬性」頁面上，指定自訂中繼資料的值。 例如，我們為對象引數指定了External值。

   ![](assets/properties-page-custom-metadata-value.png)

1. 按一下「**儲存並關閉**」。

1. 按一下DITA map檔案以開啟DITA map主控台。

1. 在&#x200B;**輸出預設集**&#x200B;索引標籤中，選取您要用來產生輸出的輸出預設集。

1. 按一下「**編輯**」。

1. 從&#x200B;**屬性**&#x200B;下拉式清單中，選取您要傳遞給發佈程式的屬性。

   ![](assets/props-in-publish-output.PNG)


選取的屬性/中繼資料會傳遞至發佈程式，並可在最終輸出中使用。

### 驗證傳遞至DITA-OT以進行處理的中繼資料（僅適用於Cloud Service）

為了驗證傳遞至DITA-OT的中繼資料值，可以使用使用雲端就緒jar的本機環境。 由於我們無法在雲端上存取本機檔案系統，因此驗證中繼資料檔案的唯一方式是透過雲端就緒的jar。

- 檔案名稱： metadata.xml
- 檔案位置： crx-quickstart/profiles/ditamaps/&lt;ditamap-1234\>

  若要存取metadata.xml：

   - 登入執行AEM執行個體的伺服器位置。
   - 移轉至crx-quickstart/profiles/ditamaps/&lt;new-created-directory-name\>/metadata.xml。
- 範例檔案格式：

  **metadata.xml**

  ```XML
  <?xml version="1.0" encoding="UTF-8" standalone="no"?>
  <root>
     <Path id="/absolutePath/sampleMap.ditamap">
        <metadata>
           <meta isArray="false" key="dc:description">This is a file</meta>
           <meta isArray="false" key="dc:title">Myfile</meta>
           <meta isArray="true" key="multivalueText">One;Two;Three</meta>
        </metadata>
     </Path>
     <Path id="/absolutePath/sampleTopic.dita">
        <metadata>
           <meta isArray="false" key="dc:description">description for the accountability</meta>
           <meta isArray="false" key="dc:title">accountability title</meta>
           <meta isArray="true" key="multivalueText">value1</meta>
        </metadata>
     </Path>
  </root>
  ```


- isArray：布林屬性，定義中繼資料是否為多值\(Array\)。 值以分號分隔。
- 路徑ID：暫時目錄下所儲存檔案的絕對路徑。

>[!NOTE]
>
> 如果檔案不存在特定的中繼資料，則含有索引鍵的&lt;meta\>標籤將不會顯示該檔案在metadata.xml檔案中的屬性。

## 設定DITA-OT命令列引數欄位以接受根對應中繼資料（僅適用於Cloud Service）

若要使用DITA-OT命令列引數欄位來傳遞根對映中繼資料，請執行下列步驟：

1. 使用[組態覆寫](download-install-config-override.md#)中提供的指示來建立組態檔。
1. 在組態檔案中，提供下列\(property\)詳細資訊，以設定預設集中的DITA-OT命令列引數欄位：

| PID | 屬性索引鍵 | 屬性值 |
|---|------------|--------------|
| `com.adobe.fmdita.config.ConfigManager` | `pass.metadata.args.cmd.line` | 布林值\(`true/false`\)。**預設值**： `true` |

- 將屬性值設定為&#x200B;**true**&#x200B;可啟用DITA-OT命令列功能，讓您透過DITA-OT命令列傳遞中繼資料。
- 將屬性值設定為&#x200B;**false**&#x200B;會停用DITA-OT命令列功能。 然後，您可以使用預設集中的「屬性」欄位來傳遞中繼資料。

## 自訂DITA map主控台 {#id188HC08M0CZ}

AEM Guides可讓您彈性擴充DITA map主控台的功能。 例如，如果您有一組與AEM Guides中可用的報表不同，您可以將這類報表新增至地圖主控台。 若要自訂地圖主控台，您必須建立AEM使用者端程式庫\（或ClientLib\），其中包含執行所需功能所需的程式碼。

>[!NOTE]
>
> 不建議直接修改頁面元件，因為產品的新版本會加以覆寫。

AEM Guides提供用於自訂地圖主控台的`apps.fmdita.dashboard-extn`類別。 每當載入地圖主控台時，就會執行並載入在`apps.fmdita.dashboard-extn`類別下建立的功能。

>[!NOTE]
>
> 如需建立AEM使用者端資料庫的詳細資訊，請參閱[使用使用者端資料庫](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/full-stack/clientlibs.html?lang=en)。

## 在產生輸出期間處理影像轉譯 {#id177BF0G0VY4}

AEM隨附一組預設工作流程和媒體控制代碼以處理資產。 在AEM中，有預先定義的工作流程可處理最常見MIME型別的資產處理。 一般而言，AEM會針對您上傳的每個影像，以二進位格式建立相同的多個轉譯。 這些轉譯可能大小不同、解析度不同、加上浮水印或其他已變更的特性。 如需AEM如何處理資產的詳細資訊，請參閱AEM檔案中的[使用媒體處理常式和工作流程處理Assets](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/asset-microservices-overview.html?lang=en)。

AEM Guides可讓您設定在為檔案產生輸出時要使用的影像轉譯。 例如，您可以選擇其中一個預設影像轉譯，或建立並使用相同的影像轉譯來發佈檔案。 發行檔案的影像轉譯對應儲存在`/libs/fmdita/config/ **renditionmap.xml**`檔案中。 `renditionmap.xml`檔案的片段如下：

>[!NOTE]
>
> 建議您在`renditionmap.xml`資料夾中為所有自訂專案建立`apps`檔案的復本。

```XML
<renditionmap>
   <mapelement>
      <mimetype>image/png</mimetype>
      <rendition output="AEMSITE">cq5dam.web.1280.1280.jpeg</rendition>
      <rendition output="PDF">original</rendition>
      <rendition output="HTML5">cq5dam.web.1280.1280.jpeg</rendition>
      <rendition output="HTML5" outputName="ditahtml5">cq5dam.thumbnail.319.319.png</rendition>
      <rendition output="EPUB">cq5dam.web.1280.1280.jpeg</rendition>
      <rendition output="CUSTOM">cq5dam.web.1280.1280.jpeg</rendition>
   </mapelement>
...
</renditionmap>
```

`mimetype`專案指定檔案格式的MIME型別。 `rendition output`專案指定輸出格式的型別以及應該用於發佈指定輸出的轉譯\（例如，`cq5dam.web.1280.1280.jpeg`\）的名稱。 您可以指定用於所有受支援輸出格式的影像轉譯 — AEMSITE、PDF、HTML5、EPUB和CUSTOM。

如果您要為輸出預設集指定不同的影像轉譯，可以使用`outputName`屬性（其值設定為預設集的標題）來定義相同輸出型別下特定輸出預設集的自訂轉譯。 當您因應不同發佈情境而需要不同的影像大小或格式時，此功能會很有用。

例如：


```XML
<renditionmap>
   <mapelement>
      <mimetype>image/png</mimetype>
      
      <rendition output="HTML5">cq5dam.web.1280.1280.jpeg</rendition>
      <rendition output="HTML5" outputName="ditahtml5">cq5dam.thumbnail.319.319.png</rendition>
      
   </mapelement>
...
</renditionmap>
```

在上述轉譯中，當`outputName`屬性設定為`ditahtml5` （預設集標題）時，`ditahtml5`預設集會使用縮圖影像`cq5dam.thumbnail.319.319.png`。 如果未指定`outputName`屬性，則所有HTML5輸出都會使用較大的影像`cq5dam.web.1280.1280.jpeg`。

如果指定的轉譯不存在，AEM Guides發佈程式會先尋找指定影像的Web轉譯。 如果找不到網頁轉譯，則會使用影像的原始轉譯。

>[!NOTE]
>
> 這些影像轉譯只會控制輸出產生。 當您開啟檔案以進行預覽或檢閱時，會使用影像的Web轉譯。

## 設定輸出記錄的自動永久刪除期間 {#id19AAI070V8Q}

產生輸出時，會建立輸出與輸出記錄。 對於大型DITA map，這些記錄可能會佔用存放庫中的大量空間。 依預設，記錄檔會儲存在存放庫的下列位置：

`/var/dxml/metadata/outputHistory`

在一段時間內，所有記錄檔的集體大小可能會達到GB。 AEM Guides可讓您設定將這些記錄檔保留在存放庫中的時段。 在指定的時段後，記錄以及輸出產生歷史記錄會從存放庫中刪除。

>[!NOTE]
>
> 輸出產生歷史記錄是「輸出」標籤中「產生的輸出」清單中的記錄專案。

設定歷史記錄清除功能會影響儲存庫中所有DITA map的輸出產生。 在DITA map的「輸出」標籤中，在指定的天數之後，以及在設定中指定的時間清除歷史記錄。

>[!NOTE]
>
> 移除記錄檔和輸出產生歷程記錄對產生的輸出沒有任何影響。

下列標籤會提供根據您的Experience Manager Guides設定，設定清除輸出歷史記錄和記錄的日期和時間：Cloud Service或內部部署。

>[!BEGINTABS]

>[!TAB Cloud Service]

使用[組態覆寫](download-install-config-override.md#)中提供的指示來建立組態檔。 在設定檔中，提供下列\(property\)詳細資訊，以設定清除輸出歷史記錄和記錄檔的日期和時間：

| PID | 屬性索引鍵 | 屬性值 |
|---|------------|--------------|
| `com.adobe.fmdita.config.ConfigManager\|output.history.purgeperiod` | 指定清除輸出歷史記錄以及輸出日誌的天數。 若要停用此功能，請將此屬性設為0。每天在指定的時間，針對此屬性指定天數之前產生的輸出執行清除程式。 | **預設值**： 5 |
| `output.history.purgetime` | 指定開始永久刪除處理的時間。 | **預設值**： 0:00 \（或12:00午夜\） |

>[!TAB 內部部署]

1. 開啟Adobe Experience Manager Web主控台設定頁面。

   存取設定頁面的預設URL為：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜尋並按一下&#x200B;**com.adobe.fmdita.config.ConfigManager**&#x200B;套件。

1. 在&#x200B;**輸出歷程記錄清除期間**&#x200B;屬性中，指定輸出歷程記錄以及輸出記錄清除的天數。 預設會設為5天。 如果您要停用此功能，則將此屬性設定為0。

1. 在&#x200B;**輸出歷程記錄清除時間**&#x200B;屬性中，指定清除程式的起始時間。 預設為0:00 \（或12:00午夜\）。 每天這個時間，清除程式都會在&#x200B;**輸出歷程記錄清除期間**&#x200B;屬性中指定的天數之前產生的輸出上執行。

   >[!NOTE]
   >
   > 依預設，清除功能會在每午夜的5天前輸出上執行。

1. 按一下&#x200B;**儲存**。

>[!ENDTABS]

## 變更最近產生的輸出清單限制 {#id1679JH0H0O2}

您可以變更DITA map在「輸出」標籤中顯示的已產生輸出最大數目。

>[!BEGINTABS]

>[!TAB Cloud Service]

使用[組態覆寫](download-install-config-override.md#)中提供的指示來建立組態檔。 在設定檔案中，提供下列\(property\)詳細資訊，以變更要在清單中顯示的輸出數量：

| PID | 屬性索引鍵 | 屬性值 |
|---|------------|--------------|
| `com.adobe.fmdita.config.ConfigManager` | `output.historylimit` | 整數值。<br> **預設值**： 25 |

>[!TAB 內部部署]

依預設，會顯示最後25個產生的輸出清單。 若要變更要在清單中顯示的輸出數目，請更新&#x200B;**組合中的**&#x200B;輸出清單限制`com.adobe.fmdita.config.ConfigManager`設定。

>[!ENDTABS]

>[!TIP]
>
> 如需有關使用輸出歷程記錄的最佳實務，請參閱&#x200B;*最佳實作指南*&#x200B;中的[輸出歷程記錄](https://helpx.adobe.com/content/dam/help/en/xml-documentation-solution/cs-mar-22/Adobe-Experience-Manager-Guides_Best-Practices_EN.pdf)區段。

## 輸出產生效能最佳化（僅適用於內部部署） {#id176LB050VUI}

AEM Guides可讓您設定輸出產生程式集區大小，以控制同時執行的輸出產生程式數目。 依照預設，處理集區大小會設定為您的系統中可用的處理核心數目加上一個。 如果您想要循序發佈，可將此值變更為1。 在這種情況下，會執行第一個發佈任務，並將下一個發佈任務儲存在發佈佇列中。

若要變更輸出產生處理集區大小，請更新&#x200B;**組合中的**&#x200B;產生集區大小`com.adobe.fmdita.publish.manager.PublishThreadManagerImpl`設定。

## 設定FrameMaker Publishing Server （僅適用於內部部署） {#id1678G0Z0TN6}

您可以使用FrameMaker Publishing Server \(FMPS\)產生DITA內容的輸出。 設定FMPS可讓您以FMPS支援的多種格式產生輸出。

>[!NOTE]
>
> 若要使用FMPS產生輸出，您必須設定FMPS伺服器。 如需安裝和設定詳細資訊，請參閱FrameMaker Publishing Server使用手冊。

若要設定AEM Guides使用FMPS，請在Web主控台中更新`com.adobe.fmdita.config.ConfigManager`套件的下列屬性。

>[!NOTE]
>
> 存取http://&lt;伺服器名稱\>：&lt;連線埠\>/system/console/configMgr URL以開啟Web主控台。

| 屬性 | 說明 |
|--------|-----------|
| FrameMaker Publishing Server登入網域 | 指定託管FrameMaker Publishing Server的網域名稱或工作群組名稱。 根據FMPS版本，提供網域名稱為:-   **FMPS 2020**： IP位址為192.168.1.101 <br>- **FMPS 2019和較舊版本**： IP位址或網域名稱 |
| FRAMEMAKER PUBLISHING SERVER URL | 指定FrameMaker Publishing Server的URL 根據FMPS版本，提供FMPS URL為：<br>- **FMPS 2020**： `http://<fmps_ip>:<port>` \(http://192.168.1.101:7000\) <br> - **FMPS 2019及舊版**： `http://<fmps_ip>:<port>/fmserver/v1/` |
| FMPS版本 | 指定FrameMaker Publishing Server的版本號碼。 根據FMPS版本，提供下列版本資訊： <br>- **FMPS 2020**： 2020 <br> - **FMPS 2019和較舊版本**： 2019或2017 |
| FrameMaker Publishing Server使用者名稱和密碼 | 指定存取FrameMaker Publishing Server的使用者名稱和密碼。 |
| fmps逾時 | \（*選擇性*\）指定AEM Guides等待FrameMaker Publishing Server回應的時間\（以秒為單位）。 如果在指定時間內未收到任何回應，AEM Guides會終止發佈工作，且工作會標籤為失敗。 <br>預設值： 300秒\（5分鐘\） |
| 外部AEM URL | *\(Optional\)* AEM URL，FrameMaker Publishing Server會在此放置產生的輸出檔案。 例如，`http://<server-name>:<port>/`。 |
| AEM管理員使用者名稱與密碼 | *\(Optional\)* AEM安裝程式管理員的使用者名稱和密碼。 FrameMaker Publishing Server將使用此資料與AEM通訊。 |
| FMPS工作執行等待逾時 | 此設定僅適用於FMPS 2020。 指定時間\（以秒為單位），過了這段時間，FMPS將停止等候此處理序執行。 |


