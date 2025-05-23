---
title: 附錄
description: 瞭解如何準備InDesign檔案以進行轉換
exl-id: 02da0e61-7a73-4c4c-9bd7-2664d90fa728
feature: InDesign File Conversion
role: Admin
level: Experienced
source-git-commit: 0513ecac38840a4cc649758bd1180edff1f8aed1
workflow-type: tm+mt
source-wordcount: '2851'
ht-degree: 0%

---

# 附錄 {#id195AD0L60Y4}

## 準備InDesign檔案以進行轉換 {#id195DBF0045Z}

InDesign為作者提供一套豐富的功能，用於建立吸引人且複雜的檔案。 這通常表示檔案的不同部分會以視覺化方式放置在頁面上，但不會嘗試在這些文字框之間提供任何流量。 未定義文字框的&#39;*讀取順序*&#39;時，IDML檔案會包含可能未遵循任何有意義的順序的內文。 最終結果將是一個或多個DITA主題，其中包含以隨機順序排列的段落、表格和圖形。

雖然可以在DITA編輯器中將DITA內容編輯成合理的順序，但在建立IDML檔案之前修正InDesign檔案會容易得多。 這可以在不改變來原始檔外觀的情況下完成。 透過正確定義閱讀順序，也有助於使來原始檔可存取。

***串連文字框***

InDesign使用字詞&#x200B;*&#39;執行緒&#39;*&#x200B;來連結一個影格到另一個影格的程式。 如需串連文字框的詳細資訊，請參閱InDesign檔案中的&#x200B;*[串連文字](https://helpx.adobe.com/in/indesign/using/threading-text.html)*&#x200B;主題。

***重疊影格***

有些InDesign檔案會因版面配置原因而使用非執行緒式重疊框架。 將此內容合併到主對話串中可能非常困難。 最佳選項可能是在DITA環境中編輯結果。

***InDesign劇本***

InDesign檔案中的每個串連內容流程都稱為&#39;*story*&#39;。 為獲得最佳結果，建議限制內文數量。 但是，在DITA輸出中可能不需要檔案的某些部分。 例如，很少需要頁尾，但如果未小心處理，它們可能會出現在主題的中間。

排除檔案中不需要的文字最簡單的方法是為其指定一個特殊的&#x200B;*段落標籤*，該標籤只用於不需要的內容。 例如，不要在頁尾重複使用&#x200B;*\[基本段落\]*，請建立專用的&#x200B;*頁尾*&#x200B;標籤。 然後在MapStyle檔案中，設定要捨棄的&#x200B;*頁尾*&#x200B;段落，如下所示：

```XML
<paraRule style="Footer" local="0" refactor="drop">
   <attributeRules createID="false"/>
</paraRule>
```

***對應到DITA doctypes***

您的來原始檔至少必須有一個段落樣式或元素可以標示主題的開頭。 檔案通常使用&#x200B;*Heading1*&#x200B;作為檔案最上層標題的名稱。 然後，您可以建立該樣式到特定DITA doctype的對應。 如果您的檔案組織良好，而且始終使用&#x200B;*標題1*，那麼您將會獲得良好的結果。

***多個DITA doctypes***

如果需要將某些&#x200B;*標題1*&#x200B;段落轉換為其他DITA doctypes，請複製InDesign的段落樣式。 視情況提供這些樣式易於辨識的名稱，例如&#x200B;*Heading1\_genTask*&#x200B;或&#x200B;*Heading1\_troubleshooting*。 然後，設定mapStyle檔案，如下所示：

```XML
<doctypes>
   <doctypeParaRule style="Heading1" local="0" mapToDoctype="concept">
      <attributeRules createID="true"/>
   </doctypeParaRule>
   <doctypeParaRule style="Heading1_genTask" local="0" mapToDoctype=" generalTask">
      <attributeRules createID="true"/>
   </doctypeParaRule>
   <doctypeParaRule style="Heading1_troubleshooting" local="0"mapToDoctype=" troubleshooting">
      <attributeRules createID="true"/>
   </doctypeParaRule>
</doctypes>
```

***結構化InDesign檔案***

