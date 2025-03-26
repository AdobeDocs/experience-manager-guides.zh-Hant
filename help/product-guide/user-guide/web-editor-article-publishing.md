---
title: 產生知識庫輸出
description: 瞭解如何從Map主控台發佈一或多篇文章。 在AEM Guides中為DITA map中的一個或多個主題產生輸出。
exl-id: d89ce69d-8d4c-4265-bfca-60763f561afd
feature: Publishing
role: User
source-git-commit: ac83f613d87547fc7f6a18070545e40ad4963616
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 0%

---

# 產生知識庫輸出 {#id218CL05J0M1}

Adobe Experience Manager Guides隨附以文章為基礎的發佈功能，可讓使用者同時發佈一或多篇知識庫文章。

此引擎也隨附OOTB內容範本(以Adobe Experience Manager核心元件為基礎)，可讓使用者建立技術內容的知識型存放庫。 此範本可自訂以符合客戶的需求。此引擎可讓使用者以累加方式建置DITA map，並在準備好時發佈主題。

如果您只更新了DITA map中幾個主題的內容，則不必每次都發佈整個對應。 您只能選取和發佈更新的主題。

對於以文章為基礎的發佈，您需要為知識庫DITA map建立輸出預設集。 您的地圖必須包含您要發佈的主題。 您也可以套用條件，並指定輸出預設集的AEM Sites詳細資料。 然後，您可以使用&#x200B;**產生輸出**&#x200B;功能產生輸出。

執行以下步驟來產生以文章為基礎的輸出：

1. [建立知識庫預設集](./generate-output-knowledge-base.md)，用於以文章為基礎的輸出。
1. 導覽至&#x200B;**文章**&#x200B;標籤，並選取您要產生輸出的主題。
1. 選取頂端的&#x200B;**產生輸出**&#x200B;以產生輸出。

   ![](images/add-preset-articles-tab_cs.png){align="left"}

1. 在&#x200B;**確認要發佈的檔案**&#x200B;提示中，選取您要發佈的檔案並透過選取&#x200B;**發佈**&#x200B;進行確認。

   ![新](images/knowledge-base-confirm-files-for-publishing.png){align="left"}

   您將檢視輸出產生程式的狀態。 **主題**&#x200B;欄會列出正在產生輸出的主題，而&#x200B;**狀態**&#x200B;欄會顯示每個主題的發佈狀態。


   ![](images/add-preset-output-generated_cs.png){align="left"}

   若要檢視輸出，請關閉&#x200B;**產生的輸出**&#x200B;對話方塊，並在預設頁面上選取&#x200B;**檢視輸出**。


   >[!NOTE]
   >
   > 您也可以從「選項」選單中「重新命名」、「複製」或「刪除」現有的輸出預設集。


**父級主題：**[&#x200B;使用編輯器](web-editor.md)
