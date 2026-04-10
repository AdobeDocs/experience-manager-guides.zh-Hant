---
title: Cloud Service效能最佳化建議
description: 瞭解效能最佳化的建議
feature: Performance Optimization
role: Admin
level: Experienced
source-git-commit: 834959a6a0e22cd5d2b2c5d0e57ceb6d45c0c666
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 0%

---

# Cloud Service效能最佳化建議 {#id213BD0JG0XA}

針對效能最佳化，請考量下列幾點：

- 若要最佳化內容與索引體驗，請參閱AEM檔案中的[最佳化內容搜尋與索引](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/indexing.html?lang=zh-Hant)。

- 使用自訂DITA-OT進行發佈時修補Xerces Jar。 此為強制設定，取決於您的使用案例。 只有當您使用自訂DITA-OT來發佈輸出時，才需要此變更。

  *必要的組態*：將自訂DITA-OT封裝中的Xerces Jar檔案取代為隨附的OOTB。 預設OOTB `xercesImpl-2.11.0.jar`檔案可在`/libs/fmdita/dita\_resources/DITA-OT.zip`檔案中使用。 請確定您重新命名`xercesImpl-2.11.0.jar`檔案，以符合要取代的舊Xerces Jar檔案。 這可在執行階段完成。

  此變更可減少發佈時間和記憶體使用率，同時發佈包含大量主題的DITA map。

