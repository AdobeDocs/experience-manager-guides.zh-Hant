---
title: 發行說明 |已修正Adobe Experience Manager Guides 4.3.1.5版本中的問題
description: 瞭解Adobe Experience Manager Guides 4.3.1.5版本中的錯誤修正
role: Leader
exl-id: 082dca28-15da-417c-b511-74eb5ac68078
TQID: https://experienceleague.adobe.com/ujQFyhAp5bIB1OJnmqvbHCaiDip7T2qsjlVAWevykK8
product_v2: id: fae5e35a-80c9-4b94-9352-1a060a6aab1did: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: a3bd6397-2eb2-4908-a61c-226e26855dcaid: ab01a588-7dea-43f2-a699-0b3f128465d6
role_v2: id: f8a45b24-4be7-4f1b-909b-60d06b483a20
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 130
ht-degree: 6%

---

# 已修正4.3.1.5版本中的問題


本文介紹Adobe Experience Manager Guides 4.3.1.5版本中不同方面修正的錯誤。



瞭解4.3.1.5版本](../release-info/upgrade-instructions-4-3-1-5.md)的[升級指示。


## 製作

- 在`<codeblock>`內的內嵌元素之間新增空格會導致產生的輸出中出現分行符號。 (15247)
- 從「插入元素」對話方塊新增元素時，會發生體驗問題。 (15108)

## 發佈

- 錯誤記錄檔顯示有關使用外部範圍發佈內容的不正確資訊。 (15242)
- 以`HTTP`開頭的DITA檔案的內部連結會被視為外部連結，並造成範圍錯誤。 (15155)
- DITA map的AEM網站重新產生失敗。 (14369)

## 管理

- **fmditaTopicrefs**&#x200B;屬性顯示相對路徑而非絕對路徑。 (15341)
