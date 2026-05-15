---
title: 升級AEM Guides
description: 瞭解如何升級AEM Guides
exl-id: 57ae906f-69e3-4319-89f6-0fa9ddb7a3ff
feature: Installation
role: Admin
level: Experienced
TQID: https://experienceleague.adobe.com/jGMljbRp60Wst7hVLeanMTLHY79Yhqo7yeUCCsLXx3k
product_v2: id: fae5e35a-80c9-4b94-9352-1a060a6aab1did: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 114
ht-degree: 2%

---

# 升級AEM Guides {#id213BD050YPH}

1. 存取您的Cloud Manager Git存放庫。

1. 更新dox/dox.installer/pom.xml檔案。

1. 將dox.version變數的值更新為Adobe提供的版本詳細資料。

1. 認可變更並執行Cloud Manager管道以部署升級的套件。


>[!NOTE]
>
> 如需有關使用CI/CD管道的詳細資訊，請參閱[在Adobe Cloud Manager中使用CI/CD管道](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/cloud-manager/use-the-cicd-pipeline-in-cloud-manager-for-aem.html)。

## 清除瀏覽器快取

完成升級程式後，所有使用者必須先清除瀏覽器快取，才能使用升級版的AEM Guides。

**上層主題：**[&#x200B;下載並安裝](download-install.md)
