---
title: ePub預設集
description: 瞭解如何從地圖控制面板建立EPUB預設集。 在AEM Guides中設定EPUB輸出預設集。
feature: Publishing
role: User
hide: true
exl-id: 1d914a5f-df1f-45eb-86ac-72485fdf07fe
source-git-commit: 1426cdaecdd358f06e76908b09330e65997e8452
workflow-type: tm+mt
source-wordcount: '810'
ht-degree: 1%

---

# ePub {#id205BED020YT}

您可以從地圖控制面板建立EPUB預設集。

>[!NOTE]
>
> 您可以選擇使用DITA-OT或FMPS來產生HTML5的方法\（如果您的系統管理員已設定\）。

若要開啟EPUB的輸出預設集，請按一下DITA map檔案、按一下輸出預設集，然後按一下EPUB選項。 下列選項適用於EPUB輸出：

| ePub選項 | 描述 |
| --- | --- |
| 輸出類型 | 您要產生的輸出型別。 若要產生EPUB輸出，請選擇EPUB選項。 |
| 設定名稱 | 為您正在建立的EPUB輸出設定提供描述性名稱。 例如，您可以指定&#x200B;_內部客戶輸出_&#x200B;或&#x200B;_一般使用者輸出_。 |
| DITA-OT命令列引數 | 指定在產生輸出時要DITA-OT處理的其他引數。 如需DITA-OT所支援之命令列引數的詳細資訊，請參閱[DITA-OT檔案](https://www.dita-ot.org/)。 |
| 產生EPUB，使用 | 選取DITA-OT以產生EPUB輸出。 |
| 套用條件，使用 | 選取下列其中一個選項： <br><br>* **未套用任何專案**：如果您不想在發佈的輸出上套用任何條件，請選取此選項。<br>* **DITAVal檔案**：選取DITAVal檔案以產生個人化內容。 您可以使用瀏覽對話方塊或輸入檔案路徑來選取多個DITAVal檔案。 使用檔案名稱附近的十字圖示可將其移除。 DITAVal檔案會依指定的順序計算，因此第一個檔案中指定的條件優先於後續檔案中指定的相符條件。 您可以透過新增或刪除檔案來維持檔案順序。 如果DITAVal檔案被移動到其他位置或被刪除，它不會自動從對映圖示板中刪除。 您必須更新位置，才能移動或刪除檔案。 您可以將滑鼠停留在檔案名稱上，以檢視儲存該檔案的AEM存放庫中的路徑。 您只能選取DITAVal檔案，如果您已選取任何其他檔案型別，則會顯示錯誤。 FrameMaker Publishing Server不支援多個DITAVAL檔案。<br>* **條件預設集**：從下拉式清單中選取條件預設集，以在發佈輸出時套用條件。 如果您在DITA map主控台的「條件預設集」標籤中新增條件，則會顯示選項。 若要進一步瞭解條件預設集，請參閱[使用條件預設集](generate-output-use-condition-presets.md#id1825FL004PN)。 |
| 目的地路徑 | AEM存放庫內儲存EPUB輸出的路徑。 |
| 檔案名稱 | 指定您要用來儲存EPUB輸出的檔案名稱。<br><br>**注意**：如果您未提供檔案名稱，則會使用DITA map的標題來產生最終的EPUB輸出檔案名稱。 如果地圖沒有標題，則會使用DITA map的檔案名稱來命名最終EPUB輸出。 系統會使用系統中設定的規則來清除檔案名稱，以處理任何無效字元。 |
| 轉換名稱 | 指定您要產生的輸出型別。 如果您想要使用自己的自訂外掛程式產生輸出（已整合在DITA-OT外掛程式中），則需要此專案。 例如，如果您要產生XHTML輸出，請指定`xhtml`。 如需DITA-OT中可用的轉換清單，請參閱OASIS DITA-OT使用手冊中的[DITA-OT轉換（輸出格式）](http://www.dita-ot.org/2.3/user-guide/AvailableTransforms.md)。 |
| 清除DITA-OT暫存檔 | 選取此選項可清除DITA-OT產生的暫存檔案。 可以在輸出產生記錄中找到DITA-OT儲存暫存檔的位置。<br><br>如果您在透過DITA-OT產生輸出時發生錯誤，可以取消選取此選項以保留暫存檔案。 然後，您可以使用這些檔案來疑難排解輸出產生錯誤。 |
| 執行後期產生工作流程 | 選擇此選項時，會顯示新的「產生後工作流程」下拉式清單，其中包含AEM中設定的所有工作流程。 您必須選取要在輸出產生工作流程完成後執行的工作流程。<br><br>**注意**：如需建立自訂輸出後產生工作流程的詳細資訊，請參閱安裝和設定Adobe Experience Manager Guides as a Cloud Service中的&#x200B;_自訂輸出後產生工作流程_。 |
| 使用基準線 | 如果您已經為選取的DITA map建立基準線，請選取此選項以指定要發佈的版本。<br><br>如需詳細資訊，請參閱[使用基準線](generate-output-use-baseline-for-publishing.md#id1825FI0J0PF)。 |
| 屬性 | 選取您要當作中繼資料處理的屬性。 這些屬性是從DITA map或bookmap檔案的「屬性」頁面設定的。 您從下拉式清單中選取的屬性會列在「屬性」欄位下方，並從下拉式清單中移除。 設定後，這些屬性也會複製到對映中的主題中。<br><br>**附註**：您也可以使用DITA-OT發佈將中繼資料傳遞給輸出。 如需詳細資訊，請參閱[使用DITA-OT](pass-metadata-dita-ot.md#id21BJ00QD0XA)將中繼資料傳遞給輸出。 |

**父級主題：**&#x200B;[&#x200B;瞭解輸出預設集](generate-output-understand-presets.md)
