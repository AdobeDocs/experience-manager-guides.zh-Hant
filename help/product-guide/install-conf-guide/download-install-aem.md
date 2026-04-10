---
title: 安裝Adobe Experience Manager
description: 瞭解如何安裝Adobe Experience Manager
feature: Introduction, Installation
role: Admin
level: Experienced
source-git-commit: 6f3f05419f4f5cdd45ab580cdee6fa869f20f01d
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 0%

---

# 安裝Adobe Experience Manager {#id213BCI020E8}

AEM Guides是安裝在Adobe Experience Manager頂端的外掛程式。 安裝AEM需要瞭解一些基本的AEM概念和建議的部署案例。 下列連結資源將協助您開始安裝AEM：

- [基本AEM概念](https://helpx.adobe.com/tw/experience-manager/6-5/sites/deploying/using/deploy.html#BasicConcepts)

- [建議的AEM部署](https://helpx.adobe.com/tw/experience-manager/6-5/sites/deploying/using/recommended-deploys.html)

>[!IMPORTANT]
>
> 如果您使用Java 11搭配AEM 6.5.x，則可能會遇到問題 — *JDK 11導致`NoClassDefFoundError`*。 參考[JDK 11導致NoClassDefFoundError \| AEM 6.5](https://helpx.adobe.com/experience-manager/kb/jdk-11-causes-noclassdeffounderror---aem-6-5.html)文章解決此問題。

一旦您確定最適合您組織的部署策略，請依照AEM檔案中&#x200B;*[快速入門](https://helpx.adobe.com/tw/experience-manager/6-5/sites/deploying/using/deploy.html#GettingStarted)*&#x200B;一節的說明執行安裝程式。

如果您打算升級AEM執行個體，則必須依照指定順序進行：

1. 解除安裝AEM Guides。
1. 升級您的AEM執行個體。
1. 重新安裝AEM Guides。

>[!IMPORTANT]
>
> 您可以考慮許多效能最佳化建議，以提升系統效能。 如需詳細資訊，請參閱[效能最佳化建議](./perf-optimization-on-prem.md)。
