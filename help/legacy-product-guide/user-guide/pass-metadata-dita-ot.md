---
title: 使用DITA-OT將中繼資料傳遞至輸出
description: 瞭解如何使用AEM Guides中的DITA-OT發佈將中繼資料傳遞至輸出。
feature: Publishing, Metadata Management
role: User
hide: true
exl-id: 55d70c6d-feb0-43f7-9f18-6d1ccdd1e728
TQID: https://experienceleague.adobe.com/I-DddG1Wq9cXsF1IZt6B0XFzbR1gbtvtKPoO-g2nLM0
product_v2:
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: a3bd6397-2eb2-4908-a61c-226e26855dca
subfeature_v2:
  - id: fd6cc9e1-e5e5-494e-b7b1-a32f2d6cd7c9
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2:
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
  - id: ebde5b41-29c9-4f5e-9ef6-1197e85409e3
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 330
ht-degree: 0%

---

# 使用DITA-OT將中繼資料傳遞至輸出 {#id21BJ00QD0XA}

中繼資料是輸出的其他資訊。 在AEM Guides中，您可以傳遞現有的中繼資料或建立自訂中繼資料標籤。 您可以使用DITA-OT發佈將中繼資料傳遞至AEM、PDF、HTML5、EPUB和自訂格式輸出。

執行以下步驟，使用DITA-OT發佈將中繼資料傳遞至輸出：

1. 在&#x200B;**Assets UI**&#x200B;中，導覽至您要傳送中繼資料至DITA-OT的DITA map檔案，並按一下該檔案。
1. 選取並編輯您要將中繼資料欄位傳遞到的輸出預設集。 例如，選取「PDF輸出預設集」。
1. 在選取的輸出預設集的「產生&lt;output\>使用」選項下選取&#x200B;**DITA-OT**。

   ![](images/custom-meta-data-output-preset.png){width="800"}

1. 從屬性下拉式清單中選取您要傳遞至DITA-OT發佈的中繼資料。

   「屬性」下拉式清單會同時列出自訂和預設屬性。 例如，在上述熒幕擷圖作者中，是自訂屬性，而`dc:description`、`dc:language`、`dc:title`和`docstate`是預設屬性。

   >[!NOTE]
   >
   > 這些屬性是從下列位置可用的metadataList檔案中挑選的： `/libs/fmdita/config/metadataList`。 依預設，此檔案中有四個屬性 — `dc:description`、`dc:language`、`dc:title`和`docstate`。

   此檔案可覆蓋於： `/apps/fmdita/config/metadataList`。

   若要傳遞您已定義值的自訂屬性，請參閱[在DITA-OT PDF輸出中使用AEM中繼資料](https://experienceleaguecommunities.adobe.com/t5/xml-documentation-discussions/use-aem-metadata-in-dita-ot-pdf-output/td-p/411880)。

1. 從&#x200B;**屬性**&#x200B;下拉式清單中，選取必要的自訂和預設屬性。 例如，選取`author`、`dc:title`和`dc:description`。 這些是在我們建立檔案後建立的標準`metadata/properties`。 選取的屬性會列在下拉式方塊下方。

   ![](images/selected-metadata-properties.png){width="300"}

1. 按一下左上方的&#x200B;**完成**&#x200B;以儲存變更。
1. 產生輸出。

選取的中繼資料屬性會傳遞至使用DITA-OT產生的輸出。

**父級主題：**&#x200B;[&#x200B;輸出產生](generate-output.md)
