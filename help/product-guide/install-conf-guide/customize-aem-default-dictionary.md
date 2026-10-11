---
title: 自訂AEM的預設字典
description: 瞭解如何自訂AEM的預設字典
feature: Web Editor Configuration
role: Admin
level: Experienced
exl-id: 51099b42-706f-42b4-993e-7d9577b5a4f0
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
    internal-label: Experience Manager Guides
feature_v2:
  - id: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
    internal-label: Configuration
subfeature_v2:
  - id: b0521e56-a0b2-40b6-bf47-ebc98751f9ba
    internal-label: Web Editor configuration
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 81a0e7f0736ba4970673dd87a888a4c60d3c1b4e
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 3%
---
# 自訂AEM的預設字典 {#id209SD8000WU}

編輯器可設定為使用AEM的拼字檢查程式或瀏覽器的拼字檢查程式。 如果您選擇使用AEM的拼字檢查程式，您就可以彈性定義自訂字詞清單。 這些自訂字詞接著會新增至AEM的字典中，且這些字詞在編輯器中不會標籤為\（不正確\）。

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


作者需要重新啟動編輯器工作階段，才能在AEM字典中更新自訂字詞清單。

>[!TAB 內部部署]

1. 登入AEM並開啟CRXDE Lite模式。

1. 導覽至下列節點：

   /apps/fmdita/config

1. 建立名為user\_dictionary.txt的新檔案。

1. 開啟檔案並新增您要在自訂字典中定義的字詞清單。

   下列熒幕擷圖顯示新增至user\_dictionary.txt檔案中的自訂字詞清單：

   ![](assets/custom-words-list-dictionary.png){width="650"}

1. 儲存並關閉檔案。


作者需要重新啟動編輯器工作階段，才能在AEM字典中更新自訂字詞清單。

>[!ENDTABS]

**父級主題：**[&#x200B;自訂編輯器](customize-overview.md)
