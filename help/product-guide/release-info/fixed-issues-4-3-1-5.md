---
title: 發行說明 | 已修正Adobe Experience Manager Guides 4.3.1.5版本中的問題
description: 瞭解Adobe Experience Manager Guides 4.3.1.5版中的錯誤修正
role: Leader
source-git-commit: 485f88e2e8724d1dc28deac13d677734fcc15c25
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 2%

---


# 已修正4.3.1.5版本中的問題


本文介紹4.3.1.5版Adobe Experience Manager Guides中不同區域所修復的錯誤。



瞭解 [4.3.1.5版的升級指示](../release-info/upgrade-instructions-4-3-1-5.md).


## 製作

- 在內嵌元素之間新增空格 `<codeblock>` 會在產生的輸出中造成分行符號。 (15247)
- 從「插入元素」對話方塊新增元素時，會發生體驗問題。 (15108)

## 發佈

- 錯誤記錄檔顯示有關使用外部範圍發佈內容的不正確資訊。 (15242)
- DITA檔案的內部連結，開頭為 `HTTP` 會被視為外部連結，並造成範圍錯誤。 (15155)
- DITA map的AEM網站重新產生失敗。 (14369)

## 管理

- **fmditaTopicrefs** 屬性會顯示相對路徑，而非絕對路徑。 (15341)

