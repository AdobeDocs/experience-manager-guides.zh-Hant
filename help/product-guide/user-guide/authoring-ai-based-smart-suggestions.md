---
title: 創作內容的AI支援智慧型建議
description: 瞭解如何在網頁編輯器中檢視並利用AI支援的智慧型建議。
exl-id: 23c5285e-0d4f-484a-a062-fe1ba1608b8d
source-git-commit: 75425d82ee55485503ea6678030c5e919e50a691
workflow-type: tm+mt
source-wordcount: '789'
ht-degree: 0%

---

# 創作內容的AI支援智慧型建議

Experience Manager Guides提供&#x200B;**智慧建議**&#x200B;功能，可協助您建立一致且精確的內容。

當您編寫內容時，**智慧型建議**&#x200B;功能可以使用AI搜尋，並顯示語義上類似您內容的現有內容。 然後，您可以選擇想要包含在目前主題中作為參考的最佳相符內容。

這可協助您重複使用檔案存放庫中的現有內容，並建立一致的內容。 例如，您正在製作包含有關&#x200B;**Adobe Firefly**&#x200B;資訊的檔案，其中包括有關&#x200B;**Adobe**&#x200B;的段落。 在這種情況下，您可以快速檢視並新增其他主題(例如&#x200B;**Adobe Photoshop**)的內容參考，其中包含相同的段落。





當您在網頁編輯器中開啟主題時，**智慧型建議**&#x200B;面板會顯示在右側。

>[!NOTE]
>
> 您的管理員必須設定&#x200B;**智慧建議**&#x200B;功能。 如需詳細資訊，請檢視Cloud Service安裝與設定指南中的[設定AI支援的智慧型編寫建議](../cs-install-guide/conf-smart-suggestions.md)區段。

![智慧型建議面板](images/smart-suggestions-panel.png){width="300" align="left"}

*檢視&#x200B;**智慧建議**面板。*

執行以下步驟，檢視將適當內容參照新增至主題的智慧建議：

1. 選取&#x200B;**智慧建議** ![智慧建議圖示](images/smart-suggestions-icon.svg)以開啟面板。



   >[!NOTE]
   >
   > 在[全域或資料夾層級設定檔](../cs-install-guide/conf-folder-level.md#conf-ai-smart-suggestions)中，您的管理員需要定義要索引的檔案或資料夾，以取得智慧型建議、檢視建議所需輸入的最小字元數，以及可在清單中檢視的最大建議數。

1. 在主題中輸入內容以檢視相關建議。 確保內容的字元長度超過管理員在資料夾設定檔中設定的值，以便顯示內容建議。

1. 選取&#x200B;**目前標籤的建議** ![智慧建議目前標籤圖示](images/smart-suggestions-current-tag-icon.svg)，以檢視您放置滑鼠指標之目前標籤的編寫建議。  根據目前標籤中的內容，顯示從索引檔案檢視和新增內容參考的建議。

   鍵盤快速鍵： **Windows** (*Ctrl* + *K*)，**macOS** (*Command* + *K*)
1. 選取&#x200B;**完整檔案的建議** ![智慧型建議完整檔案圖示](images/smart-suggestions-complete-document-icon.svg)，以根據完整檔案中的內容檢視建議。  智慧型建議![智慧型建議圖示](images/smart-suggestions-complete-document-icon.svg)圖示會顯示在找到適當相符專案的內容旁。

   鍵盤快速鍵： **Windows** ( *Ctrl* + *Shift* + *K* )、**macOS** (*Command* + *Shift* + *K* )

   >[!NOTE]
   >
   > 您只能檢視目前檢視區的建議（畫面上顯示的內容）。 若要檢視檔案中任何其他內容的建議，請向上或向下捲動以在檢視區中顯示建議，然後選取![智慧型建議圖示](images/smart-suggestions-complete-document-icon.svg)圖示。

1. 選取您已新增至檔案的標籤附近的&#x200B;**智慧建議** ![智慧建議圖示](images/smart-suggestions-complete-document-icon.svg)圖示，以檢視智慧建議。
1. 您可以在&#x200B;**內容重複使用**&#x200B;建議方塊中檢視智慧型建議。  Experience Manager Guides會提供完全相符且具有相同含義的內容建議。 例如，您可以搜尋包含確切版本號碼的主題，例如「2023.03.12版發行版本」。 您也可以搜尋「Adobe總部位於加州聖荷西」，並尋找類似內容，例如「聖荷西擁有許多軟體公司的季度，如Adobe」。
1. 選取&#x200B;**內容資訊** ![內容資訊](images/smart-suggestions-content-info-icon.svg)以檢視詳細資料。
   ![內容資訊面板](images/smart-suggestions-content-information.png){width="300" align="left"}

   *檢視內容參考的詳細資訊。*

   1. 包含內容參照的主題標題會顯示為超連結。
   1. 包含內容參照的檔案路徑。
   1. 參照內容的參照型別。
   1. 參照主題的DITA檔案名稱會顯示為超連結。
1. 選取&#x200B;**建議的內容預覽** ![智慧建議預覽圖示](images/smart-suggestions-preview-icon.svg)，將目前的內容與建議的內容進行比較。 這可協助您比較差異，並判斷您是否想要新增建議內容的內容參照，使其一致或保留您目前的內容。

   ![建議的內容預覽](images/smart-suggestions-suggested-content-preview.png){width="800" align="left"}

   *預覽目前內容與建議內容之間的比較。*

1. 按一下&#x200B;**接受**，在&#x200B;**建議的內容預覽**&#x200B;對話方塊中新增建議的內容參考。
1. 您也可以在&#x200B;**內容重複使用**&#x200B;建議方塊中選取&#x200B;**接受**&#x200B;或&#x200B;**拒絕**，以取得適當的建議。


此智慧型功能不但方便使用，而且可大幅減少手動搜尋內容的耗時，讓您更專注於產生新內容。 它還有助於改善團隊合作，並幫助保持不同作者所建立內容的一致性。

>[!NOTE]
>
>智慧型建議不會保留目前工作階段以外的資料。 如需回應，智慧型建議僅依賴內部資料庫內所建立內容的索引。 未使用外部AI工具，確保您的資料保留在系統中。