InDesign與XML的關係不密切。 雖然檔案可以包含XML DTD，且主要內文可能對該DTD有效，但也可以建立混合式檔案，其中某些內容為XML，但不包含DTD。 這些是不希望成功轉換為DITA的情況。 如果檔案包含XML零件，請嘗試將輸出儲存為XML並檢視結果是否可接受。 如果不包含，則DITA內容也將包含無效的內容，或可能完全失敗。

***表格格式***

從InDesign表格格式規則轉換成DITA中的對等表格格式是一個複雜的過程。 這是因為與DITA中使用的Oasis \(CALS\)表格模型所提供的基本選項相比，來源檔案中提供了豐富的格式功能。 提供垂直和水平文字對齊方式，雖然「對齊」文字一律根據文字方向對齊，而「InDesign」則允許「靠左對齊」和「靠右對齊」，但結果類似。

InDesign處理欄和列分隔符號的能力再次遠勝於Oasis表格模型的基本選項。 InDesign提供四種儲存格邊框 — 邊框型別\（實線或圖樣\）、邊框粗細、邊框顏色、邊框色調、邊框間隙顏色和邊框間隙色調。 所有這些都必須向下對應至每個儲存格右下方的框線\(entry element\)，其中唯一選項為0或1 — 隱藏框線或顯示框線。

InDesign的邊框規則可套用至下列層級：

- 表格樣式
- 儲存格樣式
- 每個儲存格上的本機覆寫

InDesign至DITA轉換程式會套用邊界規則，如下所示：

- 表格樣式對應至垂直規則的`colspec/@colsep`屬性。 水準規則對應至`row/@rowsep`屬性。 在這兩種情況下，如果未定義邊框，則不會建立屬性。
- 儲存格樣式對應至`entry/@colsep`和`entry/@rowsep`屬性。 這些值將覆寫任何「表格樣式」衍生的邊界規則。
- 本機覆寫會將格式直接套用至儲存格，並覆寫表格樣式和儲存格樣式。

***交替模式***

InDesign表格樣式允許欄和儲存格的排版遵循交替模式。 雖然轉換支援此功能，但只有當一個圖樣群組對應到顯示正線\(1\)，而另一個圖樣群組對應到隱藏正線\(0\)時，結果才會很明顯。

## 準備對應檔案以InDesign至DITA移轉 {#id194AF0003HT}

正確的DITA轉換需要符合來原始檔內容的對應檔案。 對於非結構化InDesign檔案，這表示所有可用的段落樣式和字元樣式都需要對應。 對於XML結構化InDesign檔案，其關聯DTD中的所有元素都必須對應。

非結構化和結構化InDesign檔案的對應檔案不同。 這是因為將非結構化來源內容轉換為DITA的處理要求較為複雜。

以下提供對應檔案的範例：

