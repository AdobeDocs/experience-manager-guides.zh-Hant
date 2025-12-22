---
title: 非UUID移轉至UUID內容
description: 瞭解如何將非UUID移轉至UUID內容
exl-id: f8b723bf-84c0-4fe6-936e-63970fb3e417
feature: Migration
role: Admin
level: Experienced
source-git-commit: 56f1bd81e74ad9b479b2dcbcf04e1ee82e9a9041
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 0%

---

# 非UUID移轉至UUID內容 {#id226TI0U20XA}


您可以根據目前使用的Experience Manager Guides版本，將非UUID內容移轉至UUID。

>[!IMPORTANT]
>
> 將內容移轉至UUID伺服器之前，請確定您有安裝了相容AEM Guides版本的非UUID伺服器。

## 相容性矩陣

請根據您目前的非UUID版本，使用下列矩陣來決定正確的移轉路徑。 這可確保移轉後的順暢轉換。

| 移轉時所需的非UUID版本 | 移轉後的UUID版本 | 支援的移轉後升級路徑 |
|---|---|---|
| 4.3.1非UUID | 4.3.2 UUID | 移轉至4.3.2版UUID後，您必須直接安裝4.6.0 (UUID)。 開始使用4.6.0後，請升級至5.1.0版，然後安裝5.1.0 Service Pack 3。 |
| 4.6.0 Service Pack 4非UUID | 4.6.1 UUID | 移轉至4.6.1版UUID後，您必須直接升級至5.1.0 (UUID)。 升級完成後，請安裝5.1.0版Service Pack 3。 |

## 移轉時間預估

移轉公用程式會以平均速率（每個資產約50毫秒）處理資產。 下表提供使用64個vCPU、128 GB RAM及SSD支援儲存裝置的系統移轉時間預估值。 對於大型存放庫或具有許多轉譯或高解析度二進位檔的資產，記憶體需求可能會增加。

>[!NOTE]
>
> 實際移轉時間可能依硬體效能、儲存輸送量、同時進行的AEM活動以及整體系統負載而有所不同。


| **資產計數** | **約 時間** |
|-----------------|-------------------------|
| 10K | ~8-9分鐘 |
| 5萬 | ~42分鐘 |
| 100K | ~1.4小時 |
| 25萬 | ~3.5小時 |
| 500K | ~7小時 |
| 75萬 | ~10.5小時 |
| 1分鐘 | ~14小時 |
| 200萬 | ~28小時（~1.2天） |
| 3分鐘 | ~42小時（~1.75天） |
| 5分鐘 | ~69小時（~2.9天） |
| 10分鐘 | ~139小時（~5.8天） |


如需移轉內容的詳細步驟，請參閱下列文章：

- [從&#x200B;**4.3.1非UUID移轉至4.3.2 UUID內容**](./migrate-non-uuid-4-3.md)
- [**4.6.0 Service Pack 4 （非UUID）至4.6.1 UUID內容移轉**](./migrate-non-uuid-uuid-4-6.md)



