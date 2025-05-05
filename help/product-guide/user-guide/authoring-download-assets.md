---
title: 下載檔案
description: 瞭解如何從AEM Guides的DITA map主控台下載檔案，以及匯出AEM存放庫中的DITA map檔案。
exl-id: ae9eb355-d3ac-446a-958b-5f2da43f5533
feature: Content Management
role: User
source-git-commit: 632b253a36822b4b5b93766153f0fc3a1116b616
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---

# 下載檔案 {#id216MC0H0BE8}

您可以下載資產，包括DITA和非DITA檔案。 您可以透過多種方式下載資產，有些是Adobe Experience Manager的原生方法，有些則受Adobe Experience Manager Guides支援。 如需原生Adobe Experience Manager資產下載資訊，請在Adobe Experience Manager檔案中檢視[從Adobe Experience Manager下載資產](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/manage/download-assets-from-aem.html)。 下節將說明透過Experience Manager Guides中的DITA map主控台下載檔案的機制。

## 匯出DITA map檔案

在Adobe Experience Manager存放庫中擁有DITA map檔案後，您就可以下載對應檔案及其相依專案。 這可讓您彈性地共用完整的對應檔案，以進行離線編輯、驗證、檢閱或只是建立備份。

執行以下步驟來下載DITA map檔案及其相依檔案：

1. 在Assets UI中，導覽至您要下載的DITA map。

1. 選取DITA map以在DITA map主控台中開啟它。

1. 選取&#x200B;**主題**&#x200B;標籤以檢視DITA map中可用的主題清單。

1. 在主工具列中選取&#x200B;**下載地圖**。

   便會顯示「下載地圖」對話方塊。

   ![](images/download-map.png){width="300" align="left"}

1. 選取&#x200B;**下載**。 在「下載對應」對話方塊中，您可以選擇下列選項：

   - **使用基準線**：選取此選項可取得為DITA map建立的基準線清單。 如果您要根據特定的「基準線」下載對映檔案及其內容，請從下拉式清單中選取「基準線」。 如需使用基準線的詳細資訊，請檢視[使用基準線](generate-output-use-baseline-for-publishing.md#)。

   - **平面化檔案階層**：選取此選項可將所有參考的主題和媒體檔案儲存在單一資料夾中。


   >[!NOTE]
   >
   > 您也可以在不選取任何選項的情況下下載地圖檔案。 在這種情況下，會下載參照的主題和媒體檔案的最後一個儲存版本。

1. 選取&#x200B;**下載**&#x200B;按鈕後，對應下載要求會排入佇列。 一旦地圖可供下載，您將會收到下列通知。

   ![](images/download-map-prompt.png){width="550" align="left"}

   - 選取&#x200B;**下載**&#x200B;以.zip格式下載對應檔。

   - 選取&#x200B;**稍後下載**&#x200B;稍後再下載對應檔。 您可以從Adobe Experience Manager通知收件匣存取下載連結。 在「收件匣」中選取產生的地圖通知，以.zip格式下載地圖。

   >[!NOTE]
   >
   > 依預設，下載的地圖會在Adobe Experience Manager通知收件匣中保留五天。

![](images/download-map-inbox.png){width="300" align="left"}

下載地圖後，您可以選取地圖，並使用頂端的開啟圖示開啟選取的報表。

**父級主題：**&#x200B;[&#x200B;管理內容](authoring.md)
