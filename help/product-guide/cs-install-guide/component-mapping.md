---
title: AEM Sites的元件對應
description: 瞭解如何為AEM Sites執行元件對應
feature: Installation
role: Admin
level: Experienced
source-git-commit: 2b29c0a4a9c7be4a8dcf1110f31912be712eb47a
workflow-type: tm+mt
source-wordcount: '1046'
ht-degree: 0%

---

# AEM Sites的元件對應（使用複合元件對應）

本文會介紹AEM網站的元件對應（使用複合元件對應）的各個層面。

## 元件對應規則

使用JSON規則陣列（您的`componentmapping.json`）將HTML轉換為元件。 儘可能保持規則簡單、明確和具體。

### 鎖定HTML元素及其類別

- 在`name`中寫入HTML標籤名稱。
- 在`class`中包含套用至該元素的CSS類別（如果類別存在）。
範例：

  ```html
  <div class ="sample-class">
  <p> Sample html element </p>
  </div>
  ```

  ```json
  {
  "name": "div",
  "class": "sample-class",
  "resourceType": "guides-components/components/table",
  "attributeMap": []
  }
  ```

定義上述元素時，請確定下列事項：

- `name`可以是逗號分隔清單（例如，`"h1, h2"`）。
- 專案上必須有`class` （所有列出的類別必須相符）。
- `resourceType`表示您打算使用`table`元件。 `guides-components`封裝是由Guides提供的OOTB。 您也可以視需要使用其他元件套件，例如`core/wcm/`。

### 使用attributeMap儲存JCR節點上的屬性

將專案新增至`attributeMap`以設定輸出節點上的屬性。 每個專案都會產生`attrs[to] = value`。
常見模式：

```json
// copy an attribute
{ "attribute": "src", "to": "image-src" }
// read content or tag name
{ "from": "textContent", "to": "jcr:title" }
{ "from": "outerHTML",  "to": "text" }
{ "from": "innerHTML",  "to": "text" }
{ "from": "name",       "to": "type" }  // the tag name, e.g., "h2"
// constant value
{ "value": true, "to": "textIsRich" }
```

以下是影像元素的HTML轉JSON範例。

```html
<img src="sample.png" class="cmp-image__image" itemprop="contentUrl" data-cmp-hook-image="image" alt="">
```

```json
{
    "name": "img",
    "resourceType": "core/wcm/components/image/v2/image",
    "attributeMap": [
      {
        "from": "src",
        "to": "fileReference"
      },
      {
        "value": ["fileReference"],
        "to": "path-attributes"
      }
    ]
  }
```

### 透過專用專案標準化路徑

如果您想要標準化（設定為絕對）值，請使用以下方式宣告哪些屬性索引鍵應該標準化：

```json
{
  "value": ["text"],
  "to": "path-attributes"
}
```

請務必注意下列重要事項：

- 將您要正規化的屬性名稱清單放入`value` （例如`["text"]`或`["href", "src"]`）。
- 系統在建置最終元件時，會標準化在這些屬性名稱下找到的任何值。


### 分割成元件前擷取HTML值

使用`from`指定在檔案分割成個別元件之前，如何從元素讀取值：

- `"textContent"`：元素的純文字
- `"outerHTML"`：專案及其內部標籤
- `"innerHTML"`：僅元素的內部標籤
- 任何其他字串：視為屬性名稱（例如，`"src"`、`"href"`）


範例：

```json
{ "from": "textContent", "to": "jcr:title" }
{ "from": "outerHTML",  "to": "text" }
{ "from": "innerHTML",  "to": "snippet" }
{ "from": "src",        "to": "image#src" }
```

### componentmapping.json中最低的端對端範例

```json
[
  {
    "name": "h1, h2",
    "class": "topic-title",
    "resourceType": "core/wcm/components/title/v2/title",
    "attributeMap": [
      { "from": "textContent", "to": "text" },
      { "from": "name",        "to": "type" }
    ]
  },
  {
    "name": "img",
    "class": "hero",
    "resourceType": "weretail/components/content/heroimage",
    "attributeMap": [
      { "from": "src", "to": "image#src" },
      { "value": ["image#src"], "to": "path-attributes" }
    ]
  },
  {
    "name": "#element",
    "resourceType": "core/wcm/components/text/v2/text",
    "attributeMap": [
      { "from": "outerHTML", "to": "text" },
      { "value": true,        "to": "textIsRich" }
    ]
  }
]
```

