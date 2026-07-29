---
title: 發行說明 | Adobe Experience Manager Guides 2026.08.0版的新增功能
description: 瞭解2026.08.0版Adobe Experience Manager Guides中的新功能和增強功能
role: Leader
source-git-commit: 087f74b41a3ce374aca06701e8b58e0d27492592
workflow-type: tm+mt
source-wordcount: '1371'
ht-degree: 0%

---

# 2026.08.0版（2026年8月）的新增功能

本文介紹2026.08.0版Adobe Experience Manager Guides as a Cloud Service所推出的新功能和增強功能。

如需此版本中修正的問題清單，請檢視[2026.08.0版本](fixed-issues-2026-08-0.md)中的已修正問題。

瞭解2026.08.0版](../release-info/upgrade-instructions-2026-08-0.md)的[升級指示。


## 管理地圖和發佈輸出的新地圖集合

新的地圖集合將地圖集合管理和輸出產生活動整合在單一介面中。 您可以從一個位置管理地圖和預設集、產生和發佈輸出、檢視產生和發佈歷史記錄等。 將相關的發佈工作整合在一起，可讓您更輕鬆地處理地圖集合，並追蹤多個地圖及其相關語言的輸出活動。 此更新也會解決大型地圖集合中顯示的效能問題。

![](assets/new-maps-collection.png)

如需更多詳細資料，請檢視[使用新的對應集合來產生輸出](../user-guide/generate-output-use-new-map-collection-output-generation.md)。


## 使用Git聯結器從Git存放庫擷取內容

Experience Manager Guides現在推出Git聯結器，可讓您將Git存放庫中的內容匯入Experience Manager Guides。 匯入內容後，團隊可以繼續使用Experience Manager Guides進行編寫、檢閱、翻譯和發佈工作流程。

為協助讓匯入的內容保持最新狀態，Git Connector也支援從來源存放庫重新擷取內容，以進行更新。 它包含智慧型變更偵測，可識別內容更新、在匯入和重新擷取作業期間保留主題和對應GUID，並提供衝突解決功能以協助管理存放庫內容與Experience Manager Guides中已有可用內容之間的差異。 如需詳細資訊，請檢視[使用Git聯結器匯入內容](../user-guide/web-editor-git-connector.md)。

![](assets/git-bulk-importer-import-all.png)


## Experience Manager Guides新增MCP支援

Experience Manager Guides現在支援模型內容通訊協定(MCP)。 您可以將Claude、Cursor等AI工具連線到Guides，而無需任何自訂工作。 透過單一MCP端點，在這個版本中，已驗證身分的使用者可以將Guides用作Headless系統，並管理主題和地圖、建立和匯出基準線，以及產生報表，同時都在他們現有的AEM許可權下操作。 這使檔案團隊能夠使用AI應用計畫和代理程式更高效地工作。

如需詳細資訊，請檢視[使用Adobe Experience Manager Guides MCP伺服器](../install-conf-guide/conf-aem-guides-mcp.md)。


## 檢閱增強功能

### 將稽核任務委派給其他稽核者

檢閱者現在可以建議其他使用者在檢閱回到作者之前，使用可用於檢閱任務的新&#x200B;**委派**&#x200B;選項來加入檢閱。 當部分內容超出檢閱者的專業知識範圍或需要在完成檢閱前有第二個意見，而無須透過專案管理員路由請求時，此功能會很有用。

選取「委派」選項會將建議傳送給作者，由作者決定是否將建議的稽核者新增至任務。 深入瞭解[將稽核任務委派給其他稽核者](../user-guide/review-complete-review-tasks.md#delegate-a-review-task-to-another-reviewer)。

![](assets/review-delegate-option.png){width="350"}

### 任務說明現在顯示在稽核UI中

稽核者現在可以直接在稽核體驗中檢視任務說明，而不是僅依賴通知電子郵件。 建立稽核任務時輸入的描述現在顯示在稽核詳細資訊對話方塊中，可透過稽核UI和編輯器介面中的&#x200B;**資訊**&#x200B;圖示存取。

這可讓檢閱者存取整個檢閱中的指示、範圍和焦點區域。 如需詳細資訊，請檢視[傳送主題以供檢閱](../user-guide/review-send-topics-for-review.md)。

![](assets/review-details.png){width="350"}

### 稽核期間標籤清單中的使用者識別

在評論或回覆中標籤使用者時，標籤下拉式清單現在會顯示每個使用者的電子郵件地址及其使用者ID。 這可以讓您更容易識別和選取正確的檢閱者，尤其是在顯示名稱可能模稜兩可的大型組織中。

如果電子郵件地址無法使用，則會改為顯示使用者ID。 如需使用檢閱UI的詳細資訊，請在註解](../user-guide/review-topics.md#tag-task-users-in-a-comment)中檢視[標籤任務使用者。


### 檢視主題的所有稽核任務

作者現在可以直接從「註解」面板檢視與目前開啟的主題相關的所有稽核任務（開啟或已關閉）。 下拉式清單會列出主題所屬的每個稽核任務，以及每個任務的狀態和專案，並讓您在它們之間切換以檢視註解，而不會離開主題或切換稽核專案。 深入瞭解[檢視主題](../user-guide/review-address-review-comments.md#view-all-review-tasks-for-a-topic)的所有稽核工作。

![](assets/review-task-selection-dropdpwn.png){width="350"}

### 使用DITAVAL條件增強稽核體驗

當稽核任務包含一個或多個附加的DITAVAL檔案時，「條件」面板現在會將每個條件顯示為切換，預先設定以符合附加的DITAVAL檔案，因此稽核者會以稽核發起者的預期方式檢視內容。 關閉切換功能會隱藏該內容以避免檢閱；開啟切換功能則會恢復該內容。

如需詳細資訊，請檢視具有DITAVAL式條件的[條件面板](../user-guide/review-topics.md#conditions-panel-with-ditaval-based-conditions)。

![](assets/review-condition-panel-ditaval.png){width="350"}

## 發佈增強功能

### 使用輸出預設集作為範本

管理員現在可以將輸出預設集指定為範本，透過Map主控台使用單一動作，將標準化設定套用至資料夾設定檔中的所有對應。 套用範本時，系統會顯示受影響的地圖數量，讓管理員在轉出前可完整檢視。 為了保持一致性，範本預設集只能由管理員修改，並且範本預設集的輸出產生功能會停用（除非在設定預設集為範本之前已經產生輸出）。

如需詳細資訊，請檢視[設定輸出產生](../install-conf-guide/template-presets-output-generation.md)的範本預設集。

### 透過內容健康狀態檢查來驗證內容品質

內容健康狀態檢查有助於在發佈之前驗證DITA map中的內容品質。 管理員可以建立可重複使用的健康情況檢查預設集，方法是結合中斷連結的檢查、重複ID和結構描述驗證。

作者可以在DITA map或選取的基準上執行健康狀態檢查，以產生跨相關主題和地圖的合併問題報告。 如需詳細資訊，請檢視[在地圖](../user-guide/map-editor-other-features.md#run-health-check-on-a-map)上執行健康狀態檢查。


## 翻譯增強功能

### 指定翻譯專案的自訂資料夾路徑

傳送內容以進行翻譯時，您現在可以選取建立新翻譯專案的資料夾，而不是所有專案預設為`/content/projects`下的單一位置。 這有助於避免雜亂的專案結構，並隨著翻譯專案數量的增加改善頁面載入效能。

如需詳細資訊，請檢視[建立翻譯專案](../user-guide/translate-documents-web-editor.md#create-a-translation-project)。

## 學習內容增強功能

此版本中的產品培訓和學習內容功能提供下列增強功能：

- SCORM輸出設定現在提供新的&#x200B;**學習者體驗**&#x200B;索引標籤，可讓您設定學習者如何與SCORM輸出互動及導覽。 設定會整理在「一般」、「導覽」和「測驗」下，讓您可控制內容協助工具、導覽流程及測驗行為，以提供量身打造的學習體驗。

  在「**導覽**」下，您現在可以控制頁面上是否啟用或停用「**下一步**」按鈕，讓學習者只會在符合該頁面的指定條件後才進行進度，例如開啟所有互動式元素、觀看所有媒體等等。 如需詳細資訊，請檢視[設定SCORM預設集](../learning-content/config-scorm-preset.md)。

  ![](assets/learner-experience.png){width="650"}

- 您現在可以在SCORM輸出中啟用學習者的PDF下載。 啟用此選項後，已發佈的SCORM輸出會新增PDF下載圖示，讓學習者可下載PDF版本的課程內容以供離線參考。 這樣可讓學習者更靈活地存取課程資料，同時讓作者更能掌控發佈的體驗。 如需設定詳細資訊和先決條件，請檢視[允許學習者下載課程PDF](../learning-content/config-scorm-preset.md)。

  ![](assets/pdf-icon.png){width="650"}

- 在已發佈的課程輸出中，學習者現在可在完成測驗嘗試後使用&#x200B;**檢閱答案**&#x200B;選項，以重新造訪他們提交的回覆，並檢視哪些答案正確或不正確。 進一步瞭解測驗](../learning-content/quiz-insert-questions.md#question-properties)中的[問題屬性。

  ![](assets/review-answer-quiz.png){width="650"}

- 在課程中的知識檢查問題中，當學習者選取錯誤答案時，現在會顯示&#x200B;**再試一次**&#x200B;按鈕，允許他們重試問題。 在單選和多選知識檢查中，此行為是一致的。 如需詳細資訊，請檢視[插入]功能表中的[其他選項](../learning-content/lc-other-insert-options.md)。

- 將HTML主題新增至學習群組地圖時，`format="html"`屬性現在會自動新增至對應的`topicref`，以確保在DITA-OT 4.x下正確處理和發佈。 如需詳細資訊，請檢視[在您的課程中新增現有內容](../learning-content/manage-course.md#add-existing-content)。

## API增強

此發行版本引進了適用於資產管理、翻譯和發佈的新Swagger API，讓您更輕鬆地將這些工作流程與現有的工具和系統連結。 如需詳細資訊，請檢視Experience Manager Guides版本](../api-reference/api-update-swagger.md)中的[API更新。