```XML
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE styleMap SYSTEM "mapStyle.dtd">
<styleMap xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="mapStyle.xsd" >
   <doctypes>
      <mapDoctypeParaRule root="itpx:stories" mapToDoctype="map">
         <attributeRules createID="true">
            <addNew name="outputclass" value="map"/>
         </attributeRules>
      </mapDoctypeParaRule>
      <doctypeParaRule style="Heading 1" local="0" mapToDoctype="concept">
         <attributeRules createID="true"/>
      </doctypeParaRule>
      <doctypeParaRule style="Heading A" local="0" mapToDoctype="topic">
         <attributeRules createID="true"/>
      </doctypeParaRule>
   </doctypes>
   <wrappingRules>
      <wrap elements="li+" context="number" wrapper="ol">
         <attributeRules createID="true"/>
      </wrap>
      <wrap elements="li+" context="bullet" wrapper="ul">
         <attributeRules createID="true"/>
      </wrap>
   </wrappingRules>
   <paragraphStyleRules>
      <paraRule style="Heading 2" local="0"  mapTo="p">
         <attributeRules createID="true"/>
      </paraRule>
      <paraRule style="Heading 3" local="0"  mapTo="p">
         <attributeRules createID="true"/>
      </paraRule>
      <paraRule style="List Paragraph" local="p[-|-|-|-|-|b|-|-]" context="bullet" mapTo="li">
         <attributeRules createID="true"/>
      </paraRule>
      <paraRule style="List Paragraph" local="p[-|-|-|-|-|n|-|-]" context="number" mapTo="li">
         <attributeRules createID="true"/>
      </paraRule>
      <paraRule style="List Paragraph" local="0" context="bullet" mapTo="li">
         <attributeRules createID="true"/>
      </paraRule>
      <paraRule style="Normal" local="0"  mapTo="p">
         <attributeRules createID="true"/>
      </paraRule>
      <paraRule style="Normal" local="p[-|-|-|-|-|b|-|-]" context="bullet" mapTo="li">
         <attributeRules createID="true"/>
      </paraRule>
      <paraRule style="Title" local="0"  mapTo="p">
         <attributeRules createID="true"/>
      </paraRule>
   </paragraphStyleRules>
   <characterStyleRules>
      <charRule style="Bold" local="0" mapTo="b">
         <attributeRules createID="false"/>
      </charRule>
      <charRule style="Code" local="0" mapTo="codeph">
         <attributeRules createID="false"/>
      </charRule>
      <charRule style="[No character style]" local="c[Bold|-|-|-|-|-|-|-]" mapTo="b">
         <attributeRules createID="false"/>
      </charRule>
      <charRule style="[No character style]" local="c[Italic|-|-|-|-|-|-|-]" mapTo="i">
         <attributeRules createID="false"/>
      </charRule>
   </characterStyleRules>
</styleMap>
```

對應檔案是結構簡單的XML檔案，列出所有來源段落樣式和字元樣式代碼。 檔案內容說明如下：

**樣式對應**

在`styleMap`元素中，您可以指定兩個選擇性屬性 — `@map_date`和`@map_version`，以記錄對應檔案的版本。

**檔案型別**

`doctypes`元素列出支援的DITA map和主題對應。

**對應檔案型別段落規則**

`mapDoctypeParaRule`專案為必要專案。 不可編輯這個專案的屬性，因為來源XML的根專案永遠對應到DITA map的根`map`專案。

**檔案型別段落規則**

`doctypeParaRule`專案為必要專案。 這可提供轉換程式來識別新主題開始的方式。 通常`@style`屬性會單獨使用，且`@local`屬性會設為0。 但是，如果所選樣式上永遠有本機格式覆寫，則必須為每個樣式新增規則及其本機覆寫。 在產生的對應檔案中，這很容易識別，其中可能找到以下內容或類似內容：

```XML
<paraRule style="Heading 1" local="0" mapTo="p">
   <attributeRules createID="true"/>
</paraRule>
<paraRule style="Heading 1" local="p[Italic|-|-|-|-|-|-|-]" mapTo="p">
   <attributeRules createID="true"/>
</paraRule>
```

在上述範例中，`@style` = &quot;Heading1&quot;有兩個`paraRule`元素。 只要建立具有`@mapToDoctype`屬性設定的對等`doctypeParaRule`專案（視需要而定）。

`doctypeParaRule`中使用的屬性說明如下：