定義要定位的元素和類別，使用`attributeMap`設定節點屬性，新增`path-attributes`專案以標準化路徑，並為要擷取的值選擇正確的`from`。 上面使用的`heroimage`是`we-retail`網站中的元件。

**注意**：請務必討論預設RTF文字，並識別使用它的元素。

## 建立自訂元件

瞭解如何建立可在儲存格中顯示影像的自訂表格元件。 此方法可確保動態內容有一個乾淨且可重複使用的設計。 內容涵蓋您建置的專案、有效的原因、重要先決條件、高階設計等等。

### 您將建置的內容

自訂表格元件，接受HTML表格內容，並以AEM核心影像元件的輸出取代其中的每個`<img>`。 這可讓您重複使用核心影像的功能（回應式影像、替代文書處理、協助工具），同時完整控制表格標示。
使用此方法，您可以為AEM網站建置其他自訂元件（使用複合元件對應）。

### 為何採取此方法

- **重複使用**：利用核心影像的成熟行為，而非重新實作。
- **一致性**：表格中的影像行為與網站其他位置的影像相同。
- **伺服器端**：在伺服器上轉譯影像，以提供效能、SEO和協助工具。

### 先決條件

- AEM SDK正在執行，且此專案已簽出。
- 核心元件安裝在您的AEM執行個體上。
- Maven可用於構建和部署。

### 高階設計

- Author在元件對話方塊中為表格提供HTML。
- Sling模型會剖析HTML、找到`<img>`個標籤，並針對每個影像呼叫轉譯核心影像元件伺服器端的服務。
- 模型會將原始`<img>`與擷取的核心影像HTML交換，並將已完成的HTML傳遞給HTL輸出。

您的表格會輸出一次，其中已包含核心影像標籤。 不需要使用者端DOM操作。

### 資料夾結構和金鑰檔案（在此存放庫中）

- 元件HTL和clientlibs： `ui.apps/src/main/content/jcr_root/apps/guides-components/components/table/`
   - `table.html` （HTL轉譯器）
   - `_cq_editConfig.xml` （重新整理接聽程式）
   - 具有`clientlibs/`、`css.txt`、`js.txt`、`css/table.css`的`js/table.js`
- Sling模型： `core/src/main/java/com/adobe/guides/aem/components/core/models/TableModel.java`
- 影像演算服務： `core/src/main/java/com/adobe/guides/aem/components/core/services/ImageComponentRenderer.java`

### 實作步驟

**定義資料表元件（元件節點）**

在`apps/guides-components/components/table`下建立元件。 如果您還沒有簡報`.content.xml`，請新增如下所示的最小，以在側面板中註冊。

```xml
<?xml version="1.0" encoding="UTF-8"?>
<jcr:root xmlns:sling="http://sling.apache.org/jcr/sling/1.0"
          xmlns:jcr="http://www.jcp.org/jcr/1.0"
          jcr:primaryType="cq:Component"
          jcr:title="Table"
          componentGroup="Guides - Custom"/>
```

向AEM指出此元件可供作者新增至頁面。

**使用HTL演算並包含樣式**

使用Sling模型並輸出已處理的HTML。 納入CSS/JS的clientlib類別。

```html
<sly data-sly-use.model="com.adobe.guides.aem.components.core.models.TableModel"
     data-sly-use.clientLib="/libs/granite/sightly/templates/clientlib.html">
</sly>
<sly data-sly-call="${clientLib.css @ categories='guides-components.table'}"></sly>
<sly data-sly-test="${wcmmode.edit && !model.hasContent}">
  <div class="cq-placeholder" data-emptytext="${component.title}"></div>
</sly>
<div data-sly-test="${model.hasContent}"
     class="gu-table-wrapper ${model.enableResponsive ? 'gu-table--responsive' : ''} gu-table--style-${model.tableStyle}"
     id="${model.componentId}">
  ${model.processedTableHtml @ context='unsafe'}
</div>
```

模型會傳回完整的HTML，且核心影像已轉譯，因此HTL只會列印它。

**新增Sling模型以處理HTML並演算核心影像**

