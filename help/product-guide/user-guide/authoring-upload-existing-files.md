---
title: 上傳檔案
description: 瞭解如何將檔案上傳至AEM存放庫並處理錯誤。 瞭解資產控制檯使用者介面、AEM案頭應用程式、資產大量擷取器，以及使用FrameMaker進行大量上傳。
exl-id: b5430242-1122-43df-a0b2-275b1dea33f2
feature: Content Management
role: User
TQID: https://experienceleague.adobe.com/GG5Bx2yyJz2GaQFmMsDZ6wq6xzb4XUAsSBxEkRNvEVE
product_v2: id: fae5e35a-80c9-4b94-9352-1a060a6aab1did: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: ab01a588-7dea-43f2-a699-0b3f128465d6id: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 536
ht-degree: 0%

---

# 上傳檔案 {#id176FF000JUI}

您很可能擁有要與Adobe Experience Manager Guides搭配使用的現有DITA內容存放庫。 對於這類現有內容，您可以使用下列任何一種方法，將內容大量上傳至Adobe Experience Manager存放庫。

>[!IMPORTANT]
>
> 檢視[將數位資產新增至Adobe Experience Manager as a Cloud Service Assets](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/manage/add-assets.html)，以瞭解Adobe Experience Manager中支援的內容上傳方法的詳細資訊。

## Assets Console使用者介面

若要使用Adobe Experience Manager as a Cloud Service Console使用者介面[新增數位資產至Assets Assets](#upload-assets)，請在您的案頭上選取所需的資產，並在Adobe Experience Manager使用者介面\（網頁瀏覽器\）上拖曳至目的地資料夾。 上傳資產時，請確定檔案名稱不包含任何不支援或禁止使用的字元。

如需詳細資訊，請檢視Adobe Experience Manager檔案中的[檔案名稱處理與禁止使用的字元](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/manage/add-assets.html#filename-handling)區段。

## Adobe Experience manager 桌面應用程式

如果您是創意專業人員，且想要管理本機案頭上的資產，請使用Adobe Experience Manager案頭應用程式。 您可以使用案頭應用程式開啟及編輯這些資產。 您也可以維護版本，並與其他使用者共用檔案。 如需詳細資訊，請檢視[Adobe Experience Manager案頭應用程式](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html)。

## 資產大量擷取器

如果您有大規模移轉和偶爾的大量擷取，請使用資產大量擷取器來上傳您的內容。 使用此工具，您可以從支援的資料存放區（例如Azure或S3）上傳大量內容。 如需詳細資訊，請檢視[資產大量擷取](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/manage/add-assets.html?lang=en#asset-bulk-ingestor)。

## 使用FrameMaker進行大量上傳

Adobe FrameMaker隨附強大的Adobe Experience Manager聯結器，可讓您輕鬆將現有DITA和其他FrameMaker檔案\（`.book`和`.fm`\）上傳到Adobe Experience Manager。 您可以使用各種檔案上傳功能，例如上傳單一檔案、上傳具有或不具有相依性的完整資料夾\（如內容參照、交叉參照和圖形\）。

如需在FrameMaker中使用大量上傳功能的詳細資訊，請檢視FrameMaker使用手冊中的&#x200B;*建立CRX資料夾及上傳檔案*&#x200B;區段。

## 上傳內容時的錯誤處理 {#id201MI0I04Y4}

如果上傳一或多個檔案失敗，會在上傳程式結束時顯示提示，其中包含上傳失敗的檔案清單，如下面的程式碼片段所示。

![](images/uuid-files-failed-to-upload_cs.png){width="650" align="center"}

如需各種檔案上傳案例如何運作的詳細資訊，請檢視[管理檔案和資料夾](authoring-file-management.md#)。

如果您使用Adobe Experience Manager案頭應用程式或資產大量擷取器等工具，則對重複檔案執行的動作會由Adobe Experience Manager伺服器中的設定控制。 請連絡您的系統管理員以瞭解此設定。

**父級主題：**[&#x200B;管理內容](authoring.md)
