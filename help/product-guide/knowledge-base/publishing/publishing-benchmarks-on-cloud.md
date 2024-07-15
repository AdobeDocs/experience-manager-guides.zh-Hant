---
title: 在AEMaaCS上發佈基準的指南
description: 瞭解AEM Cloud上發佈的系統限制。
exl-id: 2cb4dfa4-dafc-409a-8d29-dbb00fabeae5
feature: Publishing
role: User, Admin
source-git-commit: be06612d832785a91a3b2a89b84e0c2438ba30f2
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 8%

---

# AEMaaCS上的AEM Guides發佈基準

目前，AEM Guides雲端服務在發佈指南團隊正積極努力解決的地圖大小上有一些限制。

指南團隊已推出可擴充的發佈微服務，以支援大型地圖和多個同時發佈。 若要深入瞭解新的發佈微服務，請參閱[發佈微服務架構](publish-microservice-architecture-and-performance.md)

若要為任何AEM雲端環境設定新的發佈服務，請參閱[設定新的微服務式發佈](configure-microservices.md)


## 執行環境

    AEM版本： 2023.5.11983.20230511T173830Z
    指南附加版本： 2023.6.0
    AEM網站範本： AEM Guides OOTB範本
    DITA-OT版本： 3.5.4
    Publish工作流程型別：分割Publish工作流程
    微服務支援的輸出：原生PDF、PDF(Dita-OT)

## 輸出世代編號

| 輸出類型 | 地圖大小（主題參照） | 執行時間（秒） | 發佈微服務 |
|---------------|------------------------------|----------------------------|-----------------------|
| AEM網站 | 3500 | 5220 | 否 |
| 原生PDF | 3500 | 780 | 是 |
| PDF(DITA-OT) | 11000 | 960 | 是 |
| HTML5 | 3500 | 240 | 否 |
| 自訂 | 300 | 300 | 否 |

## 要記住的關鍵點

- AEM Site會在產生期間個別轉譯，以建立許多cq：Page節點和平面化。 因此，建議您避免執行大型的多重AEM Site同時發佈，因為這會造成系統負擔過重。
- AEM網站產生時間取決於所使用的範本。 如果使用複雜範本，執行時間可能會增加。
- 自訂發佈執行時間用於範例自訂輸出。 自訂發佈時間完全取決於客戶自己的轉換邏輯。
