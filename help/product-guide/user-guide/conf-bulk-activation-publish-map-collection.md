---
title: 啟動輸出
description: 在AEM Guides中啟動DITA map的輸出。 瞭解如何在發佈執行個體上啟用您的內容。
exl-id: 4da644b9-8c5f-4976-a212-960085b693b8
feature: Publishing, Bulk Activation
role: User
source-git-commit: 66d22560d40012a7475026ed44cec7bf301c1a97
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 1%

---

# 啟動輸出 {#id214GGF00V5U}

當您建立了大量啟動的地圖集合後，下一步是在發佈執行個體上啟動您的內容。 若要啟用內容，請執行下列步驟：

1. 選取 **指南** 工具清單中。

1. 按一下頂端的Adobe Experience Manager連結，然後選擇 **工具**.

1. 按一下 **大量發佈儀表板** 圖磚。

   此時會顯示大量啟用地圖集合清單。

1. 選取您要發佈的集合，然後按一下 **開啟**.

   ![](images/bulk-activation-collection-open.png){width="800" align="left"}

1. \(*可選*\)從左側邊欄套用所需的篩選器，以根據篩選對映的修改\(status\)、輸出預設集或語言。

   >[!NOTE]
   >
   >在啟動地圖集合中的輸出預設集之前，使用輸出預設集產生地圖的輸出。


根據您的設定，檢視啟用集合的不同方式。

<details>
<summary> 雲端服務 </summary>

![雲端服務上的bulk-collection-publish](images/bulk-activation-collection-quick-publish-CS.png){width="650" align="left"}

您可以將輸出啟動至 **預覽** 或 **發佈** 執行個體。

**預覽**

* 若要啟動所選地圖的輸出，請選取預先產生的地圖輸出，然後選取 **發佈至** > **預覽**.
* 若要啟動所有DITA map及其已設定預設集的輸出，請選取 **地圖** 欄，然後選取 **發佈至** > **發佈**.


**發佈**

* 若要啟動所選地圖的輸出，請選取預先產生的地圖輸出，然後選取 **發佈至** > **發佈**.

* 若要啟動所有DITA map及其設定預設集的輸出，請選取「對應」（欄）旁的核取方塊，然後選取 **發佈至** > **發佈**.


>[!NOTE]
> 
> 只有在您為地圖產生輸出時，才會啟用地圖輸出的核取方塊。

將地圖輸出排入發佈佇列時，會顯示成功訊息。

一旦為所選對映檔案啟動輸出後，稽核歷史記錄標籤即會更新，並且最新啟動的輸出會顯示在最上方。 此 **已發佈** 欄會以發佈日期和時間更新。

</details>

<details>    
<summary>  內部部署軟體 </summary>


執行下列任一項作業：

* 若要啟動所選地圖的輸出，請選取預先產生的地圖輸出，然後選取 **快速發佈**.
* 若要啟動所有DITA map及其設定預設集的輸出，請選取「對應」（欄）旁的核取方塊，然後選取 **快速發佈。**
  ![bulk-collection-publish](images/bulk-activation-collection-quick-publish.png){width="650" align="left"}

  >[!NOTE]
  > 
  >只有在您為地圖產生輸出時，才會啟用地圖輸出的核取方塊。


將地圖輸出排入發佈佇列時，會顯示成功訊息。

一旦為所選對映檔案啟動輸出後，稽核歷史記錄標籤即會更新，並且最新啟動的輸出會顯示在最上方。 此 **已發佈** 欄會以發佈日期和時間更新。

**父級主題： **[大量啟用已發佈的內容](conf-bulk-activation.md)
