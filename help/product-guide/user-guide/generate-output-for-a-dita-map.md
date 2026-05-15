---
title: 產生輸出
description: 從AEM Guides中的Map主控台和Map儀表板產生DITA map的輸出。
exl-id: d6cbd44c-e74c-4192-bcc4-fb7752c59508
feature: Publishing
role: User
TQID: https://experienceleague.adobe.com/za9qWiDoXKDhu4nnbi37Tnl-QClwQra9XCXL4G-AgEg
product_v2: id: fae5e35a-80c9-4b94-9352-1a060a6aab1did: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: a3bd6397-2eb2-4908-a61c-226e26855dcaid: afb45297-4313-4f67-818e-bc0b03abe086id: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
subfeature_v2: id: b1ef4d86-3917-4b76-a0bc-4a4771f9b3b0id: f9dbea21-a714-40dd-bc90-080d8046c93fid: fd6cc9e1-e5e5-494e-b7b1-a32f2d6cd7c9
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2: id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 567
ht-degree: 0%

---

# 產生輸出

有兩種方法可產生DITA map的輸出：

- [從Map主控台產生DITA map的輸出](#generate-output-for-a-dita-map-from-the-map-console)
- [從Map儀表板產生DITA map的輸出](#generate-output-for-a-dita-map-from-the-map-dashboard)

## 從Map主控台產生DITA map的輸出

執行以下步驟，使用Map控制檯產生DITA map的輸出：

1. [在地圖主控台](./open-files-map-console.md)中開啟地圖檔案。
2. 顯示DITA map主控台，其中包含&#x200B;**可用於產生輸出的輸出預設集**&#x200B;清單。

3. 開啟您要用來產生輸出的預設集，然後選取&#x200B;**產生輸出**&#x200B;以開始產生程式。

   <img src="images/generate-output-pdf.png" alt="中繼資料標籤" width="600">

   或者，將滑鼠停留在預設集上，然後從預設內容功能表中選取&#x200B;**產生**。


   <img src="images/generate-preset-map-console.png" alt="中繼資料標籤" width="600">

輸出產生完成後，請選取&#x200B;**檢視輸出**&#x200B;以檢視輸出。

畫面的右下角會顯示&#x200B;**Success**&#x200B;對話方塊。

如果輸出不成功，則會顯示以下錯誤訊息。

<img src="images/error-log.png" alt="錯誤記錄" width="250">

若要檢視錯誤記錄，請選取&#x200B;**解除**，將游標停留在選取的預設集索引標籤上，然後從預設集內容功能表選取&#x200B;**檢視記錄**。

>[!NOTE]
>
> 如果您的對映使用DITAVAL檔案，則會將DITAVAL檔案中參照的所有已標幟影像複製到輸出中與已發佈對映相關的位置。  此外，如果您在同一個對應中使用多個DITAVAL檔案進行篩選，請務必使用唯一的`.ditaval`檔案名稱，以避免在發佈期間出現檔案名稱重複的問題。

## 從Map儀表板產生DITA map的輸出

執行以下步驟，使用「對映」圖示板產生DITA map的輸出：

1. 在Assets UI中，導覽至並選取您要發佈的DITA map檔案。

   DITA map主控台會出現，其中列出可用於產生輸出的輸出預設集。

1. 選取要用來產生輸出的一或多個輸出預設集。

   ![](images/generate-multiple-outputs-uuid.png)

1. 選取&#x200B;**產生**&#x200B;圖示以啟動輸出產生程式。


您可以在&#x200B;**輸出**&#x200B;索引標籤中檢視輸出產生要求的目前狀態。 如需詳細資訊，請檢視[檢視輸出產生工作的狀態](./generate-output-manage-process.md#view-the-status-of-the-output-generation-task)。

>[!IMPORTANT]
>
> 如果預設集的輸出產生程式在佇列中或進行中，則無法起始相同預設集的另一個輸出產生任務。

您也可以從Map主控台產生一或多個主題或整個DITA map的AEM Sites輸出。 如需詳細資訊，請檢視[產生知識庫輸出](web-editor-article-publishing.md#id218CK0U019I)。

## 使用`chunk`屬性合併DITA map中的不同主題

DITA map可以包含不同的主題型別，例如參照、概念和工作。 `chunk=to-content`屬性可讓您合併這些主題，以在AEM Sites上產生單頁輸出。 不過，若要正確發佈合併的主題，請確保您的管理員已在DITA設定檔中設定正確的XML目錄。

系統需要XML目錄中具有關鍵字`composite`的公用識別碼，才能正確識別並套用適當的DTD規則。
此設定預設會包含在標準XML目錄中。 不過，如果您使用自訂XML目錄，請確定您的管理員已將此公用ID新增至設定。 如果沒有它，合併的主題可能無法正確發佈。

如需如何在自訂DTD/XSD中使用公用ID和系統ID的詳細資訊，請檢視[整合DITA專門化](../cs-install-guide/dita-ot-specialization.md#integrate-dita-specialization-id211mb0e00xa)。



**父級主題：**[&#x200B;輸出產生](generate-output.md)
