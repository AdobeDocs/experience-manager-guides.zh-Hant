---
title: Cloud Service效能最佳化建議
description: 瞭解效能最佳化的建議
feature: Performance Optimization
role: Admin
level: Experienced
exl-id: 6c9684d4-180f-4ccb-bfd6-6c82a8a7b720
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
    internal-label: Experience Manager Guides
feature_v2:
  - id: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
    internal-label: Configuration
subfeature_v2:
  - id: baa3aa24-d162-4a57-b73a-d27341145083
    internal-label: Performance optimization
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 81a0e7f0736ba4970673dd87a888a4c60d3c1b4e
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 5%
---
# Cloud Service效能最佳化建議 {#id213BD0JG0XA}

針對效能最佳化，請考量下列幾點：

- 若要最佳化內容與索引體驗，請參閱AEM檔案中的[最佳化內容搜尋與索引](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/indexing.html)。

- 使用自訂DITA-OT進行發佈時修補Xerces Jar。 此為強制設定，取決於您的使用案例。 只有當您使用自訂DITA-OT來發佈輸出時，才需要此變更。

  *必要的組態*：將自訂DITA-OT封裝中的Xerces Jar檔案取代為隨附的OOTB。 預設OOTB `xercesImpl-2.11.0.jar`檔案可在`/libs/fmdita/dita\_resources/DITA-OT.zip`檔案中使用。 請確定您重新命名`xercesImpl-2.11.0.jar`檔案，以符合要取代的舊Xerces Jar檔案。 這可在執行階段完成。

  此變更可減少發佈時間和記憶體使用率，同時發佈包含大量主題的DITA map。
