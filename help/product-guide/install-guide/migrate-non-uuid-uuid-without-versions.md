---
title: 將沒有版本的非UUID內容轉換為UUID內容
description: 瞭解如何移轉不含版本的非UUID內容。
exl-id: 44b5660d-9961-4463-9686-53085249fb05
feature: Migration
role: Admin
level: Experienced
hidefromtoc: 'yes'
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
    internal-label: Experience Manager Guides
feature_v2:
  - id: 5be0fc8f-1cff-5c3e-bb92-2903a56a3de6
    internal-label: Migration
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 81a0e7f0736ba4970673dd87a888a4c60d3c1b4e
workflow-type: tm+mt
source-wordcount: '88'
ht-degree: 0%
---
# 移轉不帶版本的內容

>[!IMPORTANT]
>
> 如果您打算略過或不移轉資產版本，可以選擇此移轉方法。


1. 使用AEM案頭應用程式等Adobe工具，直接從AEM Assets UI從非UUID執行個體下載資產並上傳至UUID執行個體。

1. 確保您啟用DAM更新資產工作流程，並在匯入內容以建立GUID後在所有資產上執行該工作流程。
