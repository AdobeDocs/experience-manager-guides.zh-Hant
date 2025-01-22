---
title: 在從AEM Guides產生的AEM Sites頁面中啟用內容變數(CCVAR)
description: 在從AEM Guides產生的AEM Sites頁面中使用內容變數(CCVAR)
feature: Web Editor
role: User, Admin
exl-id: f9adbb3f-6c1c-4d6f-b55d-1fb45acca91a
source-git-commit: 4020534552bdb77545c2a283f2a90adc3aebc729
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 1%

---

# 在從AEM Guides產生的AEM Sites頁面中啟用內容變數(CCVAR)

內容變數(CCVAR)是ACS Commons的功能，可讓作者直接在其編寫的文字中使用動態內容變數。 雖然CCVAR常用於AEM Sites，本文說明如何透過從&#x200B;**AEM Guides** *中編寫的內容產生的頁面，主要使用DITA map*&#x200B;中定義的關鍵字來達成類似的功能。


## 什麼是內容變數(CCVAR)？

CCVAR可讓作者將動態變數插入其內容，這些動態變數會在執行階段根據內容解析。 例如，`((page_properties.pageTitle))`等變數可在內容轉譯期間動態提取頁面標題。


## 如何在AEM Guides產生的AEM Sites頁面中啟用CCVAR？

考慮到AEM Guides是作為所有內容(包括AEM Sites、PDF或HTML5)的來源，若要在從AEM Guides產生的頁面上啟用CCVAR，您需要使用關鍵字來定義CCVAR名稱。 若要在參考線中執行此動作，請使用`<keydef>`元素在您的DITA map中定義&#x200B;**關鍵字**。 這些關鍵字可對應至動態值（或CCVAR名稱），可讓您在DITA主題中參照它們。


## 必要條件

繼續之前，請先確定符合下列必要條件：

1. **已安裝AEM ACS Commons**：
   - 確定您的AEM執行個體上已安裝&#x200B;**ACS AEM Commons**。 使用CCVAR時需要此專案。

2. **內容變數設定**：
   - 使用[正式檔案](https://adobe-consulting-services.github.io/acs-aem-commons/features/contextual-content-variables/index.html)在AEM中完成&#x200B;**內容變數**&#x200B;的設定。 其中包括：
      - 正在啟用&#x200B;**屬性彙總**。
      - 正在設定&#x200B;**HTML重寫** (如果使用HTML輸出)。
      - 正在設定&#x200B;**JSON重新寫入** （若使用JSON輸出）。



## 在AEM Guides中啟用CCVAR的步驟

### 1.在DITA Map中定義關鍵字

- 在AEM Guides中，使用DITA map中的`<keydef>`元素定義關鍵字，以對應至CCVAR。
- 例如：

```xml
  <keydef keys="product">
    <topicmeta>
      <keywords>
        <keyword>((page_properties.pageTitle))</keyword>
      </keywords>
    </topicmeta>
  </keydef>
```

- `keys`屬性（在此範例中為`product`）將用於在DITA主題中參考此變數。


## 2.在DITA主題中使用關鍵字

- 在主題中，使用CCVar的任何位置都使用關鍵字。
- 例如：

```xml
  <p>This is the title of the product: <keyword keyref="product"/> </p>
```

- `keyref`屬性指向`<keydef>`專案（`product`，在此案例中）中定義的`keys`值。
- 在產生輸出期間，關鍵字將替換為對應的CCVar值。


## 3.產生輸出

- 當您產生AEM Sites的輸出時，關鍵字參照將會解析為相應的動態值。
- 例如：
   - 如果`((page_properties.pageTitle))`解析為`My Product`，將會顯示輸出：

```xml
   This is the title of the product: My Product.
```


## 範例使用案例

假設您要動態地將頁面的語言插入DITA主題。 以下說明達成此目標的方式：

**在DITA Map中定義關鍵字**：

```xml
   <keydef keys="pageLanguage">
     <topicmeta>
       <keywords>
         <keyword>((inherited_page_properties.jcr:language))</keyword>
       </keywords>
     </topicmeta>
   </keydef>
```

**參考DITA主題中的關鍵字**：

```xml
   <p>The title of this page is: <keyword keyref="pageLanguage"/>.</p>
```

**產生的輸出**：

如果`((inherited_page_properties.jcr:language))`解析為`en`，將會顯示輸出：

```
     The language of this page is: en.
```


### 資源

如需&#x200B;**內容變數**&#x200B;的詳細資訊，請參閱官方檔案：\
[AEM Commons中的內容內容變數](https://adobe-consulting-services.github.io/acs-aem-commons/features/contextual-content-variables/index.html)
