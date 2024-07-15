---
title: 發行說明 | 已修正Adobe Experience Manager Guides 4.3.1.5版本中的問題
description: 瞭解Adobe Experience Manager Guides 4.3.1.5版中的錯誤修正
role: Leader
exl-id: 082dca28-15da-417c-b511-74eb5ac68078
source-git-commit: e40ebf4122decc431d0abb2cdf1794ea704e5496
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 2%

---

# 已修正4.3.1.5版本中的問題


本文章說明4.3.1.5版Adobe Experience Manager Guides中不同區域所修正的錯誤。



瞭解4.3.1.5版](../release-info/upgrade-instructions-4-3-1-5.md)的[升級指示。


## 製作

- 在`<codeblock>`內的內嵌元素之間新增空格會導致產生的輸出中出現分行符號。 (15247)
- 從「插入元素」對話方塊新增元素時，會發生體驗問題。 (15108)

## 發佈

- 錯誤記錄檔顯示有關使用外部範圍發佈內容的不正確資訊。 (15242)
- 以`HTTP`開頭的DITA檔案的內部連結會被視為外部連結，並造成範圍錯誤。 (15155)
- DITA map的AEM網站重新產生失敗。 (14369)

## 管理

- **fmditaTopicrefs**&#x200B;屬性顯示相對路徑而非絕對路徑。 (15341)
