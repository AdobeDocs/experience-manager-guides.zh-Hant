---
title: 原生PDF |設定用於發佈雲端服務PDF的基本輸出位置
description: 設定用於發佈雲端服務PDF的基本輸出位置
feature: Output Generation
role: Admin
level: Experienced
exl-id: d79085d6-938a-4e80-84a2-03562e6b76e0
TQID: 'https://experienceleague.adobe.com/E4J5BCDQBZdyqfQ-ksOCrMZYO1Bg9BMI-wQZRK96yqY'
product_v2:
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
    internal-label: Experience Manager Guides
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
feature_v2:
  - id: a3bd6397-2eb2-4908-a61c-226e26855dca
    internal-label: Publishing
  - id: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
    internal-label: Configuration
subfeature_v2:
  - id: fd6cc9e1-e5e5-494e-b7b1-a32f2d6cd7c9
    internal-label: Output generation
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 81a0e7f0736ba4970673dd87a888a4c60d3c1b4e
workflow-type: tm+mt
source-wordcount: '80'
ht-degree: 2%
---
# 設定用於發佈雲端服務輸出的基底輸出位置

若要配置基本輸出位置，請執行下列步驟：

1. 使用[組態覆寫](../cs-install-guide/download-install-additional-config-override.md)中提供的指示來建立組態檔。

1. 在組態檔中，提供下列（屬性）詳細資訊，以設定基礎輸出位置：

   | PID | 屬性索引鍵 | 屬性值 |
   |---|---|---|
   | `com.adobe.fmdita.config.ConfigManager` | `base.output.path` | **預設值：** &quot;/content/dam/fmdita-outputs&quot; |
