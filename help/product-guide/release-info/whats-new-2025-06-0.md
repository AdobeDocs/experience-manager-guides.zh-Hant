---
title: 發行說明 | Adobe Experience Manager Guides 2025.06.0版的新增功能
description: 瞭解2025.06.0版Adobe Experience Manager Guides中的新功能和增強功能
role: Leader
exl-id: 48f27aa6-d870-4228-8e62-db81699a25f7
source-git-commit: 158c2a99ac43fd70726bedf30f4de1a970a48864
workflow-type: tm+mt
source-wordcount: '523'
ht-degree: 3%

---

# 2025.06.0版（2025年6月）的新增功能

本文介紹2025.06.0版Adobe Experience Manager Guides as a Cloud Service所推出的新功能和增強功能。

有關此版本中的問題修正清單，請查看 [2025.06.0 版本中修正的問題](fixed-issues-2025-06-0.md)。

瞭解2025.06.0版](../release-info/upgrade-instructions-2025-06-0.md)的[升級指示。

## 已發佈輸出的暫存檔案，現在會在新設定檔中加入作者與發佈URL

Experience Manager Guides的最新發佈增強功能現在將新的`system_config.json`檔案新增至使用DITA-OT以及原生PDF輸出發佈HTML、PDF和JSON輸出時產生的暫存檔案。 此檔案會自動包含在發佈作業中，而且當您啟用預設集的&#x200B;**保留暫存檔案**&#x200B;選項並產生輸出時，也可以透過暫存檔案存取。

`system_config.json`檔案包含主要執行個體詳細資訊，包括作者URL、本機URL和發佈URL，可提供更清楚的上下文，並改善下載URL的可追蹤性。

如需更多詳細資料，請檢視[瞭解輸出預設集](../user-guide/generate-output-understand-presets.md)。

## 防止意外內容遺失的工作階段逾時提示

現在，當Adobe Experience Manager工作階段過期且您因非使用狀態而登出時，快顯訊息會通知您。 在工作階段結束後，當您嘗試在Experience Manager Guides中編輯內容時，會觸發此訊息。 此功能有助於降低遺失未儲存工作的風險，並提升體驗的整體可靠性和流動性，即使在閒置期間亦然。

![](assets/sign-out-prompt.png)

深入瞭解Experience Manager Guides中的[工作階段逾時提示](../user-guide/session-timeout-prompt.md)。

## 編輯器中增強型地圖下載選項

Experience Manager Guides在&#x200B;**下載地圖**&#x200B;對話方塊中引進了新的&#x200B;**使用實際檔案名稱**&#x200B;選項。 現在，當您下載地圖檔案時，您可以選擇保留其原始檔案名稱，而不是預設的UUID，以便更輕鬆地識別和管理您的檔案。 只有當您選取&#x200B;**保留檔案階層**&#x200B;時，才能使用此選項，當您選擇&#x200B;**平面化檔案階層**&#x200B;時，此選項會停用，讓您在組織下載的地圖時擁有更多彈性。

如需詳細資訊，請檢視[下載檔案](../user-guide/authoring-download-assets.md#download-a-dita-map-file-from-the-editor)。

![](assets/download-map-dialog-new.png){width="300" align="left"}


## 增強編輯器中的`navref`處理

編輯器的最新增強功能改善了DITA map中`navref`元素的處理。 現在，當您將`navref`元素新增至地圖時，**選取路徑**&#x200B;對話方塊會開啟，可讓您輕鬆選擇要做為地圖導覽連結的地圖參考。 新增後，新增的地圖的標題會顯示在「作者」檢視和「版面」檢視中，以便在編寫期間提供更清楚的導覽效果。  此外，新增的`navref`元素會自動解析，以在編輯器中顯示參照的對應。

如需詳細資訊，請檢視[新增導覽參考](../user-guide/map-editor-other-features.md#add-navigation-references)。

## AI助理中的效能增強

此發行版本引入了AI Assistant後端引擎的增強功能，提供改良的效能和更高的穩定性。 若要啟用此更新並繼續使用AI助理說明：

- 更新`chat.url`設定以反映新的端點URL。
- 在Cloud Manager中新增一個新的環境變數`GUIDES_AI_SITE_ID`。

如需詳細資訊，請檢視[設定AI小幫手](../cs-install-guide/conf-smart-suggestions.md)。

