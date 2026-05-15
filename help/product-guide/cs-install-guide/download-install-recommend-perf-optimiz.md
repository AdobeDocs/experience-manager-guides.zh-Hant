---
title: 效能最佳化建議
description: 瞭解效能最佳化的建議
exl-id: 92ac1f81-2f51-44b0-82c3-56b39e8f3027
feature: Performance Optimization
role: Admin
level: Experienced
TQID: https://experienceleague.adobe.com/vh0hogZNMjKrCL12WdKVuwF2qXdzy64KxIhhB-K4esA
product_v2:
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: a3bd6397-2eb2-4908-a61c-226e26855dca
  - id: b1210526-416b-4ef6-bcc0-1692e99f30e9
  - id: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
  - id: e88e74c7-6080-446a-8eb0-496f1ac5f7e6
subfeature_v2:
  - id: baa3aa24-d162-4a57-b73a-d27341145083
  - id: c8841798-1a28-4264-a46a-984860f8e6f6
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2:
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 162
ht-degree: 5%

---

# 效能最佳化建議 {#id213BD0JG0XA}

針對效能最佳化，請考量下列幾點：

- 若要最佳化內容與索引體驗，請參閱AEM檔案中的[最佳化內容搜尋與索引](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/indexing.html)。

- 使用自訂DITA-OT進行發佈時修補Xerces Jar。 此為強制設定，取決於您的使用案例。 只有當您使用自訂DITA-OT來發佈輸出時，才需要此變更。

  *必要的組態*：將自訂DITA-OT封裝中的Xerces Jar檔案取代為隨附的OOTB。 預設的OOTB xercesImpl-2.11.0.jar檔案可在/libs/fmdita/dita\_resources/DITA-OT.zip檔案中使用。 請務必重新命名xercesImpl-2.11.0.jar檔案，以符合要取代的舊Xerces Jar檔案。 這可在執行階段完成。

  此變更可減少發佈時間和記憶體使用率，同時發佈包含大量主題的DITA map。


**上層主題：**&#x200B;[&#x200B;下載並安裝](download-install.md)
