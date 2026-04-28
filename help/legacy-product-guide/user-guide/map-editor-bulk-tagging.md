---
title: 大量標籤DITA內容
description: 在AEM Guides中使用大量內容標籤來改善DITA內容可發現性。 瞭解如何在單一或多個主題上套用、移除、顯示或隱藏大量標籤。
feature: Metadata Management
role: User
hide: true
exl-id: b320e34f-ee0a-4cc3-b4f6-d322fbb29844
source-git-commit: a70b3ce942b3e69445ad1d7ba6c8f7542e0ff176
workflow-type: tm+mt
source-wordcount: '716'
ht-degree: 0%

---

# 大量標籤DITA內容 {#id179SG0TN05Z}

標籤可讓您對內容存放庫及已發佈輸出中的內容進行分組或分類。 如果您已在內容上套用標籤，即可輕鬆地在DITA map中尋找可協助您編寫內容的相關主題。 透過已發佈的輸出，使用者將可透過適當的標籤更快找到所需內容。

AEM Guides可讓您按幾下滑鼠，標籤DITA內容。 您可以使用大量標籤功能，在多個主題、DITA map或子對映上套用多個標籤。 或者，您也可以在個別主題上套用標籤。 標籤是AEM的原生功能，您可以在AEM檔案的[管理標籤](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/authoring/features/tags.html?lang=zh-Hant)章節中找到有關建立和管理標籤的更多詳細資料。

依預設，AEM Guides不會將「讀取」存取權授與資料夾（AEM存放庫中的所有標籤皆儲存於此資料夾）上的任何使用者。 若要使用AEM存放庫中定義的標籤，您必須要求系統管理員授與標籤儲存所在資料夾的存取權。

## 套用大量標籤

使用大量標籤功能，一次套用多個標籤。 執行以下步驟，將標籤套用至DITA map中的主題：

1. 在Assets UI中，導覽至DITA map檔案並按一下。

   DITA map主控台隨即出現，顯示可用於產生輸出的輸出預設集清單。

1. 按一下&#x200B;**主題**。

   將顯示DITA map中可用的主題清單。 主題的UUID會顯示在主題標題下方。

1. 選取您要套用標籤的主題或子對應。

   ![](images/apply-tags-uuid.png){width="650" align="left"}


   >[!NOTE]
   >
   > 上面的熒幕擷圖顯示選取和展開的子地圖。 選取子地圖時，也會選取子地圖下的所有主題。

1. 按一下&#x200B;**套用標籤**。

   「選取標籤」對話方塊隨即顯示。

1. 選取一或多個要套用至所選主題的標籤。

1. 確認您的選取。

   選取的標籤會套用到主題，並顯示在主題標題旁邊。

   >[!NOTE]
   >
   > 將標籤新增至主題後，如果您移動或刪除主題，這些主題的標籤也會被移除。 不過，該主題會保留在地圖中，直到您將其移除為止。


## 在個別主題上套用標籤

執行以下步驟，將標籤套用至個別主題：

1. 在Assets UI中，導覽至並選取您要套用標籤的主題檔案。

1. 在工具列中按一下&#x200B;**屬性**。

   主題的特性頁面隨即顯示。

1. 在「基本」標籤中，按一下&#x200B;**標籤**&#x200B;欄位旁的「瀏覽」圖示。

1. 選取一或多個要套用至所選主題的標籤。

1. 確認您的選取。

1. 按一下&#x200B;**套用標籤**。

   選取的標籤會套用到主題，並顯示在「標籤」欄位中。

1. 按一下「**儲存並關閉**」。


## 移除標記

根據您的業務需求，您可以變更任何DITA主題的標籤資訊。 您可以輕鬆一次移除所有標籤，或僅移除主題上無效的標籤。

執行以下步驟，從一個或多個主題中移除所有標籤：

1. 在Assets UI中，導覽至DITA map檔案並按一下。

   DITA map主控台隨即出現，顯示可用於產生輸出的輸出預設集清單。

1. 按一下&#x200B;**主題**。

   將顯示DITA map中可用的主題清單。

1. 選取您要移除標籤的主題。

1. Click **Remove Tags**.

   >[!NOTE]
   >
   > If the Delete Tags icon is not visible, ensure that you have not enabled the Hide Tags feature.

1. On the Confirm Delete dialog, click **OK** to remove tags from the selected topics.


## Show or hide tags

If you have a long list of tags applied on your topics, then you might find it a bit cumbersome to navigate. You can easily hide tags in from your DITA map console view by clicking on the Hide Tags icon. Similarly, when the tags are not visible, clicking on the Show Tags reveals all tags.

**Parent topic:**&#x200B;[&#x200B; Manage metadata](manage-metadata.md)
