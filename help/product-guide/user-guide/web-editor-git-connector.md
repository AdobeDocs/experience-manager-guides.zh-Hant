---
title: Experience Manager Guides中的Git Connector概觀
description: 瞭解Experience Manager Guides中的Git Connector有何作用、其主要功能，以及內容如何從Git存放庫移至AEM Guides工作流程。
feature: Authoring, Features of Web Editor
role: User
TQID: https://experienceleague.adobe.com/DDAXW8cUFjvHUeJIbtL6FaHYSU7NW5fkzTai-7n90ms
product_v2: id: fae5e35a-80c9-4b94-9352-1a060a6aab1did: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: ab01a588-7dea-43f2-a699-0b3f128465d6id: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
subfeature_v2: id: ad602516-aca3-4247-9ae8-f393d958efa9id: d4f22c6d-7923-41e5-9da3-527ff8df4bc8id: f89f75b0-cf2e-4e96-aec8-fe8c39cbd0ef
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2: id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
source-git-commit: eb30be6342a50ba52e8afd8b4a31148b3ad9c340
workflow-type: tm+mt
source-wordcount: 1352
ht-degree: 0%

---

# 使用Git聯結器匯入內容

>[!NOTE]
>
> 此功能預設為停用。 若要在您的環境中啟用它，請聯絡您的客戶成功團隊。

