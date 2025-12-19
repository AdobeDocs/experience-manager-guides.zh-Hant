---
title: 設定輸出產生設定
description: 瞭解如何設定輸出產生設定
exl-id: 6df31e3c-683c-4188-b917-9c1855d9b95b
feature: Output Generation
role: Admin
level: Experienced
source-git-commit: 9769a196346117237f2f72b6c88f8ac14fece740
workflow-type: tm+mt
source-wordcount: '5824'
ht-degree: 0%

---

# 設定輸出產生設定 {#id181AI0B0E30}

AEM Guides提供許多設定選項，供您自訂輸出產生流程。 本主題涵蓋可協助您設定輸出產生程式的所有設定和自訂。

## 在DITA map圖示板上設定基準線標籤 {#id223MD0D0YRM}

您可以設定和隱藏地圖圖示板上可用的「基準線」標籤。

預設不會啟用&#x200B;**隱藏基準標籤**&#x200B;選項，您必須從configMgr啟用此功能。 執行以下步驟，在Web編輯器中啟用預設選項：

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


## 設定FrameMaker Publishing Server {#id1678G0Z0TN6}

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

## 在現有AEM網站中設定混合發佈 {#id1691I0V0MGR}

如果您有包含DITA內容的AEM網站，您可以設定AEM網站輸出，將DITA內容發佈至網站內預先定義的位置。 例如，在以下AEM網站頁面熒幕擷圖中，`ditacontent`節點已保留以儲存DITA內容：

![](assets/publish-in-aem-site.png){width="300" align="left"}

頁面中的其餘節點會直接從AEM網站編輯器撰寫。 將發佈設定設為發佈DITA內容至預先定義的位置，可確保AEM Guides發佈程式不會修改任何現有的非DITA內容。

您需要在現有網站上執行下列設定，以允許將DITA內容發佈到預先定義的節點：

- 設定網站的範本屬性

- 在您的網站中新增節點以發佈DITA內容


執行以下步驟來設定您現有網站的範本屬性：

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


## 自訂AEM網站輸出 {#id166TG0B30WR}

AEM Guides支援以下列格式建立輸出：

- AEM網站

- PDF

- HTML5
- ePub
- 透過DITA-OT自訂輸出

對於AEM Site輸出，您可以針對不同的輸出任務指派不同的設計範本。 這些設計範本可以不同的版面配置呈現DITA內容。 例如，您可以為內部和外部對象指定不同的設計範本。

您也可以使用自訂的DITA Open Toolkit \(DITA-OT\)外掛程式搭配AEM Guides。 您可以上傳這些自訂DITA-OT外掛程式，以特定方式產生PDF輸出。

>[!TIP]
>
> 如需建立AEM網站輸出的最佳實務，請參閱「最佳實作指南&#x200B;*appendix.md\#*」中的[AEM網站發佈](appendix.md#)一節。

### 自訂設計範本以產生輸出 {#customize_xml-add-on}

AEM Guides使用一組預先定義的設計範本來產生AEM網站輸出。 您可以自訂AEM Guides的設計範本，以產生符合您公司品牌規範的輸出。 設計範本是各種樣式\(CSS\)、指令碼\（伺服器端和使用者端\）、資源\（影像、標誌和其他資產\）以及將所有這些資源繫結在一起的JCR節點的集合。 設計範本可以像單一伺服器端指令碼一樣簡單，只包含幾個JCR節點，或樣式、資源和JCR節點的複雜組合。 AEM Guides發佈子系統會在產生AEM Site輸出時使用設計範本，這些範本可控制所產生輸出的結構、外觀和風格。

設計範本資源在伺服器上的放置位置沒有限制，但通常會根據其功能進行邏輯組織。 例如，預設範本的所有JavaScript和CSS檔案都儲存在`/etc/designs/fmdita/clientlibs/siteoutput/default`資料夾下。 無論這些檔案位於何處，都會由JCR節點集合連結在一起。 這些JCR節點和檔案共同構成了整個設計範本。

