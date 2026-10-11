---
title: 根據UUID設定自動檔案名稱
description: 瞭解如何根據UUID設定自動檔案名稱
exl-id: bdbdf119-b928-4ed2-bab3-d99370da8aa9
feature: Filename Configuration
role: Admin
level: Experienced
TQID: 'https://experienceleague.adobe.com/HxTJaPGbwH31vitQ-Cu6wPyCuzZSWDXtq6xMY4hXEAI'
product_v2:
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
    internal-label: Experience Manager Guides
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
feature_v2:
  - id: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
    internal-label: Configuration
subfeature_v2:
  - id: ccd46b93-df7f-4458-ba4c-90a3562d9ab0
    internal-label: Filename configuration
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 81a0e7f0736ba4970673dd87a888a4c60d3c1b4e
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 1%
---
# 根據UUID設定自動檔案名稱 {#id205QG070D5Z}

依預設，建立主題或地圖檔案時，作者也可以選擇指定檔案名稱。 作者可自由依需求指派檔案名稱。 不過，這可能會導致不一致，在大型檔案系統中可以看到各種檔案名稱。 身為管理員，您可以限製作者為他們在系統中建立的檔案指定檔案名稱。 對於每個新主題或對應檔案，您可以選擇自動指派以UUID為基礎的檔案名稱。

使用[組態覆寫](download-install-additional-config-override.md#)中提供的指示來建立組態檔。 在設定檔案中，提供下列\(property\)詳細資訊，以根據UUID設定自動檔案名稱：

| PID | 屬性索引鍵 | 屬性值 |
|---|------------|--------------|
| `com.adobe.fmdita.xmleditor.config.XmlEditorConfig` | `xmleditor.uniquefilenames` | 布林值\(true/false\)。<br> **預設值**： false |

>[!NOTE]
>
> 開啟此選項後，作者在建立新主題或對應檔案時，看不到指定檔案名稱的選項。 您可以從Assets UI和Web編輯器建立新的主題或地圖檔案。

**父級主題：**&#x200B;[&#x200B;設定檔名](conf-file-names.md)
