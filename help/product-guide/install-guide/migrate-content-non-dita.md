---
title: 移轉非DITA內容
description: 瞭解如何移轉非DITA內容
exl-id: 4597d1be-5426-4eba-8490-e42d0e565427
feature: Migration
role: Admin
level: Experienced
source-git-commit: 77756fe76c3d615683dcd62627adfcf18bcbb633
workflow-type: tm+mt
source-wordcount: '2393'
ht-degree: 0%

---

# 移轉非DITA內容 {#id181AH0R02HT}

本節將引導您完成移轉程式，將非DITA檔案移轉至DITA格式。 AEM Guides提供以下來源的移轉：

- [Microsoft Word](#id1949B040Z5Z)

- [InDesign檔案](#id195AD0B0K5Z)

- [XHTML](#id1949B04L0Y4)

- [非結構化FrameMaker檔案](#id1949B050VUI)

- [任何其他結構化檔案](#id1949B0590YK)


## 移轉Microsoft Word檔案 {#id1949B040Z5Z}

AEM Guides可讓您將現有的Word檔案\(`.docx`\)移轉至DITA主題型別檔案。 您必須指定輸入和輸出資料夾位置以及其他引數，檔案會轉換為DITA檔案。 視內容而定，您可以有.dita檔案和.ditamap檔案。

為了能夠成功轉換Word檔案，您的檔案應該結構良好。 例如，您的檔案應該有標題，然後是標題1、標題2等等。 每個標題都應該有一些內容。 如果您的檔案結構不正確，程式可能無法如預期運作。

依預設，AEM Guides會使用[Word對DITA \(Word2DITA\)轉換架構](http://www.dita4publishers.org/docs/repo/org.dita4publishers.word2dita/word2dita/word2dita-intro.html)。 此轉換依存於[樣式對標籤對應](http://www.dita4publishers.org/docs/repo/org.dita4publishers.word2dita/word2dita/style-to-tag-map-overview.html)組態檔。 為了能夠成功使用Word2DITA轉換，您必須考慮以下准則來準備Word檔案以進行轉換：

>[!NOTE]
>
> 如果您在預設的樣式對標籤對應組態檔案中進行任何變更，則必須更新並使用確認已更新樣式對應的准則。

- 確定您的檔案以標題開頭；此標題已對應到DITA map標題。 此外，「標題」後面必須接著一些一般內容。

- 在標題之後，應該有標題1、標題2等。 每個標題中都必須有一些內容。 標題會轉換為新的概念型別主題。 產生之主題的階層會根據檔案中的標題層級而定，例如，標題1會位在標題2之前，而標題2會位在標題3內容之前。

- 檔案必須至少有一個標題型別內容。

- 確定您沒有任何分組的影像。 如果您已將檔案中的影像分組，請取消所有此類影像的分組。

- 移除所有頁首和頁尾。

- 粗體、斜體和底線等內嵌樣式會轉換為`b`、`i`和`u`元素。

- 所有已排序和未排序的清單都會轉換為`ol`和`ul`元素。 這也適用於巢狀清單、表格、附註或註腳內的清單。

- 所有超連結都會轉換為`xref`。

- 轉換檔案的檔案名稱是以標題文字及檔案編號為基礎。 檔案編號是根據檔案中標題文字位置的連續數字。 例如，如果標題文字是「範例標題」，且是檔案中的第10個標題，則此主題的結果檔案名稱將類似於Sample\_Heading\_10.dita。


執行下列步驟，將您現有的Word檔案轉換為DITA主題型別檔案：

1. 登入AEM並開啟CRXDE Lite模式。

1. 導覽至下列位置可用的預設組態檔：

   `/libs/fmdita/config/w2d_io.xml`

1. 在`config`節點內建立`apps`資料夾的覆蓋節點。

1. 導覽至`apps`節點中可用的組態檔：

   `/apps/fmdita/config/w2d_io.xml`

   `w2d_io.xml`檔案包含下列可設定的引數：

   - 在`inputDir`元素中，指定可以使用來源Word檔案的輸入資料夾位置。 例如，如果您的Word檔案儲存在`wordtodita`資料夾中名為`projects`的資料夾中，則指定位置為： `/content/dam/projects/wordtodita/`

   - 在`outputDir`元素中，指定輸出資料夾的位置，或保留預設輸出位置以儲存轉換的DITA檔案。 如果DAM上不存在指定的輸出資料夾，則轉換工作流程會建立輸出資料夾。

   - 針對`createRev`專案，指定是否要建立新版本的轉換DITA主題\(`true`\)，或不建立\(`false`\)。

   - 在`s2tMap`元素中，指定對應檔案的位置，該對應檔案包含Word檔案樣式到DITA元素的對應。 預設對應儲存在檔案中，檔案位於：

     ```XML
     /libs/fmdita/word2dita/word-builtin-styles-style2tagmap.xml
     ```

     >[!NOTE]
     >
     > 如需有關`word-builtin-styles-style2tagmap.xml`檔案的結構以及如何自訂的詳細資訊，請參閱[DITA For Publishers使用手冊](http://www.dita4publishers.org/docs/repo/org.dita4publishers.word2dita/word2dita/style-to-tag-map-overview.html)中的&#x200B;*樣式到標籤對應*。

   - 在props2Propagate元素中，指定應傳遞至DITA map的屬性。 必須使用此屬性，才能將預設中繼資料（例如dc:title、dc:subject、dam:keywords、dam:category）從檔案中繼資料傳遞至轉換的DITA資產。

1. 儲存 `w2d_io.xml` 檔案。

1. 在`w2d_io.xml`檔案中設定必要的引數後，登入AEM並開啟Assets UI。

1. 導覽至輸入資料夾位置\(`wordtodita`\)。

1. 將來源Word檔案上傳至此資料夾。 如需在DAM上傳內容的資訊，請參閱[上傳現有DITA內容](migrate-content-upload-existing-dita-content.md#)。


使用`config` `/config`區塊，您可以定義一或多個轉換組態區塊。 會執行轉換工作流程，並以DITA主題形式的最終輸出儲存在`outputDir`元素中指定的位置。

## 移轉Adobe InDesign檔案 {#id195AD0B0K5Z}

AEM Guides可讓您轉換InDesign檔案。 與FrameMaker類似，InDesign也可讓您建立非結構化和結構化的檔案。 非結構化檔案使用段落和字元樣式來格式化內容。 結構化檔案使用元素及其對應的屬性。

轉換程式需要將段落和字元樣式格式對應到相關的DITA元素。 同樣地，如果是結構化檔案，對應檔案將包含具有DITA元素和屬性的InDesign元素和屬性的一對一對應。

轉換程式涉及後端中的下列動作：

- *InDesign標籤語言* \(IDML\)檔案已解壓縮至工作目錄。
- 會讀取designmap.xml檔案，以找出個別InDesign劇本。
- 所有內文都會合併至單一XML例項，捨棄「空白」內文。
- 所有內嵌圖形都會匯出。
- 將標準結構（例如表格和圖形）預先轉換成DITA格式。
- 根據對應檔案將樣式或結構對應到最終輸出。
- 建立及驗證個別DITA主題與DITA map檔案。
- 刪除暫存檔案。

大致上，轉換程式需要您[準備InDesign檔案以進行轉換](appendix.md#id195DBF0045Z)和[準備對應檔案以便InDesign移轉至DITA](appendix.md#id194AF0003HT)，然後您需要遵循指定的程式來執行轉換程式。

執行以下步驟，將您現有的InDesign檔案轉換為DITA主題型別檔案：

1. 登入AEM並開啟CRXDE Lite模式。

1. 導覽至下列位置可用的預設組態檔：

   `/libs/fmdita/config/idml2dita_io.xml`

1. 若要根據您的需求建立自訂設定，請在`config`節點內建立`apps`資料夾的覆蓋節點。

1. 將下列檔案或資料夾從`libs`資料夾複製到apps資料夾：

   - `/fmdita/config/idml2dita_io.xml`
   - `/fmdita/idml2dita/config`
   - `/fmdita/idml2dita/xsl`

1. 導覽至`apps`節點中可用的組態檔：

   `/apps/fmdita/config/idml2dita_io.xml`

1. 在`idml12dita`檔案的`idml2dita_io.xml`資料夾中，新增設定對應。
1. 在`idml2dita_io.xml`檔案中新增下列屬性：

   ```
   <entry key="idml2DitaConfig">/apps/fmdita/idml2dita/config</entry>
   
   <entry key="idml2DitaXsl">/apps/fmdita/idml2dita/xsl</entry>
   ```

在`idml2dita_io.xml`檔案中設定下列引數：

- 在`inputDir`元素中，指定可使用來源InDesign檔案的輸入資料夾位置。 例如，如果您的InDesign檔案儲存在`indesigntodita`資料夾中名為`projects`的資料夾中，則指定位置為： `/content/dam/idmlfiles/indesigntodita/`

- 在`outputDir`元素中，指定輸出資料夾的位置，或保留預設輸出位置以儲存轉換的DITA檔案。 如果DAM上不存在指定的輸出資料夾，則轉換工作流程會建立輸出資料夾。

- 在`mapStyle`元素中，指定對應檔案的位置，該對應檔案包含InDesign檔案樣式到DITA元素的對應。 預設對應儲存在檔案中，檔案位於：

```XML
    /stmap.adobeidml.xml
```

>[!NOTE]
>
> 如需`stmap.adobeidml.xml`檔案結構以及如何自訂的詳細資訊，請參閱[附錄](appendix.md#id194AF0003HT)中的&#x200B;*準備InDesign到DITA移轉的對映檔案*&#x200B;區段。

1. 儲存 `idml2dita_io.xml` 檔案。

1. 在`idml2dita_io.xml`檔案中設定必要的引數後，登入AEM並開啟Assets UI。

1. 導覽至輸入資料夾位置\(`indesigntodita`\)。

1. 將來源InDesign檔案上傳至此資料夾。 如需在DAM上傳內容的資訊，請參閱[上傳現有DITA內容](migrate-content-upload-existing-dita-content.md#)。


## 移轉XHTML檔案 {#id1949B04L0Y4}

AEM Guides可讓您將現有的XHTML檔案轉換為DITA主題型別檔案。 您需要指定輸入和輸出資料夾位置以及其他引數，檔案會轉換為DITA格式。 轉換結構化HTML檔案有兩種方法：

- 將所有檔案上傳到輸入資料夾，或
- 建立包含所有檔案及媒體檔案的ZIP檔，並將其上傳至輸入資料夾。 這種方法通常用於一組相互連結的HTML檔案，而且有一個目錄\(index.html\)。 index.html檔案包含集合中所有HTML檔案的連結。

無論您是個別上傳所有檔案，還是以ZIP壓縮包形式上傳所有檔案，轉換程式都會在HTML檔案與產生的DITA檔案之間建立一對一的對應。 這基本上表示會針對輸入資料夾中的每個.html檔案建立.dita檔案。

在ZIP檔案中上傳檔案時，必須考量下列幾點：

- 所有參考的主題都應放在ZIP檔案中。

- 所有參照的媒體檔案應該使用相對連結在主題檔案中參照。

- 建立index.html檔案，並將連結新增至您要在目錄中新增的主題。 此index.html檔案用於建立DITA map檔案。 在index.html檔案中，您也可以建立巢狀主題清單，如下列程式碼範例所示：

  ```XML
  <?xml version="1.0" encoding="UTF-8"?>
  <html
  xmlns="http://www.w3.org/1999/xhtml">
      <head>
          <title>Sample Index File</title>
      </head>
      <body>
          <h1>Sample Index</h1>
          <div class="content">
              <ul class="book">
                  <li class="topicref">
                      <a href="Topic1.html">Topic 1</a>
                      <ul class="book">
                          <li class="topicref">
                              <a href="Topic1-1.html">Topic 1.1</a>
                          </li>
                          <li class="topicref">
                              <a href="Topic1-2.html">Topic 1.2</a>
                          </li>
                      </ul>
                  </li>
                  <li class="topicref">
                      <a href="Topic2.html">Topic 2</a>
                  </li>
              </ul>
          </div>
      </body>
  </html>
  ```

  請注意，每個`ul`標籤都必須將`class`屬性設定為`book`。 同樣地，每個`li`標籤的`class`都必須設定為`topicref`。

- 如果您使用內嵌樣式，請在XHTML檔案中將內嵌樣式轉換為CSS型樣式類別。 然後使用樣式屬性對應，將這些以類別為基礎的樣式轉換成轉換的DITA檔案中的DITA `outputclass`屬性。

  從這些DITA檔案產生HTML或AEM Site輸出時，`outputclass`屬性可用於在產生的HTML或AEM Site上套用樣式類別，以符合您的來源HTML內容。


除了建立ZIP檔案的考量以外，您的XHTML檔案也必須結構良好。 例如，您的檔案應該有&#x200B;*標題*，後面接著&#x200B;*標題1*、*標題2*，依此類推。 每個標題都應該有一些內容。 如果您的檔案結構不正確，移轉程式可能無法如預期運作。

若要將現有的XHTML檔案轉換為DITA主題，請執行下列步驟：

1. 登入AEM並開啟CRXDE Lite模式。

1. 導覽至下列位置可用的預設組態檔：

   `/libs/fmdita/config/h2d_io.xml`

1. 在`config`節點內建立`apps`資料夾的覆蓋節點。

1. 導覽至`apps`節點中可用的組態檔：

   `/apps/fmdita/config/h2d_io.xml`

   `h2d_io.xml`檔案包含下列可設定的引數：

   - 在`inputDir`元素中，指定可取得來源XHTML檔案的輸入資料夾位置。 例如，如果您的XHTML檔案儲存在`xhtmltodita`資料夾中名為`projects`的資料夾中，則指定位置為： `/content/dam/projects/xhtmltodita/`

   - 在`outputDir`元素中，指定輸出資料夾的位置或保留預設輸出位置。 如果DAM上不存在指定的輸出資料夾，則轉換工作流程會建立輸出資料夾。

   - 針對`createRev`專案，指定是否要建立新版本的轉換DITA主題\(`true`\)，或不建立\(`false`\)。

1. 儲存 `h2d_io.xml` 檔案。

1. 在`h2d_io.xml`檔案中設定必要的引數後，登入AEM並開啟Assets UI。

1. *\（選擇性\）*&#x200B;您也可以將相關連結區段新增至轉換的檔案。 執行以下步驟來啟用此功能：

   >[!NOTE]
   >
   > 依預設，轉換後的檔案中不會建立相關連結區段。

   1. 導覽至下列位置的h2d.xsl檔案：

      /libs/fmdita/html2dita/

   2. 搜尋下列引數：

      `<xsl:param name="generate-related-links" select="false()"/>`

   3. 將上述引數的值設定為`true()`。
   4. 儲存並關閉檔案。
1. 導覽至輸入資料夾位置\(`xhtmltodita`\)。

1. 將來源XHTML檔案上傳至此資料夾。 如需在DAM上傳內容的資訊，請參閱[上傳現有DITA內容](migrate-content-upload-existing-dita-content.md#)。


使用`<config> </config>`區塊，您可以定義一或多個轉換組態區塊。 會執行轉換工作流程，並以DITA主題形式的最終輸出儲存在`outputDir`元素中指定的位置。

## 移轉非結構化FrameMaker檔案 {#id1949B050VUI}

AEM Guides支援將非結構化Adobe FrameMaker內容(.fm和.book)移轉至結構化DITA。 此程式著重於使用範本式方法評估現有內容，以及透過轉換表格將FrameMaker樣式對應至DITA。 轉換後，您可以編輯、驗證結構化內容，並將其發佈到PDF和適用於行動裝置的HTML5等格式，並支援輸出自訂。 如需詳細資訊，請檢視[在Adobe FrameMaker中將技術檔案從非結構化移轉至DITA](https://migrate-from-unstructured-to-dita-step-by-step-guide.meetus.adobeevents.com/)。

<!-- Deprecated information -
 //The first step is to create style mappings using FrameMaker and save those settings in a .sts file. Next, if you are using custom DITA, then you can map your custom elements with the source FrameMaker formats in the `ditaElems.xml` file. For example, if you have created a custom element named `impnote` to handle all important notes, then you can define this custom element in the `ditaElems.xml` file. Once this custom element is defined, AEM Guides would not raise an error while converting FrameMaker document containing `impnote` element.

Also, If you want to specify some additional attributes with your custom or valid DITA element, you can define those in the style2attrMap.xml file. For example, you can specify the `type` attribute with the value of `important` to be passed on with the `impnote` element. This additional information can be specified in the style2attrMap.xml file.

In addition to specifying

To convert your existing unstructured FrameMaker documents into DITA format, perform the following steps:

1.  Create style mappings in FrameMaker and save those settings in a .sts file.

1.  Log into AEM and open the CRXDE Lite mode.

1.  If you have custom DITA elements, define those in the `ditaElems.xml` file available at the following location:

    `/libs/fmdita/config/ditaElems.xml`

1.  Create an overlay node of the `config` folder within the `apps` node.

1.  Navigate to the configuration file available in the `apps` node:

    `/apps/fmdita/config/ditaElems.xml`

    The `ditaElems.xml` file contains a single configurable parameter:

    -   In the `elem` parameter, specify the name of the custom element that you want to use in your converted DITA documents. This element would be passed on as is in the generated DITA documents.

1.  If you want to specify additional attributes, define those in the `style2attrMap.xml` file available at the following location:

    `/libs/fmdita/config/style2attrMap.xml`

1.  Create an overlay node of the `config` folder within the `apps` node.

1.  Navigate to the configuration file available in the `apps` node:

    `/apps/fmdita/config/style2attrMap.xml`

    The `style2attrMap.xml` file contains the following configurable parameters:

    -   In the `fmStyle` parameter, specify the source format used in the FrameMaker document that you want to map.

    -   In the`ditaAttr` element, specify the DITA attribute that you want to map with the source format.

    -   In the `ditaVal` element, specify the value for the mapped attribute. If you don't have any value, you can leave this entry blank.

1.  Save the `style2attrMap.xml` file.

1. After configuring the required parameters in the `style2attrMap.xml` file, log into AEM and open the Assets UI.

1. Navigate to and click on the FrameMaker document that you want to convert.

    The DITA map console appears showing the list of Output Presets available to generate output.

1. Select DITA output format and configure the required parameters.

    >[!NOTE]
    >
    > You must use the same settings file \(.sts\) that you created in FrameMaker. Also, specify the Settings Name and Destination Path.

1. Click the **Generate** icon to start the output generation process.


Using the `<attrMap> </attrMap>` block, you can define one or multiple blocks of configurations for conversion. Depending on the content, you could have a .dita file and a .ditamap file as the converted files.

-->

## 移轉任何其他結構化檔案 {#id1949B0590YK}

AEM Guides可讓您將現有的結構化檔案轉換為有效的DITA檔案。 您需要指定輸入和輸出資料夾位置、轉換檔案的位置、儲存最終輸出的副檔名，以及是否需要檔案的新版本。

若要將現有的結構化檔案轉換為DITA格式，請執行下列步驟：

1. 登入AEM並開啟CRXDE Lite模式。

1. 導覽至下列位置可用的預設組態檔：

   `/libs/fmdita/config/XSLConfig.xml`

1. 在`config`節點內建立`apps`資料夾的覆蓋節點。

1. 導覽至`apps`節點中可用的組態檔：

   `/apps/fmdita/config/XSLConfig.xml`

   `XSLConfig.xml`檔案包含下列可設定的引數：

   - 在`inputDir`元素中，指定可以使用來源結構化檔案的輸入資料夾位置。 例如，如果您的結構化檔案儲存在`xsltodita`資料夾中名為`projects`的資料夾中，則指定位置為： `/content/dam/projects/xsltodita/`

   - 在`outputDir`元素中，指定輸出資料夾的位置或保留預設輸出位置。 如果DAM上不存在指定的輸出資料夾，則轉換工作流程會建立輸出資料夾。

   - 在`xslFolder`元素中，指定儲存XSL轉換檔案的資料夾位置。

   - 在``xslPath``元素中，指定用來起始轉換程式的主要.XSL檔案的位置。

   - 在``outputExt``元素中，指定從轉換資料流建立之最終輸出檔案的副檔名。

   - 針對`createRev`專案，指定是否要建立新版本的轉換DITA主題\(`true`\)，或不建立\(`false`\)。

1. 儲存 `XSLConfig.xml` 檔案。

1. 在`XSLConfig.xml`檔案中設定必要的引數後，登入AEM並開啟Assets UI。

1. 導覽至輸入資料夾位置\(`xsltodita`\)。

1. 將來源結構化檔案上傳至此資料夾。 如需在DAM上傳內容的資訊，請參閱[上傳現有DITA內容](migrate-content-upload-existing-dita-content.md#)。


使用`<config> </config>`區塊，您可以定義一或多個轉換組態區塊。 會執行轉換工作流程，並以DITA主題形式的最終輸出儲存在`outputDir`元素中指定的位置。

**上層主題：**&#x200B;[&#x200B;移轉現有內容](migrate-content.md)
