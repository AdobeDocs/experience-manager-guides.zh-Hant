---
title: 發行說明| Adobe Experience Manager Guides 2026.03.0版的新增功能
description: 瞭解2026.03.0版Adobe Experience Manager Guides中的新功能和增強功能
role: Leader
source-git-commit: dedd253dba3d93beed162eb5258125928f6d315c
workflow-type: tm+mt
source-wordcount: '824'
ht-degree: 2%

---

# 2026.03.0版（2026年3月）的新增功能

本文介紹2026.03.0版Adobe Experience Manager Guides as a Cloud Service所推出的新功能和增強功能。

有關此版本中的問題修正清單，請查看 [2026.03.0 版本中修正的問題](fixed-issues-2026-03-0.md)。

瞭解2026.03.0版[的](../release-info/upgrade-instructions-2026-03-0.md)升級指示。

## 介紹Experience Manager Guides中的產品培訓和學習內容

Experience Manager Guides中的&#x200B;**產品訓練與學習**&#x200B;內容功能可讓訓練團隊和教學設計人員直接從Experience Manager Guides介面建立互動式電子學習課程。

![](assets/lc-overview.png)

透過範本導向的製作、互動式課程元件和對評估的支援，團隊可以開發符合其組織目標的高品質培訓內容。

>[!NOTE]
> 
> 所有Experience Manager Guides as a Cloud Service例項都會預設停用產品培訓和學習內容功能。 管理員可以從&#x200B;**Workspace設定** > **一般**&#x200B;在資料夾設定檔層級啟用此功能。

主要功能如下：

- 集中式學習內容管理
- 範本驅動撰寫
- 支援內容重複使用
- 評估建立與管理
- Web型稽核工作流程
- 領先業界的翻譯管理
- 使用現成的SCORM和PDF輸出格式的多管道發佈

如需詳細資訊，請參閱[快速入門手冊](../learning-content/course-overview.md)和[設定指南](../lc-config-guide/introduction.md)。


## 編輯器增強功能

此版本已進行下列編輯器增強功能：

### Schematron驗證面板的增強功能

Schematron使用者介面已進行下列增強功能，以更清楚明瞭、可用性更高，並可產生驗證結果：

- 在「驗證」面板中，若未新增Schematron檔案，則會顯示空白狀態訊息，為後續步驟提供更清楚明瞭的方向。

  ![](assets/schematron-panel.png){width="350" align="left"}
- 新增多個Schematron檔案時，它們會整理在合併的摺疊式功能表下，以便更清楚地檢視已設定的Schematron檔案。

  ![](assets/schematron-panel-error.png){width="350" align="left"}
- 根據Schematron檔案中定義的角色屬性，驗證結果現在分類為： `Fatal`、`Error`、`Warn`或`Info`。 每個類別都包含可見的計數以及內容相關工具提示，以便更清楚理解。

  ![](assets/schematron-validation-errors.png){width="350" align="left"}

如需在Experience Manager Guides中使用Schematron檔案的詳細資訊，請檢視[Schematron檔案的支援](../user-guide/support-schematron-file.md)。

### 編輯器介面的右側面板現在提供翻譯語言副本

編輯器中之&#x200B;**檔案屬性**&#x200B;下的右側面板現在提供新的&#x200B;*翻譯*&#x200B;區段。 本節可讓您直接存取目前開啟之資產（地圖、主題、影像等）的所有可用語言副本。 您不再需要導覽至Assets UI即可檢視或存取這些語言副本。

![](assets/translations-right-panel.png){width="350" align="left"}

對於每個語言副本，您可以將滑鼠停留在檔案上以找出其在存放庫中的路徑，或直接選取它以在編輯器中開啟。 除了開啟檔案之外，您也可以使用&#x200B;**選項**&#x200B;功能表執行許多動作。 您可以執行的部分動作包括編輯、預覽、複製UUID、複製路徑、新增至集合和屬性。

如需更多詳細資料，請在編輯器中檢視[右側面板](../user-guide/web-editor-right-panel.md#file-properties)。


### 在所有日誌欄位中搜尋引文

現在，您可以使用&#x200B;*新增引文*&#x200B;對話方塊中的&#x200B;*Any field*&#x200B;選項，搜尋所有日誌欄位，例如&#x200B;*Title*、*Journal title*、*Author*、*Year*、*Volume*、**Number**&#x200B;和&#x200B;**Pages**。 搜尋會根據輸入的文字傳回最接近的相符引號。

如需在Experience Manager Guides中新增引文的詳細資訊，請檢視[在您的內容中新增和管理引文](../user-guide/web-editor-apply-citations.md)。

![](assets/add-citations.png){width="350" align="left"}



## 檢閱增強功能

此版本中的「檢閱」功能提供下列增強功能：

- 將稽核者指派給稽核任務現在取決於使用中的專案選擇。 在選取使用中的專案之前，**建立稽核任務**&#x200B;頁面上的&#x200B;*指派給*&#x200B;欄位保持停用狀態。 選取專案後，**指派給**&#x200B;欄位已啟用，並僅列出與該專案相關聯的使用者和使用者群組。 這可確保稽核任務僅指派給有效的專案成員，並防止稽核者意外選擇。

  ![](assets/create-review-task-023.png)

- **指派給**&#x200B;欄位現在支援預先輸入搜尋，可讓您透過輸入文字快速找到使用者或使用者群組。

這些增強功能加在一起，讓稽核者選取更準確、更有效率，並與專案特定的稽核工作流程保持一致。

如需詳細資訊，請檢視[傳送主題以供檢閱](../user-guide/review-send-topics-for-review.md)。

## 資產管理增強功能

此版本引進了資產管理的下列增強功能：

### 使用「平面化檔案階層」來下載具有原始檔案名稱和關聯中繼資料的地圖

現在，您可以使用「平面化檔案階層」選項來下載具有原始檔案名稱的對應。 此外，下載的套件包含`metadata.json`檔案，讓相關聯的中繼資料在Experience Manager Guides外部可輕鬆存取及重複使用。

如需有關在Experience Manager Guides中下載檔案的詳細資訊，請檢視[下載檔案](../user-guide/authoring-download-assets.md)。

### 使用Regex來啟用或停用後處理

您現在可以使用Regex來啟用或停用資料夾的後處理。 此增強功能可讓管理員使用單一設定，定義套用至多個資料夾或整個資料夾階層的後處理規則，而非指定個別資料夾路徑。

如需詳細資訊，請檢視[使用Regex啟用或停用後處理](../cs-install-guide/conf-folder-post-processing.md#use-regex-to-enable-or-disable-post-processing)。




