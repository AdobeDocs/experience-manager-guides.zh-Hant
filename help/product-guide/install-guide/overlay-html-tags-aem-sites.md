---
title: 覆蓋非舊版AEM Sites輸出中的HTML標籤
description: 根據核心元件對應設定aem sites輸出的視訊和影像設定
feature: Installation
role: Admin
level: Experienced
exl-id: 726420e0-fe52-4334-b72a-8eb8bcae4d6c
source-git-commit: 6e23f52fc9124d0f07f8108da1b5fe574f553469
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 0%

---

# 覆蓋AEM Sites輸出中的HTML標籤

您可以在使用HTML預設集產生的AEM Sites輸出中，根據網頁編輯器中的核心元件對應，新增和自訂AEM Sites標籤。 若要自訂HTML標籤，您可以覆蓋`config.xml`檔案。 例如，您可以在AEM Sites輸出中設定視訊和影像地圖。

執行以下步驟以覆蓋和更新`config.xml`檔案：

1. 登入AEM並開啟CRXDE Lite模式。

1. 導覽至下列位置可用的組態檔：

   `/libs/fmdita/cq/xssprotection/config.xml`

1. 在Apps節點內建立`xssprotection`資料夾的覆蓋節點。

1. 導覽至`apps`節點中可用的組態檔：

   `/apps/fmdita/config/config.xml`

1. 更新下列影片和影像標籤。 然後，儲存檔案。

影片：

```XML
    <tag name="video" action="validate">
    <attribute name="src">
      <regexp-list>
        <regexp name="anything"/>
      </regexp-list>
    </attribute>
    <attribute name="width">
       <regexp-list>
           <regexp name="anything"/>
       </regexp-list>
    </attribute>
    <attribute name="height">
       <regexp-list>
          <regexp name="anything"/>
       </regexp-list>
     </attribute>
     <attribute name="data">
       <regexp-list>
         <regexp name="anything"/>
       </regexp-list>
    </attribute>
    <attribute name="class">
       <regexp-list>
           <regexp name="anything"/>
       </regexp-list>
    </attribute>
    <attribute name="poster">
      <regexp-list>
        <regexp name="anything"/>
        </regexp-list>
    </attribute>
    <attribute name="controls">
        <regexp-list>
            <regexp name="anything"/>
        </regexp-list>
    </attribute>
    </tag>
    <tag name="source" action="validate">
      <attribute name="src">
        <regexp-list>
           <regexp name="anything"/>
        </regexp-list>
      </attribute>
    </tag>
```

影像地圖：

```XML
        <tag name="map" action="validate">
    <attribute    name="name">
        <regexp-list>
            <regexp name="anything"/>
        </regexp-list>
    </attribute>
    </tag>
    <!-- Image & image related tags -->
    <tag name="img" action="validate">
    <attribute name="src" onInvalid="removeTag">
        <regexp-list>
            <regexp name="onsiteURL"/>
            <regexp name="offsiteURL"/>
        </regexp-list>
    </attribute>
    <attribute name="name"/>
    <attribute name="alt"/>
    <attribute name="height"/>
    <attribute name="width"/>
    <attribute name="border"/>
    <attribute name="align"/>
    <attribute name="usemap">
        <regexp-list>
            <regexp name="anything"/>
        </regexp-list>
    </attribute>
    <attribute name="hspace">
        <regexp-list>
            <regexp name="number"/>
        </regexp-list>
    </attribute>
    <attribute name="vspace">
        <regexp-list>
            <regexp name="number"/>
        </regexp-list>
    </attribute>
    </tag>
    <tag name="area" action="validate">
    <attribute name="shape">
        <regexp-list>
            <regexp name="anything"/>
        </regexp-list>
    </attribute>
    <attribute name="coords">
        <regexp-list>
            <regexp name="anything"/>
        </regexp-list>
    </attribute>
    <attribute name="href">
        <regexp-list>
            <regexp name="anything"/>
        </regexp-list>
    </attribute>
   </tag>
```




深入瞭解[安全性](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/implementing/developing/introduction/security)的最佳實務。
