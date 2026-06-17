---
title: 原生PDF發佈功能 |在目錄專案和主題內容套用自訂樣式
description: 瞭解如何建立使用樣式表及內容的樣式。
exl-id: f65c9683-a1fc-432a-854b-83e8f39d7dae
feature: Output Generation
role: Admin
level: Experienced
TQID: https://experienceleague.adobe.com/cqknNhuPThhuNTsLZzwnrUzPJguIPs4J-3rX6PVR2V8
product_v2: id: fae5e35a-80c9-4b94-9352-1a060a6aab1did: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: febac97b369bad427f0f650f2cdc69b0ca6c9f69
workflow-type: tm+mt
source-wordcount: 460
ht-degree: 0%

---

# 在目錄專案和主題內容套用自訂樣式

您可以在支援的對應元素（例如`<topicref>`和`<topichead>`）上使用`outputclass`屬性，將自訂樣式套用至目錄專案、主題或個別主題。 若要將自訂格式套用至整個主題，請在CSS中擴充`outputclass`屬性的樣式定義。

## 設定透過`<topicref>`參考的主題樣式

您可以在`<topicref>`元素上套用`outputclass`，以設定所產生PDF中目錄專案、主題標題或完整主題內容的樣式。

例如，若要識別需要檢閱的主題，請將outputclass屬性新增至DITA map中的對應`<topicref>`元素，並在CSS中定義關聯的樣式。

在下列範例中，*航班歷史記錄*&#x200B;主題已指派值為`new-topic`的`outputclass`屬性。

<img src="./assets/new-topic-attribute-in-map.png" width="500">

`new-topic`類別可用來定義下列專案的樣式：

* 目錄或迷你目錄中的主要專案
* 主要內容中的主題標題
* 主題的整個內容，包括標題

以下CSS定義會變更TOC專案的文字顏色和主題標題：

```css
.new-topic {
  color:#CC5309
}
```

此定義控制目錄中的文字顏色和主題標題。 下列PDF輸出會顯示套用至目錄專案的不同顏色：

<img src="./assets/pdf-output-toc-entry.jpg" width="500">

主題的標題也會使用相同的顏色設定樣式。

<img src="./assets/pdf-output-topic-title.jpg" width="500">

如果您希望目錄專案和主題的標題有不同的樣式，可以分別定義它們，如下所示：

```css
...
/*for styling TOC entry */
.new-topic {
  color:#CC3509
}

/* for styling topic's title */
.new-topic.title {
  color:#092ACC
}
...
```

若要將樣式套用至整個主題內容，請在類別名稱后面附加`-content`尾碼。 下列範例會將變更列新增至主題內容：

```css
...
/* for styling the topic's content */
.new-topic-content {
  -ro-change-bar-color:#A609CC;
}
...
```

使用上述樣式屬性，變更列會新增至&#x200B;*航班歷史記錄*&#x200B;主題的左側，如下所示：

<img src="./assets/pdf-output-topic-content.jpg" width="500">

## 套用樣式至`topichead`元素

您可以在`<topichead>`專案上使用`outputclass`屬性，將不同的樣式套用至目錄專案，以及為`topichead`產生的標題。

例如，如果您在DITA map中定義下列`topichead`：

```xml
<topichead navtitle="Getting Started" outputclass="new-topichead">
    ...
</topichead>
```

`new-topichead`類別會套用至目錄中的主題標題專案，以及為主題標題產生的標題。

如果您想要將不同的樣式套用至標題，請為其定義個別的類別，類似`<topicref>`如何支援目錄專案和主題標題的個別樣式：

```css
...
/* Style for the topichead TOC entry */
.new-topichead {
  color: #CC5309;
}

/* Style for the topichead heading */
.new-topichead.title {
  color: #092ACC;
}...
```

如果要設定與主題相關的內容樣式，請在類別名稱后面附加`- content`尾碼：

```css
.new-topichead-content {
    border-left: 2px solid #cccccc;
    padding-left: 8px;
}
```



## 從目錄移除空白列

如果您尚未定義任何主題的標題，則此類主題的目錄會顯示空白列。

若要從目錄和迷你目錄移除空白列，請在`layout.css`中新增下列樣式：

```css
.toc-body a:empty,
.chaptoc-body a:empty {
    display: none;
} 
```

