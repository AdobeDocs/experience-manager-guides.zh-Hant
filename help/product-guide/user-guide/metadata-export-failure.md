---
title: 在Experience Manager Guides中，中繼資料匯出因「字串太長」例外狀況而失敗
description: 瞭解Assets UI中Guides內容中繼資料匯出為何會失敗。
feature: Authoring, Publishing
role: User
product_v2: id: fae5e35a-80c9-4b94-9352-1a060a6aab1did: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: a3bd6397-2eb2-4908-a61c-226e26855dcaid: ab01a588-7dea-43f2-a699-0b3f128465d6
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2: id: c1579802-ddd4-4214-8a91-97b2066abe11
source-git-commit: 1c61df4820e559417410d25c81800637481b040c
workflow-type: tm+mt
source-wordcount: 274
ht-degree: 0%

---

# 為何資料夾的中繼資料匯出會失敗並出現「字串太長」例外狀況？

當您從Assets UI [匯出資料夾的中繼資料](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/assets/using/metadata#export-metadata)時，匯出工作可能會失敗，並出現`String is too long`例外狀況。 當資料夾包含儲存非字串值（例如`baselineObj`）的Experience Manager Guides特定屬性時，通常會發生這種情況。

**為什麼會發生這個情況？**

部分儲存在資產中繼資料節點下的屬性會由Experience Manager Guides內部使用，且包含資料（例如JSON物件），而非純字串值。 匯出資料夾的中繼資料時，如果要匯出的&#x200B;**屬性**&#x200B;設為&#x200B;**全部**，匯出作業會嘗試將每個屬性轉換為字串，但無法對儲存此類資料的屬性進行轉換。

**如何防止此情況？**

為了避免此失敗，下列屬性預設會從&#x200B;**資產中繼資料匯出工具組態**&#x200B;的中繼資料匯出中排除：

- `baseline`
- `namedoutputs`
- `conditionpresets`
- `nextgenbaselinestore`

**我仍可以匯出這些屬性嗎？**

可以。 如果您在匯出中需要一或多個這些屬性，可以編輯&#x200B;**資產中繼資料匯出工具組態**，並將它們從排除清單中移除。

從排除清單移除屬性並不保證匯出會成功。 根據基礎資料的大小和內容，工作仍可能會失敗，並出現相同的例外狀況。 如果您在重新啟用屬性後遇到此問題，請將其新增回排除清單，以恢復預設的可靠匯出行為。
