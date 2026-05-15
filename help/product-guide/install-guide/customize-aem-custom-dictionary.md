---
title: 自訂AEM的預設字典
description: 瞭解如何自訂AEM的預設字典
exl-id: 8bfd3ea7-0be8-4e7a-b389-5face043200b
feature: Web Editor Configuration
role: Admin
level: Experienced
TQID: https://experienceleague.adobe.com/q1L3-BdWTGmgtrqjOipnk-39Tw-50NT6R--khdTXhbI
product_v2: id: fae5e35a-80c9-4b94-9352-1a060a6aab1did: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
subfeature_v2: id: b0521e56-a0b2-40b6-bf47-ebc98751f9ba
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 172
ht-degree: 2%

---

# 自訂AEM的預設字典 {#id209SD8000WU}

網頁編輯器可設定為使用AEM的拼字檢查程式或瀏覽器的拼字檢查程式。 如果您選擇使用AEM的拼字檢查程式，您就可以彈性定義自訂字詞清單。 這些自訂字詞接著會新增至AEM的字典中，且這些字詞在網頁編輯器中不會標籤為\（不正確\）。

執行以下步驟來建立新增至AEM字典中的自訂單字清單：

1. 登入AEM並開啟CRXDE Lite模式。

1. 導覽至下列節點：

   /apps/fmdita/config

1. 建立名為user\_dictionary.txt的新檔案。

1. 開啟檔案並新增您要在自訂字典中定義的字詞清單。

   下列熒幕擷圖顯示新增至user\_dictionary.txt檔案中的自訂字詞清單：

   ![](assets/custom-words-list-dictionary.png){width="650"}

1. 儲存並關閉檔案。


作者需要重新啟動網頁編輯器工作階段，才能在AEM字典中更新自訂字詞清單。

**上層主題：**[&#x200B;自訂Web編輯器](conf-web-editor.md)
