---
title: 發佈主題至內容片段
description: 在AEM Guides中將主題或主題內的元素發佈到內容片段。  瞭解如何檢視主題目前的內容片段並重新發佈。
exl-id: b1769e48-d721-4e93-b10f-04b385272be7
feature: Publishing
role: User
source-git-commit: 7c7e3dcddf733793a5d6db50205ba60d24702451
workflow-type: tm+mt
source-wordcount: '925'
ht-degree: 0%

---

# 發佈內容片段

內容片段是Adobe Experience Manager中的分散式內容片段。 它們是以內容模型為基礎的結構化內容。 內容片段是純內容，沒有設計或版面配置資訊。 可獨立於Adobe Experience Manager支援的管道之外獨立編寫和管理這些管道。 內容片段為模組化，其中內容會劃分為較小的元件。

Adobe Experience Manager Guides可讓您將主題或主題內的元素發佈到內容片段。 您可以在主題與內容片段模式之間建立JSON型對應。 使用此對應將主題或主題內的元素發佈到內容片段。 然後，您可以在任何Adobe Experience Manager網站中使用內容片段，或透過內容片段支援的API擷取詳細資訊。


若要建立內容片段，請執行以下步驟：

1. 建立 [內容片段模型](https://experienceleague.adobe.com/docs/experience-manager-65/assets/content-fragments/content-fragments-models.html?lang=zh-Hant) 在Adobe Experience Manager Assets中。
1. 建立一個資料夾，您想在其中儲存根據內容片段模式建立的內容片段。 例如，「stock-content-fragments」。
1. 編輯資料夾的屬性（例如「stock-content-fragments」）並新增資料夾的路徑，其中包含雲端設定中的內容片段模式。
例如，新增 `/conf/we-retail` 在雲端設定中。 此設定將所有內容片段模式與資料夾連線。\
   ![在資料夾屬性中新增雲端設定詳細資料](images/fragment-folder-cloud-configuration.png){width="650" align="left"}
   *在資料夾屬性中新增雲端設定，以將其與片段模型連線。*

1. 若要產生內容片段，請選取「 」 **新輸出** ![新增輸出圖示](./images/Add_icon.svg) 從 **輸出** 中的區段 **檔案屬性** 主題的。
1. 選取 **內容片段**.\
   ![檔案屬性選項標籤](./images/file-properties-outputs-tab.png){width="300" align="left"}

   *從主題的檔案屬性新增內容片段*.

1. 在 **產生內容片段** 對話方塊中，填入下列詳細資訊：
   ![在「發佈為內容片段」對話方塊中新增片段模型和對應詳細資訊](images/content-fragment-publish.png){width="500" align="left"}
   *新增路徑、模型和對應詳細資訊，將主題或其元素發佈為內容片段。 您可以覆寫現有的內容片段。*

   >[!NOTE]
   >
   >您也可以從以下位置發佈內容片段： **存放庫檢視**. 選取您要發佈為內容片段的主題。 然後，從 **選項** 功能表，選取 **發佈為** > **內容片段**.

   * **路徑**：瀏覽並選取您要發佈內容片段的資料夾路徑。 如果您選取現有的內容片段，這會覆寫對應欄位的內容。
   * **標題**：輸入內容片段的標題。 依預設，標題會填入主題的標題。 您可以編輯它。 此標題用於產生內容片段的名稱。
   * **名稱**：輸入內容片段的名稱。 依預設，名稱會填入主題的標題，而空格會取代為「_」。 例如， *sample_content_fragment*. 您可以編輯它。  此名稱用於產生內容片段的URL。
   * **模型**：選取您要用來建立內容片段的內容片段模式。 模型會從已在雲端服務中設定的資料夾中選取。
   * **對應**：從下拉式清單中選取對應。 它會從 *contentFragmentMapping.json* 檔案。



     您的管理員可以在以下位置新增對應： *contentFragmentMapping.json* 檔案。 進一步瞭解如何 [建立主題與內容片段之間的對應](../cs-install-guide/conf-content-fragment-mapping-cs.md) 安裝及設定指南中的。

   * 您也可以選取不同的條件來發佈內容。  選取下列其中一個選項：


      * **無**：如果您不想對發佈的輸出套用任何條件，請選取此選項。
      * **使用DITAVAL**：選取要產生輸出（包括特定內容）的DITAVAL檔案。 您可以使用瀏覽對話方塊或輸入檔案路徑來選取DITAVAL檔案。
      * **使用屬性**：您可以在DITA主題中定義條件屬性。 然後，選取條件屬性以發佈相關內容。
     >[!NOTE]
     > 
     >只有在主題中定義了條件屬性時，才會啟用條件。



   * 選取 **覆寫現有內容** 如果您的內容片段已經存在，而且您想要覆寫它。 如果您未勾選核取方塊，而且您的Experience Manager片段已存在，內容指南會顯示錯誤。
1. 按一下 **產生** 以發佈內容片段。

1. 您可以檢視底下主題的內容片段 **輸出** 中的區段 **檔案屬性**.

   ![檢視主題的內容片段](images/outputs-options-menu.png){width="300" align="left"}

   *檢視主題目前的內容片段並重新發佈。*


發佈內容片段後，您也可以在任何Adobe Experience Manager網站中使用這些片段。




## 內容片段的「選項」選單

您也可以從以下對內容片段執行以下操作 **選項** 功能表：

* **產生**：重新發佈內容片段，以DITA主題的最新內容加以更新。 當您重新產生輸出時，您無法變更內容片段的路徑、名稱、標題、模式和對應。 不過，您可以在再生輸出時選取不同的條件。

* **複製**：複製內容片段。 您可以變更路徑、名稱、標題、模型與對應。 當您複製內容片段時，也可以選取不同的條件。

* **移除**：從輸出清單中移除內容片段。 確認提示隨即出現。 在您確認後，內容片段會從 **輸出** 清單。

  >[!NOTE]
  >
  > 此動作不會從內容片段中刪除任何內容。

* **檢視**：檢視內容片段編輯器。 您也可以進行變更並儲存。


