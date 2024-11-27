---
title: 使用DITA-OT將中繼資料傳遞至輸出
description: 瞭解如何使用AEM Guides中的DITA-OT發佈將中繼資料傳遞至輸出。
feature: Publishing, Metadata Management
role: User
source-git-commit: fa07db6a9cb8d8f5b133258acd5647631b22e28a
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---

# 使用DITA-OT將中繼資料傳遞至輸出 {#id21BJ00QD0XA}

中繼資料是輸出的其他資訊。 在AEM Guides中，您可以傳遞現有的中繼資料或建立自訂中繼資料標籤。 您可以使用DITA-OT發佈將中繼資料傳遞至AEM、PDF、HTML5、EPUB和自訂格式輸出。

執行以下步驟，使用DITA-OT發佈將中繼資料傳遞至輸出：

1. 在&#x200B;**Assets UI**&#x200B;中，導覽至您要傳送中繼資料至DITA-OT的DITA map檔案，並按一下該檔案。
1. 選取並編輯您要將中繼資料欄位傳遞到的輸出預設集。 例如，選取「PDF輸出預設集」。
1. 在選取的輸出預設集的「產生&lt;output\>使用」選項下選取&#x200B;**DITA-OT**。

   ![](images/custom-meta-data-output-preset.png){width="800" align="left"}

1. 從屬性下拉式清單中選取您要傳遞至DITA-OT發佈的中繼資料。

   「屬性」下拉式清單會同時列出自訂和預設屬性。 例如，在上述熒幕擷圖作者中，是自訂屬性，而`dc:description`、`dc:language`、`dc:title`和`docstate`是預設屬性。

   >[!NOTE]
   >
   > 這些屬性是從下列位置可用的metadataList檔案中挑選的： `/libs/fmdita/config/metadataList`。 依預設，此檔案中有四個屬性 — `dc:description`、`dc:language`、`dc:title`和`docstate`。

   此檔案可覆蓋於： `/apps/fmdita/config/metadataList`。

   若要傳遞已定義值的自訂屬性，請參閱[在DITA-OTPDF輸出中使用AEM中繼資料](https://experienceleaguecommunities.adobe.com/t5/xml-documentation-discussions/use-aem-metadata-in-dita-ot-pdf-output/td-p/411880)。

1. 從&#x200B;**屬性**&#x200B;下拉式清單中，選取必要的自訂和預設屬性。 例如，選取`author`、`dc:title`和`dc:description`。 這些是在我們建立檔案後建立的標準`metadata/properties`。 選取的屬性會列在下拉式方塊下方。

   ![](images/selected-metadata-properties.png){width="300" align="left"}

1. 按一下左上方的&#x200B;**完成**&#x200B;以儲存變更。
1. 產生輸出。

選取的中繼資料屬性會傳遞至使用DITA-OT產生的輸出。

**父級主題：**[&#x200B;輸出產生](generate-output.md)
