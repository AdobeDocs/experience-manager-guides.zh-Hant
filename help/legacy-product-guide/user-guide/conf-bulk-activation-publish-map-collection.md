---
title: 啟動輸出
description: 在AEM Guides中啟動DITA map的輸出。 瞭解如何在發佈執行個體上啟用您的內容。
feature: Publishing, Bulk Activation
role: User
hide: true
exl-id: de1fd057-60c6-4b1a-9e55-f32969eb0079
TQID: https://experienceleague.adobe.com/DjyZb6keMyvxaRF39lD1-xsugNBJPxP-WqfNnMEU-T4
product_v2:
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: a3bd6397-2eb2-4908-a61c-226e26855dca
subfeature_v2:
  - id: c38bc65b-dea9-4a6e-9de3-3daf1d2b388b
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 449
ht-degree: 2%

---

# 啟動輸出 {#id214GGF00V5U}

當您建立了大量啟動的地圖集合後，下一步是在發佈執行個體上啟動您的內容。 若要啟用內容，請執行下列步驟：

1. 從工具清單中選取&#x200B;**指南**。

1. 按一下頂端的Adobe Experience Manager連結，然後選擇&#x200B;**工具**。

1. 按一下&#x200B;**大量發佈儀表板**&#x200B;圖磚。

   此時會顯示大量啟用地圖集合清單。

1. 選取您要發佈的集合，然後按一下&#x200B;**開啟**。

   ![](images/bulk-activation-collection-open.png){width="800"}

1. \（*選擇性*\）從左側邊欄套用必要的篩選器，以根據其修改的\(status\)、輸出預設集或語言來篩選對映。

   >[!NOTE]
   >
   >在啟動地圖集合中的輸出預設集之前，使用輸出預設集產生地圖的輸出。


根據您的設定，檢視啟用集合的不同方式。

<details>
<summary> 雲端服務 </summary>

在雲端服務上![大量集合 — 發佈](images/bulk-activation-collection-quick-publish-CS.png){width="650"}

您可以啟動輸出至&#x200B;**預覽**&#x200B;或&#x200B;**發佈**&#x200B;執行個體。

**預覽**

* 若要啟用選取的地圖的輸出，請選取預先產生的地圖輸出，然後選取&#x200B;**發佈至** > **預覽**。
* 若要啟用所有DITA map及其設定之預設集的輸出，請選取&#x200B;**Map**&#x200B;欄旁的核取方塊，然後選取&#x200B;**發佈至** > **發佈**。


**發佈**

* 若要啟用選取的地圖的輸出，請選取預先產生的地圖輸出，然後選取&#x200B;**發佈至** > **發佈**。

* 若要啟動所有DITA map及其設定之預設集的輸出，請選取Map （欄）旁的核取方塊，然後選取&#x200B;**發佈至** > **發佈**。


>[!NOTE]
> 
> 只有在您為地圖產生輸出時，才會啟用地圖輸出的核取方塊。

將地圖輸出排入發佈佇列時，會顯示成功訊息。

一旦為所選對映檔案啟動輸出後，稽核歷史記錄標籤即會更新，並且最新啟動的輸出會顯示在最上方。 **已發佈**&#x200B;欄已更新為發佈日期和時間。

</details>

<details>    
<summary>  內部部署軟體 </summary>


執行下列任一項作業：

* 若要啟動選取的地圖的輸出，請選取預先產生的地圖輸出，並選取&#x200B;**快速發佈**。
* 若要啟動所有DITA map及其設定之預設集的輸出，請選取[對應] （欄）旁的核取方塊，然後選取[快速發佈]。**&#x200B;**
  ![大量集合 — 發佈](images/bulk-activation-collection-quick-publish.png){width="650"}

  >[!NOTE]
  > 
  >只有在您為地圖產生輸出時，才會啟用地圖輸出的核取方塊。


將地圖輸出排入發佈佇列時，會顯示成功訊息。

一旦為所選對映檔案啟動輸出後，稽核歷史記錄標籤即會更新，並且最新啟動的輸出會顯示在最上方。 **已發佈**&#x200B;欄已更新為發佈日期和時間。

**父級主題： &#x200B;** [大量啟用已發佈的內容](conf-bulk-activation.md)
