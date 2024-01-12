---
title: 自訂AEM預設字典
description: 瞭解如何自訂AEM預設字典
exl-id: 8bfd3ea7-0be8-4e7a-b389-5face043200b
feature: Web Editor Configuration
role: Admin
level: Experienced
source-git-commit: 0513ecac38840a4cc649758bd1180edff1f8aed1
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 2%

---

# 自訂AEM預設字典 {#id209SD8000WU}

網頁編輯器可設定為使用AEM拼字檢查程式或瀏覽器的拼字檢查程式。 如果您選擇使用AEM拼字檢查程式，您就可以彈性定義自訂字詞清單。 這些自訂字詞接著會新增到AEM字典中，且這些字詞在網頁編輯器中不會標籤為\（不正確\）。

執行以下步驟來建立新增到AEM字典中的自訂單字清單：

1. 登入AEM並開啟CRXDE Lite模式。

1. 導覽至下列節點：

   /apps/fmdita/config

1. 建立名為user\_dictionary.txt的新檔案。

1. 開啟檔案並新增您要在自訂字典中定義的字詞清單。

   下列熒幕擷圖顯示新增至user\_dictionary.txt檔案中的自訂字詞清單：

   ![](assets/custom-words-list-dictionary.png){width="650" align="left"}

1. 儲存並關閉檔案。


作者需要重新啟動網頁編輯器工作階段，才能在AEM字典中更新自訂字詞清單。

**父級主題：**[&#x200B;自訂Web編輯器](conf-web-editor.md)
