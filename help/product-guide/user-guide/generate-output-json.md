---
title: JSON
description: 瞭解如何從網頁編輯器和地圖儀表板建立JSON預設集。 在AEM Guides中設定JSON輸出預設集。
exl-id: 9eb426fc-ca0a-4932-8a55-fea731281a0a
feature: Publishing
role: User
source-git-commit: b82f1f3b42f85cce8420d3962c69cd3bafc5728d
workflow-type: tm+mt
source-wordcount: '733'
ht-degree: 0%

---

# JSON {#id231KK0180T4}

您可以從網頁編輯器建立JSON預設集：

在「存放庫」面板中，在「Map檢視」中開啟DITA map檔案，然後在「輸出」標籤中，選取+圖示以建立輸出預設集，然後從「新增預設集」對話方塊的型別下拉式清單中選取JSON。

在Web編輯器中，已在&#x200B;**一般**&#x200B;標籤下組織下列設定：

- 輸出路徑
- 索引檔案
- 套用條件使用\（如果條件為對映定義\）
- 使用基準線\（如果為地圖建立了基準線\）
- 下載暫存檔案
- 要在輸出中傳播的屬性
- Post產生工作流程

如需詳細資訊，請參閱[JSON組態](#id231KJA00REJ)。


**JSON組態**

下列選項適用於JSON預設集：

>[!NOTE]
>
> 您也可以在網頁編輯器中編輯JSON檔案。

| JSON選項 | 說明 |
| --- | --- |
| 輸出路徑 | AEM存放庫內儲存JSON輸出的路徑。 |
| 索引檔案 | 您可以為您為JSON輸出建立的索引檔案命名。 依預設，它會選取DITA map的檔案名稱並新增尾碼（如`map_filename_index.json`）。<br><br>您也可以在設定索引檔時使用變數。 如需有關使用變數的詳細資訊，請參閱[使用變數來設定目的地路徑、網站名稱或檔案名稱選項](generate-output-use-variables.md#id18BUG70K05Z)。 |
| 套用條件，使用 | 選取下列其中一個選項： <br><br>* **未套用任何專案**：如果您不想在發佈的輸出上套用任何條件，請選取此選項。<br>* **DITAVAL檔案**：選取DITAVAL檔案以產生個人化內容。 您可以使用瀏覽對話方塊或輸入檔案路徑來選取多個DITAVAL檔案。 使用檔案名稱附近的十字圖示可將其移除。 DITAVAL檔案會依指定的順序評估，因此第一個檔案中指定的條件優先於後續檔案中指定的相符條件。 您可以透過新增或刪除檔案來維持檔案順序。 如果DITAVAL檔案被移動到其他位置或被刪除，它不會自動從對映圖示板中刪除。 您必須更新位置，才能移動或刪除檔案。 您可以將滑鼠停留在檔案名稱上，以檢視儲存檔案的AEM存放庫中的路徑。 您只能選取DITAVAL檔案，如果您已選取任何其他檔案型別，則會顯示錯誤。<br>* **條件預設集**：從下拉式清單中選取條件預設集，以在發佈輸出時套用條件。 如果您在DITA map主控台的「條件預設集」標籤中新增條件，則會顯示選項。 若要進一步瞭解條件預設集，請參閱[使用條件預設集](generate-output-use-condition-presets.md#id1825FL004PN)。 |
| 使用基準線 | 如果您已經為選取的DITA map建立基準線，請選取此選項以指定要發佈的版本。<br><br>如需詳細資訊，請參閱[使用基準線](generate-output-use-baseline-for-publishing.md#id1825FI0J0PF)。 |
| 下載暫存檔案 | 選取此選項可下載DITA-OT產生的暫存檔案。 可以在輸出產生記錄中找到DITA-OT儲存暫存檔的位置。 如果您在透過DITA-OT產生輸出時發生錯誤，請選取此選項以保留暫存檔案。 然後，您可以使用這些檔案來疑難排解輸出產生錯誤。<br> <br>產生輸出後，請選取&#x200B;**下載暫存檔** ![下載暫存檔圖示](images/download-temp-files-icon.png)圖示來下載包含暫存檔的ZIP資料夾。<br><br> **注意**：如果您選取某些檔案屬性，然後下載暫存檔案，您也會在ZIP資料夾中取得&#x200B;*metadata.xml*&#x200B;檔案。 |
| 要在輸出中傳播的屬性 | 選取您要當作中繼資料處理的屬性。 這些屬性是從DITA map或bookmap檔案的「屬性」頁面設定的。 您從下拉式清單中選取的屬性會列在「屬性」欄位下方。<br><br>**附註**：您也可以定義自訂屬性，並使用DITA-OT發佈將中繼資料傳遞給輸出。 如需詳細資訊，請參閱[使用中繼資料](metadata-dita.md#id21BJ00QD0XA)。 |
| Post產生工作流程 | 選擇此選項時，會顯示新的「Post產生工作流程」下拉式清單，其中包含AEM中設定的所有工作流程。 您必須選取要在輸出產生工作流程完成後執行的工作流程。<br><br>**注意**：如需建立自訂輸出後產生工作流程的詳細資訊，請參閱「安裝與設定Adobe Experience Manager Guides」as a Cloud Service指南中的&#x200B;_自訂輸出後產生工作流程_。 |

**父級主題：**[&#x200B;瞭解輸出預設集](generate-output-understand-presets.md)
