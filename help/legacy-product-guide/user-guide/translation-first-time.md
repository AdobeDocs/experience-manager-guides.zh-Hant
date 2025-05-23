---
title: 內容翻譯的最佳實務
description: 瞭解AEM Guides內容翻譯的最佳實務。 瞭解如何設定翻譯服務、建立新翻譯專案及啟動翻譯工作。
feature: Translation
role: User
hide: true
exl-id: 09e813fd-ec22-4d2e-9ee7-098d562ad44f
source-git-commit: ea597cd14469f21e197c700542b9be7c373aef14
workflow-type: tm+mt
source-wordcount: '1295'
ht-degree: 1%

---

# 內容翻譯的最佳實務 {#id1678G0S702F}

翻譯內容時請考慮以下幾點：

- 資料夾和檔案名稱必須符合檔案命名標準，例如 — 不應有空格、單引號、大括弧、等號、特殊或非ASCII字元。

- 如果您翻譯不同語言的內容，則必須建立與每種語言對應的資料夾。 每個語言資料夾都會包含對應於該語言的內容。 例如，您可以使用語言指示項建立資料夾，例如`de`代表德文，`fr`代表法文等等。 或者，您可以使用語言和區域指示項(例如`fr-FR`代表法文（如法國所用）或`fr-CA`代表法文（如加拿大所用）來建立資料夾。
- 目標語言也應該根據執行個體上的目標語言資料夾選取實際地區設定。
- 雲端設定應與來源資料夾的雲端設定相同，且一個資料夾中應只有一個雲端設定。 如果要使用多個翻譯聯結器，您可以在/conf下建立多個資料夾。
- 資料夾中的檔案不應超過1000個。
- 確保負責啟動翻譯流程的使用者擁有來源和目標語言資料夾的讀取、修改、建立及刪除許可權。
- 由於翻譯內容需要建立翻譯專案，因此使用者必須擁有在AEM中建立專案的存取權。
- 如果要將條件預設集與地圖搭配使用，您必須在啟動翻譯程式之前建立它們。 由於「條件預設集」也隨附在翻譯版本的地圖中，因此在啟動翻譯程式之前建立預設集可確保它們在翻譯版本中可用。
- 內容翻譯程式必須從DITA map主控台(而非AEM Assets UI)啟動。
- 如果您透過人工翻譯來翻譯內容，則不得使用元件式DITA翻譯工作流程。 不過，此選項必須用於機器翻譯。
- 全球使用的內容與媒體若不需要本地化，應避免使用語言副本。
- 所有必須本地化的通用內容都應儲存在語言資料夾下的通用資料夾中。

下圖顯示當您全域使用內容和三個語言副本時，AEM中的資料夾結構範例。

![](images/aem-directory_structure.png){width="800" align="left"}

## 設定翻譯服務

執行以下步驟，設定要使用的人工或機器翻譯服務：

1. 在Assets UI中，選取來源語言資料夾。

1. 開啟資料夾屬性，然後前往&#x200B;**雲端服務**&#x200B;標籤。

1. 在&#x200B;**雲端服務**&#x200B;索引標籤中，設定您要使用的翻譯服務。

   您可以設定機器翻譯或人工翻譯。

   確保一個資料夾中只有一個轉譯聯結器的設定。 如果有多個翻譯聯結器，可在/conf下建立多個資料夾。 在開始翻譯程式之前，來源語言資料夾必須選取雲端設定。

   >[!NOTE]
   >
   > 如需有關與協力廠商翻譯服務整合的詳細資訊，請參閱AEM檔案中的[設定翻譯整合架構](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/administering/reusing-content/translation/integration-framework.html?lang=zh-Hant)。

1. 按一下&#x200B;**儲存並關閉**&#x200B;以儲存更新的資料夾屬性。


>[!TIP]
>
> 如需有關翻譯內容的最佳實務，請參閱「最佳實務」指南中的&#x200B;*翻譯*&#x200B;區段。

## 建立新的翻譯專案

執行以下步驟來建立翻譯專案：

>[!NOTE]
>
> 在執行此程式中的步驟之前，請確定您已建立必要的語言根目錄和目標資料夾，如[內容翻譯的最佳實務](#id1678G0S702F)中所述。

1. 在Assets UI中，按一下DITA map檔案。

1. 按一下&#x200B;**翻譯**&#x200B;索引標籤。

1. 從&#x200B;**目標語言**&#x200B;清單中，選取您要翻譯專案的地區設定，然後按一下&#x200B;**完成**。

   主題和相關資產的摘要和詳細資訊隨即顯示。

   >[!IMPORTANT]
   >
   > **目標語言**&#x200B;只顯示其語言資料夾是與來源語言平行建立的語言。 在任何其他層級建立的語言資料夾（例如從來源語言資料夾往下一個層級）也不會顯示。 請確定您建立的所有目標語言資料夾都與來源語言資料夾處於同一層級。

1. 選取您要傳送以進行翻譯的主題。

   您也可以使用下列主題篩選選項：

   >[!NOTE]
   >
   > 套用必要的篩選器後，按一下「篩選器」面板中的&#x200B;**完成**&#x200B;以根據您的選取專案篩選主題。

   - **翻譯狀態**：選擇根據主題的翻譯狀態來篩選主題。 可用的選項包括：不同步、缺少副本、進行中及同步。
   - **搜尋**：輸入一或多個要在主題標題中搜尋的字詞。
   - **Source型別**：選擇根據其檔案型別篩選主題。 可用的選項有：全部、DITA、DITA Map、資源。
   - **Source版本在**&#x200B;之後修改：選擇根據主題的修改日期和時間篩選主題。 在指定日期和時間之後修改的所有主題都會顯示在清單中。
   - **基準線**：按一下「使用基準線」，然後選擇在地圖上建立的基準線。 所有屬於所選「基準線」一部分的檔案都會顯示在「轉譯」頁面中。 您可以從基準線中選擇所需的檔案，然後繼續進行翻譯過程。 翻譯內容後，即可匯出翻譯的「基準線」。 如需匯出已翻譯基準線的詳細資訊，請參閱[匯出已翻譯基準線](generate-output-use-baseline-for-publishing.md#id196SE600GHS)。
1. 按一下篩選器面板底部的&#x200B;**建立/更新語言副本**。

1. 從&#x200B;**專案**&#x200B;清單中，選取&#x200B;**建立新的翻譯專案**。

   >[!NOTE]
   >
   > 如果您已經有翻譯專案，您可以新增主題至該專案。 從&#x200B;**專案**&#x200B;清單中選取&#x200B;**新增至現有翻譯專案**&#x200B;選項，並從&#x200B;**現有翻譯專案**&#x200B;清單中選擇專案。

1. 在「專 **案標題** 」欄位中，輸入專案標題。

1. 選取&#x200B;**包含DITA對應**&#x200B;選項，以傳送對應以供翻譯。
1. 按一下&#x200B;**開始**&#x200B;以建立新的翻譯專案。

   新翻譯專案會以選取的主題版本建立。 此時，會顯示快顯訊息，確認已建立翻譯專案。 一旦所有目標語言副本在翻譯專案中可用，您會在收件匣中收到通知。 一旦翻譯專案中提供了目標語言副本區域，您就可以開始翻譯工作。

   ![](images/status-translation-uuid.png){width="800" align="left"}


「翻譯」標籤包含下列區段：

- **摘要**：顯示參考的主題和原始語言數目及其代碼。
- **詳細資料**：顯示主題標題、主題型別、主題的語言代碼、來源語言、來源主題的版本、新增至主題的標籤，以及翻譯狀態。




## 開始翻譯工作 {#id225IK030OE8}

執行以下步驟以開始翻譯工作：

1. 在&#x200B;**專案**&#x200B;主控台中，導覽至您為本地化所建立的專案資料夾。

1. 按一下本地化專案，開啟詳細資訊頁面。

1. 按一下&#x200B;**翻譯工作**&#x200B;圖磚上的箭頭，然後從清單中選取&#x200B;**開始**&#x200B;以開始翻譯工作流程。

   >[!NOTE]
   >
   > 如果您使用人工翻譯服務，則需要匯出內容以供翻譯。 取得翻譯內容後，您需要將其匯入回翻譯專案。

1. 若要檢視翻譯工作的狀態，請按一下&#x200B;**翻譯工作**&#x200B;圖磚底部的省略符號。


翻譯完成後，翻譯工作的狀態會變更為&#x200B;*準備好檢閱*。 若要完成翻譯程式，您必須在「專案」主控台的「翻譯工作」方塊中，接受翻譯的復本和資產中繼資料。

>[!NOTE]
>
> 如果您拒絕翻譯工作中一個或多個主題的翻譯，則所有已拒絕主題的&#x200B;**進行中**&#x200B;翻譯狀態將恢復為原始狀態。 參照主題的狀態會根據最新翻譯狀態檢查並回覆。 此外，在目標專案中建立的翻譯檔案不會被刪除，即使它們被拒絕翻譯。

**父級主題：**&#x200B;[&#x200B;翻譯內容](translation.md)
