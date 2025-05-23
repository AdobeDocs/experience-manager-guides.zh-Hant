---
title: 產生輸出
description: 從AEM Guides中的Map主控台和Map儀表板產生DITA map的輸出。
exl-id: d6cbd44c-e74c-4192-bcc4-fb7752c59508
feature: Publishing
role: User
source-git-commit: ac83f613d87547fc7f6a18070545e40ad4963616
workflow-type: tm+mt
source-wordcount: '368'
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

## 從Map儀表板產生DITA map的輸出

執行以下步驟，使用「對映」圖示板產生DITA map的輸出：

1. 在Assets UI中，導覽至並選取您要發佈的DITA map檔案。

   DITA map主控台會出現，其中列出可用於產生輸出的輸出預設集。

1. 選取要用來產生輸出的一或多個輸出預設集。

   ![](images/generate-multiple-outputs-uuid.png){align="left"}

1. 選取&#x200B;**產生**&#x200B;圖示以啟動輸出產生程式。


您可以在&#x200B;**輸出**&#x200B;索引標籤中檢視輸出產生要求的目前狀態。 如需詳細資訊，請檢視[檢視輸出產生工作的狀態](./generate-output-manage-process.md#view-the-status-of-the-output-generation-task)。

>[!IMPORTANT]
>
> 如果預設集的輸出產生程式在佇列中或進行中，則無法起始相同預設集的另一個輸出產生任務。

您也可以從Map主控台產生一或多個主題或整個DITA map的AEM Sites輸出。 如需詳細資訊，請檢視[產生知識庫輸出](web-editor-article-publishing.md#id218CK0U019I)。




**父級主題：**&#x200B;[&#x200B;輸出產生](generate-output.md)
