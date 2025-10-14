---
title: 非UUID移轉至UUID內容
description: 瞭解如何將非UUID移轉至UUID內容
exl-id: f8b723bf-84c0-4fe6-936e-63970fb3e417
feature: Migration
role: Admin
level: Experienced
source-git-commit: e38cd858201ea657ce276eb4b358b0d4eff502b2
workflow-type: tm+mt
source-wordcount: '205'
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
| 4.3.1非UUID | 4.3.2 UUID | 移轉至4.3.2版UUID後，您可以直接安裝4.6.0 (UUID)。 開始使用4.6.0後，請升級至5.1.0版，然後安裝5.1.0 Service Pack 1。 |
| 4.6.0 Service Pack 4非UUID | 4.6.1 UUID | 移轉至4.6.1版UUID後，您可以直接升級至5.1.0版(UUID)。 升級完成後，請安裝5.1.0版Service Pack 1。 |

如需移轉內容的詳細步驟，請參閱下列文章：

- [從**4.3.1非UUID移轉至4.3.2 UUID內容**](./migrate-non-uuid-4-3.md)
- [**4.6.0 Service Pack 4 （非UUID）至4.6.1 UUID內容移轉**](./migrate-non-uuid-uuid-4-6.md)



