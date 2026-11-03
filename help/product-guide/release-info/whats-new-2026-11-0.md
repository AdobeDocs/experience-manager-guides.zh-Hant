---
title: 發行說明 | Adobe Experience Manager Guides 2026.11.0版的新增功能
description: 探索2026.11.0版Adobe Experience Manager Guides的新功能，包括地圖層級分支和AI助理內容建立。
role: Leader
source-git-commit: b9dc9674244cbcf20fba1f51665afb4440172cdb
workflow-type: tm+mt
source-wordcount: '1508'
ht-degree: 0%
---

# 2026.11.0版（2026年11月）的新增功能

本文介紹2026.11.0版Adobe Experience Manager Guides as a Cloud Service所推出的新功能和增強功能。

如需此版本中修正的問題清單，請檢視[2026.11.0版本](fixed-issues-2026-11-0.md)中的已修正問題。

瞭解2026.11.0版[&#128279;](../release-info/upgrade-instructions-2026-11-0.md)的升級指示。

## 引進地圖層級分支和合併

Experience Manager Guides引入地圖層級分支和合併功能，讓作者可同時處理多個檔案版本、功能更新和關鍵修正，而不會影響主要內容。 作者可以建立DITA map及其相依性的獨立分支，確保每個分支的編輯、鎖定和預覽都是特定的。

此功能可幫助檔案團隊管理平行工作流程、有效率地共同作業，並維護主要檔案版本的穩定性。 您可以：

- 從DITA map的主要版本建立&#x200B;**分支**，以獨立處理功能、增強功能或重要修正。
- 在編輯器中&#x200B;**切換分支**&#x200B;以管理多個檔案版本。
- **管理內容版本**&#x200B;以透過分支和合併來組織變更。
- **使用引導式比較工作流程與三向合併來解決合併衝突**。
- **將變更**&#x200B;合併至主要版本。
- **使用標準發行直接從分支**&#x200B;發行，而不修改主要版本。

深入瞭解[分支與合併](../user-guide/branching-overview.md)。

![](./assets/branching.png){width="650"}


## AI支援的內容建立和AI Assistant中的匯入技能

>[!NOTE]
>
>若要以代理模式使用AI助理，您的組織必須加入Adobe CX Enterprise Coworker並擁有必要的學分。

您現在可以使用&#x200B;**AI小幫手**，使用自然語言提示來建立和匯入DITA內容。 由&#x200B;**Adobe CX Enterprise Coworker**&#x200B;提供技術支援，新的&#x200B;**建立**&#x200B;和&#x200B;**匯入**&#x200B;技能可簡化結構化內容的建立，並幫助作者處理DITA內容，而不需要廣泛的DITA專業知識。

- **建立：**&#x200B;使用存放庫範本從自然語言提示、參考檔案或現有內容產生DITA主題和地圖。 您可以在儲存之前檢閱產生的內容，並反複調整新內容或現有內容以符合您的需求。
- **匯入：**&#x200B;將現有的PDF、DOCX或Markdown檔案轉換成結構化DITA主題和地圖。 您可以先檢閱轉換的內容，然後再將它儲存到存放庫。
- **智慧標籤：**&#x200B;根據您組織的分類法取得內容的相關標籤建議。 此增強型體驗可讓管理員在Workspace設定中設定分類名稱空間，以確保一致且受管理的標籤建議。

**AI小幫手**&#x200B;面板也引進了全熒幕模式和&#x200B;**作用中交談**&#x200B;區段，以提供增強的交談體驗。

如需詳細資訊，請檢視[在代理模式中使用AI小幫手](../user-guide/ai-assistant.md#agentic-mode)。

![](./assets/preview-import.png){width="650"}


## Experience Manager Guides新的說明助理面板

創作AI支援的&#x200B;**智慧型說明**&#x200B;功能可透過專用的&#x200B;**說明小幫手**&#x200B;面板使用，可從首頁、編輯器和地圖主控台介面存取。 此面板提供對話式搜尋體驗，可讓您以自然語言提出問題，並從Experience Manager Guides檔案中快速尋找相關資訊。 這可協助您存取情境式指引並解決查詢，而不需離開編輯器，精簡您的撰寫工作流程。

管理員可以透過Workspace設定管理「說明小幫手」面板的可用性。 **AI說明小幫手**&#x200B;區段包含啟用或停用使用者面板的切換按鈕。

如需詳細資訊，請檢視[說明助理](../user-guide/ai-based-smart-help.md)。

![](./assets/help-assistant.png){width="650"}

## Authoring增強功能

### 在新編輯器中追蹤變更面板

「新編輯器」現在提供&#x200B;**追蹤變更**&#x200B;面板，可讓您檢視主題中所有追蹤的插入和刪除。 您可以追蹤多個使用者所做的編輯，並直接從面板接受或拒絕變更。

您也可以使用&#x200B;**顯示追蹤刪除內嵌**&#x200B;設定，控制已刪除內容在編輯器中顯示的方式，此設定可讓您將已刪除內容顯示為刪除線文字，或以連結至對應變更的鉛筆圖示取代。 深入瞭解[追蹤變更](../user-guide/config-editor-settings.md#track-changes)。

![編輯器設定](./assets/track-changes-all.png){width="650"}

### 在Explorer面板中排序檔案和資料夾

編輯器中的&#x200B;**檔案總管**&#x200B;面板可讓您使用&#x200B;**排序**&#x200B;按鈕，以遞增或遞減順序排序檔案和資料夾。 依預設，專案會根據&#x200B;**使用者偏好設定**&#x200B;中的&#x200B;**編輯器檔案顯示**&#x200B;設定，依標題或檔案名稱以遞增順序排序。 這可讓您更輕鬆地在編輯器中導覽及尋找內容。

如需詳細資訊，請在檔案和資料夾的分頁載入中檢視[檔案總管](../user-guide/paginated-loading-assets.md#explorer)區段。

### 從編輯器管理非DITA檔案的版本和標籤

Experience Manager Guides可讓您直接從編輯器檢視版本記錄，並管理非DITA檔案（例如影像、多媒體、ZIP、PDF和DOCX檔案）的版本標籤。 您可以預覽這些檔案、檢閱其版本記錄、比較版本，以及還原成較舊的版本，無需導覽至Assets UI。 您也可以套用或更新現有檔案版本的版本標籤，以簡化版本識別和管理。

如需詳細資訊，請檢視[使用媒體和其他非DITA檔案](../user-guide/authoring-file-management.md#work-with-media-and-other-non-dita-files)。


![編輯器設定](./assets/version-management-non-dita-files.png){width="650"}


## 檢閱增強功能

### 使用發起人註解加強稽核共同作業

稽核發起人可以使用稽核UI將內嵌註釋和註解新增到稽核任務的主題中。 這可讓他們提供更多情境、強調特定內容，並吸引稽核者注意需要意見回饋的領域。

這些註解會與其他檢閱者的意見一起出現在&#x200B;**註解**&#x200B;面板中，提供檢閱討論內容的整合檢視。 發起者新增評論時，稽核者也會收到AEM通知，有助於在整個稽核過程中簡化共同作業和溝通。 如需詳細資訊，請檢視[新增稽核者的註解](../user-guide/review-send-topics-for-review.md#add-comments-for-reviewers)。

## 發佈增強功能

### 從Map主控台檢視和管理輸出歷史記錄

Experience Manager Guides中的地圖主控台現在包含&#x200B;**輸出歷史記錄**&#x200B;標籤，可讓您直接從編輯器檢視及管理輸出產生工作，而不需導覽至地圖儀表板。

索引標籤提供輸出產生任務的整合檢視，包括其狀態、預設集詳細資訊、產生日期和持續時間。 您可以搜尋和篩選任務、取消進行中的層代、存取產生的輸出和記錄，以及從歷史記錄中移除已完成的專案。 您也可以將輸出歷史記錄匯出為CSV檔案，以供進一步分析。 輸出產生狀態使用與「地圖」圖示板一致的顏色指示器。

如需詳細資訊，請檢視[管理輸出產生程式](../user-guide/generate-output-manage-process.md#view-and-manage-output-generation-tasks-from-the-editor)。

![編輯器設定](./assets/output-history-editor-view.png){width="650"}


### 增強的輸出歷史記錄清除選項

您可以依年齡&#x200B;**（移除超過指定天數的專案）或**&#x200B;依計數&#x200B;**（僅保留指定數目的最近專案）清除輸出歷史記錄**。

您也可以選擇只清除輸出日誌，同時保留歷史記錄專案以供稽核，或移除日誌及其相關專案。 這些選項有助於最佳化存放庫儲存空間，同時加強對輸出歷史記錄清除的控制。

如需詳細資訊，請檢視[設定輸出歷程記錄](../install-conf-guide/conf-output-generation.md#configure-auto-purging-period-for-output-history-id19aai070v8q)的自動清除期間。

### Edge Delivery Services發佈設定檔的GitLab支援

Edge Delivery Services發佈功能支援GitLab主控的存放庫及GitHub，讓您更靈活地管理和發佈DITA內容。 若要發佈至GitLab託管的網站，請在建立Edge Delivery Services發佈設定檔時，選取GitLab作為伺服器型別，並在「存取權杖」欄位中提供存放庫的專案存取權杖。

發佈預設集也包含子資料夾的欄位，因此您可以將內容發佈到設定檔中所指定根資料夾內的子資料夾。

如需詳細資訊，請檢視[設定Edge Delivery Services](../knowledge-base/publishing/configure-eds.md)。

### Salesforce發佈的增強功能

Experience Manager Guides透過改善安全性、效能和發佈效率，強化Salesforce發佈。 這些增強功能包括支援代碼交換(PKCE)的Proof Key、重新整理權杖型驗證、文章層級發佈狀態、詳細發佈記錄、輸出記錄和最佳化資產發佈，以減少重複上傳。

如需詳細資訊，請檢視[使用後端處理的增強Salesforce發佈](../user-guide/web-editor-article-publishing.md#enhanced-salesforce-publishing-using-backend-processing)。


### 支援原生PDF中來自地圖中繼資料的影像

原生PDF發佈支援動態顯示DITA map、bookmap和自訂地圖的中繼資料中所定義的影像。 您可以在多個地圖上使用單一PDF範本，同時在產生的輸出中顯示地圖特定的影像，例如產品封面影像。

將影像預留位置新增至頁面版面配置中，您可在發佈期間自動以地圖中繼資料中參照的影像填入頁面。 如此一來，您就不需要為不同的影像維護個別的範本，並簡化範本管理。

如需詳細資訊，請檢視[從地圖中繼資料](../native-pdf/design-page-layout.md#add-an-image-from-map-metadata-add-image-map-metadata)新增影像。

### 透過舊編輯器中的內容健康狀態檢查來驗證內容品質

內容健康情況檢查在舊編輯器中提供（在新編輯器中已受支援），有助於在發佈之前驗證跨DITA map的內容品質。 管理員可以建立可重複使用的健康情況檢查預設集，方法是結合中斷連結的檢查、重複ID和結構描述驗證。

作者可以在DITA map或舊編輯器中的選取基準上執行狀況檢查，以產生跨相關主題和對映的合併問題報告。 如需詳細資訊，請檢視[在地圖](../user-guide/map-editor-other-features.md#run-health-check-on-a-map)上執行健康狀態檢查。

## 適用於舊版內容移轉的Upsert API

此API可讓您透過單一API建立或更新內容及其中繼資料。 它支援在請求中指定主題內容、中繼資料和GUID。 API可在`/bin/guides/v1/asset/upsert/`的Swagger API檔案中取得。