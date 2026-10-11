---
title: 升級適用於Cloud Service的AEM Guides
description: 瞭解如何升級AEM Guides
feature: Installation
role: Admin
level: Experienced
exl-id: 9d48a7c4-384d-4ad4-a1d3-4c50d97e5d5b
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
    internal-label: Experience Manager Guides
feature_v2:
  - id: e88e74c7-6080-446a-8eb0-496f1ac5f7e6
    internal-label: Administration
subfeature_v2:
  - id: e557051c-ff02-4ff8-9421-cf452af0edd5
    internal-label: Installation
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 81a0e7f0736ba4970673dd87a888a4c60d3c1b4e
workflow-type: tm+mt
source-wordcount: '120'
ht-degree: 2%
---
# 升級適用於Cloud Service的AEM Guides {#id213BD050YPH}

升級AEM Guides時，請執行以下步驟：

1. 存取您的Cloud Manager Git存放庫。

1. 更新`dox/dox.installer/pom.xml`檔案。

1. 將`dox.version`變數的值更新為Adobe提供的版本詳細資料。

1. 認可變更並執行Cloud Manager管道以部署升級的套件。


>[!NOTE]
>
> 如需有關使用CI/CD管道的詳細資訊，請參閱[在Adobe Cloud Manager中使用CI/CD管道](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/cloud-manager/use-the-cicd-pipeline-in-cloud-manager-for-aem.html?lang=zh-Hant)。

## 清除瀏覽器快取

完成升級程式後，所有使用者必須先清除瀏覽器快取，才能使用升級版的AEM Guides。
