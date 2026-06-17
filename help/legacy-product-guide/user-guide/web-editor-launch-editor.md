---
title: 啟動網頁編輯器
description: 瞭解如何從AEM Guides的AEM導覽頁面、AEM Assets UI和DITA Map主控台啟動網頁編輯器。
feature: Authoring, Web Editor
role: User
hide: true
exl-id: 374042e4-0f1c-44cf-926c-c9fefa4b1de0
TQID: https://experienceleague.adobe.com/O-rew8ysArVVeDpj3T7oEi-hEg-phDWzb85gD2l-9gQ
product_v2: id: fae5e35a-80c9-4b94-9352-1a060a6aab1did: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: ab01a588-7dea-43f2-a699-0b3f128465d6
subfeature_v2: id: ad602516-aca3-4247-9ae8-f393d958efa9id: f89f75b0-cf2e-4e96-aec8-fe8c39cbd0ef
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 592
ht-degree: 0%

---

# 啟動網頁編輯器 {#id2056B0140HS}

您可以從下列位置啟動Web編輯器：

- [AEM導覽頁面](#id2056BG00RZJ)
- [AEM ASSETS UI](#id2056BG0307U)
- [DITA map主控台](#id2056BG090BF)

以下小節涵蓋如何從不同位置存取和啟動Web編輯器的詳細資訊。

## AEM導覽頁面 {#id2056BG00RZJ}

登入AEM時，畫面會顯示導覽頁面：

![](images/web-editor-from-navigation-page.png){width="800"}

按一下&#x200B;**Guides**&#x200B;連結，即可直接前往網頁編輯器。

![](images/web-editor-launch-page.png){width="800"}

當您未選取任何檔案就啟動網頁編輯器時，會顯示空白的網頁編輯器畫面。 您可以開啟檔案，以從AEM存放庫或「我的最愛」集合進行編輯。

- 按一下&#x200B;**指南**&#x200B;圖示(![](images/aem-guides-icon.png))以返回AEM導覽頁面。

- 根據您的設定，**關閉**&#x200B;按鈕會帶您前往目的地：



  <details>

  <summary> 雲端服務 </summary>

  如果您正在使用雲端服務，請按一下&#x200B;**關閉**&#x200B;按鈕以返回AEM導覽頁面。
  </details>

  <details>

  <summary> 內部部署軟體</summary>

  如果您使用AEM Guides內部部署軟體（4.2.1和更新版本），請按一下右側的&#x200B;**關閉**&#x200B;按鈕，返回至Assets UI中的目前檔案路徑。

  </details>

## AEM ASSETS UI {#id2056BG0307U}

另一個可以啟動Web編輯器的位置來自AEM Assets UI。 您可以選取一或多個主題，並直接在網頁編輯器中開啟它們。 若要在Web編輯器中開啟主題，請執行下列步驟：

1. 在Assets UI中，導覽至您要編輯的主題。

   >[!NOTE]
   >
   > 您也可以檢視主題的UUID。

   .

   ![](images/assets_ui_with_uuid_cs.png){width="800"}

   >[!IMPORTANT]
   >
   > 確保您對包含要編輯之主題的資料夾具有讀取和寫入許可權。

1. 若要取得該主題的獨佔鎖定，請選取該主題，然後按一下[出庫]。****

   >[!IMPORTANT]
   >
   > 如果您的管理員已設定&#x200B;**停用編輯而不簽出**&#x200B;選項，則您必須先簽出檔案才能進行編輯。 如果您未出庫檔案，將無法看到編輯選項。

1. 關閉資產選擇模式，然後按一下您要編輯的主題。

   主題預覽隨即顯示。

   您可以從「清單」檢視、「卡片」檢視和「預覽」模式開啟Web編輯器。

   >[!IMPORTANT]
   >
   > 如果您想要開啟多個主題進行編輯，請從資產UI中選取所需的主題，然後按一下編輯。 請確認您的瀏覽器未啟用快顯封鎖程式，否則只會開啟所選清單中的第一個主題進行編輯。

   ![](images/edit-from-preview_cs.png){width="800"}

   如果您不想預覽主題，並想直接在網頁編輯器中開啟主題，請從卡片檢視按一下快速動作功能表中的「編輯」圖示：

   ![](images/edit-topic-from-quick-action_cs.png){width="800"}

1. 按一下&#x200B;**編輯**，在網頁編輯器中開啟主題。

   ![](images/edit-mode.png){width="800"}


## DITA map主控台 {#id2056BG090BF}

若要從DITA map主控台開啟Web編輯器，請執行下列步驟：

1. 在Assets UI中，導覽至並按一下包含您要編輯之主題的DITA map檔案。

   將顯示DITA map主控台。

1. 按一下&#x200B;**主題**。

   隨即顯示地圖檔案中的主題清單。 主題的UUID會顯示在主題標題下方。

1. 選取要編輯的主題檔案。

1. 按一下&#x200B;**編輯主題**。

   ![](images/edit-topics-map-console_cs.png){width="800"}

1. 主題會在Web編輯器中開啟。

   >[!IMPORTANT]
   >
   > 如果您的管理員已設定&#x200B;**停用編輯而不簽出**&#x200B;選項，則您必須先簽出檔案才能進行編輯。 如果未出庫檔案，則檔案會在編輯器中以唯讀模式開啟。


**上層主題：**[&#x200B;使用網頁編輯器](web-editor.md)
