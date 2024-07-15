---
title: 自訂AEM預設字典
description: 瞭解如何自訂AEM預設字典
exl-id: ecffcd14-6728-4938-a209-5c4b12af6fbb
feature: Web Editor Configuration
role: Admin
level: Experienced
source-git-commit: 0513ecac38840a4cc649758bd1180edff1f8aed1
workflow-type: tm+mt
source-wordcount: '175'
ht-degree: 1%

---

# 自訂AEM預設字典 {#id209SD8000WU}

網頁編輯器可設定為使用AEM的拼字檢查程式或瀏覽器的拼字檢查程式。 如果您選擇使用AEM的拼字檢查程式，您就可以彈性定義自訂字詞清單。 這些自訂字詞接著會新增至AEM的字典中，且這些字詞在網頁編輯器中不會標籤為\（不正確\）。

執行以下步驟來建立新增至AEM字典中的自訂單字清單：

1. 使用您要在自訂字典中定義的字詞清單來建立user\_dictionary.txt檔案。

   >[!NOTE]
   >
   > 每個自訂字詞都必須定義在新行上。

1. 將檔案儲存在Cloud Manager的Git存放庫中的以下位置：

   /apps/fmdita/config

1. 儲存檔案。

   提交變更並執行Cloud Manager \(CI/CD\)管道以部署設定變更。


作者需要重新啟動網頁編輯器工作階段，才能在AEM字典中更新自訂字詞清單。

**上層主題：**[&#x200B;自訂Web編輯器](conf-web-editor.md)
