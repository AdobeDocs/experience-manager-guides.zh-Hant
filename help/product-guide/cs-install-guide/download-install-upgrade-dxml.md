---
title: 升級AEM Guides
description: 瞭解如何升級AEM Guides
exl-id: 57ae906f-69e3-4319-89f6-0fa9ddb7a3ff
feature: Installation
role: Admin
level: Experienced
source-git-commit: 0513ecac38840a4cc649758bd1180edff1f8aed1
workflow-type: tm+mt
source-wordcount: '98'
ht-degree: 0%

---

# 升級AEM Guides {#id213BD050YPH}

1. 存取您的Cloud Manager Git存放庫。

1. 更新dox/dox.installer/pom.xml檔案。

1. 將dox.version變數的值更新為Adobe提供的版本詳細資料。

1. 認可變更並執行Cloud Manager管道以部署升級的套件。


>[!NOTE]
>
> 如需有關使用CI/CD管道的詳細資訊，請參閱[在AdobeCloud Manager中使用CI/CD管道](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/cloud-manager/use-the-cicd-pipeline-in-cloud-manager-for-aem.html?lang=zh-Hant)。

## 清除瀏覽器快取

完成升級程式後，所有使用者必須先清除瀏覽器快取，才能使用升級版的AEM Guides。

**上層主題：**&#x200B;[&#x200B;下載並安裝](download-install.md)
