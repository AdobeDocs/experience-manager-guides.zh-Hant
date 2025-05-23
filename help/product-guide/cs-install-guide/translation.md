---
title: 翻譯內容
description: 瞭解如何翻譯內容
exl-id: 5af78233-343e-47ba-b60c-b7f4789e2406
feature: Translation
role: Admin
level: Experienced
source-git-commit: ea3083542e955a56c27cd833600370a7962c6b8d
workflow-type: tm+mt
source-wordcount: '773'
ht-degree: 9%

---

# 翻譯內容 {#id181GB0400UI}

自動翻譯頁面內容、資產和使用者產生的內容，以建立和維護多語言網站。 若要自動化翻譯工作流程，您可以將翻譯服務提供商與 AEM 相整合，並建立用於將內容翻譯成多種語言的專案。AEM 支援人工和機器翻譯工作流程。

- 人工翻譯：內容會傳送給您的翻譯提供者，並由專業翻譯人員進行翻譯。 完成後，翻譯後的內容將傳回並匯入到 AEM 中。當您的翻譯提供者與AEM整合時，內容會自動在AEM和翻譯提供者之間交換

- 機器翻譯：機器翻譯服務會立即翻譯您的內容


翻譯內容涉及以下步驟：

1. 連線AEM與您的[翻譯服務提供者](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/administering/reusing-content/translation/integration-framework.html?lang=zh-Hant)並建立翻譯整合架構設定。

1. 將語言主版的頁面與翻譯服務和框架設定建立關聯。

1. 識別要翻譯的[內容型別](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/administering/reusing-content/translation/rules.html?lang=zh-Hant)。

1. 編寫語言主版並建立語言副本的根頁面，[以備妥內容進行翻譯](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/administering/reusing-content/translation/preparation.html?lang=zh-Hant)。

1. 建立[翻譯專案](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/administering/reusing-content/translation/managing-projects.html?lang=zh-Hant)以收集要翻譯的內容並準備翻譯程式。

1. 使用翻譯專案來[管理內容翻譯](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/administering/reusing-content/translation/managing-projects.html?lang=zh-Hant)程式。


如果您的翻譯服務提供者未提供聯結器來與AEM整合，則AEM支援手動匯出和匯入XML格式的翻譯內容。

>[!TIP]
>
> 如需有關翻譯內容的最佳實務，請參閱「最佳實務指南」中的&#x200B;*翻譯*&#x200B;區段。

## 在DITA map控制面板上設定翻譯標籤

若要隱藏DITA map圖示板上的「轉譯」標籤，請執行下列步驟：

1. 使用[組態覆寫](download-install-additional-config-override.md#)中提供的指示來建立組態檔。
1. 在設定檔案中，提供下列\(property\)詳細資訊，以在地圖控制面板上設定翻譯標籤：

   | PID | 屬性索引鍵 | 屬性值 |
   |---|------------|--------------|
   | `com.adobe.fmdita.config.ConfigManager` | `tabs.translation` | 布林值\( true/ false\)。<br> **預設值**： `true` |

   >[!NOTE]
   >
   > 此設定預設為啟用，地圖控制面板上不提供翻譯標籤。


## 設定元件型翻譯工作流程

如果翻譯供應商的聯結器不支援DITA內容，則需要啟用元件型翻譯工作流程。 啟用後，可翻譯內容會以資產中繼資料的形式傳送。 但是，聯結器需要支援資產中繼資料轉譯，此工作流程才能運作。

根據設定中使用的翻譯工作流程，應設定元件型翻譯工作流程選項。 使用[組態覆寫](download-install-additional-config-override.md#)中提供的指示來建立組態檔。 在設定檔案中，提供下列\(property\)詳細資訊，以設定元件型翻譯工作流程：

| PID | 屬性索引鍵 | 屬性值 |
|---|------------|--------------|
| `com.adobe.fmdita.config.ConfigManager` | `component.translation` | 布林值： <br> -   如果您使用人工翻譯，請&#x200B;*停用* \( `false`\) **元件式翻譯工作流程**&#x200B;選項。 <br> -   如果您正在使用機器翻譯，則&#x200B;*啟用\( `true`\)* **元件式翻譯工作流程**&#x200B;選項。 |



## 設定舊版翻譯工作流程

>[!IMPORTANT]
>
> 建議您使用AEM Guides 2024.06.0及更高版本中提供的最新翻譯工作流程，以提升效能。 不過，如果您已在翻譯程式中啟用任何自訂，且受新工作流程的影響，請考慮恢復為舊版翻譯工作流程作為因應措施。

使用[組態覆寫](download-install-additional-config-override.md#)中提供的指示來建立組態檔。 在設定檔案中，提供下列（屬性）詳細資料以設定舊版翻譯工作流程：


| PID | 屬性索引鍵 | 屬性值 |
|---|------------|--------------|
| `com.adobe.fmdita.config.ConfigManager` | `translation.workflow.version.legacy` | 布林值： <br> — 如果您使用最新的翻譯工作流程，則&#x200B;*停用* \( `false`\) **執行舊版翻譯工作流程**&#x200B;選項。  <br> -   如果您使用舊版翻譯，則&#x200B;*啟用\( `true`\)* **執行舊版翻譯工作流程**&#x200B;選項。<br> **預設值**： false |




>[!NOTE]
>
> 如果您使用翻譯聯結器，請確定您已依照Adobe Experience Manager檔案中&#x200B;*[設定翻譯整合架構](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/administering/reusing-content/translation/integration-framework.html?lang=zh-Hant)*&#x200B;主題中的說明設定聯結器。

>[!IMPORTANT]
>
> 設定翻譯設定後，請務必在語言資料夾上設定適當的雲端設定。

## 設定暫存語言副本的後處理

當您啟動翻譯工作流程時，系統會建立來源內容的臨時語言副本。 您可以選擇啟用或停用這些暫存檔的後處理作業。 在後置處理作業中，會解析來自檔案的傳入和傳出參照、設定檔案狀態以及其他作業。 如果您啟用這些暫存檔的後處理，則翻譯過程可能需要更長的時間才能完成。 因此，建議停用後續處理選項。

使用[組態覆寫](download-install-additional-config-override.md#)中提供的指示來建立組態檔。 在設定檔案中，提供下列\(property\)詳細資訊，以設定暫存語言副本的後置處理：

| PID | 屬性索引鍵 | 屬性值 |
|---|------------|--------------|
| `com.adobe.fmdita.config.ConfigManager` | `postprocess.temporary.langcopies` | 布林值： <br> -   如果您不想對暫存檔執行後續處理作業，請&#x200B;*停用* \( false\) **後續處理語言復本**&#x200B;選項。<br> -   如果要在暫存檔上執行後續處理作業，請&#x200B;*啟用* \( true\) **後續處理語言副本**&#x200B;選項。<br> **預設值**： false |

