---
title: 發行說明 |已修正2026.11.0 Service Pack 1版本中Adobe Experience Manager Guides的問題
description: 瞭解關於Adobe Experience Manager Guides as a Cloud Service 2026.11.0 Service Pack 1版中的錯誤修正。
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
    internal-label: Experience Manager Guides
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
source-git-commit: 8821e671951d83439688aa33f88ac1f91f0919eb
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 0%
---
# 2026.11.0 Service Pack 1版本中的已修正問題

本文介紹Adobe Experience Manager Guides as a Cloud Service 2026.11.0 Service Pack 1版本中修正的錯誤。

## 發佈

發佈至AEM Sites （搭配複合元件對應）時，會發生下列問題：

- 重新產生所選主題或具有`microservice-based`發佈的子地圖大約需要產生完整地圖的時間長度。 (GUIDES-59322)
- 重新產生包含區塊主題的子地圖會導致目錄顯示不正確的標題和連結。 每個區塊主題專案都會顯示最後一個區塊主題的標題。 (GUIDES-58650)

使用動態基準線（舊版）或新基準線發佈至AEM Sites時，會發生下列問題：

- 在相同的發佈作業期間，基準會重建多次，這會延長發佈時間，並且在某些情況下會導致重建延遲。 使用「新基準線」時，增量發佈也會使用過時的基準線，而不是目前的基準線，因此輸出可能不會反映最新的內容。 (GUIDES-60189)
- 使用Map儀表板時發現一些效能問題。 (GUIDES-60189， GUIDES-55646)

## 已知問題

Adobe已識別2026.11.0 Service Pack 1版的下列已知問題：

- 使用Experience Manager Guides as a Cloud Service 2026.11.0或更新版本時，如果AEM在發佈程式期間（例如伺服器執行個體啟動時）重新啟動某些內部服務，發佈會失敗並出現應用程式錯誤。 (GUIDES-60804)<br>**因應措施：**&#x200B;若要解決此問題，請重試發佈。
- 透過&#x200B;**對應集合**&#x200B;或API為多個AEM Sites （使用複合元件對應）預設集或原生PDF預設集產生輸出時，輸出產生會失敗，並出現`Rebuild the Baseline`例外狀況。 <br>**因應措施：**&#x200B;請依序發佈預設集，而非同時發佈，以避免發生問題。