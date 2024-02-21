---
title: 針對特定使用者，從編輯器中的檔案內容功能表中移除「刪除」選項
description: 瞭解如何透過從特定使用者/群組的檔案快顯選單中移除「刪除」選項來自訂編輯器
source-git-commit: aacc04e2fb6ca061825e5e219ad6e03bf711b3d0
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 0%

---


# 移除Webeditor中檔案內容功能表的[刪除]選項

在本文中，我們將瞭解如何在AEM Guides網頁編輯器中，針對特定使用者或群組從檔案快顯選單中隱藏「刪除」選項。 如需檔案快顯功能表選項的其他自訂內容，請檢查Guides擴充功能框架。 可以找到更多詳細資料 [此處](https://github.com/adobe/guides-extension/tree/main).

如以下程式碼片段所示，檔案快顯功能表具有「刪除」選項可供此特定使用者使用。

![含刪除功能的檔案內容功能表](../../../assets/authoring/file-contextmenu-Delete.png)

現在，讓我們看看如何隱藏此使用者的「刪除」選項。

## 實作步驟：

- 從AEM首頁瀏覽至「工具>安全性>許可權」。
- 從搜尋方塊中選擇群組或使用者。
- 從右上角按一下「新增ACE」。
- 選擇資料夾路徑。
- 包含許可權&quot;jcr：removeChildNodes&quot;和&quot;jcr：removeNode&quot;。
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

![檔案內容功能表（不含Delete）](../../../assets/authoring/file-contextmenu-Delete-removed.png)

```
Please note that these steps would also remove 'move' and 'rename' options from the Web Editor as they are also tied to delete process at the backend.
```
