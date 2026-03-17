---
title: 管理DITA來源資產的復寫
description: 瞭解如何複製DITA來源資產
feature: Publishing
role: User
source-git-commit: 52921a33d30817434424772ff32b1b31d4878497
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 0%

---

# 管理DITA來源資產的復寫

在某些發佈環境中使用&#x200B;**快速發佈**&#x200B;或&#x200B;**管理出版物**&#x200B;發佈從DITA內容產生的輸出時，AEM也會嘗試發佈關聯的DITA來源資產，例如DITA map，在某些情況下，還會發佈DITA主題。 發生此狀況是因為AEM會將DITA資產視為所產生Sites頁面的相依性。

![](images/quick-publish-site-instance.png){width="350" align="left"}

為了防止將DITA內容意外複製到發佈環境並避免效能問題，管理員必須透過Configuration Manager明確管理DITA資產複製。 此組態可讓管理員控制所支援DITA資產型別(包括DITA map、DITA主題、XML檔案和Markdown (.md)檔案)的復寫。

若要設定DITA資產復寫功能，請檢視[為Cloud Service設定DITA資產復寫](../cs-install-guide/configure-dita-assets-replication.md)或[根據您使用的設定，為內部部署設定DITA資產復寫](../install-guide/configure-dita-asset-replication.md)

