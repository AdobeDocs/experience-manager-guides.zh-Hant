---
title: 自訂AEM的預設字典
description: 瞭解如何自訂AEM的預設字典
feature: Web Editor Configuration
role: Admin
level: Experienced
source-git-commit: 6f3f05419f4f5cdd45ab580cdee6fa869f20f01d
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 2%

---

# 自訂AEM的預設字典 {#id209SD8000WU}

網頁編輯器可設定為使用AEM的拼字檢查程式或瀏覽器的拼字檢查程式。 如果您選擇使用AEM的拼字檢查程式，您就可以彈性定義自訂字詞清單。 這些自訂字詞接著會新增至AEM的字典中，且這些字詞在網頁編輯器中不會標籤為\（不正確\）。

下列標籤提供建立自訂字詞清單的指示，這些清單會根據您的Experience Manager Guides設定新增到AEM的字典中： Cloud Service或內部部署。

>[!BEGINTABS]

>[!TAB Cloud Service]

1. 使用您要在自訂字典中定義的字詞清單來建立user\_dictionary.txt檔案。

   >[!NOTE]
   >
   > 每個自訂字詞都必須定義在新行上。

1. 將檔案儲存在Cloud Manager的Git存放庫中的以下位置：

   /apps/fmdita/config

1. 儲存檔案。

   提交變更並執行Cloud Manager \(CI/CD\)管道以部署設定變更。


作者需要重新啟動網頁編輯器工作階段，才能在AEM字典中更新自訂字詞清單。

>[!TAB 內部部署]

1. 登入AEM並開啟CRXDE Lite模式。

1. 導覽至下列節點：

   /apps/fmdita/config

1. 建立名為user\_dictionary.txt的新檔案。

1. 開啟檔案並新增您要在自訂字典中定義的字詞清單。

   下列熒幕擷圖顯示新增至user\_dictionary.txt檔案中的自訂字詞清單：

   ![](assets/custom-words-list-dictionary.png){width="650" align="left"}

1. 儲存並關閉檔案。


作者需要重新啟動網頁編輯器工作階段，才能在AEM字典中更新自訂字詞清單。

>[!ENDTABS]

**上層主題：**&#x200B;[&#x200B;自訂Web編輯器](customize-overview.md)
