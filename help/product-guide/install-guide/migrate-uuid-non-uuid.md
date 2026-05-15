---
title: 非UUID移轉至UUID內容
description: 瞭解如何將非UUID移轉至UUID內容
exl-id: f8b723bf-84c0-4fe6-936e-63970fb3e417
feature: Migration
role: Admin
level: Experienced
TQID: https://experienceleague.adobe.com/pZ0HRoSRWcGz2IT9tWAZ-vZYLc-Zc4kyYt8OXRohmTU
product_v2: id: fae5e35a-80c9-4b94-9352-1a060a6aab1did: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: b1210526-416b-4ef6-bcc0-1692e99f30e9id: e88e74c7-6080-446a-8eb0-496f1ac5f7e6
subfeature_v2: id: c8841798-1a28-4264-a46a-984860f8e6f6
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2: id: d095671a-1355-40aa-8b5f-06c33c68080bid: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 320
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

- [**4.3.1非UUID移轉至4.3.2 UUID內容移轉**](./migrate-non-uuid-4-3.md)
- [**4.6.0 Service Pack 4非UUID移轉至4.6.1 UUID內容移轉**](./migrate-non-uuid-uuid-4-6.md)