模型會讀取對話方塊欄位、剖析表格HTML、尋找每個`<img>`，並透過服務將其取代為核心影像HTML。

以下是`TableModel`的一些重要知識：

- 從資源屬性讀取`tableHtml`、`enableResponsive`、`tableStyle`。
- 使用Jsoup安全地剖析和編輯HTML。
- 呼叫`ImageComponentRenderer`以轉譯核心影像並擷取HTML。
- 保留原始`<img>`的CSS類別和樣式。
- 標準化DAM路徑（移除`/jcr:content/renditions/*`）。

```java
@Model(adaptables = {Resource.class, SlingHttpServletRequest.class},
       defaultInjectionStrategy = DefaultInjectionStrategy.OPTIONAL)
public class TableModel {
  @ValueMapValue private String tableHtml;
  @ValueMapValue private boolean enableResponsive;
  @ValueMapValue private String tableStyle;
  @OSGiService private ImageComponentRenderer imageRenderer;
  // ...
  @PostConstruct
  protected void init() {
    // parse HTML, for each <img> build image props (fileReference, alt, title)
    // call imageRenderer.renderImageComponent(...)
    // replace <img> with returned Core Image HTML
  }
  public String getProcessedTableHtml() { /* return final HTML */ }
}
```

這會集中伺服器上的邏輯，並重複使用核心影像行為。

**透過服務演算核心影像（伺服器端包含）**

`ImageComponentRenderer`轉譯核心影像元件並擷取輸出。 It

- 包裝強制`core/wcm/components/image/v2/image`的資源。
- 使用`RequestDispatcher#include`來呈現。
- 以字串形式擷取回應。

```java
@Component(service = ImageComponentRenderer.class)
public class ImageComponentRenderer {
  private static final String IMAGE_RESOURCE_TYPE = "core/wcm/components/image/v2/image";
  public String renderImageComponent(Resource base, Map<String,Object> props,
                                     SlingHttpServletRequest req, SlingHttpServletResponse resp) {
    // create wrapped resource with IMAGE_RESOURCE_TYPE and props
    // dispatcher.include(...) with a response wrapper to capture HTML
    // return captured HTML
  }
}
```

這可讓您&#x200B;**在任何需要的位置，放入核心影像**，而不只是做為子元件。

**使用者端資料庫**

為小型樣式或未來的JS建立clientlib。 上述HTL會載入`guides-components.table`類別。

```java
clientlibs/css.txt
  #base=css
  table.css
clientlibs/js.txt
  #base=js
  table.js
  
```

如此可使樣式/指令碼保持模組化且可探索。

**對話方塊欄位（作者輸入）**

新增至少具有下列屬性的對話方塊：

- **表格HTML**： `./tableHtml` (textarea)；表格的HTML。
- **啟用回應式**： `./enableResponsive` （核取方塊）；切換回應式包裝函式類別。
- **資料表樣式**： `./tableStyle` （選取）；套用樣式修飾元類別。

這些將1:1對應到Sling模型的屬性和控制項轉譯。

**允許範本上的元件**

在範本編輯器中，編輯配置容器原則>允許的元件>在&#x200B;**參考線 — 自訂**&#x200B;下啟用您的表格元件。

在原則允許之前，作者無法新增元件。

## 製作秘訣

- 貼上表格的有效HTML。 模型會清理並調整影像URL。
- 針對影像使用DAM資產路徑；轉譯會標準化為原始資產路徑。
- 儘可能在HTML中提供替代文字；否則，影像會標示為裝飾性。

## 限制

- 此服務強制核心影像v2。 若要切換版本，請更新`IMAGE_RESOURCE_TYPE`。
- 針對綜合轉譯，模型會將核心影像產生的`.coreimg.`個URL取代為直接DAM路徑，並移除`srcset`以避免損毀URL。
- 所有轉譯作業在伺服器上執行一次；JavaScript為選用。

## 快速參考（實作）

- HTL： `ui.apps/.../components/table/table.html`
- Clientlibs： `ui.apps/.../components/table/clientlibs/`
- 模型： `core/.../models/TableModel.java`
- 服務： `core/.../services/ImageComponentRenderer.java`

此模式顯示如何使用核心元件伺服器端撰寫自訂元件，在重複使用核心邏輯時保留您的標籤。
