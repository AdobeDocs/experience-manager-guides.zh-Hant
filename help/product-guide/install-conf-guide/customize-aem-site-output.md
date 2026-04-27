---
title: 設定輸出產生設定
description: 瞭解如何設定輸出產生設定
feature: Output Generation
role: Admin
level: Experienced
exl-id: 0849544d-fa7b-4c66-b418-1ffcd1ca09df
source-git-commit: d5dbd67ba44735cf1545291e9a03e3096acd8166
workflow-type: tm+mt
source-wordcount: '3190'
ht-degree: 1%

---

# 自訂現有的AEM網站輸出 {#id166TG0B30WR}

AEM Guides支援以下列格式建立輸出：

- AEM網站
- PDF
- HTML5
- ePub
- 透過DITA-OT自訂輸出

對於AEM Site輸出，您可以針對不同的輸出任務指派不同的設計範本。 這些設計範本可以不同的版面配置呈現DITA內容。 例如，您可以為內部和外部對象指定不同的設計範本。

您也可以將自訂的DITA Open Toolkit \(DITA-OT\)外掛程式與AEM Guides搭配使用。 您可以上傳這些自訂DITA-OT外掛程式，以特定方式產生PDF輸出。

>[!TIP]
>
> 如需有關建立AEM網站輸出的最佳實務，請參閱[最佳實作指南](https://helpx.adobe.com/content/dam/help/en/xml-documentation-solution/cs-mar-22/Adobe-Experience-Manager-Guides_Best-Practices_EN.pdf)中的&#x200B;*AEM網站發佈*&#x200B;一節。


## 自訂設計範本以產生輸出 {#customize_xml-add-on}

AEM Guides使用一組預先定義的設計範本來產生AEM網站輸出。 您可以自訂AEM Guides設計範本，以產生符合您公司品牌規範的輸出。 設計範本是各種樣式\(CSS\)、指令碼\（伺服器端和使用者端\）、資源\（影像、標誌和其他資產\）以及將所有這些資源繫結在一起的JCR節點的集合。 設計範本可以像單一伺服器端指令碼一樣簡單，只包含幾個JCR節點，或樣式、資源和JCR節點的複雜組合。 AEM Guides發佈子系統會在產生AEM Site輸出時使用設計範本，這些範本可控制所產生輸出的結構、外觀和風格。

設計範本資源在伺服器上的放置位置沒有限制，但通常會根據其功能進行邏輯組織。 例如，預設範本的所有JavaScript和CSS檔案都儲存在`/etc/designs/fmdita/clientlibs/siteoutput/default`資料夾下。 無論這些檔案位於何處，都會由JCR節點集合連結在一起。 這些JCR節點和檔案共同構成了整個設計範本。

AEM Guides隨附的預設設計範本可讓您自訂登入、主題和搜尋頁面元件。 您可以複製預設設計和對應的參照範本，並指定不同的元件以產生所需的輸出。

下列標籤提供指示，讓您根據您的AEM設定，指定自己的設計範本以用於產生Experience Manager Guides網站輸出： Cloud Service或內部部署。

>[!BEGINTABS]

>[!TAB Cloud Service]

1. 使用「封裝管理員」從下列位置下載預設設計範本：

   /libs/fmdita/config/templates

1. 在您的Cloud Manager Git存放庫中的以下位置建立已下載檔案的復本：

   /apps/fmdita/config/templates

1. 您也必須下載並複製從預設範本節點參照的範本。 參照的範本放置在：

   /libs/fmdita/templates/default/cqtemplates

>[!TAB 內部部署]

1. 登入AEM並開啟CRXDE Lite模式。

1. 導覽至預設的設計範本節點。 預設設計範本節點的位置為：

   `/libs/fmdita/config/templates/`

   ![](assets/templates-node.png){width="300" align="left"}

   >[!NOTE]
   >
   > 將預設設計範本從`libs`資料夾複製到`apps`資料夾，並在`apps`資料夾中進行變更。 您也必須變更從預設範本節點參考的範本。 參照的範本放置在`/libs/fmdita/templates/default/cqtemplates`節點下。 在進行任何變更之前，請先在`apps`資料夾中複製參照的範本。

1. 按一下&#x200B;*範本*&#x200B;節點中的&#x200B;*預設*&#x200B;元件以存取其屬性。

>[!ENDTABS]

下表說明AEM Guides設計範本屬性。

| 屬性 | 說明 |
|--------|-----------|
| `landingPageTemplate`、`searchPageTemplate`、`topicPageTemplate`、`shadowPageTemplate` | 為這些對應頁面指定`cq:Template`節點\（登陸、搜尋和主題\）。 依預設，這些頁面的`cq:Template`節點可以在`/libs/fmdita/templates/default/cqtemplates`節點中找到。 此節點定義登陸、搜尋和主題頁面的結構和屬性。<br> `shadowPageTemplate`用於最佳化區塊內容。 您必須將此屬性的值設定為： `fmdita/templates/default/cqtemplates/shadowpage` <br> **注意：**&#x200B;您必須指定`topicPageTemplate`的值。 `landingPageTemplate`和`searchPageTemplate`為選擇性屬性。 如果您不想產生搜尋和登入頁面，請勿指定這些屬性。 |
| `title` | 設計範本的描述性名稱。 |
| `topicContentNode` | 將在主題頁面中包含DITA內容的節點位置。 路徑是相對於主題頁面的路徑。 |
| `topicHeadNode` | 節點的位置，此節點將包含衍生自DITA內容的head值\（或metadata\）。 路徑是相對於主題頁面的路徑。 |
| `tocNode` | 包含目錄的節點位置。 路徑是相對於登陸頁面或目的地路徑的。 |
| `basePathProp` | 用來儲存已發佈網站根目錄路徑的屬性名稱。 |
| `indexPathProp` | 用於儲存已發佈網站之登陸/索引頁面路徑的屬性名稱。 |
| `pdfPathProp` | 儲存主題PDF路徑的屬性名稱（如果已啟用主題PDF產生）。 |
| `pdfTypeProp` | 用於儲存PDF產生型別的屬性名稱。 目前此屬性一律包含「主題」。 |
| `searchPathProp` | 儲存搜尋頁面路徑的屬性名稱（如果範本包含搜尋頁面）。 |
| `siteTitleProp` | 用來儲存發佈之網站標題的屬性名稱。 此標題通常與正在發佈的地圖的標題相同。 |
| `sourcePathProp` | 用來儲存目前頁面之來源DITA主題之路徑的屬性名稱。 |
| `tocPathProp` | 用於儲存已發佈站台TOC根目錄路徑的屬性名稱。 |


>[!NOTE]
>
> 建立自訂設計範本節點後，您必須更新AEM網站輸出預設集中的「設計」選項，才能使用自訂設計範本節點。

如需詳細資訊，請參閱[建立您的第一個Adobe Experience Manager網站](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html?lang=zh-Hant)和[在AEM上開發您自己的網站的基本知識](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/full-stack/develop-wknd-tutorial.html?lang=zh-Hant)。

## 使用檔案標題來產生AEM網站輸出

產生AEM Site輸出時，產生URL的方式對發現您的內容而言至關重要。 如果您使用UUID型檔案名稱，根據檔案的UUID產生URL將不利於搜尋。 身為管理員或發佈者，您可以控制要如何產生AEM網站輸出的URL。 AEM Guides提供設定，您可選擇使用檔案標題而非UUID式檔案名稱來產生AEM Site輸出的URL。 對於以UUID為基礎的檔案系統，此選項預設為開啟。 這表示當您產生UUID型檔案系統的AEM Site輸出時，會使用檔案的標題來產生URL，而非檔案的UUID。

若為使用非UUID型檔案系統的內部部署設定，會使用檔案名稱而非檔案標題來產生AEM Site輸出。 依預設，此選項是關閉的。 這表示產生AEM Site輸出時，會使用檔案名稱來產生URL，而非檔案標題。 您可以啟用此選項，選擇根據檔案標題產生URL。

下列標籤提供根據您的Experience Manager Guides設定，在AEM網站輸出中設定URL產生的指示： Cloud Service或內部部署。

>[!NOTE]
>
> 您可以進一步設定規則，以僅允許AEM網站輸出的URL中的一組字元。 如需詳細資訊，請參閱[設定檔案名稱清理規則，以建立主題並發佈AEM網站輸出](#id2164D0KD0XA)。

>[!BEGINTABS]

>[!TAB Cloud Service]

使用[組態覆寫](download-install-config-override.md#)中提供的指示來建立組態檔。 在設定檔案中，提供下列\(property\)詳細資訊，以在AEM網站輸出中設定URL產生：

| PID | 屬性索引鍵 | 屬性值 |
|---|------------|--------------|
| `com.adobe.fmdita.config.ConfigManager` | `aemsite.pagetitle` | 布林值\(true/false\)。 如果您想使用頁面標題產生輸出，則將此屬性設定為true。 預設會設定為使用檔案名稱。<br> **預設值**： false |


>[!TAB 內部部署]

1. 開啟Adobe Experience Manager Web主控台設定頁面。

   存取設定頁面的預設URL為：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜尋並按一下&#x200B;**com.adobe.fmdita.config.ConfigManager**&#x200B;套件。

1. 選取&#x200B;**使用AEM網站頁面名稱的標題**&#x200B;選項。

   >[!NOTE]
   >
   > 如果您要使用檔案名稱產生輸出，請取消選取此選項。

1. 按一下&#x200B;**儲存**。

>[!ENDTABS]

## 設定AEM網站輸出的URL以使用檔案標題（僅適用於Cloud Service）

您可以在AEM網站輸出的URL中使用檔案標題。 如果檔案名稱不存在或包含所有特殊字元，您可以設定系統在AEM Site輸出的URL中，以分隔符號取代特殊字元。 您也可以將其設定為使用第一個子主題名稱來取代。


若要設定頁面名稱，請執行下列步驟：

1. 使用[組態覆寫](download-install-config-override.md#)中提供的指示來建立組態檔。
1. 在組態檔中，提供下列（屬性）詳細資訊，以設定主題的頁面名稱。

| PID | 屬性索引鍵 | 屬性值 |
|---|------------|--------------|
| `com.adobe.fmdita.common.SanitizeNodeName` | `nodename.systemDefinedPageName` | 布林值(`true/false`)。 **預設值**： `false` |

例如，如果`<topichead>`中的&#x200B;*@navtitle*&#x200B;具有所有特殊字元，而您將`aemsite.pagetitle`屬性設定為true，則預設會使用分隔符號。 如果您將`nodename.systemDefinedPageName`屬性設為true，它會顯示第一個子主題的名稱。


## 設定檔案名稱清理規則，以AEM Sites和其他格式建立主題和發佈輸出 {#id2164D0KD0XA}

身為管理員，您可以定義檔案名稱中允許的有效特殊字元清單，這些字元最終會形成AEM網站輸出的URL。 在舊版中，使用者可定義包含特殊字元（如`@`、`$`、`>`等）的檔案名稱。 這些特殊字元會在產生AEM網站頁面時產生編碼的URL。

自3.8發行版本開始，已新增設定以定義檔案名稱中允許的特殊字元清單。 依預設，有效的檔案名稱組態包含&quot;`a-z A-Z 0-9 - _`&quot;。 這表示在建立檔案時，檔案標題中可以有任何特殊字元，但在內部，檔案名稱中將會以連字型大小\(`-`\)取代。 例如，您可以將檔案的標題設為Introduction 1或Introduction@1，針對這兩種情況產生的對應檔案名稱都是Introduction-1。

定義有效字元清單時，請記住，這些字元&quot;`*/:[\]|#%{}?&<>"/+`&quot;和`a space`將一律以連字型大小\(`-`\)取代。

>[!NOTE]
>
> 如果您未設定有效的特殊字元清單，檔案建立程式可能會為您提供一些未預期的結果。

下列標籤會提供根據您的AEM設定，在檔案名稱和Experience Manager Guides網站輸出中設定有效特殊字元的指示： Cloud Service或內部部署。

>[!BEGINTABS]

>[!TAB Cloud Service]

使用[組態覆寫](download-install-config-override.md#)中提供的指示來建立組態檔。 在設定檔案中，提供下列\(property\)詳細資訊，以便在檔案名稱和AEM Site輸出中設定有效的特殊字元：

| PID | 屬性索引鍵 | 屬性值 |
|---|------------|--------------|
| `com.adobe.fmdita.common.SanitizeNodeNameImpl` | `aemsite.DisallowedFileNameChars` | 確定屬性已設定為``'<>`@$``。 您可以在此清單中新增更多特殊字元。 |

>[!NOTE]
> 
> 上述設定適用於所有輸出格式。 這表示產生PDF、HTML或自訂輸出時，最終輸出將遵循設定的檔案名稱清理規則。

您也可以設定其他屬性，例如檔案名稱中的使用小寫、處理無效字元的分隔符號，以及檔案名稱中允許的最大字元數。 若要設定這些屬性，請在設定檔案中新增下列機碼值組：

| 屬性索引鍵 | 屬性值 |
|------------|--------------|
| `nodename.uselower` | 布林值\(true/false\)。<br> **預設值**： true |
| `nodename.separator` | 任何字元。<br> **預設值**： \_ *\（底線\）* |
| `nodename.maxlength` | 整數值。<br> **預設值**： 50 |

>[!TAB 內部部署]

1. 開啟Adobe Experience Manager Web主控台設定頁面。

   存取設定頁面的預設URL為：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜尋並按一下&#x200B;*com.adobe.fmdita.common.SanizeNodeNameImpl*&#x200B;套件。

1. 在&#x200B;**不允許發佈至AEM Sites**&#x200B;屬性的字元集中，確定屬性已設為```'<>`@$```。 您可以在此清單中新增更多特殊字元，但是它必須包含這些必要的特殊字元。

   >[!NOTE]
   >
   > 您也可以設定其他屬性，例如，檔案名稱中的&#x200B;**使用小寫**、處理無效字元的&#x200B;**分隔符號**&#x200B;以及檔案名稱中允許的&#x200B;**字元數目上限**。

1. 按一下&#x200B;**儲存**。

1. 搜尋並按一下&#x200B;**com.adobe.fmdita.config.ConfigManager**&#x200B;套件。

1. 在&#x200B;**有效字元的Regex**&#x200B;屬性中，確定屬性已設為`[-a-zA-Z0-9_]`。 您可以新增更多字元至此清單，但清單必須包含這些基本字元，且清單必須以連字型大小\(`-`\)開頭。

   >[!NOTE]
   >
   > 此屬性會定義用來建立新檔案的有效字元清單。

1. 按一下&#x200B;**儲存**。

>[!ENDTABS]

## 設定AEM網站節點結構的平面化

產生AEM Site輸出時，主題中每個元素的節點都會在內部建立。 對於包含數千個主題的DITA map，此節點結構可能會變得太深。 對於較大的網站，這種深度巢狀節點結構可能會出現效能問題。 下列快照會顯示AEM網站輸出的深度巢狀節點結構：

![](assets/deep-nested-aem-site-node-structure.png)

在上述快照中，請注意會為每個`p`元素及其後續子元素建立節點，並為主題中使用的其他所有元素建立類似的結構。

AEM Guides可讓您設定AEM網站輸出的節點結構在內部建立的方式。 您可以在指定元素處平面化節點結構，這表示您可以定義元素，將其視為主要元素，其內的所有子元素將與主要元素合併。 例如，如果您決定平面化`p`元素，則出現在`p`元素中的任何元素都將與主要`p`元素合併。 不會為`p`元素內的任何子元素建立個別附註。 下列快照顯示平面化於`p`元素的節點結構：

![](assets/flattened-aem-site-node-structure.png)

下列標籤會提供指示，讓您根據您的AEM設定來平面化Experience Manager Guides網站節點結構： Cloud Service或內部部署。

>[!BEGINTABS]

>[!TAB Cloud Service]

1. 識別您要平面化節點結構的元素：

1. 覆蓋`apps`節點中的`libs`節點，並開啟elementmapping.xml檔案。

1. 在您要平面化節點結構的元素定義中新增`<flatten>true</flatten>`屬性。 例如，如果您想要平面化`p`元素的節點結構，請在`p`元素的定義中新增flatten屬性，如下所示：

   ```XML
   <ditaelement>
         <name>p</name>
         <class>- topic/p</class>
         <componentpath>fmdita/components/dita/wrapper</componentpath>
         <type>COMPOSITE</type>
         <target>para</target>
         <flatten>true</flatten>
         <wrapelement>div</wrapelement>
      </ditaelement>
   ```

   >[!NOTE]
   >
   > 根據預設，flatten node屬性已在`p`專案上設定。

1. 使用[組態覆寫](download-install-config-override.md#)中提供的指示來建立組態檔。
1. 在設定檔中，提供下列\(property\)詳細資料：

   | PID | 屬性索引鍵 | 屬性值 |
   |---|------------|--------------|
   | `com.adobe.dxml.flattening.FlatteningConfigurationService` | `flattening.enabled` | 布林值\(true/false\)。<br> **預設值**： `false` |


現在，當您產生AEM Site輸出時，`p`元素內的節點會平面化並儲存在`p`元素本身中。 您可以在CRXDE中找到`p`元素的新平面化屬性。

![](assets/flatten-aem-site-note-props-crxde.png)

>[!TAB 內部部署]

1. 指定您要平面化節點結構的元素。

   1. 覆蓋`apps`節點中的`libs`節點，並開啟elementmapping.xml檔案。

   1. 在您要平面化節點結構的元素定義中新增`<flatten>true</flatten>`屬性。 例如，如果您想要平面化`p`元素的節點結構，請在`p`元素的定義中新增flatten屬性，如下所示：

      ```XML
      <ditaelement>
          <name>p</name>
          <class>- topic/p</class>
          <componentpath>fmdita/components/dita/wrapper</componentpath>
          <type>COMPOSITE</type>
          <target>para</target>
          <flatten>true</flatten>
          <wrapelement>div</wrapelement>
      </ditaelement>
      ```

      >[!NOTE]
      >
      > 根據預設，flatten node屬性已在`p`專案上設定。

1. 在configMgr中啟用網站節點平面化設定。

   1. 開啟Adobe Experience Manager Web主控台設定頁面。

      存取設定頁面的預設URL為：

      ```http
      http://<server name>:<port>/system/console/configMgr
      ```

   1. 搜尋並按一下&#x200B;*com.adobe.dxml.flattening.FlatteningConfigurationService*&#x200B;組合。

   1. 選取&#x200B;**屬性flattening.enabled**&#x200B;選項。

   1. 按一下&#x200B;**儲存**。


>[!IMPORTANT]
>
> 如果您在elementmapping.xml檔案中進行任何變更，請確定您開啟configMgr並儲存任何組合，以使變更生效。

現在，當您產生AEM Site輸出時，`p`元素內的節點會平面化並儲存在`p`元素本身中。 您可以在CRXDE中找到`p`元素的新平面化屬性。

![](assets/flatten-aem-site-note-props-crxde.png){width="650" align="left"}

>[!ENDTABS]

**在AEM網站輸出的內容中搜尋字串（僅適用於Cloud Service）**

依預設，您只能在AEM網站輸出中搜尋標題中的字串。 您可以設定系統搜尋標題中的字串，也可以搜尋AEM Site輸出的內容或內文。

>[!NOTE]
>
> 有時您的搜尋可能適用於內容中的某些元素，但您可以將其設定為適用於整個內容。

![](assets/flatten-aem-site-note-props-crxde-search.png)

若要啟用搜尋，您應該設定AEM網站節點結構的平面化。

注意:

您最多可以搜尋1MB的平面化內容。 例如，在上一個熒幕擷圖中，您可以搜尋&lt;p\>標籤下的內容是否為&lt;= 1Mb。

>[!NOTE]
>
> 只有在`<flatten>`屬性設定為true時，搜尋才會對元素生效。 依預設，AEM Guides將&lt;p\> &lt;ul\> &lt;lI\>等常用文字元素的`<flatten>`屬性設為true。 不過，如果您已建立某些自訂元素，則應在elementmapping.xml檔案中將`<flatten>`屬性設定為true。

**防止AEM網站節點結構平面化**

與在AEM Site輸出中指定要平面化的節點類似，您也可以指定要從此設定中排除的元素。 例如，如果您想要在`body`專案處平面化節點，但您不希望`body`中的任何`table`專案平面化，則您可以在`table`專案的定義中新增排除屬性。

若要將`table`元素從平面化中排除，請將下列屬性新增至`table`元素的定義：

`<preventancestorflattening>true|false</preventancestorflattening>`

## 在AEM網站輸出中設定已刪除頁面的版本設定

當您針對現有輸出頁面設定選取了&#x200B;**刪除和**&#x200B;建立&#x200B;**&#x200B;**&#x200B;選項來產生AEM網站輸出時，會為要刪除的頁面建立一個版本。 您可以設定系統在刪除前停止建立版本。

下列標籤會提供指示，讓您根據您的Experience Manager Guides設定，停止為正在刪除的頁面建立版本： Cloud Service或內部部署。

>[!BEGINTABS]

>[!TAB Cloud Service]

1. 使用[組態覆寫](download-install-config-override.md#)中提供的指示來建立組態檔。
1. 在組態檔中，提供下列\(property\)詳細資訊，以設定&#x200B;**不要為已刪除的頁面建立版本**&#x200B;選項：

   | PID | 屬性索引鍵 | 屬性值 |
   |---|------------|--------------|
   | `com.adobe.fmdita.confi g.ConfigManager` | `no.version.creation.on.deletion` | 布林值\(true/false\)。<br> **預設值**： `true` |

   >[!NOTE]
   >
   > 選取此選項後，使用者可直接刪除任何頁面，而不需為其建立任何版本。 如果未選取選項，則會在刪除頁面之前建立版本。

>[!TAB 內部部署]

1. 開啟Adobe Experience Manager Web主控台設定頁面。

   存取設定頁面的預設URL為：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜尋並按一下&#x200B;*com.adobe.fmdita.config.ConfigManager*&#x200B;套件。

1. 選取&#x200B;**不要建立已刪除頁面的版本**&#x200B;選項。

   >[!NOTE]
   >
   > 選取此選項後，使用者可直接刪除任何頁面，而不需為其建立任何版本。 如果未選取選項，則會在刪除頁面之前建立版本。

1. 按一下&#x200B;**儲存**。

>[!ENDTABS]

## 使用Experience Manager Guides設定自訂重寫程式（僅適用於Cloud Service） {#custom-rewriter}

Experience Manager Guides有自訂sling [**重寫程式**](https://sling.apache.org/documentation/bundles/output-rewriting-pipelines-org-apache-sling-rewriter.html)模組，可處理交叉對映時產生的連結（兩個不同對映之主題之間的連結）。 此重寫程式組態安裝在下列路徑： <br> `/apps/fmdita/config/rewriter/fmdita-crossmap-link-patcher`。

如果您的程式碼基底中有另一個自訂Sling重寫程式，請使用大於50的`'order'`值，因為Experience Manager Guides Sling重寫程式使用`'order'` 50。  若要覆寫此值，您需要大於50的值。 如需詳細資訊，請檢視[輸出重寫管道](https://sling.apache.org/documentation/bundles/output-rewriting-pipelines-org-apache-sling-rewriter.html)。