AEM Guides隨附的預設設計範本可讓您自訂登入、主題和搜尋頁面元件。 您可以複製預設設計和對應的參照範本，並指定不同的元件以產生所需的輸出。

執行以下步驟，指定您自己的設計範本，以用於AEM Site輸出產生：

1. 登入AEM並開啟CRXDE Lite模式。

1. 導覽至預設的設計範本節點。 預設設計範本節點的位置為：

   `/libs/fmdita/config/templates/`

   ![](assets/templates-node.png){width="300" align="left"}

   >[!NOTE]
   >
   > 將預設設計範本從`libs`資料夾複製到`apps`資料夾，並在`apps`資料夾中進行變更。 您也必須變更從預設範本節點參考的範本。 參照的範本放置在`/libs/fmdita/templates/default/cqtemplates`節點下。 在進行任何變更之前，請先在`apps`資料夾中複製參照的範本。

1. 按一下&#x200B;*範本*&#x200B;節點中的&#x200B;*預設*&#x200B;元件以存取其屬性。

   下表說明AEM Guides的設計範本屬性。

   | 屬性 | 說明 |
   |--------|-----------|
   | `landingPageTemplate`、`searchPageTemplate`、`topicPageTemplate`、`shadowPageTemplate` | 為這些對應頁面指定`cq:Template`節點\（登陸、搜尋和主題\）。 依預設，這些頁面的`cq:Template`節點可以在`/libs/fmdita/templates/default/cqtemplates`節點中找到。 此節點會定義登陸、搜尋和主題頁面的結構和屬性。 <br> `shadowPageTemplate`用於最佳化區塊內容。 您必須將此屬性的值設定為： <br> `fmdita/templates/default/cqtemplates/shadowpage` <br> **注意**&#x200B;您必須指定`topicPageTemplate`的值。 `landingPageTemplate`和`searchPageTemplate`為選擇性屬性。 如果您不想產生搜尋和登入頁面，請勿指定這些屬性。 |
   | `title` | 設計範本的描述性名稱。 |
   | `topicContentNode` | 將在主題頁面中包含DITA內容的節點位置。 路徑是相對於主題頁面的路徑。 |
   | `topicHeadNode` | 節點的位置，此節點將包含衍生自DITA內容的head值\（或metadata\）。 路徑是相對於主題頁面的路徑。 |
   | `tocNode` | 包含目錄的節點位置。 路徑是相對於登陸頁面或目的地路徑的。 |
   | `basePathProp` | 用來儲存已發佈網站根目錄路徑的屬性名稱。 |
   | `indexPathProp` | 用於儲存已發佈網站之登陸/索引頁面路徑的屬性名稱。 |
   | `pdfPathProp` | 儲存主題PDF路徑的屬性名稱(如果已啟用主題PDF產生)。 |
   | `pdfTypeProp` | 用於儲存PDF產生型別的屬性名稱。 目前此屬性一律包含「主題」。 |
   | `searchPathProp` | 儲存搜尋頁面路徑的屬性名稱（如果範本包含搜尋頁面）。 |
   | `siteTitleProp` | 用來儲存發佈之網站標題的屬性名稱。 此標題通常與正在發佈的地圖的標題相同。 |
   | `sourcePathProp` | 用來儲存目前頁面之來源DITA主題之路徑的屬性名稱。 |
   | `tocPathProp` | 用於儲存已發佈站台TOC根目錄路徑的屬性名稱。 |


>[!NOTE]
>
> 建立自訂設計範本節點後，您必須更新AEM網站輸出預設集中的「設計」選項，才能使用自訂設計範本節點。

