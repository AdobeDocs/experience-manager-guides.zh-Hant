---
title: 使用AEM元件自訂dita元素對應
description: 瞭解如何使用AEM元件自訂Dita元素對應
feature: Output Generation
role: Admin
level: Experienced
source-git-commit: 834959a6a0e22cd5d2b2c5d0e57ceb6d45c0c666
workflow-type: tm+mt
source-wordcount: '1268'
ht-degree: 1%

---


# 使用AEM元件自訂DITA元素對應 {#id1679J600HEL}

AEM Guides中的DITA元素對應至其對應的AEM元件。 AEM Guides在工作流程（例如發佈和稽核）中使用此對應，將DITA元素轉換為對應的AEM元件。 在`elementmapping.xml`檔案中定義對應，該檔案可使用Cloud Service設定的封裝管理員進行存取，也可以從URL： `/libs/fmdita/config/elementmapping.xml` （內部部署設定的CRXDE Lite模式）進行存取。

>[!NOTE]
>
> 請勿在``libs``節點中使用預設組態檔中的任何自訂專案。 您必須在``libs``節點中建立``apps``節點的覆蓋，並僅更新``apps``節點中的必要檔案。

您可以使用預先定義的DITA元素對應，也可以將DITA元素對映至自訂AEM元件。 若要使用自訂AEM元件，您必須瞭解`elementmapping.xml`檔案的結構。

## elementmapping.xml結構

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


## DITA元素結構描述

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
        <attribute from="attrname"         to="propname"         ispath="true|false"         rel="source|target" />    
    </attributemap>    
    <skip>true|false</skip> 
</ditaelement>
```

下表說明DITA元素結構描述中的元素：

| 元素 | 說明 |
|-------|-----------|
| `<ditaelement>` | 每個對應元素的頂層節點。 |
| `<class>` | 您正在寫入元件的目標DITA元素的類別屬性。<br>例如，DITA主題的類別屬性是： <br> `- topic/topic` |
| `<componentpath>` | 對應AEM元件的CRXDE路徑。 |
| `<type>` | 可能的值： <br> -   **複合**：處理子專案及<br> -   **STANDALONE**：略過處理子專案 |
| `<attributeprop>` | 用於將序列化DITA屬性和值作為屬性對應至AEM節點。 例如，如果您有`<note type="Caution">`個元素，而對應至此元素的元件有`<attributeprop>attr_t</ attributeprop>`，則節點的屬性和值會序列化為對應AEM節點\( `attr_t`\)的`attr_t->type="caution"`屬性。 |
| `<textprop>propname_t</textprop>` | 將`getTextContent()`輸出儲存至`propname_t.` <br>所定義的屬性 **注意：**&#x200B;這是最佳化的屬性。 |
| `<xmlprop>propname_x </xmlprop>` | 將此節點的序列化XML儲存到由&#x200B;`propname_x.<br> `**定義的屬性注意：**&#x200B;這是最佳化的屬性。 |
| `<xpath>` | 如果在元素對應中提供了XPath元素，則應該連同元素名稱和類別一起滿足XPath條件，才能使用元件對應。 |
| `<target>` | 將DITA元素放置在crx存放庫中的指定位置。<br>可能的值： <br> - **head**：在標題節點<br>之下 — **文字**：在段落節點之下 |
| `<wrapelement>` | 要將內容包裝在其中的HTML元素。 |
| `<wrapclass>` | 屬性`wrapclass.`的元素值 |
| `<attributemap>` | 包含一或多個`<attribute>`節點的容器節點。 |
| `<attribute from="attrname" to="propname" ispath="true\|false" rel="source\|target" />` | 將DITA屬性對應至AEM屬性： <br> -   **`from`**： DITA屬性名稱<br> -   **`to`**： AEM元件屬性名稱<br> -   **`ispath`**：如果屬性是路徑值\（例如： *image*\） <br> -   **`rel`**：如果路徑是來源或目標<br> **注意：**&#x200B;如果`attrname`開頭為`%`，則將`attrname minus '%'`對應至Prop &#39; `propname`&#39;。 |

**其他附註**

- 如果您計畫覆寫預設元素對應，建議您不要在預設`elementmapping.xml`檔案中進行變更。 您應該建立新的對應XML檔案，並將檔案放置於其他位置，最好是放在您建立的自訂應用程式資料夾內。

- 在`elementmapping.xml`檔案中，有許多參考fmdita/components/dita/wrapper元件的對應專案。 包裝函式是一種泛型元件，會使用其網站節點上的屬性來產生相關的HTML，以呈現相對簡單的DITA建構。 它使用`wrapelement`屬性來產生封閉標籤，並將子轉譯委派給對應的元件。 當您只想要容器元件時，這個用法就相當實用。 您可以搭配使用Wrapper元件與`div`和`p`屬性來達到相同的效果，而不需建立可轉譯特定容器標籤（如`wrapelement`或`wrapclass`）的新元件。

- 不建議在字串JCR屬性中儲存大量文字。 輸出產生中最佳化的屬性型別計算可確保大型文字內容不會儲存為字串型別。 反之，當需要儲存大於某個臨界值的內容時，屬性的型別會變更為二進位。 預設會將此臨界值設定為512個位元組，但可以在Configuration Manager \(*com.adobe.fmdita.config.ConfigManager*\)中變更，方法是變更&#x200B;**另存為二進位臨界值**&#x200B;設定。

- 如果您計畫覆寫部分\（而非全部\）元素對應，則不需要復寫整個`elementmapping.xml`檔案。 您需要建立新的XML對應檔案，並只定義要覆寫的元素。

- 在自訂位置中建立XML檔案之後，請更新`Override Element Mapping`組合中的`com.adobe.fmdita.config.ConfigManager`設定。


