---
title: 發行說明 | Adobe Experience Manager Guides 5.1.0 Service Pack 3版的新增功能
description: 瞭解Adobe Experience Manager Guides 5.1.0 Service Pack 3版中的新功能和增強功能
role: Leader
exl-id: 1b2e45a8-bea6-4b78-bd2e-cc02df86f40a
TQID: https://experienceleague.adobe.com/dXXQ1YvVduT11vvF5qyXHLqnuo1xMKkAb5I-EoD2JAA
product_v2:
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: a3bd6397-2eb2-4908-a61c-226e26855dca
subfeature_v2:
  - id: fd6cc9e1-e5e5-494e-b7b1-a32f2d6cd7c9
role_v2:
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 176
ht-degree: 0%

---

# 5.1.0 Service Pack 3版（2025年12月）的新增功能

本文介紹5.1.0 Service Pack 3版本Adobe Experience Manager Guides推出的新功能和增強功能。

如需此版本中已修正的問題清單，請檢視5.1.0 Service Pack 3版本[&#128279;](fixed-issues-5-1-0-sp3.md)中的已修正問題。

瞭解5.1.0 Service Pack 3版本[&#128279;](../release-info/upgrade-instructions-5-1-0-sp3.md)的升級指示。


## 設定特定輸出預設集的自訂影像轉譯

您現在可以使用`renditionmapping.xml`中的`outputName`屬性，為相同輸出型別下的個別輸出預設集設定不同的影像轉譯。 此增強功能可讓您在發佈需要針對不同情境設定不同影像解析度的內容時，擁有更大的彈性。 例如，您可能會想要讓主要HTML5輸出使用高解析度影像，同時為輕量版預設集使用較小的縮圖。

如需詳細資訊，請檢視[在輸出產生](../install-guide/conf-output-generation.md#handle-image-rendition-during-output-generation)中處理影像轉譯。
