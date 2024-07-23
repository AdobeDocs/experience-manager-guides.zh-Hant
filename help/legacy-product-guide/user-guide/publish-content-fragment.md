---
title: Publish內容片段的主題
description: Publish主題或AEM Guides中內容片段的主題元素。  瞭解如何檢視主題目前的內容片段並重新發佈。
feature: Publishing
role: User
source-git-commit: 76c731c6a0e496b5b1237b9b9fb84adda8fa8a92
workflow-type: tm+mt
source-wordcount: '925'
ht-degree: 0%

---

# Publish內容片段

內容片段是Adobe Experience Manager中的分散式內容片段。 它們是以內容模型為基礎的結構化內容。 內容片段是純內容，沒有設計或版面配置資訊。 可獨立於Adobe Experience Manager支援的管道之外獨立編寫和管理這些管道。 內容片段為模組化，其中內容會劃分為較小的元件。

Adobe Experience Manager Guides可讓您將主題或主題內的元素發佈到內容片段。 您可以在主題與內容片段模式之間建立JSON型對應。 使用此對應將主題或主題內的元素發佈到內容片段。 然後，您可以在任何Adobe Experience Manager網站中使用內容片段，或透過內容片段支援的API擷取詳細資訊。


若要建立內容片段，請執行以下步驟：

1. 在Adobe Experience Manager Assets中建立[內容片段模型](https://experienceleague.adobe.com/docs/experience-manager-65/assets/content-fragments/content-fragments-models.html?lang=zh-Hant)。
1. 建立一個資料夾，您想在其中儲存根據內容片段模式建立的內容片段。 例如，「stock-content-fragments」。
1. 編輯資料夾的屬性（例如「stock-content-fragments」）並新增資料夾的路徑，其中包含雲端設定中的內容片段模式。
例如，在雲端設定中新增`/conf/we-retail`。 此設定將所有內容片段模式與資料夾連線。\
   ![在資料夾屬性中新增雲端設定詳細資料](images/fragment-folder-cloud-configuration.png){width="650" align="left"}
   *在資料夾屬性中新增雲端設定，以將其與片段模型連線。*

1. 若要產生內容片段，請從主題&#x200B;**檔案屬性**&#x200B;的&#x200B;**輸出**&#x200B;區段中，選取&#x200B;**新輸出** ![新輸出圖示](./images/Add_icon.svg)。
1. 選取&#x200B;**內容片段**。\
   ![檔案屬性選項標籤](./images/file-properties-outputs-tab.png){width="300" align="left"}

   *從主題*&#x200B;的檔案屬性加入新的內容片段。

1. 在&#x200B;**產生內容片段**對話方塊中，填寫下列詳細資料：
   ![在Publish中新增片段模型和對應詳細資訊作為內容片段對話方塊](images/content-fragment-publish.png){width="500" align="left"}
   *新增路徑、模型和對應詳細資訊，將主題或其元素發佈為內容片段。 您可以覆寫現有的內容片段。*

   >[!NOTE]
   >
   >您也可以從&#x200B;**存放庫檢視**&#x200B;發佈內容片段。 選取您要發佈為內容片段的主題。 然後，從&#x200B;**選項**&#x200B;功能表選取&#x200B;**Publish As** > **內容片段**。

   * **路徑**：瀏覽並選取您要發佈內容片段的資料夾路徑。 如果您選取現有的內容片段，這會覆寫對應欄位的內容。
   * **Title**：輸入內容片段的標題。 依預設，標題會填入主題的標題。 您可以編輯它。 此標題用於產生內容片段的名稱。
   * **名稱**：輸入內容片段的名稱。 依預設，名稱會填入主題的標題，而空格會取代為「_」。 例如，*sample_content_fragment*。 您可以編輯它。  此名稱用於產生內容片段的URL。
   * **模式**：選取您要用來建立內容片段的內容片段模式。 模型會從已在雲端服務中設定的資料夾中選取。
   * **對應**：從下拉式清單中選取對應。 它會從&#x200B;*contentFragmentMapping.json*&#x200B;檔案中挑選對應。



     您的管理員可以在&#x200B;*contentFragmentMapping.json*&#x200B;檔案中新增對應。 進一步瞭解如何在安裝及設定指南中[建立主題與內容片段之間的對應](/help/product-guide/cs-install-guide/conf-content-fragment-mapping-cs.md)。

   * 您也可以選取不同的條件來發佈內容。  選取下列其中一個選項：


      * **無**：如果您不想在發佈的輸出上套用任何條件，請選取此選項。
      * **使用DITAVAL**：選取DITAVAL檔案以產生輸出，其中包含特定內容。 您可以使用瀏覽對話方塊或輸入檔案路徑來選取DITAVAL檔案。
      * **使用屬性**：您可以在DITA主題中定義條件屬性。 然後，選取條件屬性以發佈相關內容。
     >[!NOTE]
     > 
     >只有在主題中定義了條件屬性時，才會啟用條件。



   * 如果您的內容片段已經存在，而且您想要覆寫內容，請選取&#x200B;**覆寫現有內容**。 如果您未勾選核取方塊，而且您的內容片段已存在，Experience Manager Guides會顯示錯誤。
1. 按一下&#x200B;**產生**&#x200B;以發佈內容片段。

1. 您可以在&#x200B;**檔案屬性**&#x200B;的&#x200B;**輸出**&#x200B;區段下檢視主題的內容片段。

   ![檢視主題](images/outputs-options-menu.png){width="300" align="left"}的內容片段

   *檢視主題的內容片段並重新發佈。*


發佈內容片段後，您也可以在任何Adobe Experience Manager網站中使用這些片段。




## 內容片段的「選項」選單

您也可以從&#x200B;**選項**&#x200B;功能表為內容片段執行下列動作：

* **產生**：重新發佈內容片段，以使用DITA主題的最新內容加以更新。 當您重新產生輸出時，您無法變更內容片段的路徑、名稱、標題、模式和對應。 不過，您可以在再生輸出時選取不同的條件。

* **重複**：重複內容片段。 您可以變更路徑、名稱、標題、模型與對應。 當您複製內容片段時，也可以選取不同的條件。

* **移除**：從輸出清單移除內容片段。 確認提示隨即出現。 確認後，內容片段會從&#x200B;**輸出**&#x200B;清單中移除。

  >[!NOTE]
  >
  > 此動作不會從內容片段中刪除任何內容。

* **檢視**：檢視內容片段編輯器。 您也可以進行變更並儲存。


