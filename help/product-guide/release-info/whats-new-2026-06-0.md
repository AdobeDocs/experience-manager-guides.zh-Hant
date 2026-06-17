---
title: 發行說明 | Adobe Experience Manager Guides 2026.06.0版的新增功能
description: 瞭解2026.06.0版Adobe Experience Manager Guides中的新功能和增強功能
role: Leader
source-git-commit: f3f30400f776f746427e257e2c937ff3413aa9ac
workflow-type: tm+mt
source-wordcount: '943'
ht-degree: 0%

---

# 2026.06.0版（2026年6月）的新增功能

本文介紹2026.06.0版Adobe Experience Manager Guides as a Cloud Service所推出的新功能和增強功能。

如需此版本中修正的問題清單，請檢視[2026.06.0版本](fixed-issues-2026-06-0.md)中的已修正問題。

瞭解2026.06.0版[&#128279;](../release-info/upgrade-instructions-2026-06-0.md)的升級指示。


## 新的地圖收集(Beta)，用於管理地圖和發佈輸出

>[!NOTE]
>
> 此功能目前是Beta功能，預設為停用。 若要在您的環境中啟用它，請聯絡客戶成功團隊。

新的地圖收集(Beta)將地圖收集管理和輸出產生活動整合在單一介面中。 您可以從一個位置管理地圖和預設集、產生和發佈輸出、檢視產生和發佈歷史記錄等。 將相關的發佈工作整合在一起，可讓您更輕鬆地處理地圖集合，並追蹤多個地圖及其相關語言的輸出活動。

![](assets/new-maps-collection.png)

如需詳細資訊，請檢視[使用新的對應集合來產生輸出(Beta)](../user-guide/generate-output-use-new-map-collection-output-generation.md)。

## 介紹適用於原生PDF的新發佈引擎

新的發佈引擎&#x200B;*原生PDF引擎v2*&#x200B;現在可用於Experience Manager Guides中的原生PDF。 其中包括原生PDF引擎v1問題的轉譯增強功能和修正。 由於轉譯行為已更新，使用&#x200B;*原生PDF引擎v2*&#x200B;產生的PDF輸出可能與使用現有原生PDF發佈引擎&#x200B;*原生PDF引擎v1*&#x200B;產生的輸出不同。

例如，由於&#x200B;*原生PDF引擎v2*&#x200B;使用的核心字型更新，所產生PDF中的文字可能會稍微不同。 同樣地，由於影像內插和演算行為的改善，影像可能看起來更銳利。

瞭解如何在您的環境中[啟用原生PDF引擎v2](../native-pdf/conf-new-pdf-engine.md)。

如需&#x200B;**原生PDF引擎v2**&#x200B;的相關資訊，請檢視[使用原生PDF引擎v2](../native-pdf/new-pdf-engine.md)。


## 編輯器增強功能

### 支援AMA引文樣式

Experience Manager Guides現在支援美國醫學協會(AMA)的引文風格，將現有的引文架構加以擴充，以符合醫療保健、法規及生命科學等行業的客戶所要求的檔案標準。

在&#x200B;**Workspace設定**&#x200B;中選取AMA作為引文樣式時，引文會根據AMA准則自動格式化，包括數字上標轉譯、循序編號和精確的參考清單排序。 在選取AMA時，編輯器中只能使用&#x200B;**剖析引文**&#x200B;選項，讓作者可以新增及剖析引文，而不需切換內容。

原生PDF和AEM Sites輸出格式支援AMA引文樣式。 若要設定引文樣式，請移至&#x200B;**Workspace設定**，然後從引文樣式選項中選取AMA。 如需詳細資訊，請檢視[使用引文](../user-guide/web-editor-apply-citations.md)。


### 新編輯器中現在支援外部資料來源和引文

新編輯器現在支援兩種現有的Experience Manager Guides功能：與外部資料來源連線以及在檔案中使用引文的功能。

在新的編輯器中建立或更新內容時，作者可以繼續使用已設定的外部資料來源。 也支援引用，讓作者無需切換編輯器，即可新增及管理內容中的引用。

## 檢閱增強功能

### 在稽核UI和AEM收件匣(Beta)之間同步稽核任務完成

>[!NOTE]
>
> 此功能目前是Beta功能，預設為停用。 若要在您的環境中啟用它，請聯絡客戶成功團隊。

您現在可以在檢閱UI與AEM收件匣之間保持檢閱任務完成的同步。 啟用此功能後，在檢閱UI中完成任務會將其從AEM收件匣中移除，然後從AEM收件匣中完成該任務，會在檢閱UI中將其標示為已完成。 這有助於避免將相同任務完成兩次，並使稽核工作流程更加順暢。 作者與任務發起者可繼續稽核意見回饋，並在需要額外稽核時重新指派任務。 重新指派任務時，系統會為檢閱者產生新的AEM收件匣通知，讓檢閱週期順暢地繼續。

如需詳細資訊，請檢視[以檢閱者身分完成檢閱工作](../user-guide/review-complete-review-tasks.md)。

## 學習內容增強功能

此版本中的產品培訓和學習內容功能提供下列增強功能：

- 作者現在可以在學習者進修課程前，強制對學習者進行知識檢查。 為課程中的知識檢查引入新的&#x200B;**需要知識檢查才能繼續**&#x200B;選項。 啟用後，學習者必須先嘗試知識檢查，才能繼續後續的課程內容。 這有助於確保在課程的指定點完成所需的知識檢查。 如需詳細資訊，請檢視[插入]功能表中的[其他選項](../learning-content/lc-other-insert-options.md)。
- 建立學習內容時，您現在可以使用多行文字輸入欄位。 此增強功能支援單一欄位中的分行符號和文繞排，因此可更輕鬆地擷取較長的學習者回應，而不需依賴自訂指令碼。 深入瞭解[插入]功能表中的[其他選項](../learning-content/lc-other-insert-options.md)。
- SCORM輸出範本現在支援將不同的版面配置指派給課程中的不同主題型別。 這可讓您直接從輸出範本設定設定課程、測驗、概觀頁面和其他主題型別的專用版面。

  這允許每個主題型別使用適合其內容和結構的版面，而不是在所有課程頁面上套用相同的版面。 如需設定SCORM輸出範本之頁面配置的詳細資訊，請檢視[設定資料夾設定檔](../lc-config-guide/lc-folder-profile.md)。
- Experience Manager Guides現在支援將SCORM內容直接發佈至Adobe Learning Manager (ALM)。 設定ALM發佈設定檔後，作者可以產生SCORM輸出，並直接上傳至Adobe Learning Manager，無需下載及手動匯入套件。

  如需詳細資訊，請檢視[設定SCORM預設集](../learning-content/config-scorm-preset.md)。


