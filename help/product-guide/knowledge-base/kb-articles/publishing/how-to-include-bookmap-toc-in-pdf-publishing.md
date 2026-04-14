---
title: 使用NativePDF的TOC （目錄）發佈
description: 使用NativePDF發佈Dita書籤的目錄和其他書籤
feature: Native PDF Output
author: Pulkit Nagpal(punagpal)
role: User, Admin
exl-id: c551f0a8-f973-4c5a-bd34-f52890a91342
source-git-commit: 9c53ac725618db1164b0ed310a47b258a7224778
workflow-type: tm+mt
source-wordcount: '268'
ht-degree: 0%

---

# 在PDF發佈中產生書籤地圖的目錄

## 設定書籤

包含`<toc>`元素：
在書籤地圖的`<frontmatter>`元素中，找出`<booklists>`元素。  在`<toc>`中巢狀內嵌`<booklists>`專案，如下所示：

```
<frontmatter>
  <booklists>
    <toc/>  <figurelist/>
    <tablelist/>
  </booklists>
</frontmatter>
```

DITA規格也允許將TOC和書籤放在`<backmatter>`區段中。


```
<backmatter>
    <booklists>
      <toc/>
      <figurelist/>
      <indexlist/>
    </booklists>
  </backmatter>
```

書籤結構範例包含TOC、figure-list和table-list （位於前面）以及index-list （位於後面）。

```
<bookmap>
  <title>My Bookmap Title </title>
  <frontmatter>
    <booklists>
      <toc/>
      <figurelist/>
      <tablelist/>
    </booklists>
  </frontmatter>

  <chapter href="chapter1.ditamap">
  <chapter href="chapter2.ditamap">
  </chapter>

  <backmatter>
    <booklists>
      <indexlist/>
    </booklists>
  </backmatter>
</bookmap>
```

目錄和書籤清單會根據書籤地圖中定義的結構自動產生。

書籤對應設定完成後，請使用原生PDF來產生PDF輸出。 它會處理書籤地圖結構和參考，包括目錄和書籤。

## PDF中的目錄設計及其順序

原生PDF功能提供量身打造目錄版面與設計的便利方法。

您可以透過layout.css的目錄和樣式個別的頁面配置來控制設計。

PDF中的目錄和其他書籤清單順序僅以書籤地圖的結構為基礎。

![toc](../assets/publishing/toc.png)


## 常見問題

### 如何在PDF中包含Ditamap的目錄

Ditamap本身不會像書籤一樣直接擁有目錄(TOC)。 不過，Ditamap在定義內容結構方面扮演著關鍵角色，並間接對目錄產生流程作出貢獻。

如果您要發佈Ditamap，原生PDF就會提供自動產生目錄和書籤清單的功能，因此您可以從原生PDF設定啟用/停用ditamap產生目錄。

![啟用停用TOC](../assets/publishing/pageorder.png)

## 其他資源：

- [原生PDF設計頁面配置檔案](https://experienceleague.adobe.com/en/docs/experience-manager-guides/using/install-guide/on-prem-ig/output-gen-config/config-native-pdf-publish/design-page-layout)
- [預先錄製的原生PDF Essentials專家會議](https://experienceleague.adobe.com/en/docs/experience-manager-guides/using/knowledge-base/expert-session/native-pdf-publishing-essentials-feb23)

<br>
<br>

在AEM Guides社群[論壇](https://experienceleaguecommunities.adobe.com/t5/experience-manager-guides/ct-p/aem-xml-documentation)上發佈任何查詢。