- `@style`：來源InDesign檔案中的樣式名稱。
- `@local`：請參閱[\#id194CG0V005Z](#id194CG0V005Z)。
- `@mapToDoctype`：來自所有有效`doctypes`之列舉清單的DITA主題型別名稱。

**元素包裝規則**

元素環繞規則會根據一組屬性值，定義將傳入檔案中的元素環繞或移動至預先定義元素的方法。

***`wrap`元素***

這是選用元素。 `wrap`元素列出將包裝或移動的元素。 封裝通常用於必須為一系列元素指定通用父元素的情況。 例如，多個`li`元素將包裝在`ol`元素中。 此外，`wrap`可用於移動元素，例如插圖和表格的標題。

`wrap`中使用的屬性說明如下：

- `@element`：元素名稱后的加號顯示，所有具有相同名稱的相鄰元素將包裝在`@wrapper`屬性中名為的元素中。
- `@wrapper`：包裝專案的名稱。
- `@context`：提供進一步調整指定專案包裝方式的方法。 下列範例說明如何根據`@context`值\（內容定義於`paraRule`元素\）對應有序清單`ol`或無序清單`ul`中的一系列`li`元素：

  ```XML
  <wrap elements="li+" context="number" wrapper="ol">
     <attributeRules createID="true"/>
  </wrap>
  <wrap elements="li+" context="bullet" wrapper="ul">
     <attributeRules createID="true"/>
  </wrap>
  ```


下列範例顯示如何從`title`和`image`專案建立`fig`專案：

- `@elements`：列出並以逗號分隔的元素將包裝在`@wrapper`屬性中名為的元素中。 由於通常在影像下方包含圖形標題，標題會是`image`之後緊鄰的`title`元素。

  下列自動換行規則：

  ```XML
  <wrap elements="title, image" context="FigTitle" wrapper="fig">
     <attributeRules createID="true"/>
  </wrap>
  ```

  轉換下列中繼XML：

  ```XML
  <image href="Links/myImage.png" scale="59">
     <title>IDML2DITA workflow</title>
  ```

  至下列有效的DITA圖形結構：

  ```XML
  <fig id="id397504">
     <title>IDML2DITA workflow</title>
     <image href="Links/myImage.png" scale="59">
  </fig>
  ```

- `@wrapper`：包裝專案的名稱。
- `@context`：提供進一步調整指定專案包裝的方式\（內容定義於`paraRule`專案上\）。

下列範例顯示如何將`title`移入`table`：

- `@elements`：位於`table`之前或之後的`title`專案將包裝在`@wrapper`屬性中命名的專案中。 XPath-style述詞可識別標題專案的位置為`[before]`或`[after]`。

  範例：下列自動換行規則：

  ```XML
  <wrap elements="title[before]" context="TableTitle" wrapper="table">
     <attributeRules createID="true"/>
  </wrap>
  ```

  轉換下列中繼XML：

  ```XML
  <title>IDML2DITA workflow</title>
  <table id="id289742" outputclass="BasicTable">
     <tgroup cols="2">
        <colspec colname="0" colwidth="0.7*">
           <colspec colname="1" colwidth="0.3*">
  ```

  在此有效的DITA圖形結構中：

  ```XML
  <table id="id289742" outputclass="BasicTable">
     <title>IDML2DITA workflow</title>
     <tgroup cols="2">
        <colspec colname="0" colwidth="0.7*">
           <colspec colname="1" colwidth="0.3*">
  ```

- `@wrapper`：包裝專案的名稱。

- `@context`：提供進一步調整指定專案包裝的方式\（內容定義於`paraRule`專案上\）。


**段落樣式規則**

`<paragraphStyleRule>`元素說明如下：

***`paraRule`元素***

`paraRule`專案為必要專案。 這會指定所有段落樣式的對應規則。 在InDesign檔案中，所有文字都包含在段落樣式的子結構內，即使沒有任何樣式的段落也命名為`[No paragraph style]`。 方括弧，表示內建的InDesign樣式名稱。

>[!NOTE]
>
> 方括弧表示內建InDesign樣式名稱。

`paraRule`中使用的屬性說明如下：

- `@style`：來源InDesign檔案中的樣式名稱。
- `@local`：請參閱[\#id194CG0V005Z](#id194CG0V005Z)。
- `@mapTo`： DITA目標專案的名稱。

- `@context`：有多個包裝函式選擇可供使用時，此屬性可用來連結至特定的&#x200B;**換行**&#x200B;規則。 範例： `li`專案可能會包裝在`ol`或`ul`專案中。 若要識別不同的清單型別，您可以使用特定的樣式名稱或可顯示下列內容的`@local`屬性：
   - `local="p[-|-|-|-|-|b|-|-]"`其中欄位6中的&#39;`b`&#39;表示專案符號清單專案。 在此案例中，將`@context`設定為&#39;`bullet`&#39;。
   - `local="p[-|-|-|-|-|n|-|-]"`其中欄位6中的&#39;`n`&#39;表示編號清單專案。 在此案例中，將`@context`設定為&#39;`number`&#39;。

- `@commentOut`：此屬性可啟用目標專案在XML註解中的換行，因此資訊不會遺失，但使用者可以手動處理。 如果來源內容無法強制符合DITA結構規則，則此功能會很有用。

- `@refactor`：此選擇性屬性有兩個值的選擇：

- `unwrap`：移除相符的元素，同時保留其內容。

- `drop`：已移除相符的元素及其所有內容。


**字元樣式規則**

`charRule`元素說明如下：

>[!NOTE]
>
> 當`local="0"`時，內建字元樣式`[No character style]`將沒有對應，因為這些樣式會在預先處理期間移除。

***`charRule`元素***

這是選用元素。

這些是所有字元樣式的對應規則。 在InDesign檔案中，所有文字都包含在字元樣式的子元素中。

`charRule`中使用的屬性說明如下：

- `@style`：來源InDesign檔案中的樣式名稱。
- `@local`：請參閱[\#id194CG0V005Z](#id194CG0V005Z)。
- `@mapTo`： DITA目標專案的名稱。
- `@refactor`：此選擇性屬性有兩個值的選擇：
   - `unwrap`：移除相符的元素，同時保留其內容。

   - `drop`：已移除相符的元素及其所有內容。


**屬性規則**

此元素可以是下列元素前後關聯的子項：

- `mapDoctypeParaRule`
- `mapDoctypeElemRule`
- `doctypeParaRule`
- `doctypeElemRule`
- `paraRule`
- `charRule`
- `elementRule`

屬性規則的用途是管理相符元素的屬性。

根據內容，`attributeRules`元素可使用下列屬性：

- `@createID`：產生相符專案的唯一識別碼。 允許的值`true`或`false`。 可用於所有內容。
- `@copyAll`：僅針對結構化的來源檔案，從來源XML內容複製所有屬性。 允許值為`true`或`false`。 適用於內容`mapDoctypeParaRule`、`mapDoctypeElemRule`、`doctypeElemRule`和`elementRule`。


`attributeRules`中使用的屬性說明如下：

>[!NOTE]
>
> 此元素可包含多個子元素。

- `addNew`：將新屬性新增至相符的元素。 可用於所有內容。 它有兩個屬性：
   - `@name`：必須是合法的XML名稱，最好對DITA內容有效。
   - `@value`：可以是常值文字或簡單的XPath運算式。
- `copyAtt`：將單一屬性複製到目標，同時可選擇在程式中重新命名該屬性。 值不會變更。 適用於內容`mapDoctypeParaRule`、`mapDoctypeElemRule`、`doctypeElemRule`和`elementRule`。 當此專案出現時，`@copyAllAtts`值會假設為`false`。 它有兩個屬性：
   - `@name`：必須是存在於來源XML專案上的屬性名稱。
   - `@mapTo`：必須是合法的XML名稱，最好對DITA內容有效。

**本機格式碼**

在任何InDesign檔案中，段落樣式和字元樣式都可以包含數百種不同的格式覆寫。 這些屬性大多在轉換過程中不提供有用的角色。 不過，我們已找出一組會影響檔案語意且需要影響轉換程式的核心格式化功能。

`@local`屬性以特殊分隔格式顯示，其中有8個欄位與前置字元一起提供，以顯示格式覆寫型別。 格式代碼欄位列示如下：

- 前置詞&#x200B;**p**&#x200B;用於段落樣式本機覆寫，或&#x200B;**c**&#x200B;用於字元樣式本機覆寫。
- **字型樣式**，這是家族名稱和屬性，例如&#39;***粗體縮疊斜體***&#39;。
- **字型大小**&#x200B;點。
- 上標或下標的&#x200B;**字元位置**。
- 底線&#x200B;**在**&#x200B;下。
- 刪除線的&#x200B;**刪除線**。
- **將清單型別識別為專案符號或編號的清單代碼** — 不一定會被InDesign使用。
- **專案符號代碼**&#x200B;列出檔案中所有已定義的專案符號型別。
- **編號代碼**&#x200B;列出檔案中所有已定義的編號樣式。

謹慎使用此功能，否則會遺失本機格式，有助於改善從已設定樣式的內容轉入DITA的品質。 此範例可解析為專案符號清單中表示斜體、16pt文字： `p[Italic|16|-|-|-|b|-|-]`。

**結構對應**

結構對應檔案類似於「樣式對應」檔案，其簡單結構會列出所有來源元素和相關屬性型別。 提供兩個屬性`@map_date`和`@map_version`來記錄要使用的對應檔案版本。

**檔案型別**

`doctypes`元素列出支援的DITA map和主題對應。

**對應檔案型別元素規則**

`mapDoctypeElemRule`專案為必要專案。 不可編輯這個專案的屬性，因為來源XML的根專案永遠對應到DITA map的根`map`專案。

**元素包裝規則**

**`elementRules`元素**&#x200B;這會列出所有元素。

**`elementRule`元素** `elementRule`元素是必要的。 這些是所有來源元素的對應規則。 雖然InDesign檔案確實包含非結構化的樣式元素，但除非啟用&#39;***混合模式***&#39;處理，否則結構化的內容會忽略這些元素。

`elementRule`中使用的屬性說明如下：

- `@elementName`：來源InDesign檔案中的專案名稱。

- `@local`：請參閱[\#id194CG0V005Z](#id194CG0V005Z)。 \（僅對混合式檔案有用\）。

- `@mapTo`： DITA目標專案的名稱。

- `@refactor`：此選擇性屬性有兩個值的選擇：

   - `unwrap`：移除相符的元素，同時保留其內容。

   - `drop`：已移除相符的元素及其所有內容。

- `@context`：有多個包裝函式選擇可供使用時，此屬性可用來連結至特定的包裝規則。 範例： `li`專案可能會包裝在`ol`或`ul`專案中。

- `@commentOut`：此屬性可啟用目標專案在XML註解中的換行，因此資訊不會遺失，但使用者可以手動處理。 如果來源內容無法強制符合DITA結構規則，則此功能會很有用。


## 疑難排解AEM Guides

安裝及設定AEM Guides後，您就可以疑難排解問題。

## 驗證引用

您可以執行指定的指令碼來驗證參考。 這些指令碼可協助您識別中斷的參照，然後修補或修正它們。

- `/bin/fmdita/validatebtree?operation=validate` — 回報任何損壞的內容參照，但無法加以修正。
- `/bin/fmdita/validatebtree?operation=patch` — 列出中斷的內容參照和修補程式，或修正它們。

**驗證指令碼**

使用產品套件中可用的驗證指令碼，執行以下步驟來檢查參考：

1. 執行驗證指令碼\[`/bin/fmdita/validatebtree?operation=validate`\]以檢查是否有任何新的中斷參考。
1. 如果驗證指令碼報告任何錯誤，您可以使用修補程式指令碼來修補。
1. 紀錄以下提供的詳細資訊，並在必要時與客戶成功團隊分享：
1. &#x200B;
   - 驗證指令碼列印的記錄
- 「`/content/fmdita/references`」的封裝
- 根據所報告案例的任何其他必要細節

**修補程式指令碼**

使用產品套件中可用的修補程式指令碼，執行下列步驟來修補任何中斷的參照：

1. 執行修補程式指令碼`[/bin/fmdita/validatebtree?operation=patch]`以修正中斷的參照。 指令碼執行需要幾分鐘的時間，並會隨著進度列印記錄。 執行完成後，它會在結尾列印「`Done`」。

   **注意：*&#x200B;建議您複製並儲存記錄檔以供參考。

1. 一旦修正程式指令碼執行成功，您就可以執行下列檢查：
1. &#x200B;
   - 檢查已在`/content/fmdita`下建立新節點&#39;&#39;`references_backup_<timestamp>"`&#39;
- 檢查參考是否已修正

**記錄器**

您也可以為此指令碼執行建立單獨的記錄器，如下所示：

- 在類別&quot;`adobe.fmdita.common.BTreeReferenceValidator`&quot;上新增記錄器
- 設定為`DEBUG`

建立的記錄檔將記錄與指令碼執行相關的所有資訊，並在瀏覽器工作階段逾時從瀏覽器觸發指令碼時很有用。