如需詳細資訊，請參閱[建立您的第一個Adobe Experience Manager 6.3網站](https://helpx.adobe.com/experience-manager/using/first_aem63_website.html)和[在AEM上開發您自己的網站的基本知識](https://helpx.adobe.com/experience-manager/6-3/sites/developing/using/the-basics.html)。

### 使用檔案標題來產生AEM網站輸出

產生AEM Site輸出時，產生URL的方式對發現您的內容而言至關重要。 如果您使用UUID型檔案名稱，根據檔案的UUID產生URL將不利於搜尋。 身為管理員或發佈者，您可以控制要如何產生AEM網站輸出的URL。 AEM Guides提供設定，您可選擇使用檔案標題而非UUID式檔案名稱來產生AEM Site輸出的URL。 對於以UUID為基礎的檔案系統，此選項預設為開啟。 這表示當您產生UUID型檔案系統的AEM Site輸出時，會使用檔案的標題來產生URL，而非檔案的UUID。

產生AEM Site輸出時，產生URL的方式對發現您的內容而言至關重要。 如果檔案系統不是UUID型，AEM Site輸出會使用檔案名稱而不是檔案標題來產生。 身為管理員或發佈者，您可以控制要如何產生AEM網站輸出的URL。 AEM Guides提供設定，您可選擇使用檔案標題（而非檔案名稱）產生AEM Site輸出的URL。 依預設，此選項是關閉的。 這表示產生AEM Site輸出時，會使用檔案名稱來產生URL，而非檔案標題。 您可以啟用此選項，選擇根據檔案標題產生URL。

>[!NOTE]
>
> 您可以進一步設定規則，以僅允許AEM網站輸出的URL中的一組字元。 如需詳細資訊，請參閱[設定檔案名稱清理規則，以建立主題並發佈AEM網站輸出](#id2164D0KD0XA)。

若要在AEM Site輸出中設定URL的產生，請執行以下步驟：

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


### 設定檔案名稱清理規則，以建立主題和發佈AEM網站輸出 {#id2164D0KD0XA}

身為管理員，您可以定義檔案名稱中允許的有效特殊字元清單，這些字元最終會形成AEM網站輸出的URL。 在舊版中，使用者可定義包含特殊字元（如`@`、`$`、`>`等）的檔案名稱。 這些特殊字元會在產生AEM網站頁面時產生編碼的URL。

自3.8發行版本開始，已新增設定以定義檔案名稱中允許的特殊字元清單。 依預設，有效的檔案名稱組態包含&quot;`a-z A-Z 0-9 - _`&quot;。 這表示在建立檔案時，檔案標題中可以有任何特殊字元，但在內部，檔案名稱中將會以連字型大小\(`-`\)取代。 例如，您可以將檔案的標題設為Introduction 1或Introduction@1，針對這兩種情況產生的對應檔案名稱都是Introduction-1。

定義有效字元清單時，請記住，這些字元&quot;`*/:[\]|#%{}?&<>"/+`&quot;和`a space`將一律以連字型大小\(`-`\)取代。

>[!NOTE]
>
> 如果您未設定有效的特殊字元清單，檔案建立程式可能會為您提供一些未預期的結果。

若要在檔案名稱和AEM網站輸出中設定有效的特殊字元，請執行以下步驟：

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


### 設定AEM網站節點結構的平面化

產生AEM Site輸出時，主題中每個元素的節點都會在內部建立。 對於包含數千個主題的DITA map，此節點結構可能會變得太深。 對於較大的網站，這種深度巢狀節點結構可能會出現效能問題。 下列快照會顯示AEM網站輸出的深度巢狀節點結構：

![](assets/deep-nested-aem-site-node-structure.png){width="300" align="left"}

在上述快照中，請注意會為每個`p`元素及其後續子元素建立節點，並為主題中使用的其他所有元素建立類似的結構。

AEM Guides可讓您設定AEM網站輸出的節點結構在內部建立的方式。 您可以在指定元素處平面化節點結構，這表示您可以定義元素，將其視為主要元素，其內的所有子元素將與主要元素合併。 例如，如果您決定平面化`p`元素，則出現在`p`元素中的任何元素都將與主要`p`元素合併。 不會為`p`元素內的任何子元素建立個別附註。 下列快照顯示平面化於`p`元素的節點結構：

![](assets/flattened-aem-site-node-structure.png){width="300" align="left"}

若要平面化AEM Site節點結構，請執行下列步驟：

1. 指定您要平面化節點結構的元素。

   1. 覆蓋`libs`節點中的`apps`節點，並開啟elementmapping.xml檔案。

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

**防止AEM網站附註結構平面化**

與在AEM Site輸出中指定要平面化的節點類似，您也可以指定要從此設定中排除的元素。 例如，如果您想要在`body`專案處平面化節點，但您不希望`table`中的任何`body`專案平面化，則您可以在`table`專案的定義中新增排除屬性。

若要將`table`元素從平面化中排除，請將下列屬性新增至`table`元素的定義：

`<preventancestorflattening>true|false</preventancestorflattening>`

### 在AEM網站輸出中設定已刪除頁面的版本設定

當您針對現有輸出頁面設定選取了&#x200B;**刪除和**&#x200B;建立&#x200B;****選項來產生AEM網站輸出時，會為要刪除的頁面建立一個版本。 您可以設定系統在刪除前停止建立版本。

執行以下步驟，停止建立要刪除之頁面的版本：

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

   1. 選取新欄位以開啟欄位的&#x200B;**設定**。

   1. 在&#x200B;**欄位標籤**&#x200B;中，輸入中繼資料名稱 — Audience。

   1. 在&#x200B;**對應至屬性**&#x200B;設定中，指定。/jcr:content/metadata/&lt;中繼資料的名稱\>。 例如我們的範例，我們將其設為。/jcr:content/metadata/audience。

   使用這些步驟，新增所有必要的中繼資料引數。

1. 按一下&#x200B;**儲存**。


現在，所有DITA map的「屬性」頁面中都會顯示新引數。

![](assets/properties-page-custom-metadata.PNG){width="650" align="left"}

接下來，您需要在DITA map主控台中提供自訂中繼資料。 執行下列步驟，讓自訂中繼資料可在DITA map虛線板上使用：

1. 登入AEM並開啟CRXDE Lite模式。

1. 存取以下位置可用的metadataList檔案：

   /libs/fmdita/config/metadataList

   >[!NOTE]
   >
   > metadataList檔案包含顯示在地圖儀表板中DITA map的&#x200B;**屬性**&#x200B;下拉式清單中的屬性清單。 依預設，此檔案中列出四個屬性：docstate、dc:language、dc:description和dc:title。

1. 新增您在中繼資料結構Forms頁面中新增的自訂中繼資料。 例如，將對象引數新增至預設清單的結尾。

1. 按一下&#x200B;**「儲存全部」**。


現在，自訂中繼資料會顯示在DITA map主控台的&#x200B;**屬性**&#x200B;下拉式清單中。

最後，身為「發佈者」，您需要在發佈的輸出中包含自訂中繼資料。 若要在產生輸出時處理自訂中繼資料，請執行下列步驟：

1. 在Assets UI中，導覽至您要發佈的DITA map。

1. 選取DITA map檔案並開啟其屬性頁面。

1. 在「屬性」頁面上，指定自訂中繼資料的值。 例如，我們為對象引數指定了External值。

   ![](assets/properties-page-custom-metadata-value.png){width="650" align="left"}

1. 按一下「**儲存並關閉**」。

1. 按一下DITA map檔案以開啟DITA map主控台。

1. 在&#x200B;**輸出預設集**&#x200B;索引標籤中，選取您要用來產生輸出的輸出預設集。

1. 按一下「**編輯**」。

1. 從&#x200B;**屬性**&#x200B;下拉式清單中，選取您要傳遞給發佈程式的屬性。

   ![](assets/props-in-publish-output.PNG){width="650" align="left"}


選取的屬性/中繼資料會傳遞至發佈程式，並可在最終輸出中使用。

## 使用AEM元件自訂DITA元素對應 {#id1679J600HEL}

AEM Guides中的DITA元素對應至其對應的AEM元件。 AEM Guides在工作流程（例如發佈和稽核）中使用此對應，將DITA元素轉換為對應的AEM元件。 在`elementmapping.xml`檔案中定義對應，您可以從CRXDE Lite模式存取該檔案。 在CRXDE Lite模式中存取下列URL：

`/libs/fmdita/config/elementmapping.xml`

>[!NOTE]
>
> 請勿在``libs``節點中使用預設組態檔中的任何自訂專案。 您必須在``libs``節點中建立``apps``節點的覆蓋，並僅更新``apps``節點中的必要檔案。

您可以使用預先定義的DITA元素對應，也可以將DITA元素對映至自訂AEM元件。 若要使用自訂AEM元件，您必須瞭解`elementmapping.xml`檔案的結構。

### elementmapping.xml結構

以下說明`elementmapping.xml`結構的高階概觀：

1. 系統會根據元素名稱，先搜尋每個DITA元素以尋找對應的元件對應。 例如：

   ```XML
   <ditaelement>     
      <name>**substeps**</name>  
      <class>- topic/ol task/substeps</class>  
      <componentpath>dita/components/ditaolist</componentpath>  
      <type>COMPOSITE</type>  
      <target>para</target>
   </ditaelement>
   ```

   在上述範例中，所有`substeps` DITA元素都是使用`dita/components/ditaolist`元件轉譯。

1. 如果DITA元素找不到以名稱為基礎的相符專案，則會完成以`class`為基礎的相符專案。 例如：

   ```XML
   <ditaelement>  
      <name>topic</name>  
      <class>**- topic/topic**</class>  
      <componentpath>fmdita/components/dita/topic</componentpath>  
      <type>COMPOSITE</type>  
      <target>para</target>  
      <attributemap> 
         <attribute from="id" to="id" />  
      </attributemap>
   </ditaelement>
   ```

   在上述範例中，如果沒有為`task`元素定義對應，則`task`元素會對應至上述元件，因為`task`繼承自`topic`元件。

1. 當元素具有對應的元件對應時，其子元素的進一步處理由`type`決定。 例如：

   ```XML
   <ditaelement>  
      <name>title</name>  
      <class>- topic/title</class>  
      <componentpath>foundation/components/title</componentpath>  
      <type>**STANDALONE**</type>  
      <target>para</target>  
      <textprop>jcr:title</textprop>
   </ditaelement>
   ```

   `type`採用下列值：

   - COMPOSITE：子元素&#x200B;*的元素與元件*&#x200B;的對映也會繼續。

   - STANDALONE：目前專案的子專案是&#x200B;*未進一步對應*。

   在上述範例中，若`<title>`元素具有任何子元素，則不會對應至任何其他元件。 `<title>`元素的元件負責轉譯`<title>`元素內的所有子元素。

1. 如果有多個元件對應至單一DITA元素，則會選取該元素的最佳相符專案。 若要選取最佳相符元件，會考慮DITA元素的領域和結構專門化。

   如果有具有領域專門化的DITA元素，且元件對應到領域專門化，則該元件會獲得高優先順序。

   同樣地，如果有具有結構專門化的DITA元素，且元件對應結構專門化，則該元件會獲得高優先順序。

1. 您可以在元素對應中使用`<attributemap>`，將屬性值對應至對應的節點屬性。

1. `textprop`可用來將DITA元素的文字內容序列化為node屬性。 此外，它可以在元素標籤中多次使用，以將已發佈階層中多個位置的文字內容序列化。 您也可以自訂目標屬性的位置和名稱。 例如：

   ```XML
   <ditaelement> 
       <name>title</name> 
       <class>- topic/title</class> 
       <componentpath>foundation/components/title</componentpath> 
       <type>STANDALONE</type> 
       <target>para</target> 
       <textprop>**jcr:title**</textprop>
   </ditaelement>
   ```

   以上元素對應指定`<title>`元素的文字內容將會儲存為輸出節點上名為`jcr:title`之屬性的值。

1. `xmlprop`可用來將指定專案的整個XML序列化為節點屬性。 元件將可讀取此節點屬性並執行自訂轉譯。 例如：

   ```XML
   <ditaelement> 
       <name>svg-container</name> 
       <class>+ topic/foreign svg-d/svg-container</class> 
       <componentpath>fmdita/components/dita/svg</componentpath> 
       <type>STANDALONE</type> 
       <target>para</target> 
       <xmlprop>**data**</xmlprop>
   </ditaelement>
   ```

   以上專案對應指定專案`<svg-container>`的整個XML標籤將會儲存為輸出節點上名為`data`之屬性的值。

1. 有一個特殊的屬性對應，可在輸出產生程式中處理路徑解析。 例如：

   ```XML
   <attributemap> 
       <attribute from="href" to="fileReference" ispath="true" rel="source" /> 
       <attribute from="height" to="height" /> 
       <attribute from="width" to="width" />
   </attributemap>
   ```

   對於上述`attributemap`，您DITA元素中的`href`屬性將對應至名為`fileReference`的節點屬性。 現在，由於`ispath`設定為`true`，輸出產生程式會解析此路徑，然後在`fileReference`節點屬性中設定它。

   此解析如何根據屬性對應中`rel`屬性的值來決定。

   - 如果`rel=source`，則會針對目前處理中的DITA來源檔案解析`href`的值。 `href`的值已解析並置於`fileReference`屬性的值中。

   - 如果`rel=target`，則相對於根發佈位置解析`href`的值。 `href`的值已解析並置於`fileReference`屬性的值中。

   如果您不想在路徑屬性上發生任何前置處理或解析，則不需要指定`ispath`屬性。 值會依原樣複製，元件可執行所需的解析度。


### DITA元素結構描述

以下是`elementmapping.xml`檔案中DITA元素結構描述的範例：

```XML
<ditaelement>         
    <name>element_name</name>     
    <class>element_class</class>     
    <componentpath>fmdita/components/dita/component_name</componentpath>     
    <type>COMPOSITE|STANDALONE</type>      
    <attributeprop>propname_a</attributeprop>       
    <textprop>propname_t</textprop>     
    <xmlprop>propname_x</xmlprop>      
    <xpath>xpath expression string</xpath>      
    <target>head|para</target>      
    <wrapelement>div</wrapelement>      
    <wrapclass>class_name</wrapclass>      
    <attributemap>           
    <attribute from="attrname" to="propname" ispath="true|false" rel="source|target" />     
    </attributemap>     
    <skip>true|false</skip> 
</ditaelement>
```

下表說明DITA元素結構描述中的元素：

| 元素 | 說明 |
|-------|-----------|
| `<ditaelement>` | 每個對應元素的頂層節點。 |
| `<class>` | 您正在寫入元件的目標DITA元素的類別屬性。 <br>例如，DITA主題的類別屬性是： <br>`topic/topic` |
| `<componentpath>` | 對應AEM元件的CRXDE路徑。 |
| `<type>` | 可能的值： <br>- **COMPOSITE**：處理子專案以及<br>- **STANDALONE**：略過處理子專案 |
| `<attributeprop>` | 用於將序列化DITA屬性和值作為屬性對應至AEM節點。 例如，如果您有`<note type="Caution">`個元素，而對應至此元素的元件有`<attributeprop>attr_t</ attributeprop>`，則節點的屬性和值會序列化為對應AEM節點\( `attr_t`\)的`attr_t->type="caution"`屬性。 |
| `<textprop>propname_t</textprop>` | 將`getTextContent()`輸出儲存至`propname_t.`所定義的屬性&#x200B;**注意：**&#x200B;這是最佳化的屬性。 |
| `<xmlprop>propname_x </xmlprop>` | 將此節點的序列化XML儲存到由`propname_x.`定義的屬性&#x200B;**注意：**&#x200B;這是最佳化的屬性。 |
| `<xpath>` | 如果在元素對應中提供了XPath元素，則應該連同元素名稱和類別一起滿足XPath條件，才能使用元件對應。 |
| `<target>` | 將DITA元素放置在crx存放庫中的指定位置。 <br>可能的值：<br>- **head**：在標題節點下<br>- **文字**：在段落節點下 |
| `<wrapelement>` | 要將內容包裝在其中的HTML元素。 |
| `<wrapclass>` | 屬性`wrapclass.`的元素值 |
| `<attributemap>` | 包含一或多個`<attribute>`節點的容器節點。 |
| `<attribute from="attrname" to="propname" ispath="true\|false" rel="source\|target" />` | 將DITA屬性對應至AEM屬性： <br>- **`from`**： DITA屬性名稱<br>- **`to`**： AEM元件屬性名稱<br>- **`ispath`**：如果屬性是路徑值\（例如： *image*\）<br>- **`rel`**：如果路徑是來源或目標&#x200B;<br>**注意：**&#x200B;如果`attrname`以`%`開頭，則將`attrname minus '%'`對應至prop &#39; `propname`&#39;。 |

**其他附註**

- 如果您計畫覆寫預設元素對應，建議您不要在預設`elementmapping.xml`檔案中進行變更。 您應該建立新的對應XML檔案，並將檔案放置於其他位置，最好是放在您建立的自訂應用程式資料夾內。

- 在`elementmapping.xml`檔案中，有許多參考fmdita/components/dita/wrapper元件的對應專案。 包裝函式是一種泛型元件，會使用其網站節點上的屬性來產生相關的HTML，以呈現相對簡單的DITA建構。 它使用`wrapelement`屬性來產生封閉標籤，並將子轉譯委派給對應的元件。 當您只想要容器元件時，這個用法就相當實用。 您可以搭配使用Wrapper元件與`div`和`p`屬性來達到相同的效果，而不需建立可轉譯特定容器標籤（如`wrapelement`或`wrapclass`）的新元件。

- 不建議在字串JCR屬性中儲存大量文字。 輸出產生中最佳化的屬性型別計算可確保大型文字內容不會儲存為字串型別。 反之，當需要儲存大於某個臨界值的內容時，屬性的型別會變更為二進位。 預設會將此臨界值設定為512個位元組，但可以在Configuration Manager \(*com.adobe.fmdita.config.ConfigManager*\)中變更，方法是變更&#x200B;**另存為二進位臨界值**&#x200B;設定。

- 如果您計畫覆寫部分\（而非全部\）元素對應，則不需要復寫整個`elementmapping.xml`檔案。 您需要建立新的XML對應檔案，並只定義要覆寫的元素。

- 在自訂位置中建立XML檔案之後，請更新`Override Element Mapping`組合中的`com.adobe.fmdita.config.ConfigManager`設定。


## 自訂DITA map主控台 {#id188HC08M0CZ}

AEM Guides可讓您彈性擴充DITA map主控台的功能。 例如，如果您有一組與AEM Guides中可用的報表不同，您可以將這類報表新增至地圖主控台。 若要自訂地圖主控台，您必須建立AEM使用者端程式庫\（或ClientLib\），其中包含執行所需功能所需的程式碼。

>[!NOTE]
>
> 不建議直接修改頁面元件，因為產品的新版本會加以覆寫。

AEM Guides提供用於自訂地圖主控台的`apps.fmdita.dashboard-extn`類別。 每當載入地圖主控台時，就會執行並載入在`apps.fmdita.dashboard-extn`類別下建立的功能。

>[!NOTE]
>
> 如需建立AEM使用者端資料庫的詳細資訊，請參閱[使用使用者端資料庫](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/clientlibs.html)。

## 在產生輸出期間處理影像轉譯 {#id177BF0G0VY4}

AEM隨附一組預設工作流程和媒體控制代碼以處理資產。 在AEM中，有預先定義的工作流程可處理最常見MIME型別的資產處理。 一般而言，AEM會針對您上傳的每個影像，以二進位格式建立相同的多個轉譯。 這些轉譯可能大小不同、解析度不同、加上浮水印或其他已變更的特性。 如需AEM如何處理資產的詳細資訊，請參閱AEM檔案中的[使用媒體處理常式和工作流程處理Assets](https://helpx.adobe.com/experience-manager/6-5/assets/using/media-handlers.html)。

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

如果您要為輸出預設集指定不同的影像轉譯，可以使用`outputName`屬性為相同輸出型別下的特定輸出預設集定義自訂轉譯。 當您因應不同發佈情境而需要不同的影像大小或格式時，此功能會很有用。

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

在上述轉譯中，透過轉譯中定義的`outputName`屬性，ditahtml5預設集使用`cq5dam.thumbnail.319.319.png`，而若沒有`outputName`，所有HTML5輸出都使用`cq5dam.web.1280.1280.jpeg`。

如果指定的轉譯不存在，AEM Guides發佈程式會先尋找指定影像的Web轉譯。 如果找不到網頁轉譯，則會使用影像的原始轉譯。

>[!NOTE]
>
> 這些影像轉譯只會控制輸出產生。 當您開啟檔案以進行預覽或檢閱時，會使用影像的Web轉譯。

## 設定輸出記錄的自動永久刪除期間 {#id19AAI070V8Q}

產生輸出時，會建立輸出與輸出記錄。 對於大型DITA map，這些記錄可能會佔用存放庫中的大量空間。 依預設，記錄檔會儲存在存放庫的下列位置：

/var/dxml/metadata/outputHistory/

在一段時間內，所有記錄檔的集體大小可能會達到GB。 AEM Guides可讓您設定將這些記錄檔保留在存放庫中的時段。 在指定的時段後，記錄以及輸出產生歷史記錄會從存放庫中刪除。

>[!NOTE]
>
> 輸出產生歷史記錄是「輸出」標籤中「產生的輸出」清單中的記錄專案。

設定歷史記錄清除功能會影響儲存庫中所有DITA map的輸出產生。 在DITA map的「輸出」標籤中，在指定的天數之後，以及在設定中指定的時間清除歷史記錄。

>[!NOTE]
>
> 移除記錄檔和輸出產生歷程記錄對產生的輸出沒有任何影響。

執行以下步驟，設定清除輸出歷史記錄和日誌的日期和時間：

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


## 變更最近產生的輸出清單限制 {#id1679JH0H0O2}

您可以變更DITA map在「輸出」標籤中顯示的已產生輸出最大數目。 依預設，會顯示最後25個產生的輸出清單。 若要變更要在清單中顯示的輸出數目，請更新&#x200B;**組合中的**&#x200B;輸出清單限制`com.adobe.fmdita.config.ConfigManager`設定。

>[!TIP]
>
> 如需有關使用輸出歷程記錄的最佳實務，請參閱「最佳實作指南&#x200B;*appendix.md\#*」中的[輸出歷程記錄](appendix.md#)區段。

## 輸出產生效能最佳化 {#id176LB050VUI}

AEM Guides可讓您設定輸出產生程式集區大小，以控制同時執行的輸出產生程式數目。 依照預設，處理集區大小會設定為您的系統中可用的處理核心數目加上一個。 如果您想要循序發佈，可將此值變更為1。 在這種情況下，會執行第一個發佈任務，並將下一個發佈任務儲存在發佈佇列中。

若要變更輸出產生處理集區大小，請更新&#x200B;**組合中的**&#x200B;產生集區大小`com.adobe.fmdita.publish.manager.PublishThreadManagerImpl`設定。
