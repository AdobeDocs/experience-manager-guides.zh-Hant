---
title: 原生PDF | 產生PDF輸出
description: 瞭解如何使用原生PDF發佈、建立和產生PDF輸出預設集、產生原生PDF輸出後下載暫存檔案，以及在AEM Guides中使用語言變數。
exl-id: ec3d59b7-1dda-4fd1-848e-21d8a36ff5e4
feature: Publishing, Web Editor, Native PDF Output
role: User
source-git-commit: be06612d832785a91a3b2a89b84e0c2438ba30f2
workflow-type: tm+mt
source-wordcount: '3196'
ht-degree: 0%

---

# 發佈PDF輸出

使用AEM Guides，您可以產生個別主題的PDF或整個地圖檔案。 您可以使用下列三種方法之一，以PDF格式發佈您的內容：

* **DITA-OT**

使用此方法可從地圖控制面板產生地圖的PDF輸出。 您可以針對在地圖控制面板中開啟的地圖，建立輸出預設集，在產生PDF之前設定發佈屬性。 若要建立或編輯輸出預設集，請使用 *瞭解輸出預設集* 中的區段 [AEM Guidesas a Cloud Service使用手冊](https://helpx.adobe.com/content/dam/help/en/xml-documentation-solution/cs-apr-22/XML-Documentation-for-Adobe-Experience-Manager_CS_User-Guide_EN.pdf).

如需有關使用DITA-OT方法產生PDF的詳細資訊，請參閱 [使用DITA-OT產生PDF](https://help.adobe.com/en_US/xml-documentation-for-adobe-experience-manager/index.html#t=DXML-master-map%2Fgenerate-output-pdf.html).

* **FrameMaker Publishing Server(FMPS)**

使用此方法，不僅從DITA內容產生PDF輸出，還從AEM存放庫中可用的FrameMaker檔案(.book和.fm)產生輸出。 您可設定輸出預設集來建立PDF，並使用FrameMaker Publishing Server(FMPS)發佈。 您可以針對PDF和其他格式來設計和設定輸出的外觀，並將它們儲存在設定檔案(.sts)中。 然後FMPS會使用此設定檔案來產生DITA map或.book檔案的輸出。 若要建立或編輯輸出預設集，請參閱  *瞭解輸出預設集* 中的區段 [AEM Guidesas a Cloud Service使用手冊](https://helpx.adobe.com/content/dam/help/en/xml-documentation-solution/cs-apr-22/XML-Documentation-for-Adobe-Experience-Manager_CS_User-Guide_EN.pdf).

如需有關設定FMPS的詳細資訊，請參閱 [從FrameMaker檔案產生輸出](https://help.adobe.com/en_US/xml-documentation-for-adobe-experience-manager/index.html#t=DXML-master-map%2Ffm-output-generatation.html).

* **原生PDF發佈**

此方法可根據W3C CSS3和CSS分頁媒體標準產生功能豐富的PDF輸出。 透過原生PDF發佈，您可以使用範本來設定內容的版面配置和樣式，並套用各種設定來微調PDF。 此外，您可以使用範本編輯器修改和建立自己的範本。

如需原生PDF發佈的詳細資訊，請參閱 [使用原生PDF發佈](#native-pdf-publishing).


## 使用原生PDF發佈 {#native-pdf-publishing}

製作內容時，務必確保內容已針對檢視、編輯和列印進行最佳化。 使用諸如W3C CSS3之類的內容樣式標準和諸如Size、margin、orientation、page breaks、headers、footer和page numbering等頁面定義屬性的CSS分頁媒體標準，您可以設定PDF檔案的檢視和版面配置，以確保一致性和可用性。 原生PDF發佈功能會使用這些標準來產生PDF。

透過原生PDF發佈，您可以使用預先定義的範本來確保內容版面配置與結構的一致性、套用樣式表以改變輸出的外觀、最佳化PDF、設定印表機標籤、允許熒幕助讀程式支援、設定PDF一致性、嵌入字型等等。

使用原生PDF發佈來產生PDF有兩個方面：

* 使用範本將樣式套用至內容、設定版面配置及各種設定以微調您的PDF。 作者可以選擇使用/修改提供的範例範本，或建立自訂範本，並設定發佈者和開發人員使用的進階設定選項。

* 建立或設定PDF輸出預設集，以控制PDF設定。 建立PDF輸出預設集後，即可產生PDF。

如需詳細資訊，請參閱 [產生PDF輸出](#generate-pdf-output).

## 建立PDF輸出預設集 {#create-output-preset}

產生PDF輸出的第一個步驟是建立PDF輸出預設集，這是指派給地圖的發佈屬性的集合。 您可以為在「地圖檢視」面板中開啟的任何地圖建立輸出預設集，或設定現有預設集以快速產生相同地圖的PDF。

從PDF輸出預設集中，您可以選取範本、套用條件、設定限制以控制使用者與您的PDF互動的方式，以及設定進階設定，例如壓縮、符合等等。

若要建立或設定PDF輸出預設集：

1. 在輸出標籤中，按一下 **預設集** 在左側邊欄中。
「預設集」面板隨即開啟。 <br>
<img src="assets/preset-panel.png" alt="預設面板" width="600">

1. 在輸出中 **預設集** 面板，執行下列任一項作業：
   * 連按兩下預先定義的PDF輸出預設集以檢視它。
   * 按一下「+」圖示以針對 **預設集** 新增輸出預設集： **型別：PDF**

1. 若要設定現有PDF預設集的設定：
   * 按一下  **選項** ![選項](assets/options.svg) 圖示並選取所需的輸出預設集旁的 **編輯**.
您可在以下位置使用下列設定： **一般**， **中繼資料**， **版面**， **安全性**、和 **進階** 索引標籤以設定PDF輸出預設集：

**一般**

用於指定基本輸出設定，例如指定輸出路徑、PDF檔案名稱等。

| 設定 | 說明 |
| --- | --- |
| **輸出路徑** | AEM存放庫內儲存PDF輸出的路徑。 確定輸出路徑不在專案資料夾內。 如果保留為空白，輸出會在預設DITA map輸出位置中產生。<br>您也可以使用下列現成的變數來定義輸出路徑。 您可以使用單一變數或變陣列合來定義此選項。 <br> `${map_filename}`：使用DITA map檔案名稱來建立目的地路徑。 <br> `${map_title}`：使用DITA map標題建立目的地路徑。 <br>`${preset_name}`：使用輸出預設集名稱建立目的地路徑。 <br> `${language_code}`：使用對應檔案所在的語言代碼來建立目的地路徑。 <br> `${map_parentpath}`：使用對應檔案的完整路徑來建立目的地路徑。  <br>`${path_after_langfolder}`：使用語言資料夾之後的對應檔案路徑來建立目的地路徑。 |
| **PDF檔案** | 指定檔案名稱以儲存PDF。 依預設，PDF檔案名稱會新增DITA map名稱以及預設名稱。 例如，ditamap是「TestMap」，而預設集的名稱是「preset1」，則pdf的預設名稱將是「TestMap_preset1.pdf」。 <br>您也可以使用下列現成可用的變數來定義「PDF檔案」。 您可以使用單一變數或變陣列合來定義此選項。 <br>`${map_filename}`<br>`${map_title}`<br>`${preset_name}` <br> `${language_code}`。 |
| **套用條件，使用** | 對於條件式內容，請從下列選項中選擇，以根據這些條件產生PDF輸出： <br><ul> <li> **未套用任何** 如果您不想在地圖和來源內容上套用任何條件，請選取此選項。 <br><li> **Ditaval檔案** 選取DITAVAL檔案以產生條件式內容。 若要選取，請按一下「條件預設集」並找出檔案。 <br> <li> **條件預設集** 從下拉式清單中選取條件預設集，以在發佈輸出時套用條件。 如果您已為DITA map檔案新增條件，則會顯示此選項。 條件設定可在DITA map主控台的「條件預設集」標籤中使用。 若要進一步瞭解條件預設集，請參閱 [使用條件預設集](https://help.adobe.com/en_US/xml-documentation-for-adobe-experience-manager/index.html#t=DXML-master-map%2Fgenerate-output-use-condition-presets.html). <br> </ul> |
| **使用基準線** | 如果您已經為選取的DITA map建立基準線，請選取此選項以指定要發佈的版本。 另請參閱 [使用基準線](https://help.adobe.com/en_US/xml-documentation-for-adobe-experience-manager/index.html#t=DXML-master-map%2Fgenerate-output-use-baseline-for-publishing.html) 以取得更多詳細資料。 |
| **建立已發佈版本間具有變更列的PDF** | 使用下列選項來建立一個PDF，使用變更列顯示兩個版本之間的內容差異：   <br><ul><li> **先前版本的基準線** 選擇要與目前版本或其他基準比較的基準版本。 PDF中會顯示變更列，以指出修改的內容。 變更列是垂直線，以視覺化方式識別新內容或修訂的內容。 變更列會顯示在已插入、變更或刪除的內容左側。 <br> **注意**：如果您選取 **使用基準線** 並選擇要發佈的基準線，則會比較兩個選取的基準線版本。 例如，如果您選擇底下的「比較基準1.3版」 **使用基準線**，和下的1.1版 **先前版本的基準線**，則會比較基準版本1.1與基準版本1.3。 <br><li> **顯示新增的文字** 選取以綠色和底線顯示插入的文字。 依預設，會選取此選項。 <br> <li> **顯示刪除的文字** 選取以紅色顯示刪除的文字，並以刪除線標示。 依預設，會選取此選項。 <br>**注意** 您也可以使用樣式表自訂變更列、插入內容或刪除內容的樣式。<br></ul> |
| **貼文產生工作流程** | 選取以顯示包含AEM中設定之所有工作流程的下拉式清單。 您可以選取在PDF產生工作流程完成後要執行的工作流程。 |

**中繼資料**

中繼資料是內容的說明或定義。 中繼資料有助於內容管理，也有助於在網際網路上搜尋檔案。

使用「中繼資料」標籤來設定中繼資料欄位，例如作者姓名、檔案標題、關鍵字、版權資訊以及PDF輸出的其他資料欄位。 您也可以為PDF輸出新增自訂中繼資料。

此中繼資料會對應至輸出PDF之「檔案屬性」內「說明」標籤中的中繼資料。

**注意**：此中繼資料會覆寫在書籍層級定義的中繼資料。

<img src="assets/pdf-metadata.png" alt="中繼資料標籤" width="600">

從輸出預設集， **選取PDF** > **中繼資料** 以新增及自訂中繼資料選項。
* **提供XMP檔案**

  中繼資料欄位可透過匯入直接填入 [XMP](https://www.adobe.com/products/xmp.html) （可延伸中繼資料平台）檔案。 您可以從這裡下載範例XMP檔案。

[下載](assets/SampleXMP.xmp)

  或者，您可以使用Adobe Acrobat產生XMP檔案。
   1. 按一下 **檔案** > **屬性** 在Acrobat中。
   1. 在 **說明**，按一下 **其他中繼資料**.
   1. 從左側面板中選取 **進階**.
   1. 按一下 **儲存**.

  XMP檔案會儲存在裝置上。

* **提供中繼資料名稱和值**

   1. 從下拉式清單中選取以新增名稱，或直接在名稱欄位中輸入以新增自訂中繼資料。
   1. 輸入中繼資料的值，然後按一下「+」圖示。
中繼資料會新增至PDF的中繼資料清單中。

您也可以使用變數來定義中繼資料值。  您可以使用為DITA map或bookmap檔案定義的中繼資料作為變數。 中繼資料可在下找到 `/jcr:content/metadata` DITA map或書籤地圖檔案的節點。
使用變數時，會從中繼資料屬性中挑選變數值。

若要使用變數，您必須在以下位置定義它： `${<variable>}` 格式。

例如，在/中定義的其中一個中繼資料屬性`jcr:content/metadata` 節點為
`dc:title`. 您可以指定 `${dc:title}`，而標題值會用於最終輸出中。

您可以使用單一或一組變數來定義中繼資料。 例如 `${dc:title} ${dc:docstate}`。您也可以使用變數和字串的組合。  例如，`View ${dc:title} in ${dc:language}`。

使用語言變數來定義中繼資料屬性的本地化值。 系統會根據您選擇的語言，在PDF輸出中自動挑選當地語系化的值。 例如，您可以將「作者」列印為英文的中繼資料值，並將「Autorin」列印為德文。

格式： `${lng:<variable name>}`. 例如， `${lng:author-label}` 位置 `author-label` 是語言變數。

暫留在 <img src="./assets/info-details.svg" alt= "資訊圖示" width="25"> 接近選項以檢視更多相關詳細資訊。


**版面**

用來設定頁面配置，並指定PDF輸出的頁面檢視選項，例如「頁面顯示」和設定「縮放等級」。

| 設定 | 說明 |
| --- | --- |
| **PDF範本** | PDF範本提供清晰的結構，可用於定義頁面配置、內容樣式以及套用各種設定至PDF輸出。 從「PDF範本」下拉式選項中選取，以選擇您偏好的範本。 <br> 您也可以選取 **瀏覽範本** <img src="./assets/browse-templates-icon.svg"  alt= "瀏覽範本圖示" width="25">  以選擇範本。 在 **選取PDF範本** 對話方塊您也可以預覽縮圖，並檢視所選範本的標題和說明。 |
| **頁面顯示** | 使用「頁面顯示」進行頁面檢視，以顯示PDF開啟時的顯示方式。 從「頁面顯示」下拉式選項中選取，以選擇偏好的檢視。 <br><ul><li> **預設**  依照使用者電腦上的PDF檢視器預設設定顯示。  <br> <li> **單頁檢視** 一次顯示一個頁面。   <br> <li> **單頁捲動** 在連續的垂直欄中顯示單一頁面。  <br> <li> **兩頁檢視** 一次並排顯示兩頁跨頁。.<br> <li> **兩頁捲動** 以連續捲動並排顯示兩頁跨頁。 </ul> |
| **縮放** | 選取以調整頁面檢視的大小，該檢視顯示PDF在開啟時的顯示方式。  <br><ul><li> **預設** 依照使用者電腦上的PDF檢視器預設設定顯示    <br> <li> **100%** 讓頁面以實際大小顯示。     <br> <li> **符合頁面** 讓頁面寬度和高度能容納檔案窗格。.<br> <li> **符合頁面寬度** 讓頁面寬度填滿檔案窗格的寬度。  <br> <li> **符合頁面高度** 讓頁面高度填滿檔案窗格的高度。 </ul> |

**安全性**

新增開啟和讀取檔案的限制，以Protect您的PDF。 使用下列選項以避免未經授權的存取。

| 設定 | 說明 |
| --- | --- |
| **設定密碼以開啟檔案** | 選取以新增安全密碼以檢視您的PDF檔案。 在「 」中指定密碼 **使用者密碼** 欄位。 使用者只能透過輸入在此欄位中提供的密碼來開啟PDF。 |
| **設定檔案限制** | 選取「 」以限制使用者與您的PDF互動的方式。 在「 」中指定密碼 **擁有者密碼** 讓以下限制設定運作的欄位。  <br><ul><li> **列印** 選取以允許使用者列印PDF。 <br> <li> **草稿品質列印** 選取以允許使用者以較低的解析度列印PDF。  <br> <li> **內容複製** 選取以允許使用者從PDF複製內容。   <br> <li> **註解** 選取以允許使用者在PDF中新增附註或註解。  <br> <li> **內容修改** 選取以允許使用者變更PDF中的內容。  <br> <li> **為協助工具複製內容** 選取以允許熒幕助讀程式以PDF閱讀和導覽內容。  <br>  **檔案元件** 選取以允許使用者在PDF中插入頁面。  <br> **注意**：使用者需要輸入擁有者密碼，才能變更Adobe Acrobat中「檔案>屬性」的任何限制。 |

**進階**

使用下列選項來指定合併PDF、使用壓縮、選取規範遵循標準等的進階設定。

| 設定 | 說明 |
| --- | --- |
| **建立無障礙（標籤）PDF** | 選取此選項即可產生含有標籤的PDF。 標籤的PDF可讓熒幕助讀程式更輕鬆地閱讀及導覽內容、超連結、書籤等。 例如，如果表格已加上標籤，熒幕助讀程式會知道它正在讀取表格，而不只是行與文字。 |
| **目錄中包含的合併PDF** | 選取此選項，將現有PDF作為資源檔案新增至DITA map中，以將它們合併到輸出中。 PDF將會插入地圖中顯示的位置，頁面也會隨之增加。 |
| **嵌入使用的字型** | 在使用可能未安裝在使用者電腦上的字型時，請選取此選項。 選取此選項後，使用的字型會內嵌於PDF中，確保使用者可看到預期的PDF，即使字型未安裝在他們的電腦上。 <br> **注意**：只有當字型供應商提供的設定允許嵌入時，才能嵌入字型。 在內嵌字型之前，請確認您具備必要的設定或授權。 |
| **使用自動斷字** | 啟用自動連字功能後，行尾的文字會在文法正確位置以連字型大小斷字。 |
| **啟用JavaScript** | 如果您有JavaScript程式碼，而且想要在產生PDF之前用來動態轉換內容，請啟用此選項。 |
| **內嵌多媒體檔案** | 選取此選項可將任何音訊、視訊和互動式內容納入PDF。 |
| **使用完全壓縮來最佳化PDF大小** | 如果要壓縮/縮小大型PDF的大小，請選取此選項。 請記住，壓縮PDF可能會降低檔案品質。 |
| **使用影像壓縮來最佳化PDF大小** | 如果要在PDF中壓縮/減少使用的影像大小，請選取此選項。 請記住，壓縮影像可能會降低影像品質。 |
| **使用自訂解析度（每英吋畫素）** | 這是以畫素/英吋為單位的頁面顯示解析度。 在選取此選項時顯示的欄位中輸入偏好值。 預設值為每英吋96畫素。 設定較高的值以在一英吋內容納更多內容，反之亦然（如果您設定較低的值）。 |
| **顯示浮水印** | 選取此選項可在輸出中重疊浮水印。 您可以在文字方塊中輸入新的文字字串，其字元大小寫如您所需。 <br><br>使用靜態文字或語言變數來發佈浮水印的本地化版本。  系統會根據您選擇的語言，在PDF輸出中自動挑選當地語系化的值。 例如，您可以將&#39;Publisher&#39;列印成英文的浮水印，並將&#39;Auteure&#39;列印成法文。  <br> 格式： `${lng:<variable name>}`. 例如， `$ {lng:publisher-label}` 位置 `publisher-label` 是語言變數。 <br> 暫留在 <img src="./assets/info-details.svg" alt= "資訊圖示" width="25"> 接近選項以檢視更多相關詳細資訊。 |
| **啟用MathML公式** | 選取此選項以呈現內容中出現的MathML方程式。 否則預設會忽略方程式。 |
| **下載暫存檔案** | 如果您想要下載在產生原生HTML輸出時建立的臨時PDF檔案，請選取此選項。 您稍後可以在產生輸出後下載暫存檔案。 |
| **PDF符合性** | 這是您打算儲存PDF以確保其相容的標準。 從下拉式清單中選取，以從可用的PDF標準清單中選擇。 如需支援標準的詳細資訊，請參閱 [關於PDF標準](https://helpx.adobe.com/acrobat/using/pdf-conversion-settings.html#about_pdf_x_pdf_e_and_pdf_a_standards). |


## 產生PDF輸出 {#generate-pdf-output}

設定輸出預設集後，您就可以使用 **產生預設集** 功能。

1. 在 **作者** 索引標籤中，選取 **存放庫** 檢視。\
   如此將可開啟「存放庫」面板。

1. 在「存放庫」面板中，開啟DITA map檔案，位於 **地圖檢視**.

1. 在 **輸出** 標籤，按一下 **預設集** 以檢視「預設集」面板。
若要建立或設定輸出預設集，請參閱 [建立PDF輸出預設集](#create-output-preset).
1. 若要儲存您的設定，請按一下 **全部儲存** ![全部儲存](assets/SaveFloppy_icon.svg) 圖示加以調整，此圖示位於「輸出」檢視中標準工具列的左上角。
1. 按一下 **產生預設集** ![產生預設集](assets/generate-output.svg) 圖示加以調整。
您可以在「輸出預設集」面板中檢視所選輸出預設集旁的進度列。
1. 輸出產生完成後，按一下  **檢視輸出** ![檢視輸出](assets/view-output.svg) 圖示來檢視輸出。\
   A **成功** 對話方塊會顯示在熒幕右下角。
如果輸出不成功，則會顯示以下錯誤訊息。
<img src="assets/error-log.png" alt="錯誤記錄" width="250">

若要檢視錯誤記錄，請按一下 **關閉**，將游標停留在選取的預設集標籤上，然後按一下 ![選項](assets/options.svg) **選項** > **檢視記錄**.

### 產生原生PDF輸出後下載暫存檔案

如果您選取 **下載暫存檔案** 選項中，您也可以下載在產生原生HTML輸出時建立的臨時PDF檔案。 產生輸出後，您就可以使用 **下載暫存檔案** ![下載暫存檔案](assets/native-pdf-download-temporary-files-icon.svg)圖示加以調整。 此功能可協助您檢視臨時HTML樣式和版面，並協助您根據需求修正或變更CSS樣式。


>[!NOTE]
>
> 此 **下載暫存檔案**  ![下載暫存檔案](assets/native-pdf-download-temporary-files-icon.svg) 圖示只有在您使用預設集產生最後一個PDF輸出時才會顯示，您已在其中選取 **進階** 標籤。



### 使用語言變數

AEM Guides也支援語言變數。 選取 **語言變數** <img src="./assets/language-variables.svg" width="25">  在左側面板中定義現成標籤的當地語系化版本，例如PDF輸出中的「注意」、「警告」和「警告」或靜態文字。 如需詳細資訊，請參閱 [支援語言變數](../native-pdf/native-pdf-language-variables.md).

