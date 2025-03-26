---
title: 增量輸出產生
description: 瞭解AEM Sites的增量輸出產生如何在AEM Guides中運作。
exl-id: 019d9fbf-2f23-4669-8022-d693be75c1c3
feature: Publishing
role: User
source-git-commit: ac83f613d87547fc7f6a18070545e40ad4963616
workflow-type: tm+mt
source-wordcount: '579'
ht-degree: 0%

---


# 增量輸出產生

>[!NOTE]
>
> 增量輸出產生僅適用於AEM Sites輸出。 此外，您只能從DITA map或子地圖重新產生DITA \(.dita/.xml\)主題。 如果您選取DITA map、子對應、主題群組或具有`@processing-role="resource-only"`的主題，則再生選項無法使用。

可能有許多例項只更新DITA map中的幾個主題，並只即時推播這些更新的主題。 若要處理這類案例，Experience Manager Guides可讓您建立增量輸出。 如果您已更新一些主題，則不需要重新產生整個DITA map。 您只能選取更新的主題並重新產生它們。

如果您的地圖是區塊化的，而且您已更新該地圖中的單一主題，則需要為更新的主題或內容重新產生整個地圖，以反映在輸出中。 您無法在主題層級取得輸出再生選項，只能在\(chunked\)對映層級使用。 這適用於父對映和所有子對映。

執行以下步驟來重新產生特定主題或主題群組的輸出：

>[!IMPORTANT]
>
> 當您再生AEM Sites輸出時，會使用檔案的目前版本而不是附加的「基準線」來建立輸出。

## 從地圖主控台產生增量輸出

執行以下步驟，使用Map主控台產生AEM Sites的增量輸出：

1. [在Map主控台](./open-files-map-console.md)中開啟DITA map檔案。
1. 選取您要產生增量輸出的AEM Sites預設集。
1. 在&#x200B;**主題**&#x200B;索引標籤中，選取您要發佈的主題。

   ![aem網站主題清單](images/aem-presets-topic-list.png) {align="left"}

   >[!NOTE]
   >
   > 在&#x200B;**內容**&#x200B;索引標籤中選取基準線時，主題清單會顯示附加基準線中的主題及其版本。<br><br>
   > 只有在對映的結構沒有變更時，才應使用主題清單中的增量發佈。 如果地圖結構/目錄變更，則整個地圖應發佈一次以更新目錄。
1. 選取&#x200B;**儲存**&#x200B;以儲存變更。
1. 選取&#x200B;**產生輸出**&#x200B;以產生輸出。


## 從Map儀表板產生增量輸出

執行以下步驟，使用Map儀表板產生AEM Sites的增量輸出：

1. 在Assets UI中，導覽至並選取DITA map檔案。

   DITA map主控台會出現，其中列出可用於產生輸出的輸出預設集。

1. 選取&#x200B;**主題**&#x200B;索引標籤。

   隨即顯示DITA map中可用的主題清單。

1. 選取要重新產生的主題。

   >[!NOTE]
   >
   > 如果您已將新主題新增至DITA map，您將無法從此處產生這些新主題。 您必須先使用DITA map發佈函式發佈新加入的主題。

   ![](images/regenerate-topics.png){align="left"}

1. 選取&#x200B;**重新產生**。

   會顯示&#x200B;**重新產生選取的主題**&#x200B;頁面。

1. 選取要用來再生所選主題的輸出預設集。

1. 選取&#x200B;**重新產生**&#x200B;以啟動輸出產生程式。


>[!IMPORTANT]
>
> 如果您重新命名主題標題並重新產生主題，則更新的主題標題不會反映在DITA map目錄中。 若要更新目錄中的主題標題，您必須產生整個DITA map。

您可以在&#x200B;**輸出**&#x200B;索引標籤中檢視輸出產生要求的目前狀態。 如需詳細資訊，請檢視[檢視輸出產生工作的狀態](#view-the-status-of-the-output-generation-task)。



**父級主題：** [瞭解輸出預設集](generate-output-understand-presets.md)