Git Connector可讓您[將內容從連線的Git存放庫](#import-content-from-the-connected-git-repository)匯入Experience Manager Guides。 匯入內容後，您可以使用Experience Manager Guides的編寫、審閱、翻譯和發佈功能來開發和提供檔案。

當來源存放庫中的內容變更時，您可以重新擷取更新、審查衝突，並與Experience Manager Guides同步最新變更。

## 主要功能

Git聯結器可讓作者將內容直接從Git存放庫提取到Experience Manager Guides，無需手動傳輸檔案。 設定之後，作者就可以存取下列功能。

**內容擷取**

- 將任何Git存放庫（公用或私用）的檔案同步到Experience Manager Guides中。
- 依來源資料夾路徑篩選，擷取單一子目錄而非整個存放庫。
- 使用`gitignore-aware`規則引擎自動略過`.gitignore`模式或自訂規則排除的檔案。
- 重新同步時保留GUID，以便在更新後保持現有DITA互動參照不變。

**增量（差異）同步**

- 追蹤上次同步的認可，並擷取後續同步時新增、修改或刪除的檔案，而非重新匯入整個存放庫。
- 產生差異報告，列出匯入前每個變更的檔案及其變更型別。
- 不論存放庫大小為何，都能維持一致的擷取時間。 針對基準資料，檢視[效能基準](#performance-benchmarks)。

## Git Connector如何運作

下圖顯示Git聯結器如何將內容從來源存放庫移至Experience Manager Guides。

![](./images/git-connector-arch.png)

Git Connector會分四個階段將內容從Git存放庫移至Experience Manager Guides：

1. **抓取並同步**：爬蟲會連線至您設定的Git存放庫和設定檔，並視需求將內容同步至聯結器。
1. **擷取及偵測衝突**：會掃描傳入的檔案，並針對Experience Manager Guides中的現有檔案進行雜湊處理。 沒有衝突變更的檔案會自動移動；有衝突變更的檔案會標示為手動解決。
1. **持續**：已解析的內容會連同您的其他Experience Manager Guides內容一起處理並儲存到AEM中。
1. **Experience Manager Guides工作流程**：內容一經儲存後，即可像任何其他Experience Manager Guides內容一樣，用於編寫、檢閱、翻譯和發佈。

## 效能標竿

下列基準會以遞增的存放庫規模顯示Experience Manager as a Cloud Service上的完整（非增量） **大量匯入工具**&#x200B;同步處理時間。

| 縮放 | 擷取時間 | 匯入時間 | 總時間 | 批次 | 輸送量 |
|---|---|---|---|---|---|
| 1,000個檔案 | 1分53秒 | 3分30秒 | 5分29秒 | 10 × 100 | ~286個檔案/分鐘 |
| 5,000檔案 | 1分55秒 | 18分21秒 | 20分27秒 | 20 × 250 | ~273個檔案/分鐘 |
| 10,000個檔案 | 1分39秒 | 36分22秒 | 37分24秒 | 40 × 250 | ~267個檔案/分鐘 |
| 50,000檔案 | 1分25秒 | 2小時43分鐘 | 2小時58分鐘 | 200 × 250 | ~270個檔案/分鐘 |

## 使用Git聯結器匯入內容

管理員在Experience Manager Guides中設定Git Connector後，您可以從編輯器使用它，從Git存放庫匯入內容。

## 先決條件

開始使用此功能之前，請確定：

- 必須為您的環境啟用Git聯結器功能。
- （*若已啟用*）您的管理員已在您的環境中設定Git聯結器。 如需詳細資訊，請檢視[從使用者介面](../install-conf-guide/conf-git-connector.md)建立和設定Git聯結器。
- 您對包含您要匯入之內容的Git存放庫具有&#x200B;*讀取*&#x200B;存取權。
- 您知道要匯入的存放庫分支和來源資料夾。
- 您知道Experience Manager Guides中儲存匯入內容的目標資料夾。

## 從連線的Git存放庫匯入內容

執行以下步驟，從Git存放庫匯入內容：

1. 在編輯器中，開啟左側面板。
1. 選取&#x200B;**資料來源**。

   隨即顯示已連線的資料來源。

1. 選取&#x200B;**Git Connector**&#x200B;圖磚。

1. 選取+圖示，然後選取&#x200B;**大量匯入工具**。

   顯示&#x200B;**大量匯入工具**&#x200B;對話方塊。

   ![](images/git-bulk-importer-dialog.png)

1. 在&#x200B;**大量匯入工具**&#x200B;對話方塊中，提供匯入的名稱，從已設定的Git存放庫中選取子資料夾，然後選取&#x200B;**儲存並擷取**。  可匯入的檔案清單會顯示在對話方塊中。 繼續之前，請先檢閱清單並驗證內容。

   ![](images/git-bulk-importer-import-all.png)

1. 檢閱檔案後，選取&#x200B;**全部匯入**&#x200B;以將內容匯入Experience Manager Guides。

   >[!NOTE]
   >
   > 您可以啟用&#x200B;**自動同步**，以自動同步和匯入Git存放庫中的內容至Experience Manager Guides。 如果偵測到任何錯誤，則不會觸發自動同步處理，而且作者必須選取&#x200B;**全部匯入**，以手動方式匯入內容。 啟用後，匯入工具將無法停用自動同步處理。

匯入內容後，在設定Git聯結器時，內容會儲存在已設定的&#x200B;**目標AEM根路徑**&#x200B;下。

## 管理Git匯入的內容

將內容匯入Experience Manager Guides後，您可以使用可用的動作來管理內容，並將其與來源存放庫中的變更保持同步。

![](images/git-connector-imported-content-options.png){width="600"}

- **預覽**：預覽匯入的內容。 如果來源存放庫包含更新，請檢閱差異並使用&#x200B;**重新擷取**&#x200B;選項匯入最新變更。 如果差異需要合併，請檢視[解決Git聯結器衝突](#review-and-resolve-content-conflicts)。
- **刪除**：移除不再需要的Importer。
- **重新命名**：重新命名匯入工具以方便識別。
- **檢視記錄**：檢視匯入記錄檔以檢視匯入作業的詳細資料。
- **檢視報告**：檢視並下載&#x200B;**大量匯入報告**，其中包含下列詳細資料：

  - 匯入檔案總數
  - 成功匯入的次數
  - 匯入失敗的次數

  ![](images/git-connector-view-report.png){width="600"}

  您也可以下載詳細報表。 如果某些檔案無法匯入，請使用&#x200B;**重試失敗的匯入**，以嘗試再次匯入這些檔案。

## 檢閱和解決內容衝突

當您從Git存放庫重新擷取內容時，存放庫版本與Experience Manager Guides中可用的對應內容之間的內容差異會顯示為衝突。 您必須解決並合併這類衝突，才能將資料匯入Experience Manager Guides。

執行以下步驟來解決和合併衝突：

1. 開啟「大量匯入工具」對話方塊並選取&#x200B;**重新擷取**。
1. 如果偵測到衝突，**需要合併**&#x200B;索引標籤會出現，並列出包含衝突的檔案。 選取「**需要合併**」標籤，然後從清單中選取檔案以檢閱並解決衝突。
1. 對於有衝突的檔案，會顯示三向合併檢視。

   ![](images/git-connector-resolve-conflicts.png)

   左窗格(**AEM**)顯示AEM存放庫中的目前內容，而右窗格(**GIT**)顯示遠端Git存放庫的傳入內容。 中間窗格(**Result**)一開始會填入AEM存放庫內容，並做為合併編輯器，解決衝突。 最終合併的結果會產生，並顯示在中間窗格中。

1. 檢閱編輯器中反白的差異，並使用合併控制項解決衝突：

   - 如果您想要使用Git存放庫中的最新變更，請確定已選取&#x200B;**GIT**&#x200B;區段中衝突的核取方塊，然後選取對應的`<<<`控制項。 選取的Git內容會取代&#x200B;**結果**&#x200B;區段中的衝突內容。

     ![](images/git-connector-replace-with-git.png)

   - 如果要保留兩個版本的內容，請清除衝突的核取方塊，然後使用`<<<`控制項將所需內容新增到&#x200B;**結果**&#x200B;區段，而不取代現有內容。

     ![](images/git-connector-keep-both-versions.png)

   - 同樣地，您可以使用AEM區段中的`>>>`控制項，保留Experience Manager Guides中目前的可用版本。


1. 檢閱合併內容後，請執行下列其中一項動作：

   - 使用&#x200B;**接受AEM**，將&#x200B;**結果**&#x200B;區段中的內容完全取代為&#x200B;**AEM**&#x200B;區段的版本，並保留您的本機變更。
   - 使用&#x200B;**Accept GIT**&#x200B;將&#x200B;**Result**&#x200B;區段中的內容完全取代為&#x200B;**GIT**&#x200B;區段的版本，並保留儲存庫變更。

無論您使用哪個選項，**都需要完成合併**。 選取它會將目前的&#x200B;**結果**&#x200B;內容鎖定為該檔案的解析版本，並將檔案標示為合併。

將包含衝突的所有檔案標示為合併後，**全部匯入**&#x200B;按鈕就會啟用。 選取&#x200B;**全部匯入**&#x200B;以完成解決衝突的程式。

如果檔案在Git存放庫中已變更，但尚未在Experience Manager Guides中修改，則不需要合併。 這類檔案會自動包含在&#x200B;**清除更新**&#x200B;中，並可直接匯入。

![](images/git-connector-clean-updates.png){width="600"}