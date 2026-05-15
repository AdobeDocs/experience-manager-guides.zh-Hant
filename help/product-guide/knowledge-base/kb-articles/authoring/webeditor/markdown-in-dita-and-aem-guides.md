---
title: 在DITA AEM Guides中使用Markdown
description: 在DITA AEM Guides中移轉並使用Markdown
author: Pulkit Nagpal(punagpal)
exl-id: a94c0129-df40-4b61-ac60-679b2ffe7e86
TQID: https://experienceleague.adobe.com/z41KjrBkAeDaH-iKXOFLH44qOQElziip1FqcRhnKaUI
product_v2:
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: a3bd6397-2eb2-4908-a61c-226e26855dca
  - id: ab01a588-7dea-43f2-a699-0b3f128465d6
subfeature_v2:
  - id: ad602516-aca3-4247-9ae8-f393d958efa9
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 281
ht-degree: 0%

---

# 在AEM Guides中使用Markdown

## 可用選項

在AEM Guides中使用Markdown檔案有2種選項：

- 選項1 ：在AEM Guides中匯入現有的Markdown，並直接在ditamap中使用它們進行發佈

- 選項2 ：將現有的Markdown檔案轉換為DITA

讓我們來討論每個選項：

### 選項1：在AEM Guides中匯入現有的Markdown，並直接在ditamap中使用它們進行發佈

其設定更簡單，實作更快速。 但是，AEM Guides功能（例如內容重複使用）的功能利用有限。

使用者需要新增屬性`format="markdown" `或`format="mdita"`，讓發佈引擎瞭解檔案型別並據此發佈。

範例檔案： [Markdown Ditamap](https://acrobat.adobe.com/id/urn:aaid:sc:AP:da31137e-be84-44fb-8974-d038eeff0283)

![參考熒幕擷圖](../../assets/authoring/markdown_map.png)


#### 發佈至PDF和Web輸出

AEM Guides提供網頁（Html5/AEM網站）和PDF （原生PDF/DITA-OT）選項，用於發佈Markdown內容的ditamap

### 選項2 ：將Markdown轉換為DITA格式

充分利用AEM Guides功能，包括內容重複使用、條件處理翻譯、基準等。但是，必須先將`.md`轉換為`.dita`格式。

您可以使用Adobe FrameMaker和DITA-OT等外部工具將Markdown轉換為DITA。


若為Adobe FrameMaker，請參閱： [匯入Markdown](https://www.adobe.com/in/products/framemaker/features.html#import-markdown)

若為DITA-OT，請參閱： [Markdown作為輸入](https://www.dita-ot.org/dev/topics/markdown-input.html)

使用Adobe FrameMaker轉換的範例檔案： [Markdown轉換為DITA範例](https://acrobat.adobe.com/id/urn:aaid:sc:AP:874881f3-ba43-410c-abc6-2df899536d79)

#### 發佈至PDF和Web輸出

一旦Markdown檔案轉換為DITA，使用者即可順暢地將輸出發佈為AEM Guides中可用的任何格式。

AEM Guides中的可用格式： [輸出格式](../../../../user-guide/generate-output-understand-presets.md)
