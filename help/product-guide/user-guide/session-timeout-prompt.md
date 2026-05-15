---
title: 瞭解Experience Manager Guides中的工作階段逾時
description: 瞭解Experience Manager Guides中的工作階段逾時。
feature: Authoring, Publishing
role: User
exl-id: f09b1215-4753-4dfd-89ef-1629257e5efe
TQID: https://experienceleague.adobe.com/nrxkVxSUooy2-08PaUp1pjiH8w2kBBNGC9efarvepbQ
product_v2: id: fae5e35a-80c9-4b94-9352-1a060a6aab1did: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: a3bd6397-2eb2-4908-a61c-226e26855dcaid: ab01a588-7dea-43f2-a699-0b3f128465d6
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2: id: c1579802-ddd4-4214-8a91-97b2066abe11
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 249
ht-degree: 0%

---

# 為何Experience Manager Guides會在特定時段後登出？

Experience Manager Guides會在已定義的閒置時間（閒置逾時）後結束使用者工作階段。 此自動登出功能是在Adobe Experience Manager中設定。 工作階段過期時，會顯示快顯通知，通知使用者工作階段已過期。 此警報會限制使用者對內容進行任何進一步的變更。

**工作階段逾時如何運作？**

Experience Manager Guides每30秒傳送一次背景要求`token.json`以驗證工作階段。 如果工作階段仍在作用中，則會傳回有效的Token。 如果工作階段因非使用中而過期，則會傳回空白權杖，並將工作階段視為非使用中。

**工作階段過期時會發生什麼事？**

偵測到非作用中工作階段時：

- 會出現快顯通知，通知您已登出。

  ![](images/sign-out-prompt.png)

- 警報會停用與應用程式的所有互動。

- 選取&#x200B;**確定**&#x200B;會重新整理瀏覽器，並將您重新導向登入頁面。
- 登入後，系統會將您重新導向至Experience Manager Guides最後開啟的頁面。

**後續步驟**

工作階段到期警示會限制您在非作用中工作階段期間變更應用程式，有助於防止資料遺失。 為避免意外遺失內容，建議您定期在編輯器中儲存作業，尤其是在長時間離開系統之前。
