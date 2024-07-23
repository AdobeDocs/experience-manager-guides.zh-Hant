---
title: 從網頁編輯器建立輸出預設集
description: 從網頁編輯器建立輸出預設集。 瞭解如何在AEM Guides中編輯、重新命名、複製和刪除輸出預設集。
feature: Authoring, Features of Web Editor, Publishing
role: User
source-git-commit: 76c731c6a0e496b5b1237b9b9fb84adda8fa8a92
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# 從網頁編輯器建立輸出預設集 {#id218CL400JW3}

執行以下步驟來建立DITA map的輸出預設集：

1. 在Assets UI中，導覽至您要編輯的地圖檔案。

1. 若要取得對映檔案的獨佔鎖定，請選取對映檔案，然後按一下&#x200B;**簽出**。

1. 從地圖檔案的動作選單中選取&#x200B;**編輯主題**&#x200B;選項。

   會開啟對應檔案，以便在Web編輯器中編輯。

   >[!NOTE]
   >
   > 您可以使用進階地圖編輯器在地圖中新增或刪除任何主題。 如需詳細資訊，請參閱[使用進階地圖編輯器](map-editor-advanced-map-editor.md#)。

1. 在&#x200B;**輸出**&#x200B;標籤中，選取+圖示以建立DITA map的輸出預設集。

   ![](images/output-tab-preset_cs.png){width="350" align="left"}

1. 在[新增預設集]對話方塊中輸入預設集名稱，然後按一下[新增]。****

1. 輸入下列組態詳細資訊。

   1. 在&#x200B;**一般**&#x200B;索引標籤中選取必要的選項。 您可以選擇建立附帶或不附帶條件的輸出預設集。 您也可以使用DITVAL檔案。 AEM Guides也可讓您選取基準線，以發佈特定版本的DITA map。
   1. 在&#x200B;**AEM**&#x200B;索引標籤中輸入AEM網站詳細資料。 **網站**&#x200B;會顯示您的AEM存放庫中可用的AEM Sites清單。 **類別**、**區段範本**&#x200B;和&#x200B;**文章範本**&#x200B;是用來組織您輸出之外觀與感覺的結構元件。 這些範本已在AEM網站範本中預先定義。

      >[!NOTE]
      >
      > 重新整理每個下拉式清單，以便在下一個下拉式清單中取得進一步的分類。

   1. 從&#x200B;**文章**&#x200B;索引標籤，選取您要產生輸出的主題。
1. 選取頂端的&#x200B;**產生預設集**&#x200B;圖示以產生輸出。

   ![](images/add-preset-articles-tab_cs.png){width="800" align="left"}

1. 您將會看到輸出產生程式的狀態。 **主題**&#x200B;欄會列出正在產生輸出的主題，而&#x200B;**狀態**&#x200B;欄會顯示每個主題的發佈狀態。

   若要檢視輸出，請將滑鼠指標停留在主題上，然後按一下「檢視輸出」。

   ![](images/add-preset-output-generated_cs.png){width="800" align="left"}


>[!NOTE]
>
> 您也可以從「選項」選單中編輯、重新命名、複製或刪除現有的輸出預設集。

![](images/edit-preset_cs.png){width="550" align="left"}

**上層主題：**[&#x200B;網頁編輯器的文章式發佈](web-editor-article-publishing.md)
