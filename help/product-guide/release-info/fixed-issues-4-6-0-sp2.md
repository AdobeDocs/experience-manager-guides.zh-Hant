---
title: 發行說明 |已修正Adobe Experience Manager Guides 4.6.0 Service Pack 3版本中的問題
description: 瞭解Adobe Experience Manager Guides 4.6.0 Service Pack 3版的錯誤修正
role: Leader
exl-id: 8ff26c28-4a88-4eb2-b359-5b1b0138dd4b
TQID: https://experienceleague.adobe.com/bsiTHK--FPkvfF4bdYUnL-HbAMuhtBKj7wT2eCmd7hM
product_v2:
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: a3bd6397-2eb2-4908-a61c-226e26855dca
  - id: ab01a588-7dea-43f2-a699-0b3f128465d6
subfeature_v2:
  - id: ad602516-aca3-4247-9ae8-f393d958efa9
  - id: f89f75b0-cf2e-4e96-aec8-fe8c39cbd0ef
role_v2:
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
source-git-commit: cc73b81787a3c3dbe8390d93e558064327e59965
workflow-type: tm+mt
source-wordcount: 370
ht-degree: 4%

---

# 已修正4.6.0 Service Pack 3版本（2025年1月）中的問題


本文章說明4.6.0 Service Pack 3版本Adobe Experience Manager Guides中不同區域所修正的錯誤。

瞭解4.6.0 Service Pack 3版本[&#128279;](upgrade-instructions-4-6-0-sp2.md)的升級指示。

## 製作

- 從資料夾設定檔更新條件時，所有條件群組都會遺失，且條件會平面化。 (23526)
- 變更&#x200B;**內容屬性**&#x200B;面板中表格的標題列值不會套用更新的值。 (23213)
- 在版面配置檢視中使用&#x200B;**主題參照**&#x200B;元素對話方塊在DITA map中新增主題參照時，新增的參照會顯示為中斷連結。 (22859)
- 在作者檢視中使用&#x200B;**主題參考**&#x200B;元素對話方塊在DITA map中新增主題時，選取的主題會以選取的相反順序插入。 (22858)
- 從任何外部產品（例如，MS PowerPoint）複製影像並貼到參考線中時，即時上傳資產以用於檔案的功能會中斷。 (24983)
- 使用&#x200B;**搜尋和篩選**&#x200B;功能在存放庫中搜尋檔案時，無法選取多個檔案。 (25104)

## 發佈

- 當內容包含不斷行空格時，發佈至Salesforce會失敗。 (23664)
- 對於具有錯誤的主題（例如中斷的連結），Salesforce發佈將失敗，並且進度條會無限期顯示。 (22985)
- 對於連結中斷的地圖，Salesforce發佈會失敗，而進度列會無限期顯示。 (24963)
- 如果外部連結包含UUID，它會進行後續處理，並將外部連結轉換為UUID連結，從而破壞編輯器和發佈網站上的連結。 (22574)
- 即使連結的&#x200B;**範圍**&#x200B;設定為&#x200B;**外部**，`xref`也會轉換成相對連結。 (23059)
- 產生&#x200B;**區塊**&#x200B;屬性設為&#x200B;**to-content**&#x200B;之內容的原生PDF失敗。 (21772)
- 基準線的&#x200B;**編輯屬性**&#x200B;對話方塊不會顯示先前儲存的動態基準線條件。 (23964)


## 翻譯

- 對於非舊版翻譯（針對非UUID），將來源路徑中的主題移動到其他資料夾會導致目標地區設定中的參照失效。 (24152)
