---
title: 安裝Adobe Experience Manager
description: 瞭解如何安裝Adobe Experience Manager
feature: Introduction, Installation
role: Admin
level: Experienced
exl-id: d72b007c-9f0a-41be-bca2-2d6b54c30de1
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
    internal-label: Experience Manager Guides
feature_v2:
  - id: e88e74c7-6080-446a-8eb0-496f1ac5f7e6
    internal-label: Administration
subfeature_v2:
  - id: c5fd2af0-6cbb-4746-ab0d-40ecb093af12
    internal-label: Introduction
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
source-wordcount: '213'
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
