---
title: 建立大量啟用地圖集合
description: 瞭解如何在AEM Guides中建立大量啟用地圖集合。
feature: Publishing, Bulk Activation
role: User
source-git-commit: 76c731c6a0e496b5b1237b9b9fb84adda8fa8a92
workflow-type: tm+mt
source-wordcount: '735'
ht-degree: 0%

---

# 建立大量啟用地圖集合 {#id214GG0E90EV}

若要建立大量啟動對映集合，請執行以下步驟：

1. 從工具清單中選取&#x200B;**指南**。

1. 選取頂端的Adobe Experience Manager連結，然後選擇&#x200B;**工具**。

1. 選取&#x200B;**大量Publish儀表板**&#x200B;圖磚。

   系統首次顯示空白的集合頁面。 如果您先前已建立大量啟動集合，則會顯示在此頁面上。

1. 按一下&#x200B;**建立**。

1. 輸入大量啟用地圖集合的標題，然後按一下[建立]。****

   成功訊息會在建立大量啟用地圖集合時顯示。

1. 在成功訊息上按一下&#x200B;**開啟**。

1. 選取&#x200B;**編輯**，然後選取&#x200B;**新增地圖**。

1. 尋找並新增您要新增至大量啟動對映集合的DITA map。

   依預設，所有與地圖關聯的預設集和區域設定都會自動新增。

1. 透過開啟或關閉滑動按鈕來選取所需的輸出。

   您可以跨可用地區設定選擇多個輸出預設集。

1. 按一下&#x200B;**「完成」**。

DITA map檔案會新增至您的大量啟動對映集合中。

![已建立大量啟動集合](images/bulk-activation-collection-created.png){width="800" align="left"}

## 地圖和預設集索引標籤

**地圖和預設集**&#x200B;索引標籤會顯示下列資料欄中的資訊：

- **對應**：顯示DITA map檔案的標題。
- **對應路徑**：顯示DITA map檔案的完整路徑。

- **UUID**：顯示與檔案相關聯的唯一識別碼。

- **語言**：顯示DITA map的語言代碼。
- **預設集**：顯示在地圖檔案上設定的輸出預設集標題。 也會根據輸出預設集的型別顯示圖示。

  >[!NOTE]
  >
  > 小型![](images/global-preset-icon.svg)圖示表示資料夾設定檔層級預設集。

- **Modified**：指出是否在上次發佈後更新DITA map。 根據此資訊，您可以決定是否要啟動此DITA map的輸出。
- **已產生**：顯示上次產生的輸出的日期和時間。
- **已發佈**：顯示上次發佈（或已啟動）輸出的日期和時間。 如果您選取連結，會顯示&#x200B;**啟用結果**&#x200B;頁面，其中包含記錄檔，其中包含啟用內容的根路徑相關資訊。

## [Audit History]標籤

**稽核歷史記錄**&#x200B;索引標籤在下列資料欄中顯示已啟動對應輸出的相關資訊：
- **對應**：顯示DITA map檔案的標題。
- **對應路徑**：顯示DITA map檔案的完整路徑。
- **UUID** ：顯示與檔案相關聯的唯一識別碼。
- **語言**：顯示DITA map的語言代碼。
- **預設集**：顯示在地圖檔案上設定的輸出預設集標題。 也會根據輸出預設集的型別顯示圖示。
- **狀態**：將啟動狀態顯示為成功或不成功。
- **目的地**：如果您在Experience Manager Guides as a Cloud Service上產生輸出，則可以以Publish或預覽檢視輸出的目的地。

  >[!NOTE]
  >
  > 小型![](images/global-preset-icon.svg)圖示表示資料夾設定檔層級預設集。

- **Modified**：指出是否在上次發行之後更新DITA map。 根據此資訊，您可以決定是否啟動此DITA map的輸出。
- **已發佈**：顯示上次發佈（或已啟動）輸出的日期和時間。 如果您選取連結，會顯示「啟用結果」頁面，其中包含記錄檔，內含啟用內容的根路徑相關資訊。
  ![已建立大量啟動集合稽核歷程記錄標籤](images/bulk-collection-audit-history.png){width="800" align="left"}

  *在&#x200B;**稽核歷史記錄**索引標籤中檢視已啟動地圖輸出的相關資訊。*


  >[!NOTE]
  >
  > **稽核歷史記錄**&#x200B;索引標籤中的輸出是根據&#x200B;**已發佈**&#x200B;資料行排序。



## 左側面板

左側面板上有以下篩選選項：

- **已修改**：您可以選取「是」或「否」。 如果您選取「是」，則只會顯示修改過的DITA map。 修改後的對應是自上次發佈後產生的對應。
- **預設集**：選取您要篩選掉地圖檔案的預設集。 此欄顯示地圖檔案上設定的輸出預設集標題。 例如，如果您選擇&#x200B;*AEM Site*&#x200B;預設集，則只會顯示設定了&#x200B;*AEM Site*&#x200B;輸出預設集的地圖。
- **語言**：您可以選取任何可用的語言代碼，並在[地圖和預設集]索引標籤中僅顯示選取的語言。

當您從&#x200B;**對應和預設集**&#x200B;標籤切換到&#x200B;**稽核歷史記錄**&#x200B;標籤時，篩選器會更新，反之亦然。

**父級主題： **[大量啟用已發佈的內容](conf-bulk-activation.md)