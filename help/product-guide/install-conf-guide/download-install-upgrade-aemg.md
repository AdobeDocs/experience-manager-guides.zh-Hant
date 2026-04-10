---
title: 升級適用於Cloud Service的AEM Guides
description: 瞭解如何升級AEM Guides
feature: Installation
role: Admin
level: Experienced
source-git-commit: b416334318a83e882c32318bc4769d24268cdd1c
workflow-type: tm+mt
source-wordcount: '103'
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
> 如需有關使用CI/CD管道的詳細資訊，請參閱[在Adobe Cloud Manager中使用CI/CD管道](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/cloud-manager/use-the-cicd-pipeline-in-cloud-manager-for-aem.html)。

## 清除瀏覽器快取

完成升級程式後，所有使用者必須先清除瀏覽器快取，才能使用升級版的AEM Guides。
