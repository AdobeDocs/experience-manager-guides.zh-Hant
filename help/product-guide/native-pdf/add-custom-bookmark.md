---
title: 原生PDF發佈功能 | 在PDF輸出中新增自訂書籤
description: 瞭解如何建立使用樣式表及內容的樣式。
exl-id: 6e6dbba3-da41-4066-b7b2-735a3d92b70a
feature: Output Generation
role: Admin
level: Experienced
source-git-commit: 1c96f25c3b970d04d23e8faf94a8f39095f6bd2c
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 0%

---

# 在PDF輸出中新增自訂書籤

一般而言，DITA map中的TOC會復寫為最終PDF輸出中的書籤，包括選取時開啟TOC頁面的&#x200B;**內容**&#x200B;標題。 此TOC是根據DITA map中的主題或區段標題建立的。

您有時可能想要在PDF輸出中的特定內容上新增自訂書籤，以方便導覽。 若要達成此目的，請在元素上新增`outputclass`屬性，並套用下列屬性：

`bookmark-level: 3`

在此，`bookmark-level`是屬性，而數字`3`是指示書籤加入所在書籤階層中層級的值。 在下列範例中，第一層級主題「連絡人」有一個表格「連絡人清單」，我們已在其中新增值為`custom-bookmark`的`outputclass`屬性。


<img src="./assets/custom-bookmark-attribute.png" width="500">

`custom-bookmark`類別的下列定義已新增至CSS檔案中：

```css
…
/*Adding a custom bookmark*/
.custom-bookmark{
    bookmark-level: 2
}
…
```

在PDF輸出中，*連絡人清單*&#x200B;表格新增到PDF書籤清單的第2層，如下所示：

![](assets/custom-bookmark-in-pdf-output.png) {width="300" align="left"}

>[!NOTE]
>
>您必須選擇新增自訂書籤的正確層級。 如果您指定的數字小於父級主題的書籤，則自訂書籤會佔據父級書籤的位置，而所有其他書籤都會顯示為子系。 這可能會導致意外的書籤結構。

**從PDF輸出書籤中移除內容標題**

如果您不想要在PDF輸出中包含&#x200B;**內容**&#x200B;標題，您可以將&#x200B;**內容**&#x200B;放置在`<p>`元素中，而非`<h1>`元素，以移除標題。

從書籤中移除內容標題的逐步程式如下：

1. 開啟您用於PDF輸出的PDF範本。
2. 開啟&#x200B;**頁面配置**&#x200B;內的&#x200B;**目錄頁面**。
目錄頁面會顯示在右側。
3. 切換至&#x200B;**Source**&#x200B;模式，並將內容所在的元素從`<h1>`變更為`<p>`。

變更前：

```
<h1 class="toc-title">Contents</h1>
```

變更後：

```
<p class="toc-title">Contents</p>
```

儲存變更並重新產生輸出。





