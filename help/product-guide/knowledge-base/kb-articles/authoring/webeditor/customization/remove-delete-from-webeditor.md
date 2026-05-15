---
title: 針對特定使用者，從編輯器中的檔案內容功能表中移除「刪除」選項
description: 瞭解如何透過從特定使用者/群組的檔案快顯選單中移除「刪除」選項來自訂編輯器
exl-id: 31b4dd53-3938-42e1-bbc6-64806d668696
TQID: https://experienceleague.adobe.com/dzbMsXUoEibR5QxKB-Z-h4qGnQaX2NmIYLTtxVJHE-A
product_v2: id: fae5e35a-80c9-4b94-9352-1a060a6aab1did: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: ab01a588-7dea-43f2-a699-0b3f128465d6
subfeature_v2: id: ad602516-aca3-4247-9ae8-f393d958efa9
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87cid: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 241
ht-degree: 0%

---

# 移除Webeditor中檔案內容功能表的[刪除]選項

在本文中，我們將瞭解如何在AEM Guides Web Editor的檔案快顯選單中，為特定使用者或群組隱藏「刪除」選項。 如需檔案快顯功能表選項的其他自訂內容，請檢查Guides擴充功能框架。 在[這裡](https://github.com/adobe/guides-extension/tree/main)可找到更多詳細資料。

如以下程式碼片段所示，檔案快顯功能表具有「刪除」選項可供此特定使用者使用。

![含刪除的檔案內容功能表](../../../assets/authoring/file-contextmenu-Delete.png)

現在，讓我們看看如何隱藏此使用者的「刪除」選項。

## 實作步驟：

- 從AEM首頁瀏覽至「工具>安全性>許可權」。
- 從搜尋方塊中選擇群組或使用者。
- 從右上角按一下「新增ACE」。
- 選擇資料夾路徑。
- 包含許可權&quot;jcr:removeChildNodes&quot;和&quot;jcr:removeNode&quot;。
- 選擇「許可權型別」作為「拒絕」，然後按一下「新增」，如下所示。

![使用者許可權拒絕ACE](../../../assets/authoring/permission-ACE-Delete.png)

![許可權中的存取控制清單](../../../assets/authoring/delete-acl.png)

### 測試

- 以已新增ACE的使用者身分登入AEM。
- 開啟Web編輯器。
- 前往存放庫檢視，並選擇已新增ACE的資料夾。
- 開啟檔案內容功能表。
- 「刪除」選項不會出現在內容功能表中。

檔案快顯功能表現在看起來像這樣：

![不含Delete的File contextmenu](../../../assets/authoring/file-contextmenu-Delete-removed.png)

```
Please note that these steps would also remove 'move' and 'rename' options from the Web Editor as they are also tied to delete process at the backend.
```
