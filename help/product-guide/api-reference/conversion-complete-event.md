---
title: 轉換程式事件處理常式
description: 了解轉換程式事件處理常式
exl-id: 8033935d-2113-4e39-ab74-b7431b89f948
feature: Conversion Process Event Handler
role: Developer
level: Experienced
source-git-commit: 83966cc9187b13dd3b5956821e0aa038b41db28e
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 3%

---

# 轉換程式事件處理常式 {#id175UB30E05Z}

AEM Guides會公開com/adobe/fmdita/conversion/complete事件，以用於完成檔案轉換程式後執行任何後處理操作。 只要將非DITA檔案移轉至DITA檔案格式，就會觸發此事件。 例如，如果您執行Word至DITA轉換或InDesign至DITA轉換程式，則會在轉換程式結束後呼叫此事件。

您需要建立AEM事件處理常式，以讀取此事件中可用的屬性，並進行進一步處理。

事件詳細資訊說明如下：

**事件名稱**：

```HTTP
com/adobe/fmdita/conversion/complete 
```

**引數**：

| 名稱 | 類型 | 說明 |
|----|----|-----------|
| `status` | 字串 | 已執行作業的傳回狀態。 可能的選項包括： -   成功：轉換程式已成功完成。 <br> -   已完成但有錯誤：轉換程式已完成，但有一些錯誤。 <br>-   失敗：轉換程式因為發生嚴重錯誤而失敗。 |
| `filePath` | 字串 | AEM存放庫中來源檔案\（待轉換\）的絕對路徑。 |
| `outputPath` | 字串 | 儲存轉換之DITA檔案的目的地位置的絕對路徑。 |
| `logPath` | 字串 | 將儲存轉換記錄之節點的絕對路徑。 |
