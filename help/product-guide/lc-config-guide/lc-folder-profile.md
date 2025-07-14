---
title: 設定資料夾設定檔
description: 瞭解如何在Experience Manager Guides中使用學習與培訓內容時設定資料夾設定檔。
feature: Authoring
role: Admin
level: Experienced
source-git-commit: b114cbcc0f637a71a9d9b7458686a06070179983
workflow-type: tm+mt
source-wordcount: '1296'
ht-degree: 0%

---

# 設定資料夾設定檔

需要資料夾設定檔來分隔企業中不同部門或產品的組態。 針對學習和訓練內容，您可以建立並設定檔案夾層級的設定檔，以管理撰寫範本、輸出範本、輸出預設集和其他檔案夾層級的設定。

若要開始使用學習和訓練內容的資料夾設定檔設定，您需要：

1. [建立資料夾設定檔](../cs-install-guide/conf-folder-level.md#create-and-configure-a-folder-level-profile)。
2. **選取要設定的資料夾設定檔**：建立資料夾設定檔後，您必須在[使用者偏好設定](../user-guide/intro-home-page.md#user-preferences)頁面上選取資料夾設定檔，以確保作者和發佈者可以存取正確的範本。

   ![](assets/folder-profile.png){width="650" align="left"}

3. **設定資料夾設定檔設定**：對於學習與訓練內容，可以在資料夾層級設定下列設定：
   - [面板](#configure-panels)
   - [範本](#configure-templates)
   - [輸出預設集](#configure-output-presets)
   - [HTML編輯器](#html-editor-settings)
   - [發佈設定檔](#manage-publish-profiles)

若要存取這些設定，請切換到編輯器檢視，然後從&#x200B;**選項**&#x200B;功能表選取&#x200B;**設定**，如下所示：

![](assets/access-editor-settings.png)

## 設定面板

此設定會控制顯示在Experience Manager Guides中&#x200B;**編輯器**&#x200B;和&#x200B;**地圖主控台**&#x200B;的左右面板中的面板。 您可以切換按鈕，以顯示或隱藏所需的面板。

如需學習和訓練內容，請確定編輯器和地圖主控台僅啟用下列功能。

![](assets/panels-settings.png){width="350" align="left"}


### 編輯器

**左側面板**

- **集合**：可讓您整理並儲存常用的檔案，或快速存取共用的檔案。
- **存放庫**：可讓您檢視並存取所有地圖、主題、影像以及儲存在內容存放庫中的其他資產。
- **課程經理**：提供建立和管理課程的專屬工作區。
- **片段**：可讓您在學習課程的各種主題中建立和重複使用小型內容片段。
- **條件**：可讓您設定全域和資料夾層級的條件屬性。
- **變數**：可讓您建立和管理要在學習內容中使用的變數。
- **語言變數**：可讓您定義已發佈輸出或範本中靜態文字的當地語系化字串。
- **範本**：可讓您建立和管理供作者使用的範本。
- **輸出範本**：可讓您建立和管理輸出範本，以產生多種格式的輸出。
- **尋找和取代**：提供在地圖或存放庫內的資料夾中搜尋和取代檔案間文字的選項。 

**右側面板**

- **內容屬性**：包含編輯器中目前選取之元素的型別和屬性相關資訊。
- **檔案屬性**：可讓您檢視和管理所選檔案的屬性。
- **樣式**：顯示全域類別樣式選項以用於您的學習內容。
- **篩選器**：可讓您根據主題預覽模式中套用的條件來篩選內容。

### 地圖主控台

**左側面板**

- **預設集**：可讓您設定用於發佈學習課程的輸出預設集。
- **翻譯**：提供將內容翻譯成多種語言的選項。
- **報告**：可讓您產生並管理報告，讓有用的insight瞭解課程內容的整體健康狀況。
- **條件預設集**：提供為不同的對象、部門等設定條件式輸出預設集的選項。

**右側面板**

- **篩選器**：可讓您在處理報告和翻譯時使用篩選器。

## 設定範本

此設定可讓您管理編輯器[中](../user-guide/web-editor-left-panel.md)左側面板的製作和發佈範本。 您可以新增、移除或重新排序製作和輸出範本，然後作者和發佈者即可存取這些範本。

![](assets/templates-settings.png){width="350" align="left"}

「撰寫」範本分為四個類別：學習課程、學習內容、測驗和問題庫。 如果您的執行個體中設定了任何預先定義的範本，預設會顯示這些範本。

![](assets/templates-list.png){width="350" align="left"}

### 新增範本

執行以下步驟來新增範本：

1. 瀏覽至您要新增範本的範本類別，並選取&#x200B;**新增**。
2. 在選取路徑對話方塊中，選取所需的範本。
3. 選擇&#x200B;**選取**。

   ![](assets/add-templates.png){width="350" align="left"}

範本會新增至「設定」面板的個別類別中。

同樣地，您可以新增其他製作和輸出範本。 新增後，作者和發佈者可在各自的課程對話方塊中取得這些範本。 例如，管理員新增的學習課程範本可供作者建立新課程時使用。

![](assets/templates-added-course.png){width="350" align="left"}

### 使用新的撰寫和輸出範本

若要使用與&#x200B;**選取路徑**&#x200B;對話方塊中顯示的範本不同的範本，請建立自訂編寫或輸出範本。

**建立新的編寫範本**

若要使用不同的地圖或主題範本，請從編輯器的「範本」面板中建立新的編寫範本。 使用對應範本建立學習課程和學習內容、測驗或學習摘要的主題範本。

如需詳細資訊，請檢視[從編輯器建立自訂範本](../user-guide/create-maps-customized-templates.md)。

![](assets/authoring-templates-editor.png){width="350" align="left"}

**建立新的輸出範本**

執行以下步驟，為學習與訓練內容建立新的輸出範本：

1. 從編輯器的左側面板中，選取&#x200B;**更多** > **輸出範本**。

   隨即顯示「輸出範本」面板。

   ![](assets/output-templates-editor.png){width="350" height="" align="left"}
2. 在「輸出範本」面板中，選取(+)以建立新的輸出範本。

   ![](assets/create-new-output-template.png){width="350" align="left"}
3. 從下拉式選單中選取輸出範本。


   ![](assets/output-template-types.png){width="650" align="left"}
4. 根據所選的「輸出」範本型別，會顯示一個對話方塊，您可以在其中根據可用的範本建立新範本。

   ![](assets/new-scorm-template-dialog.png){width="350" align="left"}

5. 選取「**建立**」。

   已建立新的輸出範本。

6. 若要存取並新增發佈者的輸出範本，請瀏覽至&#x200B;**設定** > **範本** > **輸出範本**，然後選取&#x200B;**新增**。

   ![](assets/add-output-template-settings-panel.png){width="350" align="left"}

   輸出範本會顯示在「選取路徑」對話方塊中。
7. 選取範本並選擇&#x200B;**確認**。

   ![](assets/select-scorm-template-dialog.png){width="350" align="left"}

   選取的輸出範本現在會新增至「設定」面板。

   ![](assets/scorm-template-added.png){width="350" align="left"}

### 移除或重新排序範本

新增後，您可以從「設定」面板中移除或重新排序範本。

若要移除範本，請選取範本旁邊的&#x200B;**移除**&#x200B;圖示。

![](assets/remove-teamplates.png){width="350" align="left"}

您也可以定義類別中範本的顯示順序。 若要變更範本的顯示順序，請選取虛線並將範本拖曳到所需位置。

![](assets/reorder-templates.png){width="350" align="left"}


## 設定輸出預設集

「輸出預設集」標籤可讓您定義哪些輸出格式可用於發佈課程。 它包含兩個區段： **允許的輸出預設集型別**&#x200B;和&#x200B;**通用輸出預設集**。

![](assets/configure-course-output-presets.png){width="350" align="left"}

- **允許的輸出預設集型別**：此區段列出Experience Manager Guides執行個體支援的所有輸出預設集。 對於課程發佈，只有&#x200B;**SCORM**&#x200B;和&#x200B;**PDF**&#x200B;格式適用。 您可以選取一個或兩個選項。 產生課程輸出時，發佈者可使用選取的預設集。

  ![](assets/allowed-output-presets.png){width="350" align="left"}

- **常見輸出預設集**：此區段顯示Publishers經常建立並新增至特定資料夾設定檔的輸出預設集。 您也可以移除任何不再需要的預設集。

  ![](assets/common-output-presets.png){width="350" align="left"}

## HTML編輯器設定

此設定可讓您設定用於HTML式編寫的編輯器。 此設定中的主要組態選項如下：

![](assets/configure-html-editor-setting.png){width="350" align="left"}

- **隱藏內嵌樣式**：啟用此選項可防止作者將內嵌格式套用至課程內容。 啟用時，編輯器的右側面板中出現的所有內嵌樣式選項（例如「字型」、「邊框」、「版面」、「背景」和「欄」）對「作者」而言仍為隱藏狀態。 不過，作者仍可使用&#x200B;**樣式**&#x200B;面板中可用的全域類別型樣式選項。 這有助於維持與貴組織風格指引的一致性。
- **隱藏作者的Source檢視**：啟用此選項以限制對HTML原始碼的存取。 如果您想要簡化編輯體驗，或避免基礎程式碼意外變更，這個功能會很好用。

## 管理發佈設定檔

本節可讓您檢視、建立及管理用於發佈課程至SCORM Cloud的發佈設定檔。 每個設定檔會定義將學習課程發佈至特定SCORM雲端環境所需的連線設定和設定詳細資訊。

如果您需要發佈至不同的SCORM Cloud帳戶，可以建立多個設定檔，以確保靈活控制發佈程式。

提供伺服器詳細資訊以及相關SCORM雲端應用程式的使用者端ID和使用者端密碼，以設定SCORM雲端的發佈設定檔。

![](assets/configure-publish-profiles.png){width="350" align="left"}