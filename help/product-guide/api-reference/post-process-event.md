---
title: 後續處理事件處理常式
description: 瞭解後處理事件處理常式
exl-id: 3b105ff5-02d4-40e3-a713-206a7fcf18b2
feature: Post-Processing Event Handler
role: Developer
level: Experienced
source-git-commit: 83966cc9187b13dd3b5956821e0aa038b41db28e
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 5%

---

# 後續處理事件處理常式 {#id175UB30E05Z}

AEM Guides會公開用於執行任何後處理操作的com/adobe/fmdita/postprocess/complete事件。 只要對DITA檔案執行作業，就會觸發此事件。 對DITA檔案的下列操作會觸發此事件：

>[!NOTE]
>
> AEM 6.1中的刪除作業不會觸發此事件。

- 上傳
- 建立
- 修改
- 刪除

您需要建立AEM事件處理常式，以讀取此事件中可用的屬性，並進行進一步處理。

事件詳細資訊說明如下：

**事件名稱**：

```
com/adobe/fmdita/postprocess/complete 
```

**引數**：

| 名稱 | 類型 | 說明 |
|----|----|-----------|
| `path` | 字串 | 觸發此事件的檔案路徑。 通常，這是已對其執行操作的檔案。 |
| `status` | 字串 | 已執行作業的傳回狀態。 可能的選項包括： - <br>- SUCCESS：已成功完成後續處理作業。 <br> — 已完成，但發生錯誤：後處理作業已完成，但發生一些錯誤。 <br> — 失敗：因為發生嚴重錯誤，所以後續處理作業失敗。 |
| `message` | 字串 | 如果狀態為COMPLETED WITH ERRORS或FAILED，此引數包含有關錯誤或失敗原因的詳細資訊。 |
| `operation` | 字串 | 對檔案執行的後處理操作。 可能的選項包括：<br> — 新增<br> — 更新<br> — 刪除 |
